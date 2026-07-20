# Flowcharts
<img width="416" height="588" alt="Screenshot 2026-07-19 at 23 13 46" src="https://github.com/user-attachments/assets/615d2fa2-8f56-4838-8d7b-e506a0e106cb" />


# Challenges
Task 1 made me stop and think even though it looks simple, because the optimized counter from lecture uses loop, and loop only works with ecx, so since the task asked for ebx I had to rebuild the same idea by hand with dec and jnz, checking in gdb that ebx really did count down the same way. Task 2 needed more planning on paper than typing, I kept mixing up which register held the old value and which held the new sum, so I wrote out the first few iterations by hand before trusting the code, and seeing ebx land on 55 in gdb is what made the need for a temporary register in edx finally make sense. Task 3 reused the pointer walking idea from the arrays example but swapped the add for a cmp and jg pair to find the biggest value instead of the sum, and my first attempt skipped the first element because I started comparing before pointing ecx at the array, which I caught by checking the counter in gdb before the loop ran.
# Code
## Task 1
```nasm

section .text
        global _start

_start:
        mov ebx, 10             ; ebx will work as the counter

count:
        dec ebx                 ; decrement ebx by 1 each pass
        jnz count                ; loop while ebx is not zero

        mov eax, 1
        int 0x80

```



## Task 2
```nasm
section .text
        global _start

_start:
        mov eax, 0               ; F0
        mov ebx, 1               ; F1
        mov ecx, 9               ; number of steps needed to reach F10 (55)

fib:
        mov edx, ebx             ; save current b before it changes
        add ebx, eax             ; ebx = a + b (next fibonacci number)
        mov eax, edx             ; a becomes the old b
        loop fib                 ; ecx decrements automatically

        mov [result], ebx        ; store the final fibonacci number (55)
        mov eax, 1
        int 0x80

section .bss
        result resb 4

        
```





## Task 3
```nasm

section .text
        global _start

_start:
        mov ecx, array            ; ecx points to the first element
        mov eax, [ecx]            ; assume the first element is the largest
        mov edx, 3                ; edx = array length, used as the counter

top:
        cmp eax, [ecx]             ; compare current largest with this element
        jg skip                    ; if eax is already bigger, skip the update
        mov eax, [ecx]              ; otherwise update the largest value

skip:
        add ecx, 4                  ; move to the next element (4 bytes away)
        dec edx                     ; decrement the counter
        jnz top                     ; loop until edx reaches 0

        mov [largest], eax          ; store the largest value found
        mov eax, 1
        int 0x80

section .data
        array dd 7, 22, 15

section .bss
        largest resb 4
```
