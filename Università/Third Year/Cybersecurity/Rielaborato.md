___

Cybersecurity is the prevention of damage to computers, electronic communication systems and services, including the information contained inside them.

# Computer Security

It's a set of measures and controls that ensure:
- Confidentiality.
- Integrity.
- Availability.
for information system's __assets__.

## Assets

It's a key concept.
An asset is something that is important for a person, a company or an institution, that wants it to be protected.

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

# Key Security Concepts (CIA)

The __confidentiality__ is the concept of:
- Putting restrictions on information access and disclosure.
- Preserving said restrictions.
in order to protect personal privacy and proprietary information.

The __integrity__ is the concept of:
- Maintaining the accuracy and trustworthiness of data.
This is done by protecting the data from unauthorized modification or deletion.
This ensure that the data is:
- complete.
- reliable.
- authentic.
- nonrepudiable, preventing the denying of one's actions and responsabilities.

The __availability__ is the concept of:
- Ensuring timely, reliable access and the use of information.

# Vulnerabilities, Threats and Attacks

![|500](https://i.imgur.com/r6sxc79.png)

## Vulnerabilities

A vulnerability is a weakness in an information system, system security procedures, controls, or implementation that could be exploited or triggered by a threat source.

There are various categories of vulnerabilities:
- Corruption.
- Leaks.
- Unavailable/very slow.

The corruption of information will cause a loss of __integrity__.

A leak of information will cause a loss of __confidentiality__.

When information are unavailable or very slow to access, this will lead to a loss of __availability__.

## Threats

Threats are any circumstance or event that have the potential to exploit vulnerabilities.

They represent a security harm to an asset.

## Attacks

An attack is a threat that is being carried out.

These can be:
- Passive, like an attempt to learn or make use of information from the system, that doesn't affect the system's resources.
- Active, like an attempt to __alter__ system resources or affect their operations.
and can be done by:
- Insiders, so someone who is inside the security perimeter, that is authorized to access system resources.
- Outsider, so someone who is from outside the perimeter.

# Confidentiality

It's the property that describes the __avoidance__ of unauthorized disclosure of information.

More precisely it contains two other related concepts:
- __Data confidentiality__, which assures that private or confidential information is __not__ made available or disclosed to unauthorized people.
- __Privacy__, which assures that individuals can control what information related to them may be collected and stored by others.

## Tools for Confidentiality

We can use the concept of __encryption__ to have confidentiality.
This is done usually by using a secret encryption key, that transform information so that it can only be read using another secret decryption key.
In some cases the decryption key is the same as the encryption key.

__Access control__ is another way to implement confidentiality.
These are rules and policies that limit access to confidential information.
It grants access to information for only strictly necessary people and/or system.

So for example:
- In an university, janitors should't have access to the student's information database, as they are not useful to their work.

__Authentication__ is used as a tool to determine the identity or role that someone has.
- All the login pages we use to enter our accounts are authentication tools.

__Authorization__ is used to determine if a person or system is allowed access to resources, based on an access control policy.

# Integrity

It's the property that describes if something has not been altered in an unauthorized way.

It covers two related concepts:
- __Data integrity__, which assures that information and programs are changed only in a specified and authorized manner.
- __System integrity__, which assures that a system performs its intended function in an correct way, free from any manipulation from unauthorized entities.

Tools used for checking the integrity of informations are:
- __Backups__.
- __Checksums__, so the computation of a function that maps the contents of a file to a alphanumerical value. The mapping depends on the input file, and is designed in a way that even a single bit change will likely result in a differed output value.
- __Data correcting codes__, are methods for storing data in such a way that small changes can be easily detected and automatically corrected.

# Availability

It's the property that something is accessible and modifiable in an expected time by those authorized to do so.

Tools used for availability are:
- __Physical protections__, so infrastructure that keep information available even during unpredicted challenges.
	- For example when there is a blackout, a seconday electric generator is used.
- __Computational redundancies__, which are computers and storage devices that serve as fallbacks/redundancies in the case of failure of the main ones.

# Authenticity

It's the ability to determine that:
- Statements.
- Policies.
- Permissions.
issued by persons or systems are __genuine__.

The primary tool used for this is:
- __Digital signatures__, that allow a person/system to commit to the authenticity of their documents and also to achieve __non-repudiation__.

# Accountability

It's the principle of ensuring individuals and organizations are __responsible__ for their roles, so that the actions of an entity can be __traced uniquely to that entity__.

This supports non-repudiation, deterrence, fault isolation, intrusion detection and prevention, and after-action recovery and legal actions.

# Anonymity

It's the property that certain records or transactions not to be attributable to any individual.

Various tools are used to provide anonymity:
- Aggregation, so combining data from many so that it cannot be tied to any individual.
- Proxies, trusted agents that do actions on behalf of others, so they cannot be traced back.
- Pseudonyms.

# Threat consequences

If a threat turns into a successful attack, the consequences can vary:
- Unauthorized disclosure, which is a threat to __confidentiality__.
	- When this happens, the attacker can __expose__ sensitive data, by releasing it to unauthorized entities.
	- The attacker can gain these information by __intercepting__ the traveling data, or by __infering__ with the data, or by __intruding__ inside the system.
- Deception, which is a threat to either system or data __integrity__.
	- One can be masquerading as another entity, to fabricate information that seems to be from someone who is not actually the author.
- Disruption, which is a threat to __availability__ or system integrity.
- Usurpation, which is a threat to system __integrity__.

# Attack surfaces

When an entity tries to attack a system, it tries to exploit reachable vulnerabilities within the system.

These vulnerabilities, or __attack surfaces__, are divided into categories:
- Network attack surface.
- Software attack surface.
- Human attack surface.

## Network Attack Surface

Every surface that interacts with the outside can be subject to attacks.
The outside is commonly the Internet.
## Software Attack Surface

Software that contains vulnerabilities, like an exploitable line of code, can be used for attacks.

E.g. SQL injections.

## Human Attack Surface

Sometimes personnel can be used to create vulnerabilities, by letting them do something that is going to create a breach in the system's security, such as __social engineering__.

# Cryptographic concepts

The main technique used for providing __confidentiality__ for trasmitted and stored data is called __symmetric encryption__, also called single-key encryption.

This encryption needs to have a strong __algorithm__ to be able to be used securely.
Also both the sender and the receiver must have obtained a copy of the __secret key__ in a secure way.

This key is a __one-time__ use for that session only, so once one of the two parties are done with the session, that key will be useless.

The encryption is on a data block basis, so the plaintext input is divided into blocks, then fed into the algorithm together with the key, to encrypt it.

The __size__ of the key is crucial to a successful encrypted data transmission, because even if the encryption algorithm is secure, if the size of the key is small, one can try to brute-force it by trying every key possible.

To ensure that the encryption is secure, the standard size for a key is $128$ bit.

While brute-force attacks are simple, it is mostly ineffective, because of the size of the key. So there exist another way, called a cryptanalytic attack:
- This method relies on the nature of the algorithm, some knowledge on the general characteristics of the plaintext alphabet.
- It exploits the charateristics of the algorithm to attempt to deduce the key.


The most known symmetric encryption algorithms all use some type of ciphering (block or stream) and keys.

The modern standard is __AES__, that stands for "Advanced Encryption Standard":
- It uses $128$ bit block cipher.
- Can use $128$, $192$ or $256$ bit secret keys.

Another algorithm is __DES__, now considered insecure:
- It uses $64$ bit block cipher and $56$ bit secret keys.

There exist some issues with AES:
- Because each block of plaintext is encrypted using the same key, it's doable for cryptanalysts to be able to exploit regularities in the plaintext.

## Block and stream ciphers

The block cipher:
- Processes the input one block of elements at a time and it produces an output block for each of the input blocks.
- Can reuse keys.
- Is it more commonly used.

The stream cipher:
- Processes the input elements continuously but it produces one element at a time.
- The primary advantage against the block cipher is that it is almost always __faster__ and use far less code.
- It encrypts plaintext one byte at a time.

# Message Authentication

Message encryption is necessary to provide some form of authenticity, but by itself its not a secure form of authentication.

We use encryption and authentication tags together to provide confidentiality, and typically these steps are done separately inside an algorithm.

## MAC (Message Authentication Code)

To provide authentication we can use MACs, these are codes that are obtained by putting a message and a secure key as a input to a MAC algorithm. This will return a MAC for the input message.

A MAC algorithm needs to be not reversible.

By transmitting the MAC binded together with the message we get some form of authenticity.

The receiver needs to have the same secret key used as input to be able to compare the MAC that came together with the message.

## Cryptographic hash function

A hash functions is typically used to produce a __fingerprint__ of a file, message or other block of data. This function is in general, non-injective, meaning that given an output, no other input can result in the same output.

This function generates a set of $k$ bits that is fixed in length from a bigger set of $L$ bits.

Generally a hash function is __not__ useful from a cryptographic standpoint, it needs specific properties.

Hash functions do __not__ take a secret key as input. 

## MAC + Hash function

We can use the message as the input of the hash function, this value is then encrypted with the secret key using a MAC algorithm to create an encrypted hash value, this is then binded with the message and sent to the receiver.

Once received the encrypted hash value will be separated from the message and decrypted using the MAC key, then it will be compared with the hash value obtained from hashing the message only. If both do not have the same value, then it means that the message was corrupted.

## Properties for a useful hash function

A hash function aimed towards authentication usefulness needs to have the following properties:
- Can be applied to a block of data of any size.
- Produces a fixed-length output.
- The hash function needs to be relatively easy to compute for any give input.
- One-way or pre-image resistant, meaning that it is computationally infeasible given a known hash value, to find its input.
- Computationally infeasible to find two different inputs such that both output hash value are the same.

## Public-Key Encryption

It's a form of encryption based on mathematical functions, and is __asymmetric__:
- It uses two separate keys, one public and the other one private.

Both these keys can be used for encrypting and decrypting.

Encryption with public key:
- The data input is encrypted by an encryption algorithm using the receiver's public key.
- The ciphertext (encrypted data) is transmitted to the receiver.
- When received, the ciphertext is decrypted using its own private key. (receiver)
In this way, even if another entity intercepts the ciphertext, he can't decrypt it because he doesn't have the receiver's private key.

Encryption with private key:
- The data input is encrypted by an encryption algorithm using the sender's private key.
- The ciphertext is trasmitted to the receiver.
- When received, the ciphertext is decrypted using the sender's public key.
This is used as a way to verify the sender's signature.

# Authentication

The definition of __user authentication__ is:
- The process by which a user establishes the validity of a claimed (self-declared) identity present inside a system.

## General User Authentication Model Requirements

An authentication model needs to possess these general requirements:
-  Identify and authenticate system users, and associate the user identification with processes or devices acting on his behalf.
	- The system needs to authenticate the identity of a user __before__ allowing them access to the system.
- It is necessary to implement __multi-factor__ authentication to access both privileged and non-privileged accounts.
- It is necessary to implement __replay-resistant__ authentication mechanisms to access both privileged and non-privileged acocunts.
	- Replay-resistant means that the system is secure against attackers who may __capture and reuse__ old authentication information, like tokens and passwords.

It also needs to have some requirements about identifiers and passwords:
- Prevention of the __reuse__ of identifiers for a defined period.
- It needs to disable identifiers that are __inactive__ after a defined period of inactivity.
- It needs to enforce a minimum password __complexity__ when new passwords are created.
- It needs to prohibit the __reuse of old or similar__ password for a defined number of generations.
- Permission to allow __temporary passwords__ that are used for account recovery, but then needs to be changed immediately upon login to a permanent one.
- It is allowed to only store and trasmit cryptographically-protected passwords over cryptographically-protected mediums.

## Authentication Architectural Model

![|500](https://i.imgur.com/NRFlaPJ.png)

This model describes what happens when a new user wants to use a service:
- The subscriber is the user.
- The registration authority is responsible for verifying the user's identity when he first sign up.
- The credential service provider is responsible for issuing and managing user credentials.
- The relying party is a service that the user want to login into.
- The verifier is a generally a service that can verify the identity of a subscriber to a service (RP).

E.g. a user wants to login to a shopping website, and it can do that by using google's login system that is implemented inside the website:
- The user firstly creates a Google account, giving informations like name, birthdate and username to Google's RA.
- The RA confirms the user's details and signals to Google's CSP that a new, verified user needs credentials.
- The CSP prompts the user to create a password (and other authentication methods like 2FA)
- Now the user logs into the shopping website and is redirected to the Google login page.
- The user enters his credentials, which are sent to the verifier, that is Google's login service.
- The verifier successfully validates the user's credentials, and it sends an authenticated assertion to the RP, in this case the shopping website.
- The website receives this assertion and grants the user access to the website.

## Means of Authentication

There are four general means of authenticating a user's identity. These can be used singularly or in combination:
- Something the user __knows__, like a password, PIN or secret aswers.
- Something the user __possesses__, generally tokens, that can be both physical like a key card, or digital like a code inside an authenticator app.
- Something the user __is__, so biometrics, like fingerprints, iris, retina or face.
- Something the user __does__, so dynamic biometrics, like voice pattern, handwriting or a walking style.

The more authentication means a service use, the more its system is secure.

## Assurance levels

An assurance level describes a system's degree of certainty that a user has presented a credential that refers to his identity.

## Passwords

When a user uses a service, he provides his ID (credentials) and password.
The service system compares the given password with the one __stored__ in its DB.

The user's ID:
- Determines that the user is authorized to access the system.
	- In some systems only those who have an ID are allowed to gain access.
- Determines the user's privileges.
	- Some users may have administrator status that enables them to perform critical or protected functions.

### Password Vulnerabilities

Some of the main forms of attack against password-based authentication are:

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

### Password Hashing

The technique used to produce hashed password begins with a hashing algorithm, a salt value and the password:
- A __salt value__ is a random __fixed-length__ value that is combined with the given password.
- The hashing algorithm, given the salt and the password, outputs the corresponding __fixed-length__ hashed password, that is __unique__ (almost) and not revertable.

The hashed password is stored together with its salt in plaintext in the password file for the corresponding user ID.

The salt __does not need to be secret__ because it is only used to create a unique hash, so it all relies on the one-way hashing algorithm, which is designed to be irreversible, and also on the secrecy of the original password.

When a user wants to login, the system uses his user ID to retrieve the associated salt value, and together with the inputted password, these gets thrown into the hashing algorithm. The output of the algorithm is then compared with the stored hashed password.

### Password Cracking

There exist multiple approaches to cracking user-chosen passwords. Two basic ones are:
- Dictionary attack, it uses a large dictionary of __possible__ passwords and it tries each one.
- Rainbow table attack, it uses __pre-computed__ tables to find a password from its hash value.

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
- Smart cards, both with contact and contactless.
- RFIDs.

### Barcodes

Barcodes are simply images that are used to encode some type of information. So they are convenient to use but not very secure. (Attackers can simply take a photo of the barcode)

E.g. boarding passes use barcodes.

### Magnetic Stripe Cards

These are plastic cards with a magnetic stripe containing personalized information about the card holder.

Its vulnerability is that is easy to read and reproduce, because magnetic stripe readers can be purchased at low cost, and writers are only a little bit more expensive.
So often card holders need to use another authentication method like PINs to use their cards.

E.g. (Old) Bank cards.

### Smart tokens

These tokens can be physical or digital devices that securely store cryptographic keys or that generates unique, time-based passcodes.

Physical ones contain an embedded microprocessor.

#### Smart Cards

These are the most important category of smart tokens.

Smart cards contain an entire microprocessor with:
- Processor.
- Memory, that can be:
	- Read-only memory (ROM), that stores data that does not change during the card's life.
	- Electrically erasable programmable ROM (EEPROM), that holds application data and programs.
	- Random access memory (RAM), that holds temporary data generated when application are executed.
- I/O ports.

They are powered by a compatible reader that sends signals that charge for a little bit the microprocessor so that it can send back the information stored inside the memory.

### Electronic Identity Cards (eIDs)

These are smart cards that have been __verified__ by the government as valid and authentic.

There are various different types of functions for an eID, most of these are or have optional features:
- `ePass`, used for __offline verification__ of __biometric__ identity, reserved for government access. (CIE)
	- Its __mandatory__ to have this function.
- `eID`, used for __identification__.
- `eSign`, used for creating electronic __signatures__.


## Biometrics

Biometric refers to any measure used to uniquely identify a person based on biological or physiological traits.

These systems work by incorporating __sensors__ or __scanners__ to read in biometric information, then it compare this information with stored __templates__ of accepted users before granting access.

The comparation is based on __pattern recognition__, so its technically complex and expensive when compared to passwords and tokens.

![|500](https://i.imgur.com/8k8imaM.png)

### Biometric Accuracy dilemma

The comparison between the inputted profile and a reference profile is based on a single numeric value.

If the input value is greater than the decision threshold, then a match is declared, and it is granted access.

So the dilemma is in how low should the decision threshold be:
- A value too low can result in more matches for convenience but also more prone to false matches.
- A value too high will increase the robustness of the biometric system, resulting in an increased security, but will inevitably lead to lower matches, even if its the genuine user trying to authenticate.

![|500](https://i.imgur.com/1KxnqPe.png)

### Operations of a Biometric Authentication System

There are $3$ operations that a biometric authentication system needs to provide:
- Enrollment.
- Verification.
- Identification.

#### Enrollment

Each individual who is to be included in the database of authorized users must first be __enrolled__ in the system.

This is done by inserting an identifier (name), password or pin, and binding these information with some type of biometric characteristic of the user.

The biometric data obtained then gets digitalized into a set of number, and it will be the user's __template__.

This template is maintained together with the identifier and the pin inside the system.

#### Verification

When a user tries to verify itself, he needs to insert his pin and also his biometric data.

The system extracts the corresponding feature from the biometric input and compares it to the template stored for the user. If there is a match, then the system authenticates the user.

#### Identification

For identification, the user only needs to insert his biometric data.

The system will then compare the biometric-obtained template with the set of stored templates. If there is a match, then the user is identified.

# Access Control

Access control is a process that regulates access to a system, based on security policies. Access is permitted only to authorized entities.

There are various models of access control:

- Discretionary access control (DAC), where access is based on the __identity__ of the user requesting access and on the access __rules__ that determines what requestors are (and are not) allowed to do.
	- E.g. UNIX-based system use this type of access control.

- Mandatory access control (MAC), where access is based on __comparing__ security labels with security clearances.
	- E.g. Most military classification scheme use MAC, with naming that goes from `top secret` to `unclassified`.

- Role-based access control (RBAC), where access is based on the __roles__ that users have inside the system and on __rules__ that states what accesses each role have.

- Attributed-based access control (ABAC), where access is based on __attributes__ of the user, the __resource__ to be accessed, and on the __current environments__.


## Subject, Object and Access Rights

Subjects are entities that are capable of accessing objects.

Objects are resources to which access needs to be or is controlled.

Access right describes the way in which a subject may access an object. These right include but could be not all of them:
- Read, write, execute, delete, create and search.

## Discretionary Access Control (DAC)

Access is granted by another entity which enables the requestor to access the requested resource.

### Access Matrix

Often this is provided by using an __access matrix__.
(E.g. in UNIX systems, a user can do `chmod xx7` to give full access rights to all other entities for a file he owns)

This model takes a subject-centered approach to access control:
- It defines for each subject, the list of the objects for which he has nonempty access control rights.

### Access Control List

It defines for each object (resource) a list which enumerates __all__ the subjects (user) that have access rights to it, and for each subject, it shows the access rights (read, write, execute) that the subject has for the object.

(_Do not use resource or user, instead use object and subject_)

__Extended rules__ to this model are:
- Transferring rights for a resource.
- Creation of another subject.
- Owner access right to a subject.

### Capabilities

It defines for each subject, the list of the object for which he has nonempty access control rights, together with the specific rights (read, write, execute) for each object.

(So its the reverse of the access control list)

### Organization of the Access Control Function

Every access to a resource from a subject is mediated by the __controller__ for that resource. The controller's decision is based on the current contents of the access matrix.
Certain subjects have the authority to make __changes__ to the access matrix.

## Mandatory Access Control (MAC)

In this model of access control, each subject and object is assigned to a __security class__.

Security classes form then a strict __hierarchy__, called __security levels__.

Each subjects has a property called __security clearance__ of a given level.

Each object has a property called __security classification__ of a given level.

The confidentiality of this model is based on two properties:
- __No read up__, where a subject can only read an object of less or equal security level.
- __No write down__, where a subject can only write into an object of greater or equal security level.

## Role-based Access Control (RBAC)

In this model of access control, we define __roles__ and then specify access control rights for each of these roles, instead of granting right for subjects directly.
Its goal is to describe organizational access control __policies__.

Generally the rights of each role is based on the job's function:
- E.g. a worker of a call center of a bank doesn't need access to the full database of the bank.

Using this model increases flexibility and scalability in policy administration:
- Its easy to meet new security requirements.
- Will reduce errors in administration.
- Will reduce the cost of administration.

### Role Hierarchy (RBAC$1$)

Most of the times organizations are going to have many operations that are common to a large number of roles. So instead of creating new roles for each job position, we use a hierarchy of roles based on inheritance of permissions.

So the more specialized a role is, the more permission it has.

### Constrains caused by security policies of an organization (RBAC$2$)

These constrains are:
- Mutually exclusive roles, where a user cannot be assigned to mutually exclusive roles at the same time.
- Cardinality, so we have a constrain on the maximum number of roles a user can have.
- Prerequisite roles, where a user can be assigned to a role only if it is already assigned to another specific role.

### Consolidation (RBAC$3$)

The procedure of consolidating the role hierarchy (RBAC$2$) and the constrains (RBAC$3$) is then finalized in the RBAC$3$.

## Attribute-based Access Control (ABAC)

In this model of access control, we can define __attributes__ on both resources and subjects, and based on these, give or not access to a object for a subject.

Its the most __flexible__ and __expressive__ model of access control.

System that use this model are capable of enforcing all the other models of access control.

ABAC implements __policies__ to govern allowable behavior. A policy is a set of rules and relationships (between subject and object).
These policies are based on the privileges of subjects and how objects are to be __protected__ under which environment conditions.

Systems that use ABAC controls access to its objects by evaluating __access control policies__ against the attributes of entities, operations, and the __environment__ relevant for a request.

![|500](https://i.imgur.com/jHDcZI0.png)

Eg. a movie theater can use ABAC to enforce allowed access to movies based on the subject's age and the object's rating (R, PG-13, G).

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