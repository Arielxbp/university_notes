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
- Putting access restrictions in order to __protect personal privacy and proprietary information__.

__Integrity__ is the concept of:
- Maintaining the __accuracy and trustworthiness of data__.
- Ensuring information nonrepudiation and __authenticity__.

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
- Being confident that a transmission, message or sender is __valid__.
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

Meaning that a system to be confidential needs to:
- __Prevent unauthorized access to information__.

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

__Authorization__ is used to determine if a person or system is __allowed__ access to resources, based on an access control policy.

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
- __Checksums__, are functions that given a file, computes a distinct numerical value. (hash value)
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
- Leak.
- Corruption.
- Unavailable/very slow.

A leak of information will cause a loss of __confidentiality__.

The corruption of data will cause a loss of __integrity__.

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

Encrypting the sent message provides some __confidentiality__, but it does not provide __authentication__.

To provide authentication we use __authentication tags__, a piece of data that is related to the message but not reversible to recover the original message.

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

A malware is a program that is inserted into a system, with the intent of __compromising__ the confidentiality, integrity, or availability of the victim's data, applications or operating system. 

Malwares are differentiated based on:
- How it __spreads__ to reach the target.
- Which actions or payloads it __performs__ once a target is reached.

A malware can __propagate__ by:
- __Infecting__ existing data that is then spread to other systems.
- __Exploiting__ software vulnerabilities.
- __Social engineering__, convincing users to disable security mechanisms to __install__ malware.


A malware's __payload__ defines what it is supposed to do once inside the target's system:
- __Corruption__ of the system or of its data.
- __Theft of service__ (computational power), controlling the system as part of a botnet.
- __Theft of information__ using keyloggers.
- __Stealthing and hiding__ its presence from the system.

## Types of Malware

A __virus__ is a malware that need a host program in order to work.
- Can replicate.

__Worms__, __trojans__ and __bots__ are malwares that are complete programs. (Independent)
- Worms can replicate.
- Trojans cannot replicate.
- Bots cannot replicate.

## Attack Kits

Initially malware development and deployment required high technical skills.

__Tools__ used to develop malwares are called __attack kits__.

An attack kit is a piece of __software__ that gives assistance in creating malwares.

## Attack Sources (Who are the attackers)

Initially attackers developed malwares to demonstrate their __technical skills__.

Nowadays an attacker can be:
- Government agency.
- Criminal.
- Member of organized crime.
- An organizations that sell their services.
- National government agencies.

## Advanced Persisten Threats (APTs)

These threats will use various malware technologies in a persistent way to attack a special selected target. (e.g. Politician or administrator of an organization)

Typically these are sponsored by governments and by criminal organizations.

An APT is different from other types of malware because:
- It is careful about its targets.
- It works in a stealthy way.
- It works for long periods. (persistent)

__Stuxnet__ is one of the most known APT, specifically it's a worm:
- It targeted industrial control systems.

To perform an attack, an APT uses:
- Social engineering.
- Spear-phishing emails.
- Drive-by-downloads from websites that are likely to be used from the target.

## Virus

A virus is a software that __infects__ programs:
- It __modifies__ them to include a __copy__ of the virus, so it can replicate.
- Easily spreadable through networks.

When a virus is attached to an executable program, all the permissions granted to the program are also granted to the virus.

### Virus Components

A virus is made of $3$ components:
- The __infection mechanism__, is the mean by which it propagates in a target system.
- The __trigger__, is an event that decides when the __payload__ is activated. (Logic bomb)
- The __payload__, is what the virus does besides spreading.

### Virus Phases

