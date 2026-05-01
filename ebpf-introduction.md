# Introduction to eBPF

eBPF (extended Berkeley Packet Filter) is a Linux technology that allows safe execution of small programs inside the kernel.

It helps monitor system activities such as keyboard input, USB events, and system calls in real time.

eBPF programs are verified by the kernel before execution to ensure safety and stability.

It is the successor to the Berkeley Packet Filter (BPF, with the "e" originally meaning "extended") filtering mechanism in Linux and is also used in non-networking parts of the Linux kernel.

It is used to safely and efficiently extend the capabilities of the kernel at runtime without requiring changes to kernel source code or loading kernel modules.Safety is provided through an in-kernel verifier which performs static code analysis and rejects programs which crash, hang or otherwise interfere with the kernel negatively

# Core Concept

eBPF programs are:

1. Written in restricted C
2. Compiled to bytecode (via LLVM/Clang)
3. Loaded into the kernel using the bpf() syscall
4. Verified for safety by the kernel verifier
5. Executed on specific kernel or user-space events

# Architecture and Working

The working of eBPF follows a structured pipeline:

1. Program Development
eBPF programs are typically written in a restricted subset of the C programming language. This restriction ensures compatibility with kernel safety requirements.

2. Compilation
The program is compiled into eBPF bytecode using compilers such as LLVM/Clang.

3. Loading into Kernel
The compiled bytecode is loaded into the Linux kernel via the bpf() system call.

4. Verification
Before execution, the kernel verifier analyzes the program to ensure:

1. Memory safety
2. Absence of infinite loops
3. Controlled resource usage

If the program violates any rule, it is rejected.

5. Execution and Attachment
After successful verification, the program is attached to predefined hooks (e.g., system calls, network events) and executes when those events occur.

6. JIT Compilation
The bytecode is optionally translated into native machine code by the JIT compiler, improving execution performance significantly.
