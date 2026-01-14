___

Cybersecurity is the prevention of damage to computers, electronic communication systems and services, including the information contained inside them.

# Computer Security

It's a set of measures and controls that ensure:
- Confidentiality.
- Integrity.
- Availability.
for information system's __assets__.

## Assets

An asset is something that is important for a person, a company or an institution, that wants it to be protected.

### Types of assets

These assets can be:
- Hardware.
- Software.
- Firmware.
- Stored information.
- Information being processed and communicated.

For example:
- Staff address book.
- Patient records.
- Equipments.
- Criminal records.
- Keys for net-banking.

## Computer Security Challenges

When developing a security mechanism or algorithm:
- We must always consider a potential attack on these features.

Security requires a regular and constant monitoring in order to function.

Most of security mechanisms involve entities to be in possession of some type of secret information:
- We also need to securely create it, distribute it and protect it.

Generally many users see strong security as an obstacle to efficiency and user-friendliness of a system.

Also they seem to perceive little benefits until a security break occurs.

# Key Security Concepts (CIA)

__Confidentiality__ is the concept of:
- Putting restrictions on information access and disclosure to ensure it is not made available to unauthorized individuals.
This is done in order to protect personal privacy and proprietary information.

__Integrity__ is the concept of:
- Maintaining the accuracy and trustworthiness of data.
- Ensuring information nonrepudiation and authenticity.
This is done by protecting the data from unauthorized modification or destruction.
This ensure that the data is:
- complete.
- reliable.
- authentic.
- nonrepudiable, preventing the denying of one's actions and responsabilities.

__Availability__ is the concept of:
- Ensuring quick and reliable access to information and its usage.

## Additional Security Concepts

__Authenticity__ is the concept of:
- Some information having the property of being __genuine__ and able to be __verified and trusted__.
- Being confident that a transmission, message or sender is valid.
	- This means verifying that users are who they say they are and that each input arriving came from a trusted source.

__Accountability__ is the concept of:
- Ensuring that every action done by an entity can be traced uniquely to that entity.
This supports:
- Nonrepudiation, ensuring that an individual cannot deny having performed a specific action.
- Fault isolation, because we can trace back uniquely the source that caused the fault.
- Intrusion detection and prevention.
- After-action reconvery.
- Legal action through forensic analysis.

# Confidentiality

It's the concept that describes the __avoidance__ of unauthorized disclosure of information.

Meaning that a system to be confidential, needs to prevent unauthorized access to information.

It contains two other related concepts:
- __Data confidentiality__, which assures that private or confidential information is __not__ made available or disclosed to unauthorized people. (It's the same thing)
- __Privacy__, which assures that individuals can control what information related to them may be collected and stored by others.

## Tools for Confidentiality

### Encryption keys

We can use the concept of __encryption__ to implement confidentiality.

This is done usually by using a secret __encryption key__, that transform information so that it can only be read using another secret __decryption key__.

In some cases the decryption key is the same as the encryption key.

### Access control

__Access control__ is another way to implement confidentiality.

It describes rules and policies that limit access of confidential information.

So access to information is limited only to those people that need to access it.
- E.g. The manager needs to have access to the list of salaries of his employees.
- E.g. A janitor does not need to have access to the student's database.

### Authentication

__Authentication__ is used to determine the identity or role that someone has.
- E.g. All the login pages we use to enter our accounts are authentication tools.

So it's the process of __verifying a user__.

### Authorization

__Authorization__ is used to determine if a person or system is allowed access to resources, based on an access control policy.

So it's the process of __determining what an authenticated user is allowed to access__.

### Physical security

__Physical security__ is used to __limit access__ to protected physical resources.
- E.g. Putting locks on doors.

# Integrity

It's the property that something has not been altered in an unauthorized way.

It contains two related concepts:
- __Data integrity__, which assures that information and programs are only changed in a specified and authorized way.
- __System integrity__, which assures that a system's functions are working correctly, not being modified by unauthorized entities.

## Tools for Integrity

Tools used for checking the integrity of information are:
- __Backups__.
- __Checksums__, are functions that given a file, computes a distinct numerical value.
- __Data correcting codes__, are methods for storing data in a way that small changes can be easily detected and automatically corrected.

# Availability

It's the property that something is accessible and modifiable in a expected time by those authorized to do so.

## Tools for Availability

Tools used for availability are:
- __Physical protections__, so infrastructure that keep information available even during unpredicted challenges.
	- E.g. When there is a power outage, a backup electric generator gets activated.
- __Computational redundancies__, so computers and storage devices that serve as fallbacks/redundancies in the case of failure of the main ones.
	- E.g. Using RAID technology on a system.

# Other Security Concepts

## Authenticity

It's the ability to determine that statements, policies and permissions issued by an entity 
 are __genuine__ and can be verified. 
 
The primary tool used for this is:
- __Digital signatures__, that allow a person/system to commit to the authenticity of their documents.
	- This also achieves __non-repudiation__.

## Accountability

It's the concept of:
- Ensuring that every action done by an entity can be traced uniquely to that entity.

This supports:
- Nonrepudiation, ensuring that an individual cannot deny having performed a specific action.
- Fault isolation, because we can trace back uniquely the source that caused the fault.
- Intrusion detection and prevention.
- After-action reconvery.
- Legal action through forensic analysis.

## Anonymity (Standalone - Not included in the big 5s)

It's the property that certain records or transactions are not to be attributable to any individual.

Tools used to provide anonymity are:
- __Aggregation__, so combining data from many so that it cannot be tied to any individual.
- __Proxies__, trusted agents that do actions on behalf of others, so they cannot be traced back.
- __Pseudonyms__.
- __Mixing__ data of multiple resources.

# Vulnerabilities, Threats, Attacks and consequences

![|500](https://i.imgur.com/r6sxc79.png)

## Vulnerabilities

A vulnerability is a __weakness__ in an information system, system security procedures, controls, or implementation that could be __exploited__ or triggered by a threat agent (an attacker).

There are various categories of vulnerabilities:
- Corruption.
- Leaks.
- Unavailable/very slow.

The corruption of data will cause a loss of __integrity__.

A leak of information will cause a loss of __confidentiality__.

When information are unavailable or very slow to access, this will lead to a loss of __availability__.

## Threats

A threat represents a __potential security harm__ to an asset, that is able to exploit a vulnerability.

## Attacks

An attack is a __threat__ that is __being carried out__.

These can be:
- __Passive__, like an attempt to learn or make use of information from the system, that does not affect the system's resources.
- __Active__, like an attempt to __alter__ system resources or affect their operations.

So the difference is if it __affect the resource or not__.

Like if the attacker is just eavesdropping or monitoring the transmission of resources, that is a passive attack, because it is not modifying that resource.

While if it modifies the data stream or it creates a false stream, that is an active attack.

Attacks are also classified based on the __origin__ of the attack:
- __Insider__, so someone who is inside the security perimeter, that is authorized to access system resources.
- __Outsider__, so someone who is from outside the perimeter.

## Risk

It is a measure that indicates how much an entity is threatened by a potential attack.

Its value is based on:
- How much impact would arise if the attack happens.
- Likelihood of occurrence.

## Threat consequences

If a threat turns into a successful attack, the consequences can vary.

__Unauthorized disclosure__: threat to __confidentiality__.
- Happens when the attacker __intecepts__ traveling data.
- Happens when the attacker __intrudes__ inside the system through a security protection hole.
- Happens when the attacker __inferences__ some data by reasoning using other secondary data.

__Deception__: threat to either system or data __integrity__.
- One can be __masquerading__ (impersonating) as another entity to gain access or performing actions using the permissions of the impersonated entity.
- __Falsification__ of data that seems to be from someone who is not actually the author.
	- E.g. The man-in-the-middle attack, that intercepts, modifies and retransmits the intercepted data.

__Disruption__: threat to __availability__ or system __integrity__.
- The attacker denies everyone from accessing a resource by __incapacitating__ the system in some way. (DDoS)
- By __corrupting__ the system's data or functions.

__Usurpation__: which is a threat to system __integrity__.
- The attacker gains control of a system logically or physically.

# Attack surfaces (Possible subjects of attacks)

When an attacker tries to attack a system, it tries to __exploit__ reachable __vulnerabilities__ within the system.

These vulnerabilities, or __attack surfaces__, are divided into categories:
- __Network__ vulnerabilities (attack surface).
- __Software__ vulnerabilities (attack surface.
- __Human__ vulnerabilities (attack surface).

## Network Attack Surface

Every surface that interacts with the outside (Internet) can be subject to attacks.

In this category we have:
- Network __protocols__ vulnerabilities.
- Various forms of intruder attacks.

## Software Attack Surface

In this category we have:
- Application, utility or operating system vulnerabilities.

## Human Attack Surface

Sometimes authorized users of an system can be exploited to create vulnerabilities.

These type of attacks are generally performed by letting them do something that is going to create a __breach__ in the system's security, so __social engineering__.

# Computer Security Strategy

When developing security strategies, some fundamentals are:
- Security __policies__, these are a set of rules and practices that specify how a system provides security services to protect its resources.
- Security __implementation__, which involves prevention, detection, response and recovery actions.
- __Assurance__, that the system's security policy is enforced during the system's operations.
- __Evaluation__, of the system based on certain criteria.

# Cryptographic concepts

The main technique used for providing __confidentiality__ for trasmitted and stored data is:
- __Symmetric encryption__, also called single-key encryption.

## Symmetric Encryption

This encryption requires:
- A strong encryption __algorithm__.
- That both sender and receiver must have obtained copies of the __secret key__ in a secure way.
- They must keep the key __secure__.

### Diagram of its usage

![|700](https://i.imgur.com/XbkVGWt.png)

Most symmetric encryption algorithms are performed on __blocks of data__ and not on the full plaintext:
1) The input plaintext is divided into fixed block of bits.
2) These blocks are then fed into the algorithm together with the secret key.
3) The output ciphertext is transmitted.
4) The receiver uses the reverse of the encryption algorithm with the same secret key to decrypt the ciphertext into plaintext.