During its lifetime, a virus goes through $4$ phases:
- __Dormant__ phase, virus is __idle__, and will be activated by some event. (Some don't have this phase)
- __Triggering__ phase, virus is activated, __preparing__ to perform his function.
- __Propagation__ phase, virus places a copy of itself into other programs or into system areas on the disk. (The copies can be different from the original)
- __Execution__ phase, virus actually __performs__ the damaging actions.

### Macro and Scripting Viruses (Document virus)

These are viruses that binds themself to documents, making them:
- Platform independent.
- Easily spreadable.
- Much easier to write (for the attacker).
- Because they don't infect system programs, older file systems cannot prevent their spread.
- Users are expected to open these documents.

### Virus Classification

#### Classification by target

Targets:
- __Boot sector__ infector, infects low level parts of the system. (Eg. master boot record)
- __File__ infector, infects executables.
- __Macro__ virus, infects files with macro or scripting code interpretable by applications.
- __Multipartite__ virus, infects files in multiple ways.

#### Classification by concealment strategy

Strategies:
- __Encrypted__ virus, a portion of the virus encrypts the remainder of itself.
- __Stealth__ virus, specifically written to hide from the system's antivirus.
- __Polymorphic__ virus, it mutates with every infection.
- __Metamorphic__ virus, it can mutate and rewrite itself completely and may even change behavior and appearance.

## Worms

Worms are programs that actively seeks out more machines to infect.

A worm exploits __software vulnerabilities__ present inside a program.

Each infected machine serves as an automated launching pad for attacks on other machines.

A worm is a fully functional program, it does not need a __host__.

One of the earliest significant worm infection is the __Morris worm__:
- It tried to crack password.

### Characteristics of worms

- Polymorphic. (Mutates with every infection)
- Metamorphic. (Mutate and rewrite completely)
- Multiplatform. (System independent)
- Multi-exploit. (Uses various vulnerabilities)
- Ultrafast spreading.

### Mobile Phone Worms

Worms that infects mobile phones exploit __bluetooth wireless connections__ or multimedia messaging service (MMS).

These worms designed for mobile phones can:
- Disable the phone.
- Delete data on the phone.
- Force the phone to send costly messages.

Although mobile phone worms are possible, the majority of mobile phone malwares come from __trojan apps__.

## Drive-By-Download

It's a technique that exploits __browser__ and its __plugins__ as vulnerabilities.

When a target views a __webpage__ controlled by the attacker:
- The webpage contains malicious code that exploits the browser's vulnerabilities.
- The code downloads and installs malware __without__ the user knowing.

### Watering-Hole Attack

Variant of drive-by-download that is used in highly __targeted__ attacks.

The attacker __researches__ the target to identify websites that they are likely to visit.

It scans these sites to identify those that have vulnerabilities that allows the attacker to infect the victim.

## Malvertising

This technique uses __advertisements__ (ADs) on websites to infect their visitors.

## Clickjacking

This technique __tricks__ the target into thinking that he is typing access information to perform login.

In reality there is an __invisible frame__ controlled by the attacker where all the typed characters are.

Attackers can also register keystrokes and clicks.

## Social engineering for Malware Propagation

Social engineering is used to trick a target into assisting the compromisation of their own system.

Generally this is done by:
- Spamming the target using phishing email.
- Target downloads programs or utilities that contains harmful hidden code. (Trojan)

## Ransomware

When a ransomware is installed on an infected system:
- It __encrypts__ a large number of files.
- Then it demand a ransom payment using __untraceable__ currencies. (e.g. Bitcoin)

 __Tactics__ used to speed up the target's payment:
- __Threatening__ to publish the target's data.
- __Destroying__ the encryption key after a period of time.

### WannaCry

__WannaCry__ was a ransomware attack that propagated itself by scanning local and remote networks, attempting to exploit a vulnerability in the file sharing service. Once inside a system, it would encrypt files, to then demand a ransom payment in order to recover them.

## Payload: Botnet

This type of attack uses collection of bots capable of acting in a __coordinated manner__.

It has many use cases:
- Distributed denial of service attacks (DDoS).
- Spamming.
- Sniffing traffic.
- Keylogging.
- Spreading new malware.
- Attacking chat networks.
- Manipulating online polls or games.

Bots are different from worms because:
- Worms propagates and activates themself.
- Bots are __initially controlled__ from some __central facility__.

## Payload: Information Theft

### Keyloggers and Spyware

A __keylogger__ captures keystrokes so the attacker knows sensitive typed information.

Keyloggers use some type of __filtering__ to only return information close to keywords like "login" and "password".

A __spyware__ is a software that collects information from a computer and transmits it to another system.

### Phishing

Phishing exploits __social engineering__ to gain the user's __trust__ by:
- Masquerading as a middle-man from a trusted souce.

Typically the attacker:
- Sends spam emails that contains URL to fake websites.
- Suggests that urgent action is required by the user to authenticate their account.

A more specific technique is __spear-phishing__:
- Where the targets are carefully researched by the attacker and the emails are custom-made in order to deceive and convince them of its authenticity.

## Stealthing: Backdoor

A backdoor is a __secret entry point__ into a program.

It allows for who is aware of the backdoor to:
- Gain access without going through the normal security access procedure.

A backdoor gets activated when some __lines of code__:
- Recognizes some special sequence of inputs
- Or is activated by an unlikely sequence of events.

### Normal use of Backdoors

The normal use of backdoors are for __maintenance__.

A __maintenance hook__ is a backdoor used by programmers to debug and test programs.

## Stealthing: Rootkit

A rootkit is a set of hidden programs installed on a system to:
- Maintain __hidden access__ to that system with __root privileges__.
- While __hiding its presence__ to the greatest extent possible.

It does this by subverting the mechanisms that monitor and report on the process, files and registries of a computer.

Basically the system:
- Instead of using the genuine system programs and functions.
- It uses a set of the same programs and functions, but modified so that it doesn't check the attacker.

## Malware Countermeasure Approaches

The ideal solution is __prevention__ of malware threats.

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

- First generation: __Simple scanners__ that required a malware signature to identify it, so its limited to the detection of __already known__ malwares.

- Second generation: __Heuristic scanners__ that uses heuristic __rules__ to search for __probable__ malwares.

- Third generation: __Activity traps__, are programs that reside in the memory that identifies malware by its __actions__ rather than its __structure__.

- Fourth generation: __Full-featured__ protection, so packages consisting of a variety of anti-virus techniques that does scanning, sets up activity traps and have access control capabilities.

### Sandbox Analysis

Running potentially malicious programs in an __emulated__ sandbox or on a __virtual machine__ (VM).

This allows the code to execute in a __controlled__ environment where its behavior can be closely __monitored__ without threatening the security of the real system.

The most difficult design issue with this technique is to determine __how long to run__ each malware before it activates.

### Host-Based Behavior-Blocking Software

Software that check a program's behavior while it is running.

It __blocks instantly__ malicious actions so it is better than __detecting__ them.

The bad part is that the malicious code must __run at least one time__ before it gets eliminated.

# Database Security

Most organizations today rely on databases, but its security is not up to standards. This is caused by a series of problems:
- Databases have a sophisticated interaction protocol called __SQL__, which is complex and needs a full understanding of the security vulnerabilities of SQL to be able to create an effective security for it.
- Most organizations lack full-time database security personnel.
- Most enterprise environments consist of a __heterogeneous__ mix of database, enterprise and OS platforms, thus creating an additional complexity hurdle for security personnel.

## Databases

A __database__ is a structured collection of data, stored for use by one or more applications.

It contains the __relationships__ between data items and groups of data items, often containing __sensitive data__ that needs to be secured.

__SQL__ or structured query language, is the standardized language to define schema, manipulate and query data in a __relational database__.

### Database management system (DBMS)

It's a set of programs used to build and maintain the database.

![|400](https://i.imgur.com/xfvZOqL.png)

## SQL Injection Attacks (SQLi)

A SQLi attack works by:
- Sending malicious __SQL commands__ to the database server.

The most common objective is to __extract__ bulks of data or to __eliminate all tables__.

### How it works

It works by:
- Terminating a command __prematurely__.
- Then __append__ the __new malicious command__.
- The malicious command needs to be finished with a comment marker "--".
- The comment marker is used to ignore the rest of the query.
- This allows the attacker to prevent any additional code from executing after their malicious command.

So we have a SQLi when it is possible to:
- __Modify the syntax__ of the query by altering the __application input__.
- Basically when we can send in input a SQL query.

### SQLi Attack Avenues (methods)

An attacker can try different methods to perform a SQLi attack:
- User input.
- By forging values placed into network headers.
- From network cookies.
- Using physical user input.

### SQLi Attack types

#### Inband Attack

An __inband attack__ uses the same communication method for injecting SQL code and retrieving the results.

These attacks use:
- __Tautology__, query conditionals are always evaluated to `true`.
- __End-of-line comments__, the query part after `--` is ignored.
- __Piggybacked queries__, stacking queries on top of legitimate ones.

#### Inferential Attack

An __inferential attack__ uses particular request and observes the resulting behavior of the database to __reconstruct__ the information.

So there is no actual transfer of data.

These attacks use:
- __Incorrect queries__.
- __Blind SQL injection__, attacker asks the database "true or false" questions.
- __Out-of-band attack__, data are retrieved using a different channel, it works because outbound connectivity from the database server is chill (not properly controlled).

## Blind SQLi

When an attacker performs an SQLi attack but the system does not allow him to see the output in the form of:
- Error messages.
- Or extracted database data.

To exploit this countermeasure of not showing any message an attacker uses:
- __Benchmark__ SQL function.
- Or __Sleep__ SQL function.

If there is a __difference in time__ between same queries but:
- With one that computes one of those two function.
- Then it means that the database computed correctly something.

## SQLi Countermeasures

There are $3$ types of countermeasures to SQLi:
- Manual defensive __coding practices__.
- __Parameterized__ query inputs.
- SQL DOM. (Automated data type validation)

### Defensive coding practices

Programmers must take care of __input sanitization__.

Checking that the inputs that are supposed to be a type of value contain no other types of values.

### Parameterized query insertion

Specify more accurately the __structure__ of an SQL query.

 Pass the value parameters to queries separately so that no unsanitary user input is allowed to modify the query structure.

### SQL DOM

A set of __classes__ that enables automated data type validation.

It uses __encapsulation__ of database queries to provide a safe and reliable way to access databases.

So developers withing the API are able for example to implement input filtering and rogorous type checking.

## Database Access Control

DBMS can support many administrative __policies__, including the following:
- __Centralized__ administration, a small number of privileged users can __grant and revoke access rights__.
- __Ownership-based__ administration, the creator of a table can __grant and revoke access rights to the table__.
- __Decentralized__ administration,the creator of a table furthermore can __grant and revoke authorization rights__ to other users, so they can also grant and revoke access rights to the table.

Assignable access rights are:
- Select.
- Insert.
- Update.
- Delete.
- References.

### Cascading Authorizations

With decentralized administration, the grant option enables an access right to be cascaded to multiple users.

When user$1$  revokes an access right to a user$2$, all cascaded access rights in the chain are also revoked.

Unless that access right would have existed even without the original grant.

## Inference

Inference is the process of __deducing__ unauthorized information from authorized information based on received responses.

So in a database:
- Performing authorized queries.
- And using the received query response to deduce unauthorized information.

### How to countermeasure: Inference Detection

An __algorithm__ is need to perform inference detection.

The algorithm will remove inference by:
- Modifying the structure of the database.
- Or changing the access control policies.

## Database Encryption

The database is typically the __most__ valuable information resource for an organization.

Encryptions is the __last line of defense__ in database security:
- It can be applied to the entire database, at the record level, attribute level, or level of the individual field.

There are __disadvanteges__ to encryption:
- __Key management__, authorized users must have access to the decryption key related to their access level.
- __Inflexibility__, when part or all of the database is encrypted, it's difficult to perform queries.

To mitigate the inflexibility, it must be possible to use the database in its __encrypted form__.

# Buffer overflow

A buffer overflow is a __condition__ where more input can be placed into a buffer than the allocated capacity.

A buffer overflow is a __condition__ where more input data is written into a buffer that does not have sufficient allocated capacity to hold it.

So it overwrites other information such as __return addresses__ and __pointers__ to previous stack frames.

It is a very common attack mechanism, and while prevention techniques are already known, it's still of major concern because of:
- __Legacy code__ in widely deployed operating systems and applications.
- __Wrong programming practices__ by programmers.

## Buffer overflow Basics

When a process tries to store data beyond the limits of a fixed-sized buffer:
- It can __overwrite__ adjacent memory locations.

These memory locations can be:
- On the __stack__.
- In the __heap__.
- In the __data section__ of the process.

These locations can hold program variables, parameters or program control flow data.

So the consequences are:
- __Corruption__ of program data.
- Unexpected __transfer of control__.
- Memory access __violations__.
- __Execution__ of code chosen by the attacker.

## Buffer overflow Attacks

To exploit a buffer overflow, an attacker needs:
- __Identity__ a buffer overflow __vulnerability__ in a program that can be activated using external data.
- Understand __how the buffer is stored__ in memory and determine if it can be corrupted.

To identify vulnerable programs, an attacker does:
- __Inspection__ of program __source code__.
- __Tracing__ the execution of programs as they process __oversized__ inputs. (Like debugging)
- Using software __tools__.

## Stack Buffer Overflow

A stack buffer overflow occurs when the target buffer is on the stack.

This type of overflow is caused when a function, after calling another function, needs to store somewhere the __return address__.

Also it needs other memory locations to save:
- Parameters to be passed, like the arguments of the called function.
- Its own register values in order to continue later its execution.

![|500](https://i.imgur.com/y3uygJF.png)

## Shellcode

Many buffer overflow attack's objective is the __transfer of execution__:
- Execute code given by the attacker.

The __supplied code__ is called __shellcode__.

Originally it was created to transfer control to user command-line interpreter, the shell.

This feature was achieved in different ways for different systems.

This means that shellcode is __specific__ to a __particular processor architecture__, and usually to a specific __operating system__.

### Shellcode Caveats

It needs to be __position independent__:
- An attacker normally cannot determine in advance exactly where the target buffer is located.
- So the shellcode must be able to run no matter where in memory it's located.

Also it cannot contain "NULL" values.

## Buffer Overflow Defenses

Buffer overflow defenses are divided into $2$ categories:
- __Compile-time__ defenses, that __harden__ programs to __resist__ attacks in new programs.
- __Run-time__ defenses, which aims to __detect__ and __abort__ attacks in existing programs.

### Compile-Time Defenses

Aims to prevent or detect buffer overflows by checking the program when it is compiled.

Possible defences are:
- Modern __High-level language__ that does not permit buffer overflows.
- Encouraging __safe coding standards__.
- Using __safe libraries__ functions as alternative to unsafe functions.
- Writing __additional code__ to detect corruption of the stack frame.

### Run-Time Defenses

These defenses involve changes to the __memory management__:
- Alterating the properties for certain regions of memory.
- Using __virtual memory__ implementation to make some regions of memory __non-executable__.
- __Changing and randomizing__ the memory __location__ of key data structures like the stack, heap and global data inside the memory.
- Placing __guard pages__ between critical regions of memory, so any attempted access aborts the process.

## Variants of Buffer Overflow Attacks

### Replacement Stack Frame

The first variant is the __replacement of the stack frame__.

1) By overwriting a target buffer and saving the frame pointer address.
2) The attacker changes the saved frame pointer value to refer to a __dummy stack frame__.
3) When the functions returns to the replacement dummy frame, the control is transferred to the shellcode in the overwritten buffer.

