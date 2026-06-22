# Flowchart
<img width="748" height="817" alt="Screenshot 2026-06-21 at 22 01 16" src="https://github.com/user-attachments/assets/5c3f7a79-4b3e-4c29-b7c0-bab15922d1c6" />


# Disccussion of Challenges
The hardest part was just keeping track of all the 0s and 1s. When you have to convert each letter to 8 bits and then XOR them one by one, it gets messy really fast and I kept losing my place. I had to go back and redo a couple of them because I misaligned the bits.

The other thing that tripped me up at first was understanding why XOR works for encryption at all. It felt weird that just doing the same operation twice gets you back to the original. Once I thought about it more it started to make sense, but it was not obvious at first.

# Encryption Process

Message: cat  
Key: dog

## Step 1: Convert message to binary (ASCII)

| Character | ASCII | Binary   |
|-----------|-------|----------|
| c         | 99    | 01100011 |
| a         | 97    | 01100001 |
| t         | 116   | 01110100 |

## Step 2: Convert key to binary (ASCII)

| Character | ASCII | Binary   |
|-----------|-------|----------|
| d         | 100   | 01100100 |
| o         | 111   | 01101111 |
| g         | 103   | 01100111 |

## Step 3: Apply XOR bit by bit

c XOR d:
01100011
01100100
--------
00000111

a XOR o:
01100001
01101111
--------
00001110

t XOR g:
01110100
01100111
--------
00010011

## Step 4: Convert to hexadecimal

| Binary   | Hex |
|----------|-----|
| 00000111 | 07  |
| 00001110 | 0E  |
| 00010011 | 13  |

Encrypted message: 07 0E 13


# Decryption Process

To decrypt, we apply XOR again using the same key (dog) on the encrypted binary.

Encrypted binary XOR key:

00000111 XOR 01100100 (d):
00000111
01100100
--------
01100011 --> 99 --> 'c' 

00001110 XOR 01101111 (o):
00001110
01101111
--------
01100001 --> 97 --> 'a' 

00010011 XOR 01100111 (g):
00010011
01100111
--------
01110100 --> 116 --> 't' 

Decrypted message: cat 

The decrypted message matches the original, confirming XOR encryption works correctly.

## XOR with different key and message lengths

What happens if your message is longer than your key? You just repeat the key over and over until it matches the length of the message. For example if your message is "hello" (5 letters) and your key is "ab" (2 letters), you would stretch the key to "ababa" so both are the same length. Then you XOR each letter of the message with the letter above it in the key. It is basically like tiling the key across the message. Simple but it works.
