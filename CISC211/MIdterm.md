
# Question 1

## Values
```nasm
; var1 = 8, var2 = 3, var3 = 8
; result = (8 + 2) / (8 - 3) = 10 / 5 = 2
```
## Code 
```nasm
section .text
        global _start

_start:
        ; var1 = 8, var2 = 3, var3 = 8
        ; result = (var1 + 2) / (var3 - var2) = 10 / 5 = 2

        mov ax, [var1]          ; load var1 into ax
        add ax, 2               ; ax = var1 + 2 = 10
        mov bl, [var3]          ; load var3 into bl
        mov cl, [var2]          ; load var2 into cl
        sub bl, cl              ; bl = var3 - var2 = 5
        div bl                  ; al = quotient, ah = remainder
        mov [result], al

        ; display result on screen (ASCII representation)
        add al, 48              ; convert result to ASCII
        mov [output], al
        mov eax, 4
        mov ebx, 1
        mov ecx, output
        mov edx, 1
        int 0x80

        mov eax, 1
        int 0x80

segment .bss
        result resb 1
        output resb 1

segment .data
        var1 dw 8
        var2 db 3
        var3 db 8
```
## Register Table 

After division, the quotient and remainder are stored as follows:


<img width="232" height="168" alt="Screenshot 2026-07-10 at 12 43 20" src="https://github.com/user-attachments/assets/5a544179-6f9d-48af-aaf0-fccdc4ab1376" />


## Screeenshot

<img width="1187" height="776" alt="Screenshot 2026-07-10 at 12 53 50" src="https://github.com/user-attachments/assets/e33fe809-2ec8-4d41-a11a-eefeba2dd0d0" />

# Question 2



<img width="658" height="440" alt="Screenshot 2026-07-10 at 13 12 46" src="https://github.com/user-attachments/assets/2eaddd69-7a87-4423-9450-344432414838" />


# Question 3
## Design and thought process

To check if a number is odd or even without using AND or OR, I used the TEST instruction since the lecture mentions it can do exactly that without changing the original value. The idea is that every odd number has a 1 in the least significant bit and every even number has a 0 there. TEST checks that bit and sets the zero flag depending on the result. From there I used jz to jump to the even block if the flag was set, the same way the lecture example uses jz to jump between blocks. If the jump does not happen the number is odd and the program prints "odd number", otherwise it prints "even number".

## Code
```nasm
section .text
        global _start

_start:
        mov eax, [number]       ; load number into eax
        test eax, 1             ; test least significant bit
        jz even                 ; if ZF=1 (bit is 0), number is even

odd:
        mov eax, 4              ; sys_write
        mov ebx, 1              ; stdout
        mov ecx, msg_odd        ; pointer to odd message
        mov edx, len_odd        ; length of odd message
        int 0x80
        jmp done

even:
        mov eax, 4              ; sys_write
        mov ebx, 1              ; stdout
        mov ecx, msg_even       ; pointer to even message
        mov edx, len_even       ; length of even message
        int 0x80

done:
        mov eax, 1              ; sys_exit
        int 0x80

segment .bss
        result resb 1

segment .data
        number DD 7
        msg_odd  db 'odd number', 0xA
        len_odd  equ $ - msg_odd
        msg_even db 'even number', 0xA
        len_even equ $ - msg_even
```
## Screenshot
<img width="1187" height="774" alt="Screenshot 2026-07-10 at 13 08 47" src="https://github.com/user-attachments/assets/63c4d9fb-cfe7-4d89-8cd3-e35b36b9c02f" />