This attack is preventable by using any stack protection mechanism to detect modifications to the stack frame.

### Return to System Call

The second variant is the __return to system call__.

Where the attacker replaces the return address with a standard library function:
- Used to circumvent the non-executable region of memory defense.

This attack is preventable by using any stack protection mechanism to detect modifications to the stack frame.

### Heap Overflow

The third variant is the __heap overflow__.

The attacker tries to use buffers located in the heap, where memory is requested by programs to use in dynamic data structures.

This attack is preventable by making the heap non-executable.

### Global Data Overflow

The fourth variant is the __global data overflow__.

The attacker tries to use buffers located in the global data section in the memory.

Generally this is located above the program code, and has function pointers and vulnerable buffers.

This attack is preventable by making the global data non-executable.

# DoS

__Availability__ is one of the fundamental security services that describes:
- A system being __accessible__ and usable on demand by authorized users.

A denial-of-service attack is:
- An action that prevents the authorized use of networks, systems, or applications by __exhausting resources__ such as CPU, memory, bandwidth and disk space.

So this type of attack attempts to exhaust some critical resource associated with the targeted service.

Categories of attacked resources:
- Network bandwidth.
- System resources, are network handling softwares.
- Application resources.

## Classic DoS Attack

A classic DoS attack is done by using the __ping__ command to flood a target server:

