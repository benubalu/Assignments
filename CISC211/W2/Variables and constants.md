# Flowchart
<img width="586" height="698" alt="Screenshot 2026-06-28 at 22 26 05" src="https://github.com/user-attachments/assets/58dd73d4-030c-4031-b8b0-df795a0dfc91" />


# Challenges

The hardest part was understanding that you cannot just add two values together directly in assembly. I did not realize at first that you have to load one variable into a register first and then add the other one to it before storing the result. I also got confused about where each variable goes since var1 and var2 go in one section and result goes in a different one because it has no initial value. On top of that, the program does not print anything when it runs so I had to use gdb to actually verify that the result was correct, which was something I had never done before and took a little time to figure out.
# Assembly Code

section .text
        global _start

_start:
        ; ======== write your code below ===========

        mov al, [var1]
        add al, [var2]
        mov [result], al

        ; ======== write your code above ===========

        mov eax,1
        int 0x80

segment .bss
        result resb 1

segment .data
        var1 db 10
        var2 db 15

### Code well structured in Jupyter Hub 
<img width="1470" height="807" alt="Screenshot 2026-06-28 at 22 28 38" src="https://github.com/user-attachments/assets/ec3a38d3-7b4b-4149-93b7-4d5f0e291963" />
