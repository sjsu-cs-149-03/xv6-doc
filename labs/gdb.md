# Common issues with running GDB

1. Running GDB from the wrong directory. You need to run `make qemu-gdb` AND `riscv64-unknown-elf-gdb` (or the alternative `gdb-multiarch`) inside the `xv6-labs` directory. Not in `~` and not in `xv6-labs/kernel` or `xv6-labs/user`.

2. Running the wrong type of gdb. If you run just `gdb`, it will not be able to understand the machine code that your binary is in (your computer is using x86 and the binary `kernel/kernel` is using RISCV). You need to run `riscv64-unknown-elf-gdb` or the alternative `gdb-multiarch`. If you are on Athena, run `riscv64-unknown-elf-gdb`.

3. gdb not being able to find what you are trying to debug. You might need to run `target remote localhost:<PORT NUMBER FROM POINT 6 ABOVE>`.

4. Not adding in the file that you are trying to debug. If you get an error that says something about running `file` command or unknown symbol, you need to run `file kernel/kernel` so that gdb knows where to look to find the code you are trying to debug.

5. If you quit GDB, and then re-run `gdb-multiarch` (or `riscv64-unknown-elf-gdb`) without also re-running `make qemu-gdb`, weird things might happen. Most of the times it works but sometimes it does not and then you just need to restart both and start over. This might exhibit itself in a behavior of GDB not being responsive to your requests.

6. Not using GDB to help you debug! I know that using GDB is really annoying in the beginning but it is super super helpful in the later labs and we want you all to know the basic commands to make debugging less painful in the future.
* * *
		
This is a derivative work based on [MIT 6.1810 Operating System Enginnering Fall 2023](https://pdos.csail.mit.edu/6.828/2023/labs/gdb.html) 
used under [Creative Commons License](https://creativecommons.org/licenses/by/3.0/us/).

[![Creative Commons License](https://i.creativecommons.org/l/by/3.0/us/88x31.png)](https://creativecommons.org/licenses/by/3.0/us/)