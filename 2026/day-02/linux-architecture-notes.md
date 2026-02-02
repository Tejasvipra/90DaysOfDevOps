1] Core components of Linux (Kernel, User Space, init/systemd)
init / systemd:
init means initialize
init is the father of all processes
It is the first process that starts when the system boots
Process ID (PID) of init/systemd is always 1
PPID means Parent Process ID
Command to see CPU details:
cat /proc/cpuinfo

Runlevels in Linux (init based):
init 0 – Halt (shutdown)
init 1 – Single user mode (maintenance)
init 2 – Multi-user mode without network (varies by distro)
init 3 – Multi-user mode with network, no GUI
init 4 – Unused / custom
init 5 – Multi-user mode with GUI
init 6 – Reboot
Modern Linux uses systemd, which replaces runlevels with targets.

Kernel:
Kernel is the heart of the operating system
It is a program that directly interacts with hardware
It manages CPU, memory, disk, and devices
OS acts as a mediator between user and hardware
Linux uses a monolithic kernel

User Space:
User space is where users and applications run
It includes commands, shells, libraries, and applications
User space programs do not directly access hardware
They communicate with hardware through the kernel

2] How processes are created and managed
A process is a running instance of a program
When the system boots, system processes start automatically
init/systemd is the first process and starts all other services
Applications need processes to run
Each process uses system resources like CPU, memory, and RAM
Linux manages processes using PIDs, priorities, and scheduling

3] What systemd does and why it matters
systemd is the system and service manager in modern Linux
It starts and manages services during boot
Services are defined using unit files
It allows services to start automatically, stop, restart, and check status
It matters because without systemd, services cannot be managed properly
It makes boot faster and service management easier
