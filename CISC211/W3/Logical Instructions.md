# Flowchart
<img width="548" height="654" alt="Screenshot 2026-07-05 at 23 48 44" src="https://github.com/user-attachments/assets/eab2e2e4-c127-4737-87c3-c834124d80e3" />

# Challenges
The XOR part was actually pretty straightforward once I understood that XORing any value with itself always gives 0 because every bit cancels itself out. The TEST instruction was harder to wrap my head around because it works like AND but does not actually change the original value, which felt strange at first. I had to re-read the lecture a couple of times to understand why that is useful. The jump instructions like jz were also new to me and figuring out how to use them to branch the code depending on the result took some trial and error.
# Tasks
## Task 1
XOR compares each bit of two values and returns 0 when both bits match. So when you XOR any value with itself every single bit matches and the whole thing becomes 0. It is basically a quick way to clear a register without having to move a 0 into it
```nasm
section .text
        global _start
 
_start:
        mov eax, [var1]
        xor eax, eax
        mov [result], eax
 
        mov eax, 1
        int 0x80
 
segment .bss
        result resb 4
 
segment .data
        var1 DD 25
```
 
## Task 2
The TEST instruction does the same thing as AND but does not actually change the value you are testing. It just checks it and sets the flags. Here it checks the last bit of the number to figure out if it is odd or even. If that bit is 0 the number is even, if it is 1 it is odd. The useful part is that the original number stays exactly the same after the check 
```nasm
section .text
        global _start
 
_start:
        mov eax, [var1]
        test eax, 1
        jz even
        mov [result], dword 1      ; odd: store 1
        jmp done
even:
        mov [result], dword 0      ; even: store 0
done:
        mov eax, 1
        int 0x80
 
segment .bss
        result resb 4
 
segment .data
        var1 DD 8
```
 