### Symmetric Encryption Attack

An attacker can perform __cryptanalytic attacks__ to try to deduce the secret key being used, based on the characteristics of the algorithm and the texts.
This type of attack relies on:
- The nature of the algorithm.
- Some knowledge about the characteristics of the plaintext alphabet.
- Some sample tuples of (plaintext, ciphertext).

Also __brute-force__ attacks are possible, where the attacker tries __all possible__ keys on some ciphertext until the result plaintext is readable.

### Defences against Attacks

The __size__ of the key is crucial for a successful encrypted data transmission, because even if the encryption algorithm is secure, if the size of the key is small, attackers can brute-force it by trying every possible key.

So to ensure that the encryption is secure, the standard size for a secret key is $128$ bit.

While brute-force attacks are simple, they are mostly ineffective if the key is big enough. 

## Block and stream ciphers

The block cipher:
- Processes the input one block of elements at a time.
- Produces an output block for each input blocks.
- Can reuse keys.
- Is more commonly used.

The stream cipher:
- Processes the input elements continuously.
- Produces output one element at a time.
- The primary advantage against the block cipher is that it is almost always __faster__ and use less code.
- Encrypts plaintext one byte at a time.

## Most known Symmetric Encryption Algorithms

### AES (Advanced Encryption Standard)

The modern standard is __AES__:
- It uses $128$ bit block cipher.
- It can use $128$, $192$ or $256$ bit secret keys.

__Electronic codebook mode__ (ECB) is the simplest approach used to encrypt multiple blocks of data, because:
- For each block of plaintext, it encrypts it using the same key.

But because of this, cryptanalysts may be able to exploit regularities found in the plaintext.

### DES (Data Encryption Standard)

Another algorithm is __DES__:
- It uses $64$ bit block cipher.
- It uses $56$ bit secret keys.

DES is now considered __insecure__, mainly because of the size of the secret keys being only $56$ bit.

#### 3DES

There is a variant of DES, called 3DES:
- It uses $64$bit block cipher.
- It uses $112$ or $168$ bit secret keys.

It basically __repeats__ the basic DES algorithm $3$ times using $3$ unique keys.

Because it computes $3$ times, the algorithm is __slow__, so it's not preffered.

### RC4 (ARCFOUR)

RC4 is an algorithm that:
- Uses a __stream cipher__.
- Uses from $40$ up to $2048$ bits secret keys.

It is also considered insecure for modern standards.

# Message Authentication

The sender always needs to verify that received messages are authentic:
- That the contents have not been modified.
- It's sent from the authentic source.

Encrypting the sent message provides some __confidentiality__, but it does not provide __authenticity__.

To provide authenticity we use __authentication tags__, a piece of data that is related to the message but not reversible to recover the original message.

So now we need algorithms that:
- Encrypts plaintext.
- And create an authentication tag.

## MAC (Message Authentication Code)

Given a message:
1) An algorithm uses the secret key $k$ and the message itself to calculate the message authentication code.
2) The message plus the code are sent to the receiver.
3) The receiver performs the same calculation using the message and the same key $k$ to calculate a new message authentication code.
4) The received code is compared to the newly calculated code.
5) If the key is secure (known only to the sender and receiver), then the codes should match.

If the codes match:
- Then the message has not been modified, because the code is related to the message, so if an attacker modifies the message, then the newly calculated code should be different.
- Then the receiver knows that the sender is verified, because no one else knows the secret key. 

Obviously a MAC algorithm needs to be __irreversible__.

## Cryptographic hash function

A hash function is typically used to produce a __fingerprint__ of a file, message or other block of data.

It generates from an input of $p$ bits an output of $k$ bits fixed in length, where $p\geq k$.

The output is called __hash value__ or __checksum__.

Generally these functions are __non-injective__:
- Meaning that given an output, no other input can result in the same output.

Hash functions do __not__ take a secret key as input. 

### Properties of a hash function for authentication purposes 

A hash function aimed towards authentication usefulness needs to have the following properties:
- Can be applied to a block of data of any size.
- Produces a output fixed in length.
- The function is relatively easy to compute for any input.
- One-way or pre-image resistant, meaning that it is computationally impossible given a known hash value, to find its input.
- Computationally infeasible to find two different inputs such that both output hash value are the same.

### Security of Hash Functions

There are two way two attack a secure hash function:
- Exploiting logical vulnerabilities present in the algorithm.
- Or brute-forcing __if__ the length of the result hash value is relatively small. 

## MAC + Hash function

### Using symmetric encryption

It is possible to get MACs using hash functions:
1) The message is used as the input of the hash function.
2) The hash value is then encrypted using the secret key in a MAC algorithm.
3) The encrypted hash value plus the message are sent to the receiver.
4) The receiver decrypts the encrypted hash value using the same secret key in the algorithm.
5) The receiver also uses the received message as the input of the hash function.
6) The decrypted hash value is compared to the just hashed value from the received message.

### Using public-key encryption

Instead of the secret key, that needs to be secure and known to both the sender and receiver, this can be a __public key__.

This provides:
- A digital signature.
- And it removes the problem of sending both the sender and receiver the same secret key.

## Public-Key Encryption

It's a type of encryption based on __mathematical functions__.

This encryption is __asymmetric__, so it uses two separate keys:
- A public one and a private one for each user.
- The public key is public and is used by others users.
- Both keys need to be able to do both encrypting and decrypting.
- To distribute them some type of protocol is needed.

__RSA__ is one of the most known asymmetric encryption algorithms.

### Encrypting using public key

1) Plaintext plus receiver's __public__ key into the encryption algorithm.
2) Received ciphertext plus receiver's __private__ key into the decryption algorithm.

### Encrypting using private key

1) Plaintext plus sender's private key into the encryption algorithm.
2) Received ciphertext plus sender's public key into the decryption algorithm.

This also implements some form of authenticity because the receiver is able to verify the sender's signature using the sender's public key.

### Uses of public-key cryptosystems

- To provide __digital signatures__.
- To distribute symmetric keys.
- To encrypt secret keys.

### Requirements for public-key cryptosystems

- Pairs of (public key, private key) are computationally easy to create.
- Both key can do both encryption and decryption.
- Computationally impossible for attackers to recover the original message.
- Computationally impossible to get the private key by using the public key.

## Digital Signature

A digital signature is a piece of data that is the result of a cryptographic transformation of data.

It is used to provide:
- Verification of the sender's authentication.
- Checking the integrity of the data.
- Non-repudiation of the sender.

### How to use digital signature

The sender:
1) Sender's message into hash function.
2) Hash value plus sender's private key into a digital signature generation algorithm.
3) The result signature plus message gets sent.

