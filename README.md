# PS2Link

**PS2Link** is a **PlayStation 2 debugging and communication tool** that allows a PC to interact with the PS2 over a network connection. It provides a console, file transfer, and debugging interface, enabling developers to run and debug `.ELF` applications on the PS2 from a PC.

---

## Features

- Remote execution of `.ELF` applications on PS2.  
- Debug console over TCP/IP or UDP.  
- File transfer to/from the PS2.  
- Memory inspection and modification.  
- Network-based I/O for homebrew development.  

---

## Supported Platforms

- **PlayStation 2**: all FAT models with network adapter (SCPH-30000 to SCPH-50000, SCPH-10350 Ethernet Adapter).

---

## Components

- **ps2link.elf**: ELF loader running on the PS2.  
- **host program (ps2client)**: PC-side application for sending commands, transferring files, and debugging.  
- **Network drivers**: Requires `smap.irx` or `smap-linux.irx` loaded on the PS2 for Ethernet support.  

---

## Installation

1. Copy `ps2link.elf` to your PS2 memory card or USB device.  
2. Ensure a network driver is loaded (`smap.irx` for retail, `smap-linux.irx` for PS2 Linux).  
3. Connect PS2 and PC to the same LAN.  
4. Launch `ps2link.elf` on the PS2.  
5. Run the host program on your PC and connect using the PS2's IP address.

---

## Usage

### Launch ELF from PC

```bash
ps2client -c ps2link.elf
```

### Transfer Files

```bash
ps2client -t /path/to/file
```

### Debugging

```bash
ps2client -d
```

## Debug Console

Use host program to open a console session to the PS2.

Commands:
    memread <addr> <len>: Read memory.
    memwrite <addr> <data>: Write memory.
    run <elf>: Execute an ELF file.

---

## Required modules

`PS2Link` requires the following IRX modules:

    PS2LINK.IRX               from: ps2link
    PS2DEV9.IRX                     ps2sdk
    PS2IP-NM.IRX                    ps2sdk
    NETMAN.IRX                      ps2sdk
    SMAP.IRX                        ps2sdk-eth
    IOPTRAP.IRX                     ps2sdk
    POWEROFF.IRX                    ps2sdk
    UDPTTY.IRX                      ps2sdk
