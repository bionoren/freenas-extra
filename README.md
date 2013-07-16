FreeNAS + Crashplan
===================

# Build Instructions

See [http://www.bionoren.com/blog/2013/03/freenas-crashplan/](http://www.bionoren.com/blog/2013/03/freenas-crashplan/) 

# Prebuilt ISOs


Every method of running Crashplan on FreeBSD has unresolved limitations thus within this repository you will find three editions of FreeNAS + Crashplan:

    FreeNAS-8.3.1-RELEASE-p2-x64.iso (Linux Compatiblity Client + linux-sun-jre1.7.0)
    FreeNAS-8.3.1-RELEASE-p2-x64-jdk16.iso (FreeBSD Native + JDK16)
    FreeNAS-8.3.1-RELEASE-p2-x64-openjdk7.iso (FreeBSD Native + OpenJDK7)
    
Check the issues section for a overview of the pros/cons of each edition.

**Note:** *There is not, and will never be support for 32bit platforms.*

# Native (without LCE)

When running Crashplan without the linux compatibility environment you need to replace JTUX/JNA to address a number of crashing bugs when using Crashplan natively on FreeBSD. In addition you should also modify bin/run.conf as follows:

    -Dos.name=Linux (optional; if your version of Java supports it)
    -Djava.nio.channels.spi.SelectorProvider=sun.nio.ch.KqueueSelectorProvider

Additionally you may need to symlink libc.so to libc.so.6:

    ln -s /usr/lib/libc.so /usr/lib/libc.so.6

Finally you should delete libjtux64.so or symlink it to libjtux.so.

# Debugging

* Check engine_error.log and service.log.0 for exceptions and/or crashes. See Known Issues below. 
* If Crashplan's JNA library is newer than the one provided, try building devel/jna on a FreeBSD computer and using the generated jar file. 
* Every method of running Crashplan
on FreeBSD has unresolved limitations. Be sure to check the issues list to see
if the community is stuck too.

