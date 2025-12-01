___

## Profiling

We want to accelerate our code, by using techniques like:
- Multithreading
- GPU
- ...

Increase of resources does not equal to better efficiency.


We can do profiling or tracing:
- Profiling is the act of measuring the properties of an application by __summarizing__ a set of events over the execution interval.
- Tracing is the act of recording the stream of the events to provide additional informantion on where and when it itakes place during the execution.

Results depend on the test case chosen.

## Size

The amount of events monitored influences the report size.

This is particularly important when tracing, because it takes more disk.

So we should never start by tracing.

Measurements affects performances:
- Overhead.
- Perturbation.
- Accuracy.

Focus measurements on a set of events:
- Time
- Memory
- ...

Identify a suittable test case for this set.

Apply filters.

## Performance factors and metrics

For sequential:
- Vectorization
- LX cache misses, hints.
- I/O volume

For parallel:
- Workload decomposition (suddivide the work)
- Communications
- Amount of serial work
- Synchronization

### Metrics

Profiling:
- Time
- Counts (visits) to the CPU
- Bytes transferred
- HW counters.

Tracing:
- Timestamp
- Communicator

## Reports

Profiles performance metrics are summarized over the program execution time.

The difference between exclusive and inclusive time is:
- Inclusive is the time including the time of the children.

Flat profile

Call graph

Traces result can be visualized using a cartesian plot:
- Location on the $Y$ axis
- Time on the $X$ axis

## Measurement techniques

### Instrumentation

Special code is added at the beginning and the end of functions to measure an event.

Probe are used, they are similar to clocks.

There are two kinds of instrumentation:
- Source-code modifiers: intrusive, need to recompile the code.
- Binary profilers:

Sampling and instrumentation

Instrumentation is better suited for irregular code.

Cpu time and wall time

