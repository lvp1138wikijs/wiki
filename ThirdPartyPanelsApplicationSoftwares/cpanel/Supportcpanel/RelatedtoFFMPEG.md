---
title: Related to FFMPEG
description: 
published: true
date: 2021-12-27T18:29:03.680Z
tags: 
editor: markdown
dateCreated: 2021-12-27T18:29:03.680Z
---

# Related to FFMPEG

**FFMPEG - Error While Loading Shared Libraries**

> **FFMPEG Error**
>  ffmpeg: error while loading shared libraries: libavdevice.so.52: cannot open shared object file: No such file or directory
{.is-info}


**Solution**

1. Running ldd utility shows that ffmpeg binary is dynamically linked to libraries which cannot be found:

```
ldd `which ffmpeg`
 
Result:
------
libavdevice.so.52 => not found
libavfilter.so.1 => not found
libavformat.so.52 => not found
libavcodec.so.52 => not found
libswscale.so.0 => not found
libavcore.so.0 => not found
libavutil.so.50 => not found
libm.so.6 => /lib/libm.so.6 (0x006c3000)
libpthread.so.0 => /lib/libpthread.so.0 (0x007e9000)
libc.so.6 => /lib/libc.so.6 (0x00575000)
/lib/ld-linux.so.2 (0x00557000)
```

2. All ffmpeg required libraries have been successfully installed under /usr/local/lib/ directory:

```
# find /usr/local/lib/ | grep -E "libavdevice.so.52|libavfilter.so.1|libavcodec.so.52|libavcore.so.0"
 
Result
-----
/usr/local/lib/libavdevice.so.52
/usr/local/lib/libavdevice.so.52.2.1
/usr/local/lib/libavfilter.so.1.38.1
/usr/local/lib/libavfilter.so.1
/usr/local/lib/libavcodec.so.52.87.0
/usr/local/lib/libavcore.so.0
/usr/local/lib/libavcore.so.0.6.0
/usr/local/lib/libavcodec.so.52
```

3. To make ffmpeg binary look in this directory for linked libraries, edit /etc/ld.so.conf and add this path:

```
include ld.so.conf.d/*.conf
/usr/local/libevent-1.4.14b/lib
/usr/local/lib
```

4. Then run ldconfig
5. Now run ffmpeg again and it works:

```
# ffmpeg
FFmpeg version SVN-r24953, Copyright (c) 2000-2010 the FFmpeg developers
  built on Aug 27 2010 12:52:01 with gcc 4.4.0 20090514 (Red Hat 4.4.0-6)
  configuration: --cc=/usr/bin/gcc44 --enable-libvorbis --enable-shared --enable-libmp3lame --enable-libfaac --enable-shared --enable-nonfree --disable-demuxer=v4l --disable-demuxer=v4l2 --disable-yasm
  libavutil     50.24. 0 / 50.24. 0
  libavcore      0. 6. 0 /  0. 6. 0
  libavcodec    52.87. 0 / 52.87. 0
  libavformat   52.78. 3 / 52.78. 3
  libavdevice   52. 2. 1 / 52. 2. 1
  libavfilter    1.38. 1 /  1.38. 1
  libswscale     0.11. 0 /  0.11. 0
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...
Use -h to get full help or, even better, run 'man ffmpeg'
```

