# Flowchart
<img width="590" height="753" alt="Screenshot 2026-06-28 at 21 21 10" src="https://github.com/user-attachments/assets/37e93cdf-5f71-43f0-8fee-4a6e3d9bcf46" />

# Challenges
Honestly the hardest part was just understanding what was going on in general. Everything in assembly feels very manual and there are a lot of moving parts to keep track of at once. I had to re-read the lecture notes and the Hello World example multiple times before I felt comfortable enough to start writing anything. When I finally ran the code the first time, the output was not coming out right because I had accidentally used the same length for all three messages, so some lines were getting cut off. It took me a bit to figure out what was causing it but once I fixed the lengths it worked.

# Assembly code 

## Expected output
 
I came,

I saw,

I conquered.
 
## Source code – caesar.asm

```nasm
section .data
    msg1 db 'I came,', 0xA
    len1 equ $ - msg1

    msg2 db 'I saw,', 0xA
    len2 equ $ - msg2

    msg3 db 'I conquered.', 0xA
    len3 equ $ - msg3

section .text
    global _start

_start:
    mov eax, 4
    mov ebx, 1
    mov ecx, msg1
    mov edx, len1
    int 0x80

    mov eax, 4
    mov ebx, 1
    mov ecx, msg2
    mov edx, len2
    int 0x80

    mov eax, 4
    mov ebx, 1
    mov ecx, msg3
    mov edx, len3
    int 0x80

    mov eax, 1
    xor ebx, ebx
    int 0x80
```
