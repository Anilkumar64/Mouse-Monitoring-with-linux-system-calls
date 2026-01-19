linux-input-monitor

A lightweight Linux input event monitor written in C++17 that reads raw events from the Linux kernel via /dev/input/eventX.

This project is inspired by tools like evtest, but built from scratch for learning, clarity, and systems-level understanding.

🚀 Features

Reads raw input events from Linux input subsystem

Supports keyboard and mouse devices

Decodes:

Event type (EV_KEY, EV_REL, EV_SYN, …)

Key / button codes

Press / release / hold values

Clean modular C++ design

Built using CMake

Includes a helper script to list input devices

🧠 What this project demonstrates

This project shows hands-on knowledge of:

Linux /dev/input/event* devices

Kernel → userspace I/O using read()

Memory-safe handling of struct input_event

Event-driven programming

Multi-file C++ project structure

CMake-based builds

Practical Linux debugging skills

This is systems programming, not toy code.

📁 Project Structure
linux-input-monitor/
├── CMakeLists.txt
├── include/
│   └── input_event_parser.hpp
├── src/
│   ├── main.cpp
│   ├── device.cpp
│   ├── event_reader.cpp
│   └── event_printer.cpp
├── tools/
│   └── list_devices.sh
└── build/

🔧 Build Instructions
Requirements

Linux

GCC / Clang with C++17 support

CMake ≥ 3.10

Build (out-of-source)
mkdir build
cd build
cmake ..
make


The binary will be created as:

build/input-monitor

▶️ Usage
1️⃣ List available input devices
./tools/list_devices.sh


Example output:

AT Translated Set 2 keyboard  -> /dev/input/event3
Logitech USB Mouse           -> /dev/input/event6

2️⃣ Run the monitor (requires root)
sudo ./input-monitor /dev/input/event3

📌 Example Output
Time: 1716289123.123456 [EV_KEY] KEY_A PRESSED
Time: 1716289123.223456 [EV_KEY] KEY_A RELEASED
Time: 1716289124.001234 [EV_REL] Code: REL_X Value: -2
Time: 1716289124.001235 [EV_SYN]

⚠️ Notes & Warnings

Root permissions are required to read /dev/input/event*

Event numbers (event0, event1, …) are not stable

Do NOT use this on production systems without understanding permissions

This tool is for learning, debugging, and exploration

🛠 Technologies Used

C++17

Linux input subsystem

POSIX system calls (open, read, close)

CMake

Bash (helper script)

📈 Future Improvements

Planned or possible extensions:

Full key-code to name mapping

--keyboard / --mouse filters

Event logging to file

Statistics mode (keypress count, mouse distance)

Signal handling (Ctrl+C graceful exit)

Replace shell script with --list C++ option

👤 Author

Anil Kumar (Anilkumar64)
Linux systems programming learner with a focus on low-level I/O and kernel interfaces.