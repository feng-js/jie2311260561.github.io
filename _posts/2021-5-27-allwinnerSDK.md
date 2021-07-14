---
layout: post
title:  "全志科技D1哪吒SDk 下载编译使用及收获"
date:   2021-07-06 18：54
categories: Ubuntu
tags: Ubuntu20.04 
excerpt: 下载来全志官方SDK编译过程中的小细节
---

# 还学习了markdown的新的辅助快捷工具

- 粗体 ctrl+b
- 斜体 ctrl+i
- 删除线 alt+s
- 切换数学环境 ctrl+m
- 同步预览 ctrl+shift+v
- 检查任务列表项 alt+c
- 格式化表格 alt+shift+f
- 格式化任务列表 alt+c

网页链接
[bogle](https://segmentfault.com/a/1190000017461306)
- hello
  - xixixii
- hello 1

```
opencv_aruco430.lib opencv_bgsegm430.lib opencv_bioinspired430.lib opencv_calib3d430.lib opencv_ccalib430.lib opencv_core430.lib opencv_datasets430.lib opencv_dnn430.lib opencv_dnn_objdetect430.lib opencv_dnn_superres430.lib opencv_dpm430.lib opencv_face430.lib opencv_features2d430.lib opencv_flann430.lib opencv_fuzzy430.lib opencv_hfs430.lib opencv_highgui430.lib opencv_imgcodecs430.lib opencv_imgproc430.lib opencv_img_hash430.lib opencv_intensity_transform430.lib opencv_line_descriptor430.lib opencv_ml430.lib opencv_objdetect430.lib opencv_optflow430.lib opencv_phase_unwrapping430.lib opencv_photo430.lib opencv_plot430.lib opencv_quality430.lib opencv_rapid430.lib opencv_reg430.lib opencv_rgbd430.lib opencv_saliency430.lib opencv_shape430.lib opencv_stereo430.lib opencv_stitching430.lib opencv_structured_light430.lib opencv_superres430.lib opencv_surface_matching430.lib opencv_text430.lib opencv_tracking430.lib opencv_video430.lib opencv_videoio430.lib opencv_videostab430.lib opencv_xfeatures2d430.lib opencv_ximgproc430.lib opencv_xobjdetect430.lib opencv_xphoto430.lib
```

**配置环境变量**



gdbusmessage.c:2698:30:
      if (signature_str)
      tupled_signature_str = g_strdup_printf ("(%s)", signature_str);

dbusauth.c 1298
      if (line == NULL)
            goto out;
          debug_print ("SERVER: WaitingForBegin, read '%s'", line);



```
rm: cannot remove '/home/jie/allwinner/tina-d1-open/tmp/info/.overrides-packageinfo-1859194': Permission denied
make[3]: *** No rule to make target '/home/jie/allwinner/tina-d1-open/tmp/info/.files-packageinfo-1861882'.  Stop.
cat: /home/jie/allwinner/tina-d1-open/tmp/info/.files-packageinfo-1861882: No such file or directory
cat: /home/jie/allwinner/tina-d1-open/tmp/info/.overrides-packageinfo-1861882: No such file or directory
rm: cannot remove '/home/jie/allwinner/tina-d1-open/tmp/info/.files-packageinfo.stamp.4ecc855bd5022757c3b7544e2dfb29c7': Permission denied
touch: cannot touch '/home/jie/allwinner/tina-d1-open/tmp/info/.files-packageinfo.stamp.d41d8cd98f00b204e9800998ecf8427e': Permission denied
touch: cannot touch '/home/jie/allwinner/tina-d1-open/tmp/info/.files-packageinfo.stamp': Permission denied
make[2]: *** [build/scan.mk:84: /home/jie/allwinner/tina-d1-open/tmp/info/.files-packageinfo.stamp] Error 1
make[1]: *** [/home/jie/allwinner/tina-d1-open/build/toplevel.mk:84: prepare-tmpinfo] Error 2
make: *** [/home/jie/allwinner/tina-d1-open/build/toplevel.mk:304：world] 错误 2
[2]+  已完成               $T/tools/build/buildserver --path $T

#### make failed to build some targets (1 seconds) ####

```

有来自于 tmp 的权限不足不能操作的问题  将文件夹所有的权限修改为 777 



strerror-sym.c 47
	return errnos_msgstr + errnos_msgidx[idx];  更改为   	return msgstr + errnos_msgidx[idx];



```
strerror-sym.c:47:9: error: 'errnos_msgstr' undeclared (first use in this function)
  return errnos_msgstr + errnos_msgidx[idx];
         ^~~~~~~~~~~~~
strerror-sym.c:47:9: note: each undeclared identifier is reported only once for each function it appears in
strerror-sym.c:47:25: error: 'errnos_msgidx' undeclared (first use in this function                                                                                                                           )
  return errnos_msgstr + errnos_msgidx[idx];
                         ^~~~~~~~~~~~~
make[7]: *** [Makefile:946: gpg_error-strerror-sym.o] Error 1

```



./out/d1-nezha/compile_dir/target/libgpg-error-1.27/src/errnos-sym.h   这个文件为空  编译不通过 没有定义
感谢全志官方群大佬的鼎力相助发了我一手 头文件  这是缺少头文件中的内容

```
/* Output of mkstrtable.awk.  DO NOT EDIT.  */

/* errnos.in - List of system error values.
   Copyright (C) 2003, 2004 g10 Code GmbH

   This file is part of libgpg-error.

   libgpg-error is free software; you can redistribute it and/or
   modify it under the terms of the GNU Lesser General Public License
   as published by the Free Software Foundation; either version 2.1 of
   the License, or (at your option) any later version.

   libgpg-error is distributed in the hope that it will be useful, but
   WITHOUT ANY WARRANTY; without even the implied warranty of
   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
   Lesser General Public License for more details.

   You should have received a copy of the GNU Lesser General Public
   License along with libgpg-error; if not, write to the Free
   Software Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA
   02111-1307, USA.  */



/* The purpose of this complex string table is to produce
   optimal code with a minimum of relocations.  */

static const char errnos_msgstr[] =
  "GPG_ERR_E2BIG" "\0"
  "GPG_ERR_EACCES" "\0"
  "GPG_ERR_EADDRINUSE" "\0"
  "GPG_ERR_EADDRNOTAVAIL" "\0"
  "GPG_ERR_EADV" "\0"
  "GPG_ERR_EAFNOSUPPORT" "\0"
  "GPG_ERR_EAGAIN" "\0"
  "GPG_ERR_EALREADY" "\0"
  "GPG_ERR_EAUTH" "\0"
  "GPG_ERR_EBACKGROUND" "\0"
  "GPG_ERR_EBADE" "\0"
  "GPG_ERR_EBADF" "\0"
  "GPG_ERR_EBADFD" "\0"
  "GPG_ERR_EBADMSG" "\0"
  "GPG_ERR_EBADR" "\0"
  "GPG_ERR_EBADRPC" "\0"
  "GPG_ERR_EBADRQC" "\0"
  "GPG_ERR_EBADSLT" "\0"
  "GPG_ERR_EBFONT" "\0"
  "GPG_ERR_EBUSY" "\0"
  "GPG_ERR_ECANCELED" "\0"
  "GPG_ERR_ECHILD" "\0"
  "GPG_ERR_ECHRNG" "\0"
  "GPG_ERR_ECOMM" "\0"
  "GPG_ERR_ECONNABORTED" "\0"
  "GPG_ERR_ECONNREFUSED" "\0"
  "GPG_ERR_ECONNRESET" "\0"
  "GPG_ERR_ED" "\0"
  "GPG_ERR_EDEADLK" "\0"
  "GPG_ERR_EDEADLOCK" "\0"
  "GPG_ERR_EDESTADDRREQ" "\0"
  "GPG_ERR_EDIED" "\0"
  "GPG_ERR_EDOM" "\0"
  "GPG_ERR_EDOTDOT" "\0"
  "GPG_ERR_EDQUOT" "\0"
  "GPG_ERR_EEXIST" "\0"
  "GPG_ERR_EFAULT" "\0"
  "GPG_ERR_EFBIG" "\0"
  "GPG_ERR_EFTYPE" "\0"
  "GPG_ERR_EGRATUITOUS" "\0"
  "GPG_ERR_EGREGIOUS" "\0"
  "GPG_ERR_EHOSTDOWN" "\0"
  "GPG_ERR_EHOSTUNREACH" "\0"
  "GPG_ERR_EIDRM" "\0"
  "GPG_ERR_EIEIO" "\0"
  "GPG_ERR_EILSEQ" "\0"
  "GPG_ERR_EINPROGRESS" "\0"
  "GPG_ERR_EINTR" "\0"
  "GPG_ERR_EINVAL" "\0"
  "GPG_ERR_EIO" "\0"
  "GPG_ERR_EISCONN" "\0"
  "GPG_ERR_EISDIR" "\0"
  "GPG_ERR_EISNAM" "\0"
  "GPG_ERR_EL2HLT" "\0"
  "GPG_ERR_EL2NSYNC" "\0"
  "GPG_ERR_EL3HLT" "\0"
  "GPG_ERR_EL3RST" "\0"
  "GPG_ERR_ELIBACC" "\0"
  "GPG_ERR_ELIBBAD" "\0"
  "GPG_ERR_ELIBEXEC" "\0"
  "GPG_ERR_ELIBMAX" "\0"
  "GPG_ERR_ELIBSCN" "\0"
  "GPG_ERR_ELNRNG" "\0"
  "GPG_ERR_ELOOP" "\0"
  "GPG_ERR_EMEDIUMTYPE" "\0"
  "GPG_ERR_EMFILE" "\0"
  "GPG_ERR_EMLINK" "\0"
  "GPG_ERR_EMSGSIZE" "\0"
  "GPG_ERR_EMULTIHOP" "\0"
  "GPG_ERR_ENAMETOOLONG" "\0"
  "GPG_ERR_ENAVAIL" "\0"
  "GPG_ERR_ENEEDAUTH" "\0"
  "GPG_ERR_ENETDOWN" "\0"
  "GPG_ERR_ENETRESET" "\0"
  "GPG_ERR_ENETUNREACH" "\0"
  "GPG_ERR_ENFILE" "\0"
  "GPG_ERR_ENOANO" "\0"
  "GPG_ERR_ENOBUFS" "\0"
  "GPG_ERR_ENOCSI" "\0"
  "GPG_ERR_ENODATA" "\0"
  "GPG_ERR_ENODEV" "\0"
  "GPG_ERR_ENOENT" "\0"
  "GPG_ERR_ENOEXEC" "\0"
  "GPG_ERR_ENOLCK" "\0"
  "GPG_ERR_ENOLINK" "\0"
  "GPG_ERR_ENOMEDIUM" "\0"
  "GPG_ERR_ENOMEM" "\0"
  "GPG_ERR_ENOMSG" "\0"
  "GPG_ERR_ENONET" "\0"
  "GPG_ERR_ENOPKG" "\0"
  "GPG_ERR_ENOPROTOOPT" "\0"
  "GPG_ERR_ENOSPC" "\0"
  "GPG_ERR_ENOSR" "\0"
  "GPG_ERR_ENOSTR" "\0"
  "GPG_ERR_ENOSYS" "\0"
  "GPG_ERR_ENOTBLK" "\0"
  "GPG_ERR_ENOTCONN" "\0"
  "GPG_ERR_ENOTDIR" "\0"
  "GPG_ERR_ENOTEMPTY" "\0"
  "GPG_ERR_ENOTNAM" "\0"
  "GPG_ERR_ENOTSOCK" "\0"
  "GPG_ERR_ENOTSUP" "\0"
  "GPG_ERR_ENOTTY" "\0"
  "GPG_ERR_ENOTUNIQ" "\0"
  "GPG_ERR_ENXIO" "\0"
  "GPG_ERR_EOPNOTSUPP" "\0"
  "GPG_ERR_EOVERFLOW" "\0"
  "GPG_ERR_EPERM" "\0"
  "GPG_ERR_EPFNOSUPPORT" "\0"
  "GPG_ERR_EPIPE" "\0"
  "GPG_ERR_EPROCLIM" "\0"
  "GPG_ERR_EPROCUNAVAIL" "\0"
  "GPG_ERR_EPROGMISMATCH" "\0"
  "GPG_ERR_EPROGUNAVAIL" "\0"
  "GPG_ERR_EPROTO" "\0"
  "GPG_ERR_EPROTONOSUPPORT" "\0"
  "GPG_ERR_EPROTOTYPE" "\0"
  "GPG_ERR_ERANGE" "\0"
  "GPG_ERR_EREMCHG" "\0"
  "GPG_ERR_EREMOTE" "\0"
  "GPG_ERR_EREMOTEIO" "\0"
  "GPG_ERR_ERESTART" "\0"
  "GPG_ERR_EROFS" "\0"
  "GPG_ERR_ERPCMISMATCH" "\0"
  "GPG_ERR_ESHUTDOWN" "\0"
  "GPG_ERR_ESOCKTNOSUPPORT" "\0"
  "GPG_ERR_ESPIPE" "\0"
  "GPG_ERR_ESRCH" "\0"
  "GPG_ERR_ESRMNT" "\0"
  "GPG_ERR_ESTALE" "\0"
  "GPG_ERR_ESTRPIPE" "\0"
  "GPG_ERR_ETIME" "\0"
  "GPG_ERR_ETIMEDOUT" "\0"
  "GPG_ERR_ETOOMANYREFS" "\0"
  "GPG_ERR_ETXTBSY" "\0"
  "GPG_ERR_EUCLEAN" "\0"
  "GPG_ERR_EUNATCH" "\0"
  "GPG_ERR_EUSERS" "\0"
  "GPG_ERR_EWOULDBLOCK" "\0"
  "GPG_ERR_EXDEV" "\0"
  "GPG_ERR_EXFULL";

static const int errnos_msgidx[] =
  {
    0,
    14,
    29,
    48,
    70,
    83,
    104,
    119,
    136,
    150,
    170,
    184,
    198,
    213,
    229,
    243,
    259,
    275,
    291,
    306,
    320,
    338,
    353,
    368,
    382,
    403,
    424,
    443,
    454,
    470,
    488,
    509,
    523,
    536,
    552,
    567,
    582,
    597,
    611,
    626,
    646,
    664,
    682,
    703,
    717,
    731,
    746,
    766,
    780,
    795,
    807,
    823,
    838,
    853,
    868,
    885,
    900,
    915,
    931,
    947,
    964,
    980,
    996,
    1011,
    1025,
    1045,
    1060,
    1075,
    1092,
    1110,
    1131,
    1147,
    1165,
    1182,
    1200,
    1220,
    1235,
    1250,
    1266,
    1281,
    1297,
    1312,
    1327,
    1343,
    1358,
    1374,
    1392,
    1407,
    1422,
    1437,
    1452,
    1472,
    1487,
    1501,
    1516,
    1531,
    1547,
    1564,
    1580,
    1598,
    1614,
    1631,
    1647,
    1662,
    1679,
    1693,
    1712,
    1730,
    1744,
    1765,
    1779,
    1796,
    1817,
    1839,
    1860,
    1875,
    1899,
    1918,
    1933,
    1949,
    1965,
    1983,
    2000,
    2014,
    2035,
    2053,
    2077,
    2092,
    2106,
    2121,
    2136,
    2153,
    2167,
    2185,
    2206,
    2222,
    2238,
    2254,
    2269,
    2289,
    2303,

  };

static GPG_ERR_INLINE int
errnos_msgidxof (int code)
{
  return (0 ? 0
  : ((code >= 0) && (code <= 140)) ? (code - 0)
  : -1);
}
```



# gcc交叉编译链所在文件夹
/home/jie/allwinner/tina-d1-open/prebuilt/gcc/linux-x86/riscv/toolchain-thead-glibc/riscv64-glibc-gcc-thead_20200702/bin




# 分区

查看磁盘分区的UUID
sudo blkid

UUID="84844acd-2f75-4f01-9b78-3bf959707ef0"

```
$ sudo vim /etc/fstab
加入：
UUID=11263962-9715-473f-9421-0b604e895aaa /data ext4 defaults 0 1
```
修改完/etc/fstab文件后，运行sudo mount -a命令验证一下配置是否正确。


修改文件夹所属用户 进行文件共享

```

sudo chown michael testfile //修改文件拥有者为 michael 
chgrp -R hxls gcn/

然而我自己的修改方式
sudo chown jie:jie lost+found
```


# d1 sdk 本来的地方

```
build   Config.in  dl      logs      out      prebuilt  scripts  toolchain
config  device     lichee  Makefile  package  rules.mk  target   tools


build      device  logs      package   scripts  toolchain
config     dl      Makefile  prebuilt  target   tools
Config.in  lichee  out       rules.mk  tmp

```

