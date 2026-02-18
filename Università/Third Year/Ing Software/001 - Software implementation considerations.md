___

I'll compare the two directories to identify the changes. Let me examine both folders and their key files.

I can see that 2000 has two new files: channels.h and msg.h. Let me compare the main files to understand the architectural changes.

Now let me compare the sender and receiver implementations:

Based on my comparison, here are the key changes between 1000 and 2000:

Major Architectural Changes:
1. New Message and Channel Infrastructure
Added msg.h: Defines two message types (Msg1 and Msg2) with structured data
Msg1: contains counter
Msg2: contains counter and amount
Added channels.h: Defines two channel classes (Channel1 and Channel2) that contain message queues
2. Communication Model Refactoring
Version 1000 (Direct coupling):

Components had direct queue\<int> and Msg y members
System connected components via direct queue pushes in connect() method
Output stored in component's y member variable
Version 2000 (Channel-based):

Components hold pointers to shared Channel objects
Channels are created in System constructor and passed to components via init()
Components push/pop directly to/from shared channels
Removed connect() method entirely
Removed set_output() from System (now called internally by components)
3. Sender Changes
Input: queue\<int> q → Channel1 \*ChIn
Output: Msg y → Channel2 \*ChOut
init() now takes channel pointers as parameters
set_output() is now private and called internally (pushes to ChOut)
Updates message directly to output channel
4. Receiver Changes
Input: queue \<Msg> q → Channel2 \*ChIn
Output: int y → Channel1 \*ChOut
Now sends messages back via set_output() which pushes Msg1 to channel
Processing logic changed from x = 1 or 0 to x = ceil(m.amount) or floor(m.amount)
5. System Simplification
Added channel creation (Ch1, Ch2) in constructor
Removed connect() method (channels provide direct connection)
Removed set_output() method (components handle their own output)
init() passes channel references to components
Summary: Version 2000 introduces a more modular, decoupled architecture using explicit channel objects and structured messages, replacing the direct queue-to-queue coupling of version 1000.

___

The files look very similar. Let me do a more detailed comparison of the Sender's [next_state](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html) method since that's where I noticed a difference:

Perfect! Now I can see the key difference. Let me check the commons.h and any other potential differences:

Based on my comparison, here are the **changes from 2000 to 3000**:

## Key Change: Sender Behavior Modification

### **Sender's [next_state()](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html) Logic** - Critical behavioral change:

**Version 2000**:

```cpp
void Sender::next_state(double present_time) {

  if ( (present_time < time) || (ChIn -> q.empty()) )

    // toot early or queue is empty: do nothing

    { return; }

  

  // queue is not empty and present_time >= time

  x++;

  ChIn -> q.pop();

  set_output();

}
```

- **Requires** input queue to be non-empty to update
- Only updates when both conditions met: time reached AND queue has message

**Version 3000**:
```cpp
void Sender::next_state(double present_time) {

  if (present_time < time)

    // too early

    { return; }

  

  // queue update counter

  x++;

  if (!(ChIn -> q.empty()))

    // queue is not empty: dequeue

    { ChIn -> q.pop(); }

  set_output();

}
```

- **Always** updates when time is reached (regardless of queue state)
- Conditionally dequeues only if queue is not empty
- Counter increments and output is generated even with empty input queue

## Summary:

**Version 3000** makes the Sender more **autonomous** - it will continue updating its counter and sending messages periodically even without receiving input messages from the Receiver. In Version 2000, the Sender would block if the input queue was empty.

This is a **fundamental behavioral change** in the feedback loop dynamics between Sender and Receiver, making the system more resilient to message delays or losses.

___

Based on my comparison, here are the **changes from 3000 to 4000**:

## Major Change: Introduction of State Machine (Scheduler) Pattern

### **1. Sender: State Machine Implementation**

**New State Variable**:

- Added [int sck](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html) (scheduler) to track component state
- Initialized to `0` in [init()](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html)

**Modified [set_time()](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html) Logic**:

```cpp
// Version 4000

if (ChIn -> q.empty()) {

    sck = 0;  // idle/waiting state

    time = time + 1;    

} else {

    sck = 1;  // active/processing state

    time = time + 10 + 10*(*(p -> ptr_UnifRealDist))(p -> RandomEngine);

}
```

- Now explicitly sets scheduler state based on queue status

**Refactored [next_state()](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html)**:

```cpp
switch (sck) {

case 0:  // busy waiting, do nothing

    busy_waiting(present_time);

    break;

case 1:

    thread1(present_time);

    break;

default:

    fprintf(stderr, "sender.nextstate: error sck\n");

    exit(1);

}
```

**New Private Methods**:

