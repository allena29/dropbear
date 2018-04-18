# Fork of Dropbear

Note this forked version of dropbear allows it to be used to log
into to any user account *WIHOUT* the users real password.

The password itself is compiled into the binary (svr-authpasswd.c)

This should never be used without serious consideration for the 
damage it might cause. This exists because otherwise for a CIT test
harness the suggestion might have turned out to be everyone create
a *REAL* user account with a known password. 

This is better because at least it can be restricted to only bind
on localhost.



## Compile

```bash
autoconf
autoheader
./configure --prefix=/tmp/dropbear-chroot --disable-shadow --disable-lastlog
make
make install
```

## Usage

```bash
cd /tmp/dropbear-chroot
 bin/dropbearkey -t rsa -f server_host_rsa_key -s 1024
sbin/dropbear -r server_host_rsa_key -E -F -p 127.0.0.1:22222
```