The aim of this attack is to overwhelm the capacity of the network connection to a target organization.

In this way packets of transmitted data are discarted as capacity decreases.

Given that the source of the attack is __clearly identified__, defense mechanisms against it are fairly simple to implement.

Unless the attacker is using a __spoofed address__.

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
- Spoofed addresses sends many SYN packets to a target server.
- Server will send back to each fake address a SYN-ACK packet.
- Those addresses are mostly unused or busy, they won't reply.
- Server for each of those requests it __maintains in his table an entry__ of known TCP connections, and it will resend a SYN-ACK packet a few times before closing the connection.
- If this __table is fully occupied__ by non-existent connections, __real incoming__ TCP requests will __be denied__ during the period of time before the closing of the fake connections.

## Flooding Attacks

Flooding attacks are classified based on the network protocol used.

These have the intent to overload the network capacity on some __link__ (router) to a server.

An attacker can use __many types of network packets__ do perform this attack:
- __ICMP__ flood. (Pings to target server)
- __UDP__ flood. (UDP packets to target server)
- __TCP SYN__ flood.

## Distributed Denial of Service Attacks (DDoS)

A DDoS is a variant of the DoS attack that is distributed:
- It uses __multiple systems__ to generate the attack.

The attacker exploits a flaw in the operating system or in a common application to gain access (worms) and installs the malicious program on it, making them a __zombie__.

Large collections of such systems under the control of one attacker can be obtained, forming a __botnet__.

### Mirai (DDoS attack)

Mirai is a 2016 malware that launched a DDoS attack on the website of a well-known security expert.

The owners of Mirai released the malicious code on the Internet, and quickly other groups replicated the malware.

A lot of these replicated Mirai are believed to be behind most of the massive DDoS attacks.

### Renting a DDoS botnet

An attacker can launch DDoS attacks by:
- Using publicly available tools.
- Or by paying a small fee to hire a DDoS-as-a-service botnet.

### SIP invite scenario (Dos attack)

SIP is a text-based protocol.

There are servers that provide SIP services.

A SIP request will trigger in the server a moderate amount of consumed resources.

So the attacker will continuously send invites in order to deplete the server's network capacity.

## Hypertext Transfer Protocol Based Attacks (HTTP Attacks)

Two types of HTTP based attacks:
- __HTTP flood__.
- __Slowloris__ - R.U.D.Y. (Are you dead yet)

### HTTP Flood

This type of attack bombards web servers with __HTTP requests__ coming from many bots by using stress test tools like __LOIC__ and __HOIC__.

A variant of the HTTP flood attack is the __recursive one__, where the bot starts from a given HTTP link and it follows all the links on the provided website in a recursive way.

This is called __spidering__.

### Slowloris - R.U.D.Y

__TLDR__: Attempts to monopolize by sending HTTP requests that never complete.

Slowloris is a type of HTTP based attack that exploits the common server technique of using multiple threads to support multiple requests to the same server application.

It attempts to monopolize all of the available request handling threads on the Web
server by sending HTTP requests that never complete.

Since each request consumes a thread, the Slowloris attack eventually consumes all of the Web server’s connection capacity, effectively denying access to legitimate users.

Existing intrusion detection and prevention solutions that relies on __signatures__ to detect attacks will generally __not__ work on Slowloris.

## Reflection Attacks

A reflection attack goal is to generate enough volumes of packets to flood the link to the target system by using a middle-man (another system).

### How it works

1) Attacker uses a spoofed source address of his target.
2) Attacker sends packets to a service provided by another system.
3) System sends the response to the target.
4) Target will respond to the arrived response.
5) Loop.

A basic defense against these type of attacks is to block spoofed-sourced packets.

## DNS Amplification Attacks

A DNS amplification attack exploits the DNS behavior to __convert a small request to a much larger response__ (amplification).

These requests are then sent to the target, flooding them.

A basic defense against these type of attack is to prevent the use of spoofed source addresses.

