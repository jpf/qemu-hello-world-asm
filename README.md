These are the commands to run to boot a small version of GNU/Linux in QEMU, have it print "Hello, World", and then dump out all of the ASM needed to boot linux and print "Hello, World"


    $ git clone git://git.qemu-project.org/qemu.git
    $ cd qemu/
    $ ./configure --target-list=i386-softmmu --enable-debug-tcg --enable-debug-info --enable-debug --enable-trace-backends=simple
    $ make
    $ wget http://wiki.qemu.org/download/linux-0.2.img.bz2
    $ bunzip2 linux-0.2.img.bz2 
    $ ./i386-softmmu/qemu-system-i386 linux-0.2.img -display curses

At this point, edit /sbin/init to display "Hello, World" and end with "/sbin/reboot -p -f"

$ ./i386-softmmu/qemu-system-i386 linux-0.2.img -no-reboot -d in_asm 2>&1 | tee qemu-hello-world-asm
