# Assignment 4 Report

## Basic Information

- Assignment: Assignment 4 - Scheduling
- Repository commit used for handin: `[fill after git commit]`
- Time spent: `[fill your total hours here]`

## Implementation Summary

This assignment implements three required parts:

1. Per-process variable-length time slice.
2. `setpriority(int priority)` system call with priority range `[0, 10)`.
3. Scheduling statistics printed when a process exits.

The implementation uses:

- `priority` and `remain_quantum` in `struct proc`.
- `run_time`, `wait_time`, `create_time`, `ready_since`, and `exit_time` for accounting.
- Timer-interrupt based time-slice consumption in `usertrap()`.
- Round-robin queue reuse after a process exhausts its quantum.

The available quantum is reset with:

```c
FULL_QUANTUM - priority * 2
```

where a lower priority value means a higher scheduling priority.

## Files Modified

- `os/proc.h`
- `os/proc.c`
- `os/sched.c`
- `os/trap.c`

## Checkpoint

Required command on Linux:

```bash
make runsmp
```

Expected user-level test:

- `schedtest` appears in `applist:`
- The kernel can stably pass all 10 rounds
- Final output contains:

```text
===
schedtest: 10-times tests passed
===
```

## Screenshots

Insert the following screenshots in the PDF version:

1. Boot log showing `make runsmp` started successfully.
2. `applist:` output showing `schedtest`.
3. Final successful `schedtest` output.

## Notes

- This report template was prepared on Windows.
- Final screenshots must be collected after running the kernel on Linux with the RISC-V toolchain and QEMU installed.
