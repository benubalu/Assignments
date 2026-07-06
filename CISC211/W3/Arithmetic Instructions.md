# Flowchart
<img width="416" height="641" alt="Screenshot 2026-07-05 at 23 20 45" src="https://github.com/user-attachments/assets/f25b08a8-66b6-408b-abc0-7b65d007555e" />

# Challenges
Honestly this one was harder than the previous labs because there were four separate equations and each one worked a little differently. The negation and multiplication took me a while because I kept trying to do too much at once and had to break it down step by step. The addition one was easier to understand but I still had to be careful about which register I was using. The division was the one that confused me the most because I had to pick numbers that would divide evenly and also make sure everything was set up in the right register before running it. I spent more time on this one than I expected just trying to get the order of instructions right.
# Codes
## Equation 1
section .text
        global _start

_start:
        mov al, [var1]
        neg al
        mov bl, 10
        imul bl

        mov [result], ax

        mov eax, 1
        int 0x80

segment .bss
        result resb 2

segment .data
        var1 db 5
        
## Equation 2
section .text
        global _start

_start:
        mov eax, [var1]
        add eax, [var2]
        add eax, [var3]
        add eax, [var4]
        mov [result], eax

        mov eax, 1
        int 0x80

segment .bss
        result resb 4

segment .data
        var1 DD 5
        var2 DD 10
        var3 DD 15
        var4 DD 20
        
## Equation 3

section .text
        global _start

_start:
        mov al, [var1]
        neg al
        mov bl, [var2]
        imul bl
        movsx eax, ax
        add eax, [var3]
        mov [result], eax

        mov eax, 1
        int 0x80

segment .bss
        result resb 4

segment .data
        var1 db 3
        var2 db 4
        var3 DD 20
        
## Equation 4

section .text
        global _start

_start:
        mov eax, [var1]
        mov ebx, 2
        mul ebx
        mov ebx, [var2]
        sub ebx, 3
        div ebx
        mov [result], eax

        mov eax, 1
        int 0x80

segment .bss
        result resb 4

segment .data
        var1 DD 10
        var2 DD 5
