
Tools Used in CS-149
====================

For this class you'll need the RISC-V versions of a couple different tools: QEMU 5.1+, GDB 8.3+, GCC, and Binutils.

If you are having trouble getting things set up, please come by to office hours or post on Canvas. We're happy to help!

### Debian or Ubuntu
```bash
sudo apt-get install git build-essential gdb-multiarch qemu-system-misc gcc-riscv64-linux-gnu binutils-riscv64-linux-gnu 
```
### Arch Linux
```bash
sudo pacman -S riscv64-linux-gnu-binutils riscv64-linux-gnu-gcc riscv64-linux-gnu-gdb qemu-emulators-full
```
### Installing on Windows

Students running Windows are encouraged to either install Linux on their local machine or use WSL 2 (Windows Subsystem for Linux 2).

We also encourage students to install the [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701) tool in lieu of using Powershell/Command Prompt.

To use WSL 2, first make sure you have the [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10) installed. Then add [Ubuntu 20.04 from the Microsoft Store](https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6). Afterwards you should be able to launch Ubuntu and interact with the machine.

_IMPORTANT: Make sure that you are running version 2 of WSL. WSL 1 is implemented with a different architecture than WSL 2, which may cause future problems with the 6.1810 labs. To sanity check, run `wsl -l -v` in a Windows terminal to confirm that WSL 2 and the correct Ubuntu version are installed._

To install all the software you need for this class, run:

```bash
$ sudo apt-get update && sudo apt-get upgrade
$ sudo apt-get install git build-essential gdb-multiarch qemu-system-misc gcc-riscv64-linux-gnu binutils-riscv64-linux-gnu
```

From Windows, you can access all of your WSL files under the _"\\\\wsl$\\"_ directory. For instance, the home directory for an Ubuntu 20.04 installation should be at _"\\\\wsl$\\Ubuntu-20.04\\home\\\<username>\\\"_.

### Running a Linux VM

If you're running an operating system on which it's not convenient to install the RISC-V tools, you may find it useful to run a Linux virtual machine (VM) and install the tools in the VM. Installing a Linux virtual machine is a two step process. First, you download the virtualization platform.

*   [**Multipass**](https://multipass.run/) (free, available for Mac, Linux, Windows)
*   [**OrbStack**](https://orbstack.dev/) (free, available for Mac. Recommend on Mac)

Once the virtualization platform is installed, start an Ubuntu:22.04 Virtual Machine,
install the tools required for **Debian/Ubuntu** above inside the VM. 

### Installing on macOS

It is recommended to follow the **Running a Linux VM** section to install the required tools.

However, if you want to install directly on macOS, here is the guide:
**Note : for Mac ARM (Apple Silicon Chip), gdb is not available, you may need to use lldb instead.**
First, install developer tools:
```bash
$ xcode-select --install
```
Next, install [Homebrew](https://brew.sh/), a package manager for macOS:
```bash
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
Next, install the [RISC-V compiler toolchain](https://github.com/riscv/homebrew-riscv):
```bash
$ brew tap riscv/riscv
$ brew install riscv-tools
```
The brew formula may not link into /usr/local. You will need to update your shell's rc file (e.g. [~/.bashrc](https://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html)) to add the appropriate directory to [$PATH](http://www.linfo.org/path_env_var.html).
```bash
PATH=$PATH:/usr/local/opt/riscv-gnu-toolchain/bin
```
Finally, install QEMU:
```bash
brew install qemu
```
Testing your Installation
-------------------------

To test your installation, you should be able to compile and run xv6. You can try this by following the instructions in the [first lab](util.md).

You can also double check your installation is correct by running the following:

```bash
$ qemu-system-riscv64 --version
QEMU emulator version 5.1.0
```
And at least one RISC-V version of GCC:

```bash
$ riscv64-linux-gnu-gcc --version
riscv64-linux-gnu-gcc (Debian 10.3.0-8) 10.3.0
...
```

```bash
$ riscv64-unknown-elf-gcc --version
riscv64-unknown-elf-gcc (GCC) 10.1.0
...
```

```bash
$ riscv64-unknown-linux-gnu-gcc --version
riscv64-unknown-linux-gnu-gcc (GCC) 10.1.0
...
```
* * *

This is derivative work based on [MIT 6.1810 Operating System Engineering](https://pdos.csail.mit.edu/6.828/2023/) used under Creative Commons License.

[![Creative Commons License](https://i.creativecommons.org/l/by/3.0/us/88x31.png)](https://creativecommons.org/licenses/by/3.0/us/)