|                                          | Catalyst & AMD GPU Pro             | ROCm 1.x                             |
| ---------------------------------------- | ---------------------------------- | ------------------------------------ |
| Core Features                            |                                    |                                      |
| Shared Virtual  Memory                   | Coarse Grained                     | Coarse Grained HSA Memory Allocation |
| Memory Allocation                        |                                    |                                      |
| Page Migration Support                   | NO                                 | NO                                   |
| HMM Support                              | NO                                 | NO                                   |
| Raw Pointers                             | NO                                 | NO                                   |
| Platform Atomics                         | NO                                 | YES                                  |
| User Mode Queues                         | NO                                 | YES                                  |
| Hardware Scheduler for Queues            | NO                                 | YES                                  |
| Max Number of Queues  Restrictions       | Theoretical Unlimited Kernel Level | 1024                                 |
| Max Number of Processes                  | 512                                | >512                                 |
| Max Number of Concurrent  Independent Processes | 1                                  | 15                                   |
| Process Preemption                       | NO                                 | YES                                  |
| User Mode SDMA                           | NO                                 | YES                                  |
| Defined Memory Model                     | NO                                 | YES                                  |
| Process Concurrency                      | NO                                 | YES                                  |
| Peer to Peer GPU Support with  Large BAR | NO                                 | YES                                  |
| Peer to Peer GPU VIA RDMA                | NO                                 | YES                                  |
| Peer to Peer DirectGMA                   | YES                                | NO                                   |
| DirectGMA  for    SD/IO                  | YES                                | NO                                   |
| Headless  OpenGL on EGL  Interop         | NO                                 | YES                                  |
| OpenGL/X11 Interop                       | YES                                | YES                                  |
| Largest Single Memory  Allocation for  GPU Memory | 3/4 total GPU Memory               | Total GPU Memory - 250 Megbytes      |
| Developent Features                      |                                    |                                      |
| Full HSA API Support                     | NO                                 | YES                                  |
| Open Source Driver and  Runtime          | NO                                 | YES                                  |
| Command Line Profiler                    | YES                                | YES                                  |
| Open Source Native LLVM AMDGPU  Compiler | NO                                 | YES                                  |
| Native ISA Programing Binary  Interface  ( ABI) | NO                                 | YES                                  |
| Finalizer (HSAIL to SC  Shader  Compiler ) | YES                                | YES                                  |
| Programing Languges                      |                                    |                                      |
| HCC Single Source Compiler C  & C++      | YES  Limited Features              | YES                                  |
| HIP C++ Kernel Language with C  Runtime API with HIPIFY for Porting CUDA applications | NO                                 | YES                                  |
| OpenCL 1.2                               | YES                                | YES                                  |
| OpenCL 2.0                               | YES                                | Kernel Languge and Limited Host API  |
| OpenMP 4.5 Support                       | NO                                 | YES - In development                 |
| Continum IO Python  Support              | No                                 | YES                                  |
| Command line Offline   Compiler ( Compiles GPU Kernels  independent of the driver. ) | NO                                 | YES                                  |
| GCN Assembler  Support                   | NO                                 | YES                                  |
| OpenUCX                                  | NO                                 | YES - In development                 |
| OpenMPI                                  | NO                                 | YES - In development                 |
| MPICH                                    | NO                                 | NO                                   |
| System Management  Features              |                                    |                                      |
| System Management API                    | NO                                 | YES                                  |
| Clock Management API and  Public Tools   | NO                                 | YES                                  |
| CPU  Support                             |                                    |                                      |
| Intel Core i3,i5,i7                      | Optimized for Intel Core   CPU's   | Optimized for version V3 or newer    |
| Intel Xeon  E5 & E7                      | Supported                          | Optimized for version V3 or newer    |
| AMD Ryzen                                | Supported                          | Optimized                            |
| AMD Naples                               | Supported                          | Optimized                            |
| GPU ASIC Support                         |                                    |                                      |
| Hawaii ( S9150, S9170, S9100,  W9100, W8100) | YES                                | YES                                  |
| Fiji ( Fiji Nano,  S9300x2)              | YES                                | YES                                  |
| Tonga ( W7100, S7100, S7150,  S7150x2)   | YES                                | YES                                  |
| Polaris (  WX4100,WX5100,WX7100, RX460,RX470, RX480) | YES                                | YES                                  |