The receiver:
1) Received message into hash function.
2) Hash value plus sender's signature plus sender's public key into a digital signature verification algorithm.
3) The algorithm checks if the signature is valid or not.

### Digital envelope

![|500](https://i.imgur.com/8eaPJlD.png)

In this case we encrypt:
- The message.
- And the symmetric key used to encrypt the message.

# Password Cracking

## John the Ripper

John the Ripper is an open source offline password __security auditing__ (password security check) and password __recovery tool__.

It is used as a password __cracker__ that can brute-force various operating system's passwords.

It uses both the CPU and the GPU to perform its calculations.

### How it works

Given a password hash value and the hash function (algorithm), John will:
- Use every possibile password as input for the given algorithm.
- If the result hash value of a password is the same as the given password hash value.
- Then we have a match, so it cracked the password.

Given a password, __modification rules__ are used to generate similar alternatives to the given password.
- E.g. StrongPassword -> 3tr0ng#passw0rd

### Work modes

John has multiple work modes:
- __Single crack__, uses the login names and other useful strings from the system as possible passwords, plus some default modification rules.
- __Wordlist__ mode, tries a list of passwords for each hash value, also uses modification rules.
- __Incremental__ mode (brute-force), tries __all__ possible characters combination as password.
- __External__ mode, where it uses custom user-made functions that will generate the possible passwords that it tries.

## Rainbow tables

Given a set of passwords, we store all the corresponding hashes in a table called __pre-computed hash table__.

So this table is a dictionary with pairs (hash value, password).

When given a hash value, we search inside the pre-computed table for the password that is the input for the given hash value.

So the base version of the rainbow table is like an alternative brute-force:
- Uses a lot of space but no time.

While the brute-force method needs to compute every hash value:
- Uses a lot of time but no space.

### Hash chains

An alternative rainbow table implementation is by using __hash chains__:
- This will need to compute some hashes but it uses less space.

So it is a __trade-off__:
- Longer chains results in more time used to compute the chains, but less chains are stored.
- More chains results in more space used to store them, but are computed in less time.

#### How it works

It uses a __reduction function__:
- Given a hash value, it computes a string.

This implementation works by computing a chain of hashes and passwords using the hash function and a reduction function:
1) It start from a generated password.
2) The generated password is hashed using the hash function.
3) The result hash value is then used as input for the reduction function.
4) The result string is used as input for the hash function.
5) This is repeated for a fixed number of times.
6) In the end it saves in the table the starting generated password with the last result string of the reduction function.

Given a hash value for which we want to know the password:
1) Use the hash value as input for the reduction function.
2) Find the result string in the table as a last string and get the associated start string.
3) Use the start string to compute the chain.
4) Stop when we find a string that used as input for the hash function returns the given hash value.
5) That string is the password that generates the given hash value.

#### Problems

Hash chains can __loop__.

Hash chains can __merge__, caused by __collisions__.

To fix collisions, we need to use a __sequence__ of reduction functions.

# Authentication

User authentication is the process of __verifying__ a user's claimed identity inside a system.

## Identification and Authentication requirements for protecting data

- Authenticate the identity of an user __before__ granting them access.
- Implementation of __multi-factor__ authentication to access.
- Implementation of __replay-resistant__ authentication to access, so attackers cannot use captured old authentication information (e.g. tokens, password) to access.

## Authentication Architectural Model

