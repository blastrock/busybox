busybox for flix
================

This is a very small fork of busybox to make it work for flix, with a bundled
configuration.

How to build
------------

Set your sysroot in ``.config``, the variable is ``CONFIG_SYSROOT``, then::

    $ make
    $ make install

This will install busybox in a directory named ``_install``. You can then create
an image for flix with the following command::

    $ cd _install
    $ find -type f -o type l | cpio -o > ../module.img

This will create a module.img file in the root of busybox. You can copy this
file inside the debug directory of flix and trigger a build to have a complete
image that you can boot.