## Memcached DDoS attack

Memcached is a high-performance __caching mechanism__ for dynamic websites that allows to speed up the delivery of web contents.

The idea:
- Make a request that stores a large amount of data.
- Send a spoofed request to make such data to be delivered to the target via UDP.

## DoS Attack Defences

DoS attacks cannot be prevented entirely, because high traffic volumes __can be legitimate__:
- E.g. __high publicity__ about a specific website.
- E.g. activity on a __very popular__ website.

To defend against DDoS attacks:
- One can prevent the attack preemptively before it. (__Preemptive__)
- One can detect the attack during it and filter it. (__Detect and fix when happening__)
- One can source traceback and identify the attack during it and after. (__Traceback and identify__)
- One can react after the attack has been done. (__React after__)

### Preventing DoS attacks

To prevent DoS attacks we can:
- __Block__ spoofed source addresses.
- __Filter__ to ensure that the path back to the claimed source address is the one being used by the current packet.
- Use __modified__ TCP connection handling code.
	- By cryptographically encoding critical information in a cookie that is sent as the server's initial sequence number, so if the client responds with an ACK packet containing the incremented sequence number then the server will know that the client is legitimate.
- __Block__ suspicious services and combinations.
- Use __mirrored__ and __replicated__ servers to provide services.

### Responding to DoS attacks

Organization that owns a service should contact the ISP to provide:
- __Filtering__ upstream.
- __Antispoofing__.
- __Directed broadcast__.
- __Rate limiting filters__.

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

It's an authentication mechanism that is rarely used now.

It consisted in:
- Client browser starts a request without sending any client-side credentials.
- Server replies with a status message "401 Unauthorized" binded together with a specific authentication header, which contains information on the authentication method.
- The browser gets the client's credentials and include them in the authorization header.

The credentials are encoded in `base64` or __hashed__, and sent to the server.

## Monitoring and manipulating HTTP

The payload is encapsulated in TCP packets as __cleartext__.

In this way communication is easy to __monitor__ and __manipulate__.

__Sniffing tools__ are used to monitor a communication:
- Wireshark.

Manipulation of a communicatio by using:
- Traditional browser and extensions.
- Proxies.
- Advanced softwares like netcat, curl, ...

__HTTPS__ in this regard is not secure at all, we can just use:
- Browser extensions (Tamper Data).
- Proxies.
to monitor/manipulate payloads sent with HTTPS protocol.

## Proxy HTTP

It's used by attackers to find exploits by doing __traffic shaping__ or/and __mangling__.

## HTTP Sessions

HTTP protocol is __stateless__:
- Every request is __independent__ from the previous ones.

Modern dynamic web applications need the ability to maintain some kind of __sessions__.

The solution is the use of __sessions__.

By maintaining sessions:
- Server can __avoid asking log-ins__ for every requested page.
- Store __user preferences__.
- Keep track of __past actions__ of the user. (E.g. a shopping card, favorites)

These sessions are implemented by web applications themselves and are __transmitted__ between the client and the server.

The transmission of a session can be done using:
- __HTTP payload__. (e.g. `<INPUT TYPE="hidden" NAME="sessionid" VALUE="6767">`)
- URL, as __a query__. (e.g. `http://website.com/page.php?sessionid=6767`)
- Header HTTP: __cookies__.

## Cookies

Cookies are files of data:
- Created by the server.
- And stored by the client.

Cookies are transmitted between client and server using __HTTP header__.

A cookie contains data like:
- Expiration date.
- Path for which it's valid.
- Domain for which it's valid.
- A "secure" flag that indicate if it must be transmitted on a secure channel only.
- A "httpOnly" flag that states if no API is allowed to access the cookie.

A cookie creates a session:
- Session data is stored on the server.
- Server sends a session ID to the client using a cookie.
- Each client request sends back the obtained ID to the server.
- Server uses these IDs to retrieve information.

### Security of cookie sessions

Cookies are used for critical elements like authentication.

Cookies __can bypass authentication__ defenses, so are targeted by attackers.

Cookies should be __valid__ only for a __small amount of time__.

### Session hijacking (Attack)

1) Attacker eavesdrop a trasmission of cookie.
2) Attacker uses eavesdropped information to access.

### Session fixation (Attack)

1) Attacker sends a request to a server.
2) Server sends a session ID using a cookie.
3) Attacker sends the session ID to the target.
4) Target will use received session ID for future requests.

## Content Isolation

Most browsers security mechanism rely on:
- __Isolating__ documents depending on its origin.
- Pages of different sources should not be allowed to interact.
- Content coming from website $A$ can only read and modify content coming from $A$, and __cannot access__ content coming from website $B$.

In this way malicious websites cannot run scripts that access data and functionalities of other websites visited by the victim.

## Same Origin Policy

Prerequisite for different window tabs to interact with each other is:
- If and only if the __protocol__, __domain name__ and __port__ are the same.

### Same Origin Policy implication

- A website __cannot read or modify__ cookies or other DOM elements of another website.
- Modification of other window tab should need __security checks__.
- A website __can request a resource__ from another website, but it __cannot process it__.

### Same Origin Policy limits

- Cannot isolate pages of different users of a same service.
- Different domains cannot easily interact.

To fix the difficult interaction:
- Both domain can set their TLD address to the same.
- E.g. "play.google.com" and "mobile.google.com" both use "google.com".

## Web Attacks

### Client side attacks

#### Cross-Site Scripting (XSS)

The target is the user's application.

It's caused by a lack of __input sanitization__.

By modifying the original webpage injecting HTML and Javascript code.

There are $3$ types of XSS:
- __Reflected__.
	1) Server's webpage is vulnerable to XSS.
	2) The exploit is inside the URL.
	3) Any client that visits the webpage also is attacked.
- __Stored__.
	1) Attacker sends to the server the code to inject.
	2) Server stores received code in the database.
	3) Any client that visits the webpage of that server will receive the injected code.
- __DOM-based__.
	1) Similar to the reflected one.

An XSS attack can:
- __Capture information__.
- __Show false information__.
- __Inject false form fields__.
- ...

#### Cross-Site Request Forgery (also On-Site)

__TLDR__: Have a target to execute some actions, using his credentials like session cookie.

__TLDR__: Tricking a logged-in user into unknowingly sending a malicious request to a trusted website.

Can be:
- __Reflected__ type.
- __Stored__ type.

How it works:
1) User logs-in a webpage service.
2) Website authenticates the user and gives him the session cookie.
3) User accesses the malicious webpage.
4) Malicious webpage __forges a hidden request__ for the service's webpage. (e.g. Bank transfer)
5) Hidden request uses the valid session cookie so the service is ok with it.

To countermeasure CSRF attacks:
- No request can take an action for someone if it does not have that __person's token__.

# Cryptography - Symmetric Encryption

The main use of cryptography is to __alter__ a message so that only the intended receiver can alter it back to then read the original message.

Other purposes are:
- Preserving __confidentiality__.
- __Authenticating__ sender and receiver. (Authentication)
- Facilitate the message __integrity__.
- __Non-repudiation__, sender will not be able to deny the act of sending a message.

## Advantages of Symmetric cryptography

- Easy to use.
- Efficient.
- Relatively short keys.
- Many applications of use.
- Easily combine multiple ciphering.

## Limitations of Symmetric cryptography

- Users __need to share the same secret key__.
- Intercept the key during its transmission.
- Number of keys required increases rapidly as users increase.
- __Cannot provide authentication__.

## Symmetric Cryptosystem

Always assume that the communication channel is __not secure__ and can be __eavesdropped__.

The plaintext typically has the __same length__ as the ciphertext.

Encryption and decryption function are __bijections__:
- One is the reverse of the other.

Both functions needs to be __efficient__.

### Symmetric cryptosystem: Brute force Attack

A brute-force attack tries all possible secret keys to decrypt a ciphertext.

An attacker needs to know the __structure__ of the plaintext.

To defend against brute-force attacks:
- Every secret key should be __long enough__ to make the computing computationally very slow or impossible.

## Symmetric Key Cryptography (How to make ciphertext)

This type of cryptography uses:
- __Substitution__, each character in the text is __replaced__ by another character of the same alphabet. (Or another alphabet)
- __Transposition__, the __order__ of the characters in the text is changed.

## Substitution Ciphers

### Caesar cipher

Caesar cipher is a substitution type cipher.

It works by:
- Replacing each character in the plain text with the character $3$ positions forward in the alphabet.
- And if the end of the alphabet is reached, start over in the alphabet.

The __key__ of the cipher is:
- The number of positions to change forward.
- Default is $3$.

### Weakness and Improvement for Cyclic subsitution (permutation)

It is easy to find the key when using cyclic permutations:
- Alphabet has $N$ characters.
- Then the key has $N$ possible values.

To improve this method we use __random permutations__:
- Map every character with another random character of the alphabet.

In this way a single alphabet can yield $N!$ combinations for the key.

### Poly-Alphabetic Ciphers

Poly-alphabetic substitution cipher:
- The word is the key.
- It determines the displacement of a designated character that will replace the plaintext character.

In this way, the same character in the plaintext may be represented by a different designated character.

__TLDR__: Some characteristic of the word is used as key for the ciphering.
- E.g. Odd positioned character are substituded into $X$ while even ones into $Y$.

### Vigenére Code

All possible cyclic permutations are used.

![|500](https://i.imgur.com/JhW07k2.png)

### One-time pad

It works by __displacing__ the character for the value of the padded character.

This method is __unbreakable__, because:
- __Shannon's theorem__, there must be at least as many keys as there are possible messages.

The key needs to be __as long as the plaintext__.

Keys __cannot be reused__.

## Frequency Analysis (Cryptanalysis)

By doing a __frequency analysis__, single alphabet subsitution characters can be:
- Analyzed by calculating the frequencies of characters in a ciphertext.
- And then comparing the frequencies of characters in typical texts of the same language.

## Transposition Ciphers

Change the order of the letters in the message.

Types:
- Permutation.
- Column transposition.
- Keyed column transposition, rearranges the columns based on a permutation.

## Feistel network: Product cipher (Ciphering method)

__Product cipher__ works by:
- Executing two or more simple ciphers in sequence.
- Final result is cryptographically __stronger__ that any simple cipher used in the process.
- Used simple ciphers should be both subsitution and permutation types.

## Computationally secure encryption schemes

An encryption is computationally secure if:
- Cost of breaking cipher is greater than the value of information.
- Time required to break cipher is greater than the expiration date of the information.


## Block Ciphers

A plaintext is __divided into blocks__ of __fixed length__.

Each block is encrypted by himself.

## Block Cipher modes

A block cipher mode:
- Describes __the way it encrypts and decrypts__ a sequence of message blocks.

$5$ modes of operation have been defined: (__Important__)
- __Electronic Code book__, each block uses the same key. (ECB)
- Cipher Block Chaining, input to cipher is already modified from the XOR with previous ciphered text and next plain text blocks. (CBC)
- Cipher Feedback. (CFB)
- Output Feedback. (OFB)
- Counter, each block of plaintext is XORed with an encrypted counter. (CTR)

### Binary Cryptography

Messages are made with bits.

Uses a __XOR__ gate and a key to encrypt the binary message into a ciphertext.

To decrypt it we just need to use a XOR gate with the same key.

The obtained ciphertext gives an attacker zero information about the plaintext.

### Substitution Boxes

This method defines a __matrix__ where each __cell__ is the corresponding cipher for that row and column input.

Given a string made of bits:
- It splits it in $2$ blocks.
- The first block is the __row__.
- The second block is the __column__.
- The identificated cell is the cipher of the input string.

![|500](https://i.imgur.com/PK4v3MJ.png)

### Data Encryption Standard (DES)

It's a variation of the Feistel network.

2DES is not more secure than single DES:
- Encrypt plain with $2^{56}$ size keys.
- Decrypt cypher with $2^{56}$ size keys.
- Compare to find a match.

So 2DES expected security of $2^{112}$ size keys is not real.

3DES is more secure than single DES:
- It uses keys of bigger size.

### Advanced Encryption Standard (AES)

Uses $10$ __rounds of invertible transformation__ to compute the result ciphertext.

Each round works by:
1) __S-box substitution__ step.
2) __Permutation__ step.
3) __Matrix multiplication__ step.
4) __XOR__ step with key.

## Stream Ciphers

In a way, stream ciphers are block ciphers with __block size of length__ $1$.

Requires:
- __Large keys__ to work.
- __Long periods without repetition__.
- __Statistically unpredictable__.

### RC4 (ARCFOUR)

Uses __bytes__ for its operations.

Widely used for SSL/TLS.

# Hash

The objective of a __hash function__ is to:
- Produce a __fingerprint__ of a data.

The function should be:
- __Usable for all sizes__ of data.
- Produce a __fixed-size output__.
- Relatively __easy to compute for any given input__.
- Computationally __impossible to find the input of a hash value__.
- Computationally __impossible to find different inputs with same hash value__.

## How it works (Simple hash function)

A simple hash functions:
- Uses bit-by-bit __XOR__ of every block.
- Iterates through all the characters in same position for all blocks.
- Hash value for position $i$ is computed from XOR of every character in $i$ position of every block.

## Secure Hash Algorithm (SHA)

Uses $256$, $384$, or $512$ bit hash values.

__Block size__ for SHA-$N$ is: $2N$. (Not for 384) (Always use __upper value__ if N has more values)

__Security value__ for a SHA-$N$ is: $N/2$. (Always use __lower value__ if N has more values)

# Message Authentication

## HMAC

It's derived from [[Third Year/Cybersecurity/Rielaborato#MAC (Message Authentication Code)|MAC]].

It uses cryptographic hash code plus MAC.

It's generally faster than MAC.

It's used in:
- IP security.
- Transport layer security. (TLS)
- Secure electronic transaction. (SET)

### HMAC Objectives

- Usage of __available hash functions__.
- Maintain __performance__ of original hash functions.
- Easy __replaceability of hash function__ in use.

### HMAC Structure

![|400](https://i.imgur.com/4ZmCV6P.png)

### Security of HMAC

Depends on the cryptographic __strength of the used hash function__.

# Public-key Cryptography (Or Asymmetric Cryptography)

Asymmetric cryptography is used to:
- __Exchange a secret key__ that is used for __symmetric cryptography__.

![|500](https://i.imgur.com/nQ6ldSR.png)

## Advantages of public-key cryptography

- No need to communicate private keys.
- Provides __authentication__ of the sender, because only he should have his private key used to encrypt.
- Provides __confidentiality__ of the sent message, because only the receiver should be able to decryt.
- Brute-force is computationally impossible.

## Limits of public-key cryptography

- It's __computationally expensive__ to use.
- __Less efficient__ because it's slow and expensive.
- __Not everything is encrypted__ because it's slow and expensive.
- Private-key encrypted messages can be decrypted by anyone.
- Public keys __can be modified__ by someone.

## Digital Signature

A signature __testifies__ some information.
- The signature's user __is binded__ to this information.

It provides:
- Message __integrity__.
- __Non-repudiation__.

## Digital Certificate

A digital certificate is a __document__ that __certifies__ the relationship between a __public key and its owner__.

This is done with a __digital signature__.

But then we need to __verify__ this signature with another public key.

This public key __needs to be trusted__:
- Trusted public keys are stored in certificates of __certification autorities__ (CA).

![|700](https://i.imgur.com/bc71AZk.png)

### Certification Authority (CA)

A certification authority is an __organization__ that __issues digital certificates__.

Its function is to:
- __Receive application__ for keys that wants to be trusted.
- __Verifies applicant's identity__, checks their trustworthiness.
- __Store public keys__.
- __Protect public keys__ from unauthorized modification.
- __Delete keys__ that are __invalid__ or __expired__.

Certification authorities are __organized in a hierarchy__ called:
- Public Key Infrastructure. (__PKI__)
- The standard is __X.509__

To verify a certificate:
- It needs to verify all the signatures from the bottom to the top.

A certificate is __made of__:
- Public key with the identity of the key's owner.
- Signature of a trusted third party.

## RSA (Public key Algorithm)

RSA is based on the knowledge that:
- Given a product of __two large prime numbers__.
- Those two prime numbers cannot be easily determined. 

It uses:
- Exponentiation of integers modulo a large number

![|500](https://i.imgur.com/t6XidL7.png)

### RSA attacks

- __Brute force__, tries all possible private keys.
- __Math attack__, tries to factor the product of two primes.
- __Timing attack__.
- __Chosen ciphertext attack__.

#### Timing attack

A __snooper__ can determine a private key by:
- Keeping track of how long a computer takes to decipher messages.

To counter this attack:
- __Constant time__, make sure that all computation take the same time.
- __Random delays__.
- __Blinding__, make the computing of what ciphertext bits unknown.

## Other Public key Algorithms

- Digital Signature Standard. (DSS)
- Elliptic-Curve Cryptography. (ECC)
- El Gamal.

# Internet Security Protocols and Standards

## (Secure) Multipurpose Internet Mail Extension (MIME and S/MIME)

It's a standard that provides the ability to:
- Encrypt using public key.
- And signing of e-mail messages.

### How it works: Sign + Encrypt

![|600](https://i.imgur.com/9UpnNSg.png)

### How it works: Decrypt + Verify

![|600](https://i.imgur.com/7EAKnXH.png)

### Signed and Clear-Signed data

The __preferred algorithm__ used for __signing__ S/MIME messages is:
- RSA signature.
- Or DSA signature of a SHA-256 message hash.

#### How it works

1) Take the message to be sent and map it into a fixed size code of 256 bits using SHA-256.
2) The 256 bit digest (output) is unique for that message, meaning it's impossible to modify it.
3) S/MIME uses RSA to encrypt the digest plus the sender's private RSA key.
4) The result is the digital signature, which is binded to the message.

The receiver of the message will:
1) Use RSA to decrypt the signature using the sender's public RSA key.
2) Verify the signature.

### Enveloped Data

The __default algorithm__ used for __encrypting__ S/MIME messages are:
- AES.
- RSA.

## DomainKeys Identified Mail (DKIM)

It's a __specification__ of cryptographically signing e-mail messages permitting a signing domain to claim resposibility for a message in the mail stream.

## Internet mail architecture

- Message handling system. (MHS)
- Mail transfer agent. (MTA)
- Mail user agent. (MUA)
- Mail delivery agent. (MDA)
- Message store. (MS)
- Simple Mail Transfer Protocol. (SMTP)

## S/MIME and DKIM comparison

S/MIME signs only the message content:
- Header information about the sender's origin can be modified by attackers.

DKIM allows good senders to prove that they did send a particular message.

DKIM prevents forgers from __masquerading__ as good senders.

## Secure Sockets Layer and Transport Layer Security (SSL and TLS)

It's a set of protocols that __relies on TCP__.

### TLS Concepts

A __TLS session__ is an association between a client and a server.

It is created by the __handshake protocol of TCP__.

It __defines a set of crpytographic security parameters__.

It is __used to avoid the expensive negotiation__ of new parameters for each connection.


A __TLS connection__ is a transport that provides a suitable type of service.

Every connection is associated with one session.

### TLS Record protocol operation

It provides two services:
- __Confidentiality__, handshake protocol defines a __shared secret key__ that is used for symmetric encryption of TLS payloads.
- __Message integrity__, handshake protocol also defines a __share secret key__ that is used to form a message authentication code (MAC).

### Change Cipher Spec Protocol (1/4 TLS specific protocols)

It's the simplest one out of four.

It consist of __a single message__ which consists of:
- A __single byte__ with the value $1$.

The only purpose of this message is to:
- __Cause pending state to be copied into the current state__.

This will lead to the __update of the cipher suite__ in use.

### Alert Protocol (2/4)

Used to transmit __TLS-related alerts__.

Alert messages are __encrypted__.

There are two severity values for the message:
- Warning.
- Fatal.

If fatal then:
- TLS __immediately terminates the connection__.
- __No new connections on this session can be made__.

### Handshake Protocol (3/4)

Used __before any application data is transmitted__.

It allows the server and client to:
- __Authenticate each other__.
- __Negotiate encryption and MAC algorithms__.
- __Negotiate cryptographic keys to be used__.

It works by sending a series of messages between client and server.

The exchange has __four phases__:

![|500](https://i.imgur.com/QNx52fH.png)

### Heartbeat Protocol (4/4)

A __periodic signal__ generated by the __system's hardware or software__ that:
- Indicates normal operation.
- Or used __to synchronize other parts of a system__.

It's typically used to:
- __Monitor the availability of a protocol entity__.
- Tell the sender if the receiver is __still alive__.
- __Generate activity in the connection__ during idle moments.

It's used during the __phase 1__ of the handshake protocol.

## SSL/TLS Attacks

There are four categories of SSL/TLS attack:
- On the handshake protocol.
- On the record and application data protocols.
- On the public key infrastructure.
- Other.

### Heartbleed exploit (Handshake protocol attack)

Normal work of handshake protocol:
1) Client sends heartbeat request with payload.
2) Server copies request into its memory.
3) Server replies with heartbeat response and payload.
4) Client verifies payload.

__Heartbleed exploit__:
1) Client sends heartbeat request with __disguised payload__.
2) The payload __seems tiny but is actually larger__.
3) Server copies request and the disguised payload into memory.
4) Server replies with heartbeat response.
5) And includes a __large payload with other data from server memory__.
6) Client obtains extra data like keys, passwords and other secret information.

## HTTPS (HTTP over SSL) (HTTP Secure)

It's a combination of HTTP and SSL to:
- Implement __secure__ communication between browser and server.

## IP Security (IPsec)

__TLDR__: A set of application security mechanism below the transport layer that provide strong security.

Various application security mechanisms:
- S/MIME.
- Kerberos.
- SSL/HTTPS.

Security concerns __cross protocol layers__.

When implemented inside a __firewall or router__:
- It provides __strong security__ to all passing traffic.
- It's resistant to bypass.

### IPsec in Transport mode

Protects only the payload.

Used for host-to-host communication.

### IPsec in Tunnel mode

Encapsulates the entire IP packet, including the original IP headers.

Used for site-to-site communication. (site-to-site VPN)

## Virtual Private Network (VPN)

A virtual network that is __built on top of an existing network infrastructure__.

It can provide:
- __Secure__ communications mechanism for data and other information transferred between two endpoints.

It is based on the __use of encryption__.

A VPN's security objectives are:
- __Confidentiality__.
- __Integrity__.
- __Peer authentication__.
- Replay protection.
- Access control.
- Traffic analysis protection.

A VPN's __usability__ objectives are:
- Transparency, VPN should be invisible to users, software and hardware.
- Flexibility, VPN can be used between users, applications, hosts and websites.
- Simplicity.

### Tunneling

Operation of a network connection on top of another network connection.

Tunneling allows two hosts or sites to:
- __Communicate through another network__ that they do not want to use directly.

Tunneling offers the basic method for providing a VPN.

### SSL VPN

It's a VPN which services include:
- __Authentication__.
- __Encryption__.
- __Access control__.
- __Endpoint security control__.
- __Intrusion prevention__.

## Anonymity: Tor

The central point is:
- __Ask someone else to send it for you__.

Encryption __only protects the content of the traffic__, not the __sender__.

VPNs can't provide anonymity because:
- __VPN providers will collaborate with the law__.

### Tor idea

The concept for Tor is:
- Messages are repeatedly encrypted.
- Then they are sent through many network nodes called __onion routers__ or __Tor relays__.
- Each relay __removes a layer of encryption__ to unconver routing instructions.
- Then based on those instructions it sends the message to the next relay.
- So only the first router knows the source.
- And only the last router knows the destination.

$3$ Tor relays are used for each connection:
- The __entry__ relay knows only the sender's location.
- The middle relay knows nothing.
- The __exit__ relay knows only the website.

### Tor + HTTPS

If an user uses Tor without HTTPS:
- The exit relay knows everything.
- The last distance between exit relay and website contains everything.
- So if the packet is sniffed, replicated, ...
- Then GGs.

If an user uses Tor with HTTPS:
- The exit relay only knows the website it need to sent the packet.
- The last distance between exit relay and website contains only the website address.
- So no information can be sniffed, replicated, ...
- GGs.

