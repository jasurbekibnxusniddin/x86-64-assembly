# x86-64-assembly
x86-64 Assembly

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