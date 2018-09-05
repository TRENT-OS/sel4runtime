<!--
     Copyright 2018, Data61
     Commonwealth Scientific and Industrial Research Organisation (CSIRO)
     ABN 41 687 119 230.

     This software may be distributed and modified according to the terms of
     the BSD 2-Clause license. Note that NO WARRANTY is provided.
     See "LICENSE_BSD2.txt" for details.

     @TAG(DATA61_BSD)
-->
# Calling Conventions for Intel 64

* `%rsp` contains the stack pointer,
* `%rbp` contains the frame pointer,
* `%rax` contains the return value, and
* `%rbx`and `%r12` to `%r15` are callee-save registers.

Additionally:

* The stack must always be 16-byte aligned, i.e. `%rsp` mod 16 == 0.

# Prologue

1. push `%rbp` onto the stack,
2. read the current value of `%rsp` into `%rbp`

```asm
push %rbp
mov  %rsp, %rbp
```

# Epilogue

```asm
leave
ret
```

# Argument Passing

Arguments are passed on the stack in `%rbp+8+(8 * n)`