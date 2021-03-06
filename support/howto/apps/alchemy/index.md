---
title: Tablet setup in Alchemy
summary: How to setup a tablet to work with Alchemy
---
> Alchemy is an open drawing project aimed at exploring how we can sketch,
> draw, and create on computers in new ways. Alchemy isn’t software for
> creating finished artwork, but rather a sketching environment that focuses
> on the absolute initial stage of the creation process.  Experimental in
> nature, Alchemy lets you brainstorm visually to explore an expanded range of
> ideas and possibilities in a serendipitous way.
>
> — [Alchemy website](http://al.chemy.org/)

In this tutorial you can learn how to setup a tablet, which uses the
evdev driver, to work with this application.

Alchemy BETA 008
================

This is the latest version of this program. You can download it
[here](http://al.chemy.org/download/).

Tablet setup
------------

This software automatically recognises your tablet, there is no need to
configure anything in Alchemy.

If your tablet is not recognised, there might be a problem with loading
the JPen library.

If you start Alchemy in a terminal and the following message appears:

    08-Jun-2012 15:11:24 jpen.provider.NativeLibraryLoader$4 run
    INFO: loading JNI library: jpen-2-2-x86_64 ...
    08-Jun-2012 15:11:24 jpen.provider.NativeLibraryLoader$4 logOnFail
    INFO: jpen-2-2-x86_64 couldn't be loaded
    08-Jun-2012 15:11:24 jpen.provider.NativeLibraryLoader$4 run
    INFO: loading JNI library: jpen-2-2-ia64 ...
    08-Jun-2012 15:11:24 jpen.provider.NativeLibraryLoader$4 logOnFail
    INFO: jpen-2-2-ia64 couldn't be loaded

then the JPen library has not loaded.

To correct the problem do the following. Download the JPen library
(jpen-2-100101-lib.zip) from
[here](http://sourceforge.net/projects/jpen/files/jpen/2-100101/jpen-2-100101-lib.zip/download)
to ~/Downloads. It's assumed that you have extracted Alchemy to your home
directory and therefore the Alchemy installation path is ~/Alchemy.

1. Open a terminal and change to the Alchemy directory.

        $ cd Alchemy/

2. Rename the Alchemy's lib directory to libold.

        $ mv lib libold

3. Extract the jpen-2-100101-lib.zip into the Alchemy directory.

        $ unzip ~/Downloads/jpen-2-100101-lib.zip

4. Create a new lib directory under the Alchemy directory.

        $ mkdir lib

5. Copy libjpen-2-2-ia64.so, libjpen-2-2.so, libjpen-2-2-x86\_64.so,
   libjpen-2-3.jnilib from the zip file into the lib directory.

        $ cp -t ./lib ./jpen-2-100101/libjpen-2-2-ia64.so \
                      ./jpen-2-100101/libjpen-2-2.so \
                      ./jpen-2-100101/libjpen-2-2-x86_64.so \
                      ./jpen-2-100101/libjpen-2-3.jnilib

6. Copy jpen-2.jar from the zip into the Alchemy installation directory.

        $ cp -t . ./jpen-2-100101/jpen-2.jar

7. Start Alchemy with the following command.

        $ java -Djava.library.path=lib -jar Alchemy.jar

If you have successfully set up everything, the following message should
appear in the terminal:

        08-Jun-2012 15:27:03 jpen.provider.NativeLibraryLoader$4 run
        INFO: loading JNI library: jpen-2-2-x86_64 ...
        08-Jun-2012 15:27:03 jpen.provider.NativeLibraryLoader$4 run
        INFO: jpen-2-2-x86_64 loaded

Which means the JPen library loaded correctly and your tablet should be
recognised.

Device testing
--------------

If you choose *Pressure Shapes* in the *Create* menu, you can see how
pressure is affecting the shape of what you are drawing.

![Alchemy Beta 008 Selecting pressure shapes for
drawing](pressureshapes.png "Alchemy Beta 008 Selecting pressure shapes for drawing")

More information
================

You can find more information about Alchemy on the [official
website](http://al.chemy.org/).
