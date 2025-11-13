___

# Message Authentication

## Cryptographic hash function

A hash functions is typically used to produce a __fingerprint__ of a file, message or other block of data.

This function generates a set of $k$ bits that is fixed in length from a bigger set of $L$ bits.

Non-injective means that no other input can result in the same output.

Generally a hash function is __not__ useful from a cryptographic standpoint, it needs specific properties.

Hash functions do __not__ take a secret key as input. 

## MAC + Hash function

We can use the message as the input of the hash function, this value is then encrypted with the secret key using a MAC algorithm to create an encrypted hash value, this is then binded with the message and sent to the receiver.

Once received the encrypted hash value will be separated from the message and stripped of the MAC key, then it will be compared with the hash value obtained from hashing the message only. If both do not have the same value, then it means that the message was corrupted.

# Properties for a useful hash function

A hash function aimed towards authentication usefulness needs to have the following properties:
- Can be applied to a block of data of any size.
- Produces a fixed-length output.
- The hash function needs to be relatively easy to compute for any give input.
- One-way or pre-image resistant, meaning that it is computationally infeasible given a known hash value, to find its input.
- Computationally infeasible to find two different inputs such that both output hash value are the same.

# Public-Key Encryption Structure

