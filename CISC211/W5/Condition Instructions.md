# Flowcharts
<img width="432" height="359" alt="Screenshot 2026-07-19 at 22 19 00" src="https://github.com/user-attachments/assets/8e944323-d956-45be-bb1f-7e47beef808e" />


# Challenges

The even number sequence was not too bad once I understood how the counter example from the lecture worked. The main thing I had to figure out was how to increment by 2 instead of 1 to get only even numbers. The hardest part was the largest number task because the lecture example only shows three numbers but here I needed five. I had to repeat the same compare and jump pattern two more times and keep track of which label was which. It took a few tries to get the order right and make sure the largest value was always in eax by the time the program reached the exit block.

# Code 
## Even numbers up to 20
 ```nasm
section .text
        global _start

_start:
        mov eax, 0              ; start from 0

increase:
        add eax, 2              ; increment by 2 (only even numbers)
        mov [tmp], eax          ; save eax
        push eax                ; push eax value

        mov eax, 4
        mov ebx, 1
        mov ecx, tmp
        mov edx, 1
        int 0x80                ; print number

        mov eax, 4
        mov ebx, 1
        mov ecx, space
        mov edx, 1
        int 0x80                ; print newline

        pop eax                 ; restore eax value
        cmp eax, 20             ; end at 20
        jl increase             ; jump if less

        mov eax, 1
        int 0x80

segment .bss
        tmp resb 1

section .data
        space dd 10             ; newline character

 ```

## Largest number among five integer values

 ```nasm
section .text
        global _start

_start:
        mov eax, [num1]
        cmp eax, [num2]         ; compare num1 with num2
        jg label1
        mov eax, [num2]

label1:
        cmp eax, [num3]         ; compare current largest with num3
        jg label2
        mov eax, [num3]

label2:
        cmp eax, [num4]         ; compare current largest with num4
        jg label3
        mov eax, [num4]

label3:
        cmp eax, [num5]         ; compare current largest with num5
        jg exit
        mov eax, [num5]

exit:
        mov [largest], eax      ; store the largest value
        mov eax, 1
        int 0x80

section .data
        num1 dd 15
        num2 dd 42
        num3 dd 8
        num4 dd 73
        num5 dd 31

segment .bss
        largest resb 2

 ```
        
