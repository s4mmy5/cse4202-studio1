# Studio 1: Cross-compiling

## Questions
1. Contributors
- Jonathan Rodriguez-Gomez

2. Linux Lab Information
- hostname: iht32-1501.engr.wustl.edu
- CPU info:
	- Model Name: Intel(R) Xeon(R) CPU E5-2630 v3 @ 2.40GHz
	- Logical Cores: 16

3. Private Directory
Directory "/project/scratch01/compile" does not exist. Only "/project/scratch01/compiling" exists and that one is just a dangling symlink. I will continue with the steps in my home directory, which has path: "/home/compute/j.rodriguezgomez/Classes/CSE4202/cse4202-studio1".

- ls -ld output: 
```
drwx------. 2 j.rodriguezgomez domainusers 4096 Jan  9 13:51 j.rodriguezgomez/
```

- Explanation of chmod 700: The basic permission system in linux divides permissions based on owner, group, everyone else. For each of these categories a 3-bit field is used to one-hot encode permissions; 4 corresponds to read, 2 corresponds to write, and 1 corresponds to execute. By issuing the 700 argument we are achieving the following permissions:
    - owner (j.rodriguezgomez): obtains read, write and execute permissions.
    - group (domainusers): obtains no permissions.
    - everyone else: obtains no permissions.

4. Kernel Info
- Kernel Version: 5.10.17
- Kernel Version NAME: Kleptomaniac Octopus

5. Kernel Configuration Options

- Brief Function Description
  - Name: Kernel performance events and counters
  - Description: Provides an abstraction of software and hardware performance events i.e. the kernel provides a consistent way to access features such as performance counter registers.
  - Symbol: PERF\_EVENTS


- Reasoning behind Preemptive Model:
After quickly exploring the documentation explains how our chosen option "Preemptible Kernel (Low-Latency Desktop)" prioritizes low latency over throughput since kernel code can be interrupted without explicit preemption points.

    - Another possible reason: kernel preemption might make our system more resilient to bugs in our kernel modules since the system can always context switch to a higher priority section.

6. Compilation Time

Start:    Fri Jan  9 15:38:49 CST 2026
End:      Fri Jan  9 16:24:00 CST 2026
Duration: 00:45:11

Reason for cross-compilation: As we saw at the start of this studio the linuxlab is running in an x86\_64 machine, however raspberry pis use an arm64 ISA, therefore native compilation in x86\_64 would not be compitable with our raspberry pi, therefore we must use a cross-compilation toolchain.
