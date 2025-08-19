---
title: "One-Pass Assembler"
excerpt: "A system programming project that implements a one-pass assembler in C++ which generates object programs from assembly code.<br/><img src='/images/one_pass_assembler.png'>"
collection: portfolio
permalink: /projects/one-pass-assembler
---

* Need for an Assembler  
    * Computers cannot directly execute assembly language instructions; they require machine-readable object code.  
    * Assemblers are used to convert human-readable assembly code into object code that can be executed by the machine.  
    * A **one-pass assembler** is more efficient than a two-pass assembler, since it builds the symbol table and generates object code simultaneously.  
    * Handling **forward references** (symbols used before being defined) is one of the major challenges in one-pass assembly.

<img src='/images/one_pass_assembler.png'>

* About the project  
    * Implemented in **C++** as part of a System Programming assignment.  
    * Uses an **OPTAB (Opcode Table)** to map assembly mnemonics to machine opcodes.  
    * Builds a **SYMTAB (Symbol Table)** to manage labels and addresses dynamically.  
    * Handles **forward references** using backpatching techniques.  
    * Supports assembler directives such as `WORD`, `BYTE`, `RESB`, `RESW`.  
    * Generates object program records in the standard format:  
        * **Header Record (H)**  
        * **Text Records (T)**  
        * **End Record (E)**  

<hr>

* Example Input (Assembly Code)  
```asm
COPY    START   1000
FIRST   STL     RETADR
CLOOP   JSUB    RDREC
        LDA     LENGTH
        COMP    ZERO
        JEQ     ENDFIL
        JSUB    WRREC
        J       CLOOP
ENDFIL  LDA     EOF
        STA     BUFFER
        LDA     THREE
        STA     LENGTH
        JSUB    WRREC
        LDL     RETADR
        RSUB
RETADR  RESW    1
LENGTH  RESW    1
ZERO    WORD    0
THREE   WORD    3
EOF     BYTE    C'EOF'
BUFFER  RESB    4096
        END     FIRST


Read more about project on <a href="https://github.com/ath-vk/One-Pass-Assembler-/tree/master" target="_blank" rel="noopener noreferrer">github</a>.