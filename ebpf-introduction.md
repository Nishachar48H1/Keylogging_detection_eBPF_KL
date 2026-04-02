# Introduction to eBPF

eBPF (extended Berkeley Packet Filter) is a Linux technology that allows safe execution of small programs inside the kernel.

It helps monitor system activities such as keyboard input, USB events, and system calls in real time.

eBPF programs are verified by the kernel before execution to ensure safety and stability.

In this project, eBPF is used to monitor keyboard behavior and detect abnormal keystroke injection attacks caused by malicious USB devices like Rubber Ducky.
