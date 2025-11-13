___

# Attacks

## Passive



## Active

This type of attacks are made to alter system resources and/or their operation.

# Confidentiality

It's the property that describes the __avoidance__ of unauthorized disclosure of information.

More precisely it contains two other related concepts:
- Data confidentiality, which assures that private or confidential information is __not__ made available or disclosed to unauthorized people.
- Privacy, which assures that individuals can control what information related to them may be collected and stored by others.

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


