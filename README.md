
# CAS-I Building a CPU and functional OS from scratch

In this project, we’re setting out to create a virtual CPU and operating system, taking cues from systems designed around the 6502 microprocessor. The 6502 has been a staple in the history of computing, powering iconic systems like the Apple II and the Commodore 64. Our goal is to capture the essence of working with such classic hardware but in a modern, virtual environment.  We’ll be leveraging the robust capabilities of the ESP32 dev board as our host hardware. Known for its generous SRAM and ample processing power, the ESP32 provides an ideal platform for developing a capable and efficient emulator.  And it's cheap!  An ESP32-S3-DevKitC-1-N16R8 ESP32 S3 Development Board goes for about $13 on Amazon.

## Starting with the CPU

The first step in our project is to design the CPU. We’re going virtual, which means no soldering irons or physical chips; instead, we’ll use simulation software realize the CPU.  This approach not only saves on cost and space but also allows for easy tweaking and experimentation.

We’ll base our instruction set on the 6502’s, known for its simplicity and effectiveness. However, we’re not just making a carbon copy. We’ll adapt and possibly extend the instruction set to suit our needs, ensuring our virtual CPU is both a nod to the past and a tool for the present.

## Building the OS

With our CPU architecture defined, we’ll move on to developing the operating system. This OS will be tailored to our custom CPU, designed to handle basic I/O operations, memory management, and more. The aim is to create an OS that’s not only functional but also provides a platform for programming and experimentation.

This OS will be simple by modern standards, reminiscent of early computing systems, but with enough functionality to be genuinely useful for educational purposes or just for fun.

## Why This Project?

Embarking on a project like this offers a unique opportunity to delve into the nuts and bolts of computer architecture and operating system design. It’s a hands-on way to understand how software interacts with hardware, and how the designs of the past continue to influence modern computing.

Whether you’re a seasoned programmer, a hobbyist, or a student of computer science, this project promises a rewarding challenge. It’s about learning, experimenting, and paying homage to one of the most influential pieces of computing history, all while creating something new and unique.


