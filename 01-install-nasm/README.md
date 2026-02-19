# Install NASM on Ubuntu 24.04

**NASM**, which stands for Netwide Assembler, is an assembler for the x86 and x86-64 computer architectures. It is used to convert assembly language code into machine code that can be executed by the CPU.

This tutorial explains how to install NASM on Ubuntu 24.04.

## Install NASM
Update the package lists:
```sh
sudo apt update
```

Execute the following command to install NASM:
```sh
sudo apt install -y nasm
```

We can check NASM version as follows:
```sh
nasm --version
```

# Testing NASM
Create a main.asm file:

```sh
nano main.asm
```

Add the following code:
```asm
section .data
    hello: db 'Hello world', 0x0A ; Define a string with a newline character
    helloLen: equ $-hello         ; Calculate string length

section .text
    global _start                 ; Entry point for the program

_start:
    mov eax, 4                    ; System call number (sys_write)
    mov ebx, 1                    ; File descriptor (stdout)
    mov ecx, hello                ; Pointer to the string
    mov edx, helloLen             ; Length of the string
    int 0x80                      ; Call kernel

    mov eax, 1                    ; System call number (sys_exit)
    xor ebx, ebx                  ; Exit code 0
    int 0x80                      ; Call kernel
```
Compile a code:
```asm
nasm -f elf64 -o test.o main.asm
```

Link object file and create an executable:
```sh
ld test.o -o test
```

Note: if ld command is not present in the system, it can be installed with sudo apt install -y binutils command.

Run a program:
```sh
./test
```

# Uninstall NASM
If NASM is no longer needed, you can remove it using the following command:
```sh
sudo apt purge --autoremove -y nasm
```