![|700](https://i.imgur.com/NRFlaPJ.png)

This model describes what happens when a new user wants to use a service:
- The __subscriber__ is the user.
- The __registration authority__ is responsible for verifying the user's identity when he first signs up.
- The __credential service provider__ is responsible for issuing and managing user credentials.
- The __relying party__ is a service that the user want to login into.
- The __verifier__ is a generally a service that can verify the identity of a subscriber to a service (RP).

### Example of use

A user wants to login to a shopping website, and it can do that by using Google's login system that is implemented inside the website:
- The user firstly creates a Google account, giving informations like name, birthdate and username to Google's RA.
- The RA confirms the user's details and signals to Google's CSP that a new, verified user needs credentials.
- The CSP prompts the user to create a password (and other authentication methods like 2FA)
- Now the user logs into the shopping website and is redirected to the Google login page.
- The user enters his credentials, which are sent to the verifier, that is Google's login service.
- The verifier successfully validates the user's credentials, and it sends an authenticated assertion to the RP, in this case the shopping website.
- The website receives this assertion and grants the user access to the website.

## Methods used to authenticate users

There are four general ways to authenticate an user's identity.

These methods can be used singularly or in combination:
- Something the user __knows__, like a password, PIN or secret aswers.
- Something the user __possesses__, generally tokens, that can be both physical like a key card, or digital like a code inside an authenticator app.
- Something the user __is__, so biometrics, like fingerprints, iris, retina or face.
- Something the user __does__, so dynamic biometrics, like voice pattern, handwriting or a walking style.

The more authentication methods a service uses, the more secure its system becomes.

## Assurance levels for user authentication

Assurance levels indicate how sure a system is about:
- The identity of an user.
- The authentication provided to access.

There are $3$ levels of __identity assurance__ (IAL):
- Level $1$, no need to link the user to a real-life identity. (e.g. An user can be a bot)
- Level $2$, the user's identity needs to be verified using some proof online.
- Level $3$, the user's identity needs to be verified using some proof in-person. (offline/real-life)

There are $3$ levels of __authentication assurance__ (AAL):
- Level $1$, only the ID and password are necessary to access. 
- Level $2$, furthermore also a 2FA is needed.
- Level $3$, furthermore also a more secure 2FA is needed. (It's like the SPID levels)

## Password based authentication

To login, an user needs to have:
- An ID.
- And the password associated with that ID.

The system compares the given password with the one stored for that ID.

And based on the given ID, the system:
- Determines that the user is authorized to access. (Guests cannot access certain features)
- Determines the permissions of the user, what actions inside the system he can perform.

### Password Vulnerabilities

Some of the main ways to attack password-based authentication systems are:

- __Offline dictionary attack__, that is gaining the hashed password file, then using it to compare passwords hashes against hashes of commonly used password.
	- Countermeasure: Prevention of unauthorized access to the password file.

- __Specific account attack__, that is when the attacker submits password guesses until the correct one is discovered.
	- Countermeasure: Lockout mechanism after a number of defined failed login attempts.

- __Popular password attack__, that using a set of popular password on a wide range of accounts.
	- Countermeasure: Policies to negate the creation of accounts with popular password pattern.

- __Password guessing__ against single user, that is when the attacker tries to gain knowledge about the account's user to then try guessing the password based on that knowledge.
	- Countermeasure: Training the users to use difficult to guess passwords and enforcing to change the password every so often.

- __Workstation hijacking__, that is waiting to get physical access to a unattended logged-in workstation.
	- Countermeasure: Automatic logout after a period of inactivity.

- __Exploiting user mistakes__.
	- Countermeasure: Raise user awareness on this topic.

- __Exploiting multiple password use__, that is when the same user uses the same or a similar password on multiple services.
	- Countermeasure: Raise user awareness on account stealing.

- __Electronic monitoring__, that is when a password communicated across a network is eavesdropped by an attacker.

### Social Engineering

Social engineering is a type of attack where by __deceiving__ users of a system the attacker gains access to the system information.

There are many ways to deceive:
- By __pretexting__, so creating a story that convices an administrator to reveal secret information.
- By __baiting__, so giving something in return if an user performs certain actions.

### Password criteria and guidelines

Verifiers and CSPs:
- Shall not impose composition rules. (e.g. requiring forced mixtures of characters types)
- Shall not require users to change passwords periodically.
- Shall not permit the subscriber to store a __hint__ that is accessible to an unauthenticated claimant.
- Shall not prompt subscribers to use knowledge-based authentication or security questions. (e.g "What was the name of you first pet?")
- Shall require passwords to be a minimum of $8$ characters.
- Should require passwords to be a minimum of $15$ characters.
- Should permit a maximum password length of at least $64$ characters.
- Should accept accept all printing ASCII characters and the space character in passwords.

## Tokens

There are various forms of authentication tokens:
- Memory cards.
- Barcodes.
- Magnetic stripe cards.
- Smart cards, with contact and contactless.
- RFIDs.

### Barcodes

A barcode is an image used to encode some type of information.

So they are convenient to use but not secure:
- An attacker can take a photo of the barcode.

### Magnetic Stripe Cards

It's a plastic card that has a magnetic stripe containing personalized information about the card holder.

An attacker can easily read and reproduce a card because:
- Blank cards are cheap to buy.
- Card readers are cheap to buy.
- Card cloners are relatively cheap to buy.

So often card holders need to use another authentication method like a PIN to use their cards.

### Smart tokens

These tokens can be physical or digital devices that securely store cryptographic keys or that generates unique, time-based passcodes.

Physical ones contain an embedded microprocessor.

#### Smart Cards

A smart card contain a microprocessor with:
- Processor.
- Memory.
- I/O ports.

The memory can be of $3$ types:
- __Read-only memory__ (ROM), stores data that does not change during the card's life.
- __Electrically erasable programmable ROM__ (EEPROM), like ROM but can be erased and written again.
- __Random access memory__ (RAM), stores temporary data that is generated when applications are executed.

They are powered by a compatible reader that sends signals that charge for a little bit the microprocessor so that it can send back the information stored inside the memory.

### Electronic Identity Cards (eIDs) (Smart Card for authentication purposes)

These are smart cards that have been __verified__ by the government as __valid__ and __authentic__.

An eID card have many uses:
- As an __ePass__, for biometric identity verification. (Face image, fingerprints)
- As an __eID__, for identification. (Name, birth, address, expiration)
- As an __eSign__, to generate __digital signatures__.

#### Password Authenticated Connection Establishment (PACE)

This feature present on eID cards is used to:
- Make sure that the contactless __RF chip__ in the card cannot be read without the card holder's permission.

### One-time password device (OTP device)

It's a physical device that contains a __secret key__ used to generate OTPs.

Given the secret key plus the time as input into a __hash function__ it generates the OTP.

It has a physical module that protects the secret key from being read.

A system that uses OTP devices to authenticate need to allow some time difference for the generated OTP using it, because the physical device's clock can vary a bit.

## Biometrics

Biometric refers to any method used to uniquely identify a person using their biological or physiological characteristics.

Biometric systems work by:
- Incorporating __sensors__ or __scanners__ to read biometric information.
- Then it compares this information with stored __templates__ of accepted users before granting access.
- This comparison is based on __pattern recognition__.

Its technically complex and expensive when compared to passwords and tokens.

![|500](https://i.imgur.com/8k8imaM.png)

### Biometric accuracy problem

The comparison between the given biometric feature and a reference feature is based on __numerical values__.

If the input value is greater than the __decision threshold__, then it accepts the input, granting access to the user.

So the problem is __how low__ should the threshold be:
- If too low -> more matches, so more __convenient__ -> but more __false__ matches.
- If too high -> more __secure__ -> but less matches, so even the genuine user can fail.


![|500](https://i.imgur.com/1KxnqPe.png)

### Operations of a Biometric Authentication System

There are $3$ operations that a biometric authentication system needs to provide:
- __Enrollment__, registering the user's biometric input plus a PIN.
- __Verification__, checking if the user's biometric input is valid in order to authenticate the user with the given PIN. (Login)
- __Identification__, checking if exists an user with the given biometric input. (Identify user)

## Authentication Security Problems

There are many way to perform an attack to a system's user authentication service:
- Client attacks.
- Host attacks.
- Eavesdropping.
- Replay, repeating a captured secret user authentication information.
- Trojan horse, to capture secret user authentication information.
- Denial of service, to disable a user authentication service.

# Access Control

Access control is a __process that regulates access__ to a system based on that system's security policies.

It's objective is to protect __confidentiality__ and __integrity__ of information.

## Access control models

__Discretionary__ access control (DAC):
- Access is based on the __identity__ of the requesting user and on __authorization rules__ that determines what requestors are allowed to do. (e.g. UNIX systems)

__Mandatory__ access control (MAC):
- Access is based on __comparing__ security __labels__ with security __clearances__. (e.g. Military)

__Role-based__ access control (RBAC):
- Access is based on the __roles__ that users have in the system and on __rules__ that describes what each role can access.

__Attributed-based__ access control (ABAC):
- Access is based on __attributes__ of the user, the __resource__ to be accessed and on the __current environments__.

## Subject, Object and Access Rights

A __subject__ is an entity capable of accessing objects.

An __object__ is a resource to which access is controlled.

__Access rights__ describes the way in which a subject may access an object.

Most common rights are:
- Read, write, execute, delete, create and search.

## Discretionary Access Control (DAC)

In the DAC model, access to an object can be granted by __another entity__ using an __access matrix__.

This matrix is a table that describes what each subject is allowed to do on each object. 

There exists an __extended access matrix__ that also includes:
- Transferring rights from a subject to another.
- Creating another subject.
- Taking ownership of other subjects.

(E.g. In UNIX systems, an user can perform `chmod xx7` to give full access rights to all other entities for a file he owns)

### Access Control List

Each object has an __access control list__, that is used to enumerate all the subjects that have access rights to it.

For each subject in the list it shows all access rights that the subject has for the object.

We can also use the reverse of it, so that:
- For each subject we enumerate all the objects that he has access rights to, and it shows them.
(Subject-centered approach to access control)

### Organization of the Access Control Function

All accesses done by a subject to an object is checked by the __controller__ for that object.

When checking the controller decides based on the current situation of the matrix.

## Mandatory Access Control (MAC)

In the MAC model, each subject and object is assigned to a __security class__.

Security classes form a rigid __hierarchy__, called __security levels__.

Each subjects has a property called __security clearance__ of a given level.

Each object has a property called __security classification__ of a given level.

The confidentiality of this model is based on two properties:
- __No read up__, a subject can only read an object of less or equal security level.
- __No write down__, a subject can only write into an object of greater or equal security level.

## Role-based Access Control (RBAC)

In the RBAC model, we define __roles__ and then specify rights for each of these roles, instead of granting right for subjects directly.

The goal is to describe organizational access control __policies__.

Roles are created based on the jobs.

The permissions that each role have are based on the role's work.

So a subject's permissions are described by his role.

Subjects have access to objects based on their assigned role.

This model increases flexibility and scalability in policy administration, because:
- It is easy to meet new security requirements.
- It reduces administration errors.
- It reduces administration costs.

### RBAC$1$: Role Hierarchy

An organization can have operations that are __common__ to multiple roles.

We can define a __hierarchy of roles__, that uses __inheritance__:
- A parent role's permissions are passed down to the child role.
- More specialized roles have more permissions.
- More generalized roles have less permissions.

### RBAC$2$: Constrains

An organization can have specific __administrative rules__ and __security policies__ that results in special __contrains__.

These constrains can be:
- __Mutually exclusive__ roles, an user cannot be assigned to mutually exclusive roles at the same time.
- __Cardinality__, there is a maximum number of roles a user can have.
- __Prerequisite__ roles, an user can be assigned to a role only if it is already assigned to another specific role.

### RBAC$3$: Actually including both RBAC$1$ and $2$

It's the __complete__ version of RBAC, that includes all the features from RBAC$1$ and 2.

## Attribute-based Access Control (ABAC)

In the ABAC model, we define __attributes__ on subjects and objects.

Based on rules and these attributes it decides whether to give or not a subject access to an object.

It's the most __flexible__ and __expressive__ model of access control.

Systems that use this model are able to simulate all the other models of access control.

ABAC needs access control __policies__ to define its behavior.

### ABAC policies

A policy is a set of rules and relationships between subject and object based on their attributes:
- E.g. New movies can be watched only by premium users.

![|500](https://i.imgur.com/jHDcZI0.png)

# Malware

A malware is a program that is inserted into a system, with the intent of __compromising__ the confidentiality, integrity, or availability of the system's data, application or operating system. (Otherwise to annoy or disrupt the system's user)

Malwares can be classified based on their properties like:
- How it spreads to reach the desired targets.
- What actions or payloads it performs once a target is reached.

## Types of Malware

So we can have:
- __Viruses__, malware that need a __host__ program to function.
	- Viruses can and will replicate themselves.
- __Worms__, __trojans__ and __bots__, are malwares that are independent, so self-contained programs.
	- Worms can and will replicate themselves.
	- Trojans do not replicate themselves.
	- Bots do not replicate themselves.

## Propagation Mechanisms

Malwares can propagate by:
- Infecting already existing content that is then sent to other systems to spread.
- Exploiting software vulnerabilities using worms or drive-by-downloads to allow the malware to replicate.
	- Drive-by-download is an attack that uses code on a compromised website that exploits a browser vulnerability to attack when the site is viewed.
- Social engineering attacks that successfully convince users to install trojans or to respond to phishing attacks.

## Payloads of Malware

All malware possess some __payload__, these define what a malware is supposed to do. These actions performed by malware once inside a target system can be:
- __Corruption__ of the system or of its data.
- Turn the system into a zombie __agent__ of attack as part of a __botnet__.
- __Theft__ of sensible information by __keylogging__ the system. (Capturing keystrokes)
Also, generally all types of malware will try to __hide__ itself and its presence on the system.

## Attack Kits

Initially malware development and deployment required high technical skills.
General tools used for development are called __attack kits__. These are software that provide assist in creating malware.

## Attack Sources

Initially attackers developed malwares only to demonstrate their technical competence.

Now instead attackers are:
- Politically motivated attackers.
- Criminals.
- Organized crime.
- Organizations that sell their services to __companies__ and even __nations__.
- National government agencies.

## Advanced Persisten Threats (APTs)

These threats applies persistent application of a wide variety of intrucion technologies and malware to selected targets, like political figures or businesses.
Typically these are sponsored by governments and by criminal organizations.

They differ from other types of malware and attacks by their __careful__ target selection and __stealthy__ intrusion efforts over __extended periods__ (Persistent).

Eg. Stuxnet was an APT.

Generally these used techniques that varies from:
- Social engineering.
- Spear-phishing emails.
- Drive-by-downloads from websites likely used from the target.

## Virus

A virus is a software that __infects__ programs:
- It modifies them to include a __copy__ of the virus, so it replicates itself.
- It can easily spread through network environments.

When a virus is attached to an executable program, all the permissions granted to the program is also possessed by the virus.

### Virus Components

Viruses are made of $3$ components:
- The __infection vector__, is the mean by which a virus propagates in the system, enabling it to replicate.
- The __trigger__, an event or condition that determines when the __payload__ is activated, known also as a __logic bomb__.
- The __payload__, that is what the virus does, besides spreading.

### Virus Phases

During its lifetime, a virus generally goes through $4$ phases:
- __Dormant phase__, where the virus is idle, and will eventually be awaken by some event.
	- Not all viruses have this stage.
- __Triggering phase__, where the virus is activated to perform his function.
- __Propagation phase__, where the virus places copies of itself into other programs or into certain system's area on the disk.
	- The clone may __not__ be identical to the original version.
- __Execution phase__, where the virus actually performs the damaging functions.

### Macro and Scripting Viruses

These are viruses that attaches themself to documents, making them:
- Platform independent.
- Easily spreadable.
- Much easier to write (for the attacker).
- Because they don't infect system programs, older file systems cannot prevent their spread, also since users are expected to open them (documents) to be able to modify them.

### Virus Classification

Viruses can be classfied by their:
- Target.
	- Boot sector infector, infects low level parts of the system. (Eg. master boot record)
	- File infector, infects executables.
	- Macro virus, infects files with macro or scripting code interpretable by applications.
	- Multipartite virus, infects files in multiple ways.
- Concealment strategy.
	- Encrypted virus, where a portion of the virus encrypts the remainder of itself.
	- Stealth virus, designed explicitly to hide itself from the system's antivirus.
	- Polymorphic virus, so it can mutate itself with every infection.
	- Metamorphic virus, so it can mutate and rewrite itself completely every time and may even change behavior and appearance.

## Worms

Worms are programs that actively seek out more machines to infect generally through system vulnerabilities or by communicating with the network attached to the infected system.
Each of these infected machine serves as an automated launching pad for attacks on other machines.

Worms don't need a host to attach to, they are fully functional programs.

One of the earliest significant worm infection is the __Morris worm__.

__WannaCry__ was a ransomware attack that propagated itself by scanning local and remote networks, attempting to exploit a vulnerability in the file sharing service. Once inside a system, it would encrypt files, to then demand a ransom payment in order to recover them.

### Mobile Phone Worms

Worms that infect mobile phones use __bluetooth wireless connections__ or multimedia messaging service (MMS) to communicate.

These specific worms designed for mobile phones can:
- Completely disable the phone.
- Delete data on the phone.
- Force the device to send costly messages.

The vast majority of mobile phone malware is caused by the use of __trojan apps__.

## Drive-By-Download

This is a common technique that exploits browser and plugin vulnerabilities.
So when the user views a webpage controlled by the attacker, it contains code that exploits the bug to download and install malware on the system without the user's knowledge or consent.

## Watering-Hole Attack

This is a variant of drive-by-download that is used in highly targeted attacks.

The attacker __researches__ their victims to identify websites that they are likely to visit, and then it scans these sites to identify those that have vulnerabilities that allows the attacker to infect the victim.

## Malvertising

This technique uses __advertisements__ on websites to infect their visitors.

## Clickjacking

This technique is also known as a __user-interface__ redress attack.

It tricks the user into thinking that he is typing sensible information like passwords or banking data when using those services (Eg. when purchasing something), but in reality he is typing it into an invisible frame controlled by the attacker that is place on top if the actual website.

Attackers can also register keystrokes and clicks.

## Social engineering for Malware Propagation

This technique tricks users to __assist__ in the compromise of their own system.

Generally this is done by:
- Spamming the target using phishing emails.
- The user downloads programs or utilities that contains harmful hidden code. (Trojan)

## Ransomware

When a ransomware is installed on infected systems, it __encrypts__ a large number of files, to then demand a ransom payment using untraceable currencies like Bitcoin.

Tactics such as:
- Threatening to publish sensitive and personal information
- Permanently destroy the encryption key after a period of time
are used to increase the pressure on the victim to __pay up__.

## Botnets

This type of attack uses collection of bots capable of acting in a __coordinated manner__.

These can be used in:
- Distributed denial of service attacks (DDoS).
- Spamming.
- Sniffing traffic.
- Keylogging.
- Spreading new malware.
- Attacking IRC chat networks.
- Manipulating online polls or games.

Bots are different from worms because:
- Worms propagates and activates themself.
- Bots are initially controlled from some __central facility__.

## Keyloggers and Spyware (Information Theft)

A __keylogger__ captures keystrokes to allow the attacker to monitor sensitive information.

Keyloggers generally use some type of filtering to only return information close to keywords like `login` or `password`.

A __spyware__ is a type of software that collects information from a computer and transmits it to another system by monitoring browser information, network traffic, and more generally the system.

## Phishing (Information Theft)

This technique exploits __social engineering__ to leverage the user's __trust__ by masquerading as communication medium from a trusted souce.

Typically the attacker:
- Sends spam emails that contains URL to fake websites.
- Suggests that urgent action is required by the user to authenticate their account.

A more advanced method is __spear-phishing__:
- Where the targets are carefully researched by the attacker and the emails are specifically crafted (custom-made) in order to deceive and convince them of its authenticity.

## Backdoors (also called trapdoors) (Stealthing) 

A backdoor is a __secret entry point__ into a program that allows someone who is aware of the backdoor to gain access without going through the normal security access procedure.

The backdoor is __code__ that recognizes some special sequence of input or is triggered by being run from a certain user ID or by an unlikely sequence of events.

### Normal use of Backdoors

The normal use of backdoors are for __maintenance__.

A __maintenance hook__ is a backdoor used by programmers to debug and test programs.

## Rootkit (Stealthing)

A rootkit is a set of programs installed on a system to maintain __hidden access__ to that system with __root privileges__, while hiding evidence of its presence to the greatest extent possible.

It does this by subverting the mechanisms that monitor and report on the process, files and registries of a computer.

## Malware Countermeasure Approaches

The __prevention__ of malware threats are the ideal solution for it.

Users can do this by:
- Improving their awareness to threats.
- Mitigating vulnerabilities.
- Mitigating threats.
- Having a strict policy.

If prevention fails, technical mechanisms like __anti-virus__ softwares can be used to support the threat mitigation options:
- Detection of malware.
- Identification of malware.
- Removal of malware.

### Generations of Anti-Virus Software

- First generation: Simple scanners that required a malware signature to identify it, so its limited to the detection of __already known__ malwares.

- Second generation: Heuristic scanners that uses heuristic __rules__ to search for probable malware instances.

- Third generation: Activity traps, so programs that reside in the memory that identify malware by its __actions__ rather tha its structure in an infected program.

- Fourth generation: Full-featured protection, so packages consisting of a __variety__ of anti-virus techniques that does scanning, sets up activity traps and have access control capabilities.

### Sandbox Analysis

Another technique for detecting malware is by running potentially malicous programs in an __emulated__ sandbox or on a __virtual machine__ (VM).

This allows the code to execute in a __controlled__ environment where its behavior can be closely monitored without threatening the security of the real system.

The most difficult design issue with this technique is to determine how __long__ to run each malware before it activates.

# Database Security

Most organizations today rely on databases, but its security is not up to standards. This is caused by a series of problems:
- Databases have a sophisticated interaction protocol called SQL, which is complex and needs a full understanding of the security vulnerabilities of SQL to be able to create an effective security for it.
- Most organizations lack full-time database security personnel.
- Most enterprise environments consist of a __heterogeneous__ mix of database, enterprise and OS platforms, thus creating an additional complexity hurdle for security personnel.

A __database__ is a structured collection of data, stored for use by one or more applications.
It contains the relationships between data items and groups of data items, often containing sensitive data that needs to be secured.

SQL or structured query language, is the standardized language to define schema, manipulate and query data in a __relational database__.

## SQL Injection Attacks (SQLi)

This type of attack is one of the __most prevalent__ and dangerous network-based security threats, designed to exploit the nature of __web application pages__.

The attack sends malicious SQL __commands__ to the database server (Eg. `DROP TABLE`).

Its most common atack __goal__ is the bulk __extraction__ of data.

The technique consists of terminating a command prematurely and appending a new command (the malicious query), finishing with a comment marker `--` which tells the databse to ignore the rest of the query. This allows the attacker to prevent any additional code from executing after their injected command.

So we have a SQLi when it is possible to:
- Modify the syntax of the query by altering the application input.

Attackers can use different avenues to perform a SQLi attack:
- From user input.
- By forging values placed in network headers.
- By injecting the database so the queries are modified.
- From network cookies.
- Using physical user input.

Attack __types__ can be grouped into $3$ main categories:
- Inband.
- Inferential.
- Out-of-band.

An __inband attack__ uses the same communication channel for injecting SQL code and retrieving the results. These attacks generally include the use of:
- __Tautology__, so query conditionals are always evaluated to `true`.
- __End-of-line comments__, so the query part after `--` is ignored.
- __piggybacked queries__, so stacking queries on top of legitimate ones.

An __inferential attack__ uses particular request and observes the resulting behavior of the database server to __reconstruct__ the information. So in these attacks there is no actual transfer of data.
These type of attack are:
- __Incorrect queries__.
- __Blind SQL injection__, where the attacker asks the server `true/false` questions.
- __Out-of-band attack__, where data are retrieved using a different channel, it works because outbound connectivity from the database server is lax.

## SQLi Countermeasures

There are $3$ types of countermeasures to SQLi:
- Manual defensive coding practices.
- Parameterized query insertion.
- SQL DOM.

### Defensive coding practices

Programmers must take care of __input sanitization__, so for example checking that inputs that are supposed to be a type of value contain no other types of values.

### Parameterized query insertion

This approach attempts to prevent SQLi by allowing the application developer to more accurately specify the __structure__ of an SQL query, and pass the value parameters to it separately such that no unsanitary user input is allowed to modify the query structure.

### SQL DOM

This is a set of __classes__ that enables automated data type validation and escaping.
It uses __encapsulation__ of database queries to provide a safe and reliable way to access databases.
So developers withing the API are able for example to implement input filtering and rogorous type checking.

## Database Access Control

A DBMS can support a range of administrative __policies__, including the following:
- __Centralized__ administration, where a small number of privileged users may grant and revoke access rights.
- __Ownership-based__ administration, where the owner (creator) of a table may grant and revoke access rights to the table.
- __Decentralized__ administration, where in addition of granting and revoking access rights to a table, the owner of the table may grant and revoke authorization rights to other users, allowing them to be able to grant and revoke access rights to the table.

Typical access rights are:
```SQL
SELECT - INSERT - UPDATE - DELETE
-- AND REFERENCES IN OTHER TABLES
```


### Cascading Authorizations

By using a decentralized administration, the grant option enables an access right to cascade through a number of users.

And when the owner of the table revokes an access right for a user, __any__ cascaded access right is also __revoked__, unless that access right would exist even if the original grant from the owner had never occurred.

### Role-Based Access Control

A role-based access control eases administrative burden and improves security.
So databases that use RBAC needs to provide the following capabilities:
- Create and delete roles.
- Define permissions for a role.
- Assign and cancel assignment of users to roles.

## Inference

Inference (deduction), related to database security, is the process of performing __authorized queries__ and __deducing unauthorized information__ from the legitimate responses received.

## Database Encryption

The database is typically the __most__ valuable information resource for any organization, so its protected by multiple layers of security.

Encryptions is the __last line of defense__ in database security:
- It can be applied to the entire database, at the record level, attribute level, or level of the individual field.

There are a few disadvanteges to encryption:
- Key management, where authorized users must have access to the decryption key for the data.
- __Inflexibility__, because when part or all of the database is encrypted, it becomes difficult to perform __record searching__.

To mitigate the inflexibility, it must be possible to work with the database in its __encrypted form__.

# Buffer overflow

A buffer overflow, also known as a buffer overrun or buffer overwrite, is a condition at an interface under which more input can be placed into a buffer (or data holding area) than the capacity allocated, overwriting other information such as __return addresses__, __pointers__ to previous stack frames.

It is a very common attack mechanism, and while prevention techniques are already known, its still of major concern because of:
- Legacy code in widely deployed operating systems and applications.
- Continued careless programming practices by programmers.

## Buffer overflow Basics

When a process attempts to store data beyond the limits of a fixed-sized buffer, it may __overwrite__ adjacent memory locations, that could be located:
- On the __stack__, in the __heap__, or in the __data section__ of the process.

These locations could hold other program variables, parameters or program control flow data. So the consequences can be:
- __Corruption__ of program data.
- Unexpected __transfer of control__.
- Memory access __violation__.
- __Execution__ of code chosen by the attacker.

## Buffer overflow Attacks

To exploit a buffer overflow, an attacker needs:
- To identity a buffer overflow __vulnerability__ in a program that can be triggered by using externally source data.
- To understand how that buffer is __stored__ in the processes memory, to then potentially corrupt adjacent memory locations and altering the flow of execution of the program.

To identify vulnerable programs, an attacker uses:
- Inspection of __program source code__.
- Tracing the execution of programs as they process __oversized__ inputs.
- Using __tools__ such as `fuzzing`.

## Programming Languages influence on Buffer Overflow

At the machine level, data that is manipulated by machine instructions, executed by the processor, are stored in either the processor's __registers__ or in __memory__ (RAM).

Older languages such as `C` allows direct access to memory, hence are more vulnerable to buffer overflow, caused by having a large legacy of widely used, unsafe functions too.

On the other side, modern high-level languages have a strong notion of __type__ and valid operations, so they are not vulnerable to buffer overflows, but have more overhead.

## Stack Buffer Overflow

A stack buffer overflow occurs when the targeted buffer (Eg. an array using malloc) is located on the stack, usually as a local variable in a function's stack frame.

This type of overflow is caused when one function, after calling another one needs somewhere to save the __return address__. It also needs locations to save a bunch of parameters to be passed (arguments of the newly called function) and to possibly save its own register values to resume later.

![|500](https://i.imgur.com/y3uygJF.png)

## Shellcode

Many buffer overflow attacks in the end consists of the __transfer of execution__ to code supplied by the attacker.

The supplied code is often saved in the buffer being overflowed.

Originally it was created to transfer control to user command-line interpreter, the shell. This feature was achieved in different ways for different systems.

This means that shellcode is __specific__ to a __particular processor architecture__, and usually to a specific __operating system__, and because it's machine code, to write shellcode one needed to understand deeply assembly.

Targeted programs for shellcodes can be:
- A trusted system utility.
- A network service daemon.
- A commonly used library code.

A shellcode's function can be:
- Launch a remote shell for the attacker.
- Create a reverse shell for the attacker.
- Flush firewall rules that currently are blocking other attacks.
- Break out of a chroot environment, so gaining full access to the system.

### Shellcode Caveats

There are several generic restrictions on the content of shellcode.

First, it has to be __position independent__, it means that it cannot contain any absolute address.
Thisi is because the attacker generally cannot determine in advance exactly where the target buffer will be located in the stack frame of the function in which it is defined.

So the shellcode must be able to run no matter where in memory it is located.

Secondly, it cannot contain any `NULL` values, so all buffer overflows caused by using unsafe string manipulation routines are not done by using shellcode.

## Buffer Overflow Defenses

Buffer overflow defenses can be broadly classified into $2$ categories:
- __Compile-time defenses__, which aim to harden programs to __resist__ attacks in new programs.
- __Run-time defenses__, which aim to __detect__ and __abort__ attacks in existing programs.

### Compile-Time Defenses

These type of defenses aim to prevent or detect buffer overflows by instrumenting programs when they are compiled. Possible approaches are:
- Choosing a high-level language that does not permit buffer overflows.
- Encouraging safe coding standards.
- Using safe standard libraries.
- Including additional code to detect corruption of the stack frame.

Most of these approaches require __recompilation__ of existing programs.

### Run-Time Defenses

These type of defenses can be deployed as operating systems updates, to provide some protection for existing vulnerable programs.

These defenses involve changes to the __memory management__, so the alteration of the properties of regions of memory, or making predicting the location of targeted buffers sufficiently difficult to prevent many types of attacks. Possible approaches are:
- Using virtual memory support to make some regions of memory __non-executable__.
- Changing the address at which the stack is located in a random manner for each process.
	- By Manipulating location of key data structures like the stack, heap and global data.
	- We can go further by randomizing location of standard library functions.
- Placing guard pages between critical regions of memory, so any attempted access aborts process.

## Variants of Buffer Overflow Attacks

### Replacement Stack Frame

The first variant is the __replacement of the stack frame__.
By overwriting a target buffer and saving the frame pointer address, the attacker changes the saved frame pointer value to refer to a __dummy stack frame__. When the functions returns to the replacemente dummy frame, the control is transferred to the shellcode in the overwritten buffer.

This attack is preventable by using any stack protection mechanism to detect modifications to the stack frame.

### Return to System Call

The second variant is the __return to system call__.
Where the attacker replaces the return address with a standard library function, in order to circumvent the non-executable region of memory defense.

This attack is preventable by using any stack protection mechanism to detect modifications to the stack frame.

### Heap Overflow

The third variant is the __heap overflow__.
The attacker tries to use buffers located in the heap, where memory is requested by programs to use in dynamic data structures.

This attack is preventable by making the heap non-executable.

### Global Data Overflow

The fourth variant is the __global data overflow__.
The attacker tries to use buffers located in the global data section in the memory. Generally this is located above the program code, and has function pointers and vulnerable buffers.

This attack is preventable by making the global data non-executable.

# DoS

__Availability__ is one of the fundamental security services. It relates to a system being __accessible__ and usable on demand by authorized users.

A denial-of-service attack is:
- An action that prevents the authorized use of networks, systems, or applications by __exhausting resources__ such as CPU, memory, bandwidth and disk space.

So this type of attack attempts to exhaust some critical resource associated with the targeted service.
- E.g. flooding a web server with many requests in a small period of time, making the server __unable__ to respond to __valid__ requests from users in an acceptable time. (Application resources)
- E.g. overloading or crashing the network handling software. (System resources)

## Classic DoS Attack

A classic DoS attack is done by using the __ping__ command to flood a target server:

The aim of this attack is to overwhelm the capacity of the network connection to the target organization. In this way packets of transmitted data are discarted as capacity decreases.

Given that the source of the attack is __clearly identified__, defense mechanisms against it are fairly simple to implement. Unless the attacker is using a __spoofed address__.

## Source Address Spoofing

Generally attackers will use spoofed addresses to perform DoS attacks.

To do that they use __forged__ source addresses, usually via the raw socket interface on the operating system.

This makes attacking systems harder to identify.

Security researchers, in order to develop defences against spoofing, are advertising routes to unused IP addresses to monitor attack traffic.
Because those are unused addresses, no real packets should arrive their way, so the only packets that do arrive are remains of spoofed DoS attacks.
This is called __backscatter traffic__.

## SYN Spoofing

A similar attack to the DoS attack is the SYN spoofing attack.

The attacker exploits the TCP $3$-way-handshake that is used to establish a secure connection from client to server:
- By sending from spoofed addresses many SYN packets to a target server
- This will cause the server to send back to each of those fake addresses a SYN-ACK packet
- But because those addresses are mostly unused or busy, they wont reply.
- Meanwhile the server for each of those requests it maintains in his table an entry of known TCP connections, and it will resend a SYN-ACK packet a few times before closing the connection.
- So if this table is fully occupied by non-existent connections, real incoming TCP requests will be denied during the period of time before the closing of the fake connections.

## Flooding Attacks

Another category of attacks are flooding attacks, these are classified based on the network protocol used.

These have the same intent to overload the network capacity on some __link__ to a server.

Attackers can use many types of network packets do perform this attack:
- ICMP flood. (These are pings to the target server)
- UDP flood.
- TCP SYN flood.

### Distributed Denial of Service Attacks (DDoS)

A DDoS is a type of the classic DoS attack, but distributed, that is using __multiple systems__ to generate the attack.

The attacker uses a flaw in the operating system or in a common application to gain access and installs the malicious program on it, making them a __zombie__.

Large collections of such systems under the control of one attacker can be obtained, forming a __botnet__.

#### Mirai

Mirai is a 2016 malware that launched a DDoS attack on the website of a well-known security expert.

The owners of Mirai released the malicious code on the Internet, and quickly other groups replicated the malware.

A lot of these replicated Mirai are believed to be behind most of the massive DDoS attacks.

#### Rent a DDoS botnet

In many cases, attackers can launch DDoS attacks by using publicly available tools or by paying a small fee to hire a DDoS-as-a-service botnet from the dark web.

### SIP invite scenario

SIP is a text-based protocol.

A SIP request will trigger in the server a moderate amount of consumed resources.

So the attacker will continuously send invites in order to deplete the server's network capacity.

## Hypertext Transfer Protocol Based Attacks (HTTP Attacks)

There are two types of HTTP based attacks:
- HTTP flood
- Slowloris - R.U.D.Y. (Are you dead yet)

### HTTP Flood

This type of attack bombards web servers with HTTP requests coming from many bots by using stress test tools like __LOIC__ and __HOIC__.

A variant of the HTTP flood attack is the recursive one, where the bot starts from a given HTTP link and it follows all the links on the provided website in a recursive way. This is called __spidering__.

### Slowloris - R.U.D.Y

Slowloris is a type of HTTP bassed attack that exploits the common server technique of using multiple threads to support multiple requests to the same server application.

It attempts to monopolize all of the available request handling threads on the Web
server by sending HTTP requests that never complete.

Since each request consumes a thread, the Slowloris attack eventually consumes all of the Web server’s connection capacity, effectively denying access to legitimate users.

Existing intrusion detection and prevention solutions that relies on __signatures__ to detect attacks will generally __not__ work on Slowloris.

## Reflection Attacks

A reflection attack goal is to generate enough volumes of packets to __flood__ the link to the target system by using an intermediary (server) without alerting it.

The attacker sends packets to a know service on the intermediary with a spoofed source address of the actual target system.

When the intermediary responds, it will send the response to the target, but this will be reflected by the intermediary.

A basic defense against these type of attacks is to block spoofed-sourced packets.

## DNS Amplification Attacks

A DNS amplification attack exploits the DNS behavior to convert a small request to a much larger response (amplification). These requests are then sent to the target, flooding them.

A basic defense against these type of attack is to prevent the use of spoofed source addresses.

## Memcached DDoS attack

Memcached is a high-performance caching mechanism for dynamic websites that allows to speed up the delivery of web contents.

The idea is to make a request that stores a large amount of data to then send a spoofed request to make such data to be delivered to the target via UDP.

## DoS Attack Defences

DoS attacks cannot be prevented entirely, because high traffic volumes may be actually legitimate.
- E.g. high publicity about a specific website.
- E.g. activity on a very popular website.

To defend against DDoS attacks:
- One can prevent the attack preemptively before it.
- One can detect the attack during it and filter it.
- One can source traceback and identify the attack during it and after.
- One can react after the attack has been done.

### DoS Attack Prevention

To prevent DoS attacks we can:
- __Block__ spoofed source addresses, prefferably on routers as close to the source as possible.
- __Filter__ to ensure that the path back to the claimed source address is the one being used by the current packet.
- Use __modified__ TCP connection handling code.
	- By cryptographically encoding critical information in a cookie that is sent as the server's initial sequence number, so if the client responds with an ACK packet containing the incremented sequence number then the server will know that the client is legitimate.
- __Block__ suspicious services and combinations.
- Use __mirrored__ and __replicated__ servers when high-performance and reliability is required.

### Responding to DoS Attacks

Generally the organization that owns a service should contact the ISP to impose:
- Filtering upstream.
- Antispoofing.
- Directed broadcast.
- Rate limiting filters.

An alternative can be the ISP tracing packet flow back to the source to stop them, but this can be quite difficult and time consuming.

# Web Security

When displaying online resources, servers and clients use __scripting__ languages to create dynamic contents for web users.

Client side scripting can be done by:
- Javascript, VBscript, ActiveX, Ajax.
These languages tell the browser the instructions to execute according to the user behavior.

Server side scripting can be done by:
- Javascript, PHP, ASP.NET, Java, Adobe ColdFusion, Perl, Ruby, Go, Python.
These languages build the answer based on the context:
- User identity.
- The actual request.
- The ongoing session.
- ...

##  HTTP Authentication

It's an authentication mechanism that is rarely used nowadays.

It consisted in:
- Client browser starts a request without sending any client-side credentials.
- Server replies with a status message "401 Unauthorized" binded together with a specific authentication header, which contains information on the authentication method.
- The browser gets the client's credentials and include them in the authorization header.

The credentials are encoded in `base64` or __hashed__, and sent to the server.

## Monitoring and manipulating HTTP

THe payload is encapsulated in TCP packets as __cleartext__, this makes the communication __easy__ to monitor and __manipulate__.

We can monitor a communication by using:
- Sniffing tools, like Wireshark.

We can manipulate a communication by using:
- Traditional browser and extensions.
- Proxies.
- Advanced softwares like netcat, curl, ...

__HTTPS__ in this regard is not secure at all, we can just use:
- Browser extensions (Tamper Data).
- Proxies.
to monitor/manipulate payloads sent with HTTPS protocol.

### Proxy HTTP

It's used by attackers to find exploits by doing traffic shaping or/and mangling.

## HTTP Sessions

Because the HTTP protocol is __stateless__, every request is independent from the previous ones.

The problem is that modern dynamic web applications require the ability to maintain some kind of sessions.

The solution is the use of __sessions__. By maintaining sessions:
- The server can avoid asking log-ins for every requested page.
- Store user preferences.
- Keep track of past actions of the user. (E.g. a shopping card, favorites)
- ...

These sessions are implemented by web applications themselves and are __transmitted__ between the client and the server.

The transmission is done by:
- HTTP payload, like `<INPUT TYPE="hidden" NAME="sessionid" VALUE="6767">`
- URL, as a query like `http://website.com/page.php?sessionid=6767`
- Header HTTP. (E.g. with cookies)

The most common way to implement sessions are by using cookies.

## Cookies

Cookies are files of data created by the server and __memorized__ by the client.

These are transmitted between the two using HTTP header.

A cookie can contains data like:
- expiration date of himself.
- The path for which it is valid.
- The domain on which it is valid.
- A `secure` flag that states whether the cookie must be transmitted on a secure channel only.
- A `httpOnly` flag that states if no API is allowed to access `document.cookie`.

A cookie creates a session:
- The session data is stored on the server.
- The server sends a session ID to the client through a cookie.
- For each client request, it sends back the obtained ID to the server.
- So the server uses these IDs to retrieve information.

### Cookies: Security

Because cookies are used for critical elements like authentication, and can bypass authentication schemas (defenses), they can be targeted by attackers.

So cookies should be considered valid for only a __small__ amount of time.

## Content Isolation

Most browser's security mechanism rely on the possibility of __isolating__ documents depending on the resource's origin.

Meaning that:
- Content coming from website $A$ can only read and modify content coming from $A$, and __cannot access__ content coming from website $B$.

In this way a malicious website cannot run scripts that access data and functionalities of other websites visited by the victim.

The 




# Symmetric Encryption

The main purpose of cryptography is to __alter__ a message so that only the intended recipients can alter it back to then read the original message.

Other purposes of cryptography are:
- Preserving confidentiality.
- Authenticating sender and receiver of messages.
- Facilitate the message integrity.
- To ensure that the sender will not be able to deny the act of sending his message (non-repudiation).

## Symmetric Cryptosystem

The main idea is that we assume the communication channel is __insecure__ and can be eavesdropped.

So the sender and the receiver will use:
- A secret key $K$.
- An encryption function $E_{k}(P)$.
- A decryption function $D_{k}(C)$.
- The actual message, as a plaintext.

The sender before sending the message, will encrypt the plaintext with the key by using the encryption function. The result is a __ciphertext__ that has the same length as the plaintext.

The receiver receives the ciphered text, and will use the decryption function to decrypt the ciphertext. He has the same key used by the sender to encrypt the message, and will use it inside the decrypt function.

### Efficiency

Both functions $E_{k}$ and $D_{k}$ should have __efficient__ algorithms.

### Consistency

All messages encrypted by using the encryption functions __need__ to be the same original message after passing them to the decryption function.$$D_{k}(E_{k}(P))=P$$

## Brute force Attack

For the attacker to perform a brute force attack, he is required to have some knowledge about the structure of the plaintext that he is trying to decrypt.

The attacker will try all the possible keys for the decryption and will try to determine if the obtained result is a likely plaintext.

### Countermeasure

Every key should be a sufficiently long random value to make exhaustive search attacks almost impossible.

## Types of attacks

An attacker may have:
- A collection of ciphertext.
- A collection of plaintext/ciphertext pairs.
- A collection of plaintext/ciphertext pairs for plaintexts selected by the attacker.
- A collection of plaintext/ciphertext pairs for ciphertexts selected by the attacker.

## Symmetric Key Cryptography

This type of cryptography uses:
- Substitution, where each character in the text is __replaced__ by another character of the same or different alphabet.
- Transposition, where the __order__, but not the value of the characters in the text is changed.

### Caesar cipher (Substitution)

The Caesar cipher is a simple substitution cipher that works by:
- Replacing each character in the plain text with the character $3$ positions forward in the alphabet.
- And if the end of the alphabet is reached, start over in the alphabet.

Alternatives can be instead of using the next $3$ positions,  any other number. This is considered then the key to decrypt a ciphered text done by a Caesar cipher.

## Weakness and Improvement

With cyclic permutation, it is easy to find the key as there are only $N$ possibilities to try, where $N$ is the number of characters in the alphabet.

So an improvement over it can be by using __random permutation__ of the alphabet, where we map every letter of the alphabet with another but random letter.

In this way a single alphabet can yield $26!$ combinations.

## Frequency Analysis (Cryptanalysis)

By doing a frequency analysis, single alphabet subsitution characters can be analyzed by calculating the frequencies of characters in a ciphertext, and comparing the frequencies of characters in typical texts of the same language.

## Poly-Alphabetic Ciphers

It is still relatively easy to find the key in a random permutation with single alphabet.

So instead we can use a poly-alphabetic substitution cipher:
- The word will work as key, because it will determine the displacement of designated character that will replace the plaintext character.

In this way, the same character in the plaintext may be represented by a different designated character.

### Cyclic permutation (Example of poly-alphabetic cipher)

We assign $2$ random letters as the key for $2$ coding.

It works by:
- Replacing the plaintext letter with a mapped letter from the first coding or the second coding based on the position, even or odd, of the plaintext letter.

(___insert example image here___)

### Vigenére Code



### One-time pad



#### Weaknesses



## Transposition Ciphers

This ciphering is done by changing the order of the letters in the message.

## Block Ciphers




### Binary Cryptography

Most of modern codes tend to use binary cryptography, so encoding messages as only $1$ and $0$.

Using a XOR gate and a key we can encrypt the binary message into a ciphertext.
To decrypt it we just need to use a XOR gate with the same key.

The obtained ciphertext gives an attacker zero information about the plaintext.

### Substitution Boxes



### Actual Block Ciphers used

DES, 3DES and AES are all encryption schemes actually used in practice.

#### Data Encryption Standard (DES)


