# Core System🧑‍🔧
---
## 🚏Overall 
In this topic, we will disscuss about the system core of **Arm Cortex**. In addition, I will use **STM HAL library** to initialize these modules by hand and applicate them.

**P/S: This topic is created base on almost STM references and CubeIDE**

---
## 🗒️Table of Contents
In this section, I will list all the features that I concern on CubeIDE.

Here're them:

I. **DMA (Direct Manager Access)**

II. **GPIO (General Purpose In-Out)**

III. **IWDG (Independent Watchdog)**

IV. **NVIC (Nested Vectored Interrupt Controller)**

V. **RCC (Reset & Clock Controller)**

VI. **SYS (SysTick timer)**

VII. **WWDG (Window Watchdog)**

---
## I. DMA (Direct Manager Access)

---*Reference links:*--- 

* 🦾Getting started with DMA:

https://wiki.st.com/stm32mcu/wiki/Getting_started_with_DMA

* 🎞️What is DMA? Direct Memory Access Explained!! (SIMPLIFIED):
GH-issue_number https://youtu.be/LqsDmPFKmXU?si=pKmuUt5zVYp40Ro3

\------------------------

In a process, normally, when the external device interface with microcontroller, it has to send a request to the PC, the PC acess MCU's memory and PC send the data to to external device. However, the PC just be able to hanlde that process one at each time. So if there are many external devices interface to PC at the same time, the whole process will be degraded!😫 

To sovle it, we using the Direct Memory Access - AKA DMA👽. It is a powerful feature of computer systems that enables input/output (I/O) devices to access the main system memory (random-access memory, or RAM) independently of the central processing unit (CPU). In simpler terms, DMA allows devices like disk drives, graphics cards, network cards, and sound cards to directly interact with memory without involving the CPU. Here are the key points:  

📶Use Cases for DMA:
* Data Transfer Rate: When the CPU cannot keep up with the data transfer rate (e.g., high-speed disk I/O), DMA ensures efficient data movement.
* Parallel Processing: DMA enables the CPU to work on other tasks while I/O devices handle data transfers.
* Reduced CPU Overhead: Computers with DMA channels can transfer data between devices with significantly less CPU involvement compared to systems without DMA.
* Memory-to-Memory Operations: DMA can also copy or move data within the system memory, offloading expensive memory operations from the CPU.

💠DMA Modes of Operation:
* Standard DMA (Third-Party DMA): In this mode, a dedicated DMA controller generates memory addresses and initiates memory read or write cycles. The CPU interacts with registers in the DMA controller to set up the transfer.
* RDMA (Remote Direct Memory Access): RDMA allows computers in a network to exchange data directly in main memory without involving the processor, cache, or operating system of either computer.
