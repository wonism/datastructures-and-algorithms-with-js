# Spider monkey installation
__Install SpiderMonkey__
```sh
$ curl -O http://ftp.mozilla.org/pub/mozilla.org/js/js-1.8.5.tar.gz
$ curl -O http://svn.macports.org/repository/macports/trunk/dports/lang/spidermonkey/files/patch-jsprf.c
$ tar xvzf js-1.8.5.tar.gz
$ cd js/src
$ patch -p0 -i ../../patch-jsprf.c
$ make -f Makefile.ref
$ sudo su
$ JS_DIST=/usr/local/spidermonkey make -f Makefile.ref export
$ exit
$ sudo ranlib /usr/local/spidermonkey/lib/libjs.a
```

__Using DYLD_LIBARY_PATH__
```sh
$ export DYLD_LIBRARY_PATH=$DYLD_LIBRARY_PATH:/usr/local/spidermonkey/lib
```

__then reload your env__
```sh
$ . ~/.profile
```

__Avoding DYLD_LIBRARY_PATH__
```sh
$ sudo ln -s /usr/local/spidermonkey/include /usr/local/include/js
$ sudo ln -s /usr/local/spidermonkey/lib/libjs.dylib /usr/local/lib/libjs.dylib
# If you're feeling saucey, the js shell can be useful for quick syntax checking and the like.
$ sudo ln -s /usr/local/spidermonkey/bin/js /usr/local/bin/js
```