- [busy_waiting(double present_time)](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html) - handles idle state (does nothing)
- [thread1(double present_time)](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html) - handles active state (contains previous logic: increment counter, dequeue, set output)

### **2. Receiver: Timing Behavior Change**

**Modified [set_time()](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html)**:

```cpp
// Version 3000: conditional timing

if (ChIn -> q.empty()) {

    time = time + 1;    

} else {

    time = time + 10 + 10*(...);

}

  

// Version 4000: unconditional timing

time = time + 10 + 10*(*(p -> ptr_UnifRealDist))(p -> RandomEngine);
```

- **Always** uses the longer random delay (10 + 10*rand)
- No longer adjusts timing based on queue state
- Previous conditional code commented out with `#if 0`

## Summary:

**Version 4000** introduces a **formal state machine architecture** to the Sender using a scheduler variable ([sck](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html)), separating idle and active behaviors into distinct methods. The Receiver becomes **time-independent of its input queue status**, always using the same timing pattern. This makes the code more structured and maintainable, following a clearer finite state machine pattern.

___

## **Description of 5000-customer-server**

This is a **discrete-event simulation** of a **customer-server supply chain system** with inventory management.

### **Architecture:**

**Components:**

1. **Customer** - Places orders and receives deliveries
2. **Server** - Processes orders and manages inventory storage

**Communication Channels:**

- [ChOrd](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html) (Channel for Orders): Customer → Server
- [ChDel](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html) (Channel for Deliveries): Server → Customer

**Message Types:**

- [OrderMsg](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html): `{item, amount}` - customer order requests
- [DeliveryMsg](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html): `{item, amount}` - server delivery responses

### **Customer Behavior (Multi-threaded):**

**Thread 0 - Send Orders** (period ~10 time units):

- Randomly selects 1 of 10 items ([NUM_ITEMS = 10](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html))
- Orders random amount (1-6 units)
- Tracks pending orders in [orders[]](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html) array
- Pushes [OrderMsg](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html) to output channel

**Thread 1 - Check Deliveries** (period ~5 time units):

- Checks input channel for deliveries
- Decrements [orders[]](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html) when delivery received
- Processes one delivery per activation

### **Server Behavior (Multi-threaded):**

**Initial State:**

- Storage initialized with 100-200 units per item (random)

**Thread 0 - Process Deliveries** (period ~3 time units):

- Checks order queue
- Fulfills order up to available storage: [MIN(storage[item], ordered_amount)](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html)
- Updates storage: [storage[item] -= delivered_amount](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html)
- Sends [DeliveryMsg](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html) back to customer

### **Key Features:**

1. **Asynchronous Communication** - Channels decouple sender/receiver timing
2. **Multi-threaded Components** - Each has independent periodic activities
3. **Inventory Constraint** - Server can only deliver what's in stock
4. **Timing with Noise** - `period * (1 + 0.05 * uniform(-1,1))` adds variability

___

Based on my comparison, here's the **change from 5100 to 5200**:

## Key Change: Conditional Inventory Replenishment Policy

### **Server's [supply()](vscode-file://vscode-app/c:/Users/Arielxbp/AppData/Local/Programs/Microsoft%20VS%20Code/_/resources/app/out/vs/code/electron-browser/workbench/workbench.html) Method**

**Version 5100** - Unconditional restocking:

```cpp
void Server::supply(double present_time) {

    // schedule supply

    thtime[1] = thtime[1] + ptime[1]*(1 + noise());

    // set storage

    for (i=0; i < NUM_ITEMS; i++) {

        storage[i] = storage[i] + 10*(*(p -> ptr_UnifRealDist))(p -> RandomEngine);

    }

}
```

- Adds 0-10 units to **ALL items** every period
- No consideration of current stock levels

**Version 5200** - Threshold-based restocking:

```cpp
void Server::supply(double present_time) {

    // schedule supply

    thtime[1] = thtime[1] + ptime[1]*(1 + noise());

    // set storage

    for (i=0; i < NUM_ITEMS; i++) {

        if (storage[i] <= 50)

            {storage[i] = storage[i] + 20*(*(p -> ptr_UnifRealDist))(p -> RandomEngine);}

    }

}
```

- **Only restocks items with inventory ≤ 50 units**
- Adds 0-20 units (2x larger replenishment than 5100)
- Implements a "reorder point" inventory policy

---

## Summary:

**Version 5200** introduces **smarter inventory management**:

1. **Conditional replenishment**: Only orders supply when stock is low (≤ 50 units)
2. **Larger order quantities**: 0-20 units vs 0-10 units when restocking
3. **Efficiency improvement**: Avoids overstocking, focuses resources on depleted items

This models a more realistic **just-in-time (JIT) or reorder point** inventory control system, where replenishment is triggered by low stock levels rather than happening unconditionally.

___

