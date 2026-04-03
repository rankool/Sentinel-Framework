Sentinel-Framework
Windows 11 Systems Monitoring & Telemetry Research
A thread-safe, modular C++20 framework designed for low-level systems event interception and memory-resident telemetry. This project explores the implementation of user-mode hooks with a focus on resource isolation and minimal system footprint.

Core Architecture
Thread Isolation: The monitor operates on a detached worker thread to ensure the primary application remains responsive during high-frequency event interception.
RAII Management: Leverages the Resource Acquisition Is Initialization (RAII) pattern to manage Windows HHOOK and HANDLE lifecycles, preventing memory leaks and orphaned hooks.
Thread Safety: Utilizes std::mutex and std::lock_guard for synchronized access to telemetry buffers, ensuring data integrity during concurrent read/write operations.

Technical Trade-offs
User-Mode vs. Kernel-Mode: Chose WH_KEYBOARD_LL (Low-Level) hooks to maintain a balance between granular interception and system stability without requiring a signed kernel driver.
Asynchronous Dispatch: Implemented a message-loop architecture that separates interception from data processing, reducing the risk of "lagging" the system input stream.

Build Requirements
Standard: C++20
Platform: Windows 10/11
Compiler: MSVC (Visual Studio 2022)

