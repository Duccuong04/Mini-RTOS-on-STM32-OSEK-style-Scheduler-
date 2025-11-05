# Mini RTOS on STM32F103

## Overview
This project implements a simple real-time operating system (RTOS) for the STM32F103 microcontroller.
It demonstrates basic concepts of task creation, stack management, and context switching using the PendSV interrupt on the ARM Cortex-M3 core.

## Features
- Task Control Block (TCB) with stack pointer and linked structure
- Manual stack initialization for each task
- Cooperative and preemptive scheduling
- Context switching handled in assembly (PendSV_Handler)
- UART logging for debugging

## File Description
| File | Description |
|------|--------------|
| main.c | Initializes the system, creates tasks, and starts the scheduler |
| kernel.h | Defines data structures and kernel function prototypes |
| kernel.s | Assembly file that implements context switch and scheduler launch |
| uart.h | Provides UART initialization and logging functions |

## How it Works
1. Each task is created with its own stack using osKernelStackInit.
2. The first task is started by calling osSchedulerLaunch.
3. When PendSV interrupt occurs, the current task context (registers) is saved to its stack, and the next task context is restored.
4. The scheduler switches tasks in a round-robin manner.
