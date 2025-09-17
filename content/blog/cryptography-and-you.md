---
title: "Cryptography and You"
date: 2025-09-05T00:00:00-04:00
draft: false
categories: ["tech"]
summary: "I've taken cryptography for granted."
---

I've taken cryptography for granted. I once took an introduction to cryptography during
undergrad, but back then I only really appreciated the beauty of the mathematics and none of the practical
benefits. 

But the older I get and the more technology integrates itself into our daily lives, the more I realize I should be
taking this cryptography business more seriously. My mindset has shifted from "why worry? I have nothing to hide"
to "oh, people can exploit all types of information... Maybe I should be more careful".

These next few posts is me trying to convince myself that it *is* important. It starts with understanding how cryptography works
at a high level, then how it impacts me currently, and then how to be deliberate about using it.

### The view from 30000 feet
First of all, what is cryptography? It is the study of securing communication. Plain and simple. It has a long history,
and the original techniques were pretty rudimentary. For example, the Caesar cipher (named after, you guessed it, 
Julius Caesar) creates a ciphertext by taking each letter $c$ in the plaintext, and replacing it with $c + k \mod N$
where $k$ is an integer (Caesar chose $3$) and $N$ is the size of the alphabet. 

Fast forward to now, and we have two relevant schemes: asymmetric cryptography (known as public key cryptography) and 
symmetric cryptography. We will focus on these since these are the main schemes we interact with on a daily basis.

#### Symmetric Cryptography
In this scheme, there is a single shared secret key $k$ that both parties use to encrypt the plaintext (original message) and 
decrypt the ciphertext (encrypted message). 

The two most common algorithms in this category is AES and DES. 

A major downside of this scheme is that both parties need to have this shared secret key. If you are meeting someone for the 
first time over the Internet, the only choice might be to share the secret key over an unencrypted channel and hope that an 
attacker isn't paying attention. Or it is? 

#### Asymmetric Cryptography
Instead of two parties having to share the same secret key, we can introduce the concept of public keys. Supposing we
have two parties (Alice and Bob) communicating. Alice generates two keys $(k^A_\text{pub}, k^A_\text{priv})$ and Bob generates 
two keys $(k^B_\text{pub}, k^B_\text{priv})$. Whenever Alice wants to send a message to Bob, she encrypts her message using 
her private key $k^A_\text{priv}$ and Bob's public key $k^B_\text{pub}$. Bob then uses his private key $k^B_\text{priv}$ to 
decrypt the message. Alice and Bob only have to share their public keys with each other in order to encrypt their messages. 

The most common algorithm in this category is RSA.

This scheme is called asymmetric because the amount of work needed to decrypt an encrypted message depends on having 
the proper private key. With the private key, it's easy to decrypt. Without the private key, it's nearly impossible. 
Hence the asymmetry. 

Believe it or not, we are using these algorithms every day to keep our data and communication channels secured. They are
baked into many of the tools and protocols that power our every day workflows, like `ssh` and `https`. In the next post
I will talk about where we can find them!