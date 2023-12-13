# FreeIPA Stuff for Amazon Linux 2023

## Information

For some reason Amazon decided to make some questionable decisions regarding
their packaging strategy and communication facilitation.

This choice has made using FreeIPA challenging for me.

Until Amazon decides to support FreeIPA, I've built my own packages that work
with Amazon Linux 2023.

I've included both the specs, and the source RPMs in a split base64-encoded .tgz
file.

I take no responsibility for anything that may happen from anything you might do
regarding anything I've shared.

Also, the specs really suck.

I just hacked shit together to get it to work ASAP instead of taking the time to
update the spec file in a method that package/distro maintainers may desire.

ymmv.

## The Spec Files

Are in the specs directory. Like I mentioned earlier, they're hacks. If you
really wanna make them pretty and better and all that shit then go ahead and
submit a PR…

Or suggest (repeatedly) to the Amazon Linux maintainers that they
support FreeIPA.

## The SRPM Files

Are in the srpms directory and may be extracted using tar and base64 as
shown below. Do your own due diligence and make sure I'm not a hacker,
or don't, cuz I'm not.

All the sources and specs were cobbled together from various bits that I was
able to get built and working quickly.

```
cat srpms/srpms-tgz-* | base64 -d | tar zxvf -

SRPMS/
x SRPMS/freeipa-4.11.0-7.amzn2023.src.rpm
x SRPMS/pyusb-1.2.1-3.amzn2023.src.rpm
x SRPMS/python-yubico-1.3.3-13.amzn2023.src.rpm
x SRPMS/python-deprecated-1.2.14-3.amzn2023.src.rpm
x SRPMS/python-deprecated-1.2.13-4.amzn2023.buildreqs.nosrc.rpm
x SRPMS/python-wrapt-1.14.1-6.amzn2023.src.rpm
x SRPMS/python-deprecated-1.2.13-4.amzn2023.src.rpm
x SRPMS/python-jwcrypto-1.4.2-7.amzn2023.src.rpm
x SRPMS/python-augeas-1.1.0-10.amzn2023.src.rpm
x SRPMS/python-ldap-3.4.3-4.amzn2023.src.rpm
x SRPMS/python-qrcode-7.4.2-7.amzn2023.buildreqs.nosrc.rpm
x SRPMS/python-pypng-0.0.21-6.amzn2023.src.rpm
x SRPMS/python-qrcode-7.4.2-7.amzn2023.src.rpm
x SRPMS/certmonger-0.79.19-1.amzn2023.src.rpm
x SRPMS/python-rjsmin-1.2.1-4.amzn2023.src.rpm
x SRPMS/python-lesscpy-0.14.0-13.amzn2023.src.rpm
x SRPMS/argparse-manpage-4.5-1.amzn2023.buildreqs.nosrc.rpm
x SRPMS/argparse-manpage-4.5-1.amzn2023.src.rpm
```

## Are You Sure It Works?

It does for me…

```
[I]➜ ssh root@10.69.69.69
root@10.69.69.69's password: 
   ,     #_
   ~\_  ####_        Amazon Linux 2023
  ~~  \_#####\
  ~~     \###|
  ~~       \#/ ___   https://aws.amazon.com/linux/amazon-linux-2023
   ~~       V~' '->
    ~~~         /
      ~~._.   _/
         _/ _/
       _/m/'
Last login: Wed Dec 13 00:57:13 2023 from 10.6.6.6
[root@tim-amzn-freeipa ~]# tar zxvf freeipa-rpms.tgz 
freeipa-rpms/
freeipa-rpms/argparse-manpage-4.5-1.amzn2023.noarch.rpm
freeipa-rpms/python3-argparse-manpage+setuptools-4.5-1.amzn2023.noarch.rpm
freeipa-rpms/python3-argparse-manpage-4.5-1.amzn2023.noarch.rpm
freeipa-rpms/python3-augeas-1.1.0-10.amzn2023.noarch.rpm
freeipa-rpms/python3-deprecated-1.2.13-4.amzn2023.noarch.rpm
freeipa-rpms/python3-jwcrypto-1.4.2-7.amzn2023.noarch.rpm
freeipa-rpms/python3-lesscpy-0.14.0-13.amzn2023.noarch.rpm
freeipa-rpms/python3-pypng-0.0.21-6.amzn2023.noarch.rpm
freeipa-rpms/python3-pyusb-1.2.1-3.amzn2023.noarch.rpm
freeipa-rpms/python3-qrcode-7.4.2-7.amzn2023.noarch.rpm
freeipa-rpms/python3-yubico-1.3.3-13.amzn2023.noarch.rpm
freeipa-rpms/certmonger-0.79.19-1.amzn2023.x86_64.rpm
freeipa-rpms/python-rjsmin-docs-1.2.1-4.amzn2023.x86_64.rpm
freeipa-rpms/python-wrapt-doc-1.14.1-6.amzn2023.x86_64.rpm
freeipa-rpms/python3-ldap-3.4.3-4.amzn2023.x86_64.rpm
freeipa-rpms/python3-rjsmin-1.2.1-4.amzn2023.x86_64.rpm
freeipa-rpms/python3-wrapt-1.14.1-6.amzn2023.x86_64.rpm
freeipa-rpms/freeipa-client-4.11.0-7.amzn2023.x86_64.rpm
freeipa-rpms/freeipa-client-common-4.11.0-7.amzn2023.noarch.rpm
freeipa-rpms/freeipa-client-epn-4.11.0-7.amzn2023.x86_64.rpm
freeipa-rpms/freeipa-client-samba-4.11.0-7.amzn2023.x86_64.rpm
freeipa-rpms/freeipa-common-4.11.0-7.amzn2023.noarch.rpm
freeipa-rpms/freeipa-python-compat-4.11.0-7.amzn2023.noarch.rpm
freeipa-rpms/freeipa-selinux-4.11.0-7.amzn2023.noarch.rpm
freeipa-rpms/python3-ipaclient-4.11.0-7.amzn2023.noarch.rpm
freeipa-rpms/python3-ipalib-4.11.0-7.amzn2023.noarch.rpm
```

```
[root@tim-amzn-freeipa ~]# dnf install freeipa-rpms/*
Last metadata expiration check: 0:01:59 ago on Wed Dec 13 00:56:15 2023.
Dependencies resolved.
================================================================================
 Package                   Arch   Version                    Repository    Size
================================================================================
Installing:
 argparse-manpage          noarch 4.5-1.amzn2023             @commandline  17 k
 certmonger                x86_64 0.79.19-1.amzn2023         @commandline 593 k
 freeipa-client            x86_64 4.11.0-7.amzn2023          @commandline 121 k
 freeipa-client-common     noarch 4.11.0-7.amzn2023          @commandline  35 k
 freeipa-client-epn        x86_64 4.11.0-7.amzn2023          @commandline  34 k
 freeipa-client-samba      x86_64 4.11.0-7.amzn2023          @commandline  30 k
 freeipa-common            noarch 4.11.0-7.amzn2023          @commandline 646 k
 freeipa-python-compat     noarch 4.11.0-7.amzn2023          @commandline  27 k
 freeipa-selinux           noarch 4.11.0-7.amzn2023          @commandline  28 k
 python-rjsmin-docs        x86_64 1.2.1-4.amzn2023           @commandline 169 k
 python-wrapt-doc          x86_64 1.14.1-6.amzn2023          @commandline 201 k
 python3-argparse-manpage  noarch 4.5-1.amzn2023             @commandline  46 k
 python3-argparse-manpage+setuptools
                           noarch 4.5-1.amzn2023             @commandline 9.9 k
 python3-augeas            noarch 1.1.0-10.amzn2023          @commandline  33 k
 python3-deprecated        noarch 1.2.13-4.amzn2023          @commandline  22 k
 python3-ipaclient         noarch 4.11.0-7.amzn2023          @commandline 495 k
 python3-ipalib            noarch 4.11.0-7.amzn2023          @commandline 585 k
 python3-jwcrypto          noarch 1.4.2-7.amzn2023           @commandline  78 k
 python3-ldap              x86_64 3.4.3-4.amzn2023           @commandline 216 k
 python3-lesscpy           noarch 0.14.0-13.amzn2023         @commandline  94 k
 python3-pypng             noarch 0.0.21-6.amzn2023          @commandline  64 k
 python3-pyusb             noarch 1.2.1-3.amzn2023           @commandline  86 k
 python3-qrcode            noarch 7.4.2-7.amzn2023           @commandline  94 k
 python3-rjsmin            x86_64 1.2.1-4.amzn2023           @commandline  30 k
 python3-wrapt             x86_64 1.14.1-6.amzn2023          @commandline  57 k
 python3-yubico            noarch 1.3.3-13.amzn2023          @commandline  60 k
Installing dependencies:
 augeas-libs               x86_64 1.13.0-1.amzn2023.0.2      amazonlinux  408 k
 authselect                x86_64 1.2.3-1.amzn2023.0.2       amazonlinux  122 k
 authselect-libs           x86_64 1.2.3-1.amzn2023.0.2       amazonlinux  221 k
 autofs                    x86_64 1:5.1.7-21.amzn2023.0.3    amazonlinux  360 k
 avahi-libs                x86_64 0.8-14.amzn2023.0.10       amazonlinux   68 k
 c-ares                    x86_64 1.19.0-1.amzn2023          amazonlinux  110 k
 cifs-utils                x86_64 6.15-1.amzn2023.0.2        amazonlinux   95 k
 cups-libs                 x86_64 1:2.3.3op2-18.amzn2023.0.7 amazonlinux  265 k
 cyrus-sasl-gssapi         x86_64 2.1.27-18.amzn2023.0.3     amazonlinux   27 k
 dbus-tools                x86_64 1:1.12.28-1.amzn2023.0.1   amazonlinux   53 k
 krb5-pkinit               x86_64 1.21-3.amzn2023.0.3        amazonlinux   62 k
 krb5-workstation          x86_64 1.21-3.amzn2023.0.3        amazonlinux  500 k
 libdhash                  x86_64 0.5.0-47.amzn2023.0.2      amazonlinux   29 k
 libicu                    x86_64 67.1-7.amzn2023.0.3        amazonlinux  9.6 M
 libipa_hbac               x86_64 2.5.0-1.amzn2023.0.3       amazonlinux   30 k
 libkadm5                  x86_64 1.21-3.amzn2023.0.3        amazonlinux   80 k
 libldb                    x86_64 2.6.2-1.amzn2023.0.2       amazonlinux  184 k
 libnetapi                 x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux  149 k
 libsmbclient              x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux   80 k
 libsss_autofs             x86_64 2.5.0-1.amzn2023.0.3       amazonlinux   31 k
 libsss_certmap            x86_64 2.5.0-1.amzn2023.0.3       amazonlinux   66 k
 libsss_sudo               x86_64 2.5.0-1.amzn2023.0.3       amazonlinux   28 k
 libtalloc                 x86_64 2.3.4-1.amzn2023.0.2       amazonlinux   31 k
 libtdb                    x86_64 1.4.7-1.amzn2023.0.2       amazonlinux   52 k
 libtevent                 x86_64 0.13.0-1.amzn2023.0.2      amazonlinux   45 k
 libwbclient               x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux   47 k
 nss-tools                 x86_64 3.90.0-3.amzn2023.0.3      amazonlinux  433 k
 oddjob                    x86_64 0.34.7-2.amzn2023.0.3      amazonlinux   65 k
 oddjob-mkhomedir          x86_64 0.34.7-2.amzn2023.0.3      amazonlinux   27 k
 policycoreutils-python-utils
                           noarch 3.4-6.amzn2023.0.2         amazonlinux   72 k
 python3-cffi              x86_64 1.14.5-1.amzn2023.0.3      amazonlinux  242 k
 python3-cryptography      x86_64 36.0.1-1.amzn2023.0.3      amazonlinux  1.1 M
 python3-decorator         noarch 4.4.2-4.amzn2023.0.2       amazonlinux   27 k
 python3-dns               noarch 2.1.0-3.amzn2023.0.3       amazonlinux  308 k
 python3-gssapi            x86_64 1.6.9-3.amzn2023.0.2       amazonlinux  461 k
 python3-ldb               x86_64 2.6.2-1.amzn2023.0.2       amazonlinux   55 k
 python3-libipa_hbac       x86_64 2.5.0-1.amzn2023.0.3       amazonlinux   24 k
 python3-netaddr           noarch 0.8.0-3.amzn2023.0.2       amazonlinux  1.5 M
 python3-ply               noarch 3.11-11.amzn2023.0.2       amazonlinux  103 k
 python3-pyasn1            noarch 0.4.8-4.amzn2023.0.2       amazonlinux  136 k
 python3-pyasn1-modules    noarch 0.4.8-4.amzn2023.0.2       amazonlinux  215 k
 python3-pycparser         noarch 2.20-3.amzn2023.0.2        amazonlinux  125 k
 python3-samba             x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux  3.3 M
 python3-samba-dc          x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux  336 k
 python3-sss               x86_64 2.5.0-1.amzn2023.0.3       amazonlinux   33 k
 python3-sss-murmur        x86_64 2.5.0-1.amzn2023.0.3       amazonlinux   13 k
 python3-sssdconfig        noarch 2.5.0-1.amzn2023.0.3       amazonlinux   56 k
 python3-talloc            x86_64 2.3.4-1.amzn2023.0.2       amazonlinux   22 k
 python3-tdb               x86_64 1.4.7-1.amzn2023.0.2       amazonlinux   23 k
 python3-tevent            x86_64 0.13.0-1.amzn2023.0.2      amazonlinux   20 k
 python3-tomli             noarch 2.0.1-4.amzn2023           amazonlinux   33 k
 python3-typing-extensions noarch 3.7.4.3-2.amzn2023.0.2     amazonlinux   48 k
 samba                     x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux  950 k
 samba-client              x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux  673 k
 samba-client-libs         x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux  5.0 M
 samba-common              noarch 2:4.17.12-1.amzn2023.0.1   amazonlinux  153 k
 samba-common-libs         x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux  106 k
 samba-common-tools        x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux  464 k
 samba-dc-libs             x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux   35 k
 samba-dcerpc              x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux  691 k
 samba-ldb-ldap-modules    x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux   33 k
 samba-libs                x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux  127 k
 samba-winbind             x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux  418 k
 samba-winbind-modules     x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux   66 k
 sssd-common               x86_64 2.5.0-1.amzn2023.0.3       amazonlinux  1.5 M
 sssd-common-pac           x86_64 2.5.0-1.amzn2023.0.3       amazonlinux   86 k
 sssd-ipa                  x86_64 2.5.0-1.amzn2023.0.3       amazonlinux  256 k
 sssd-krb5                 x86_64 2.5.0-1.amzn2023.0.3       amazonlinux   64 k
 sssd-krb5-common          x86_64 2.5.0-1.amzn2023.0.3       amazonlinux   78 k
 sssd-tools                x86_64 2.5.0-1.amzn2023.0.3       amazonlinux  212 k
 sssd-winbind-idmap        x86_64 2.5.0-1.amzn2023.0.3       amazonlinux   19 k
 tdb-tools                 x86_64 1.4.7-1.amzn2023.0.2       amazonlinux   36 k
Installing weak dependencies:
 cifs-utils-info           x86_64 6.15-1.amzn2023.0.2        amazonlinux   20 k
 samba-tools               x86_64 2:4.17.12-1.amzn2023.0.1   amazonlinux   28 k
 sssd-dbus                 x86_64 2.5.0-1.amzn2023.0.3       amazonlinux  125 k
 sssd-nfs-idmap            x86_64 2.5.0-1.amzn2023.0.3       amazonlinux   31 k

Transaction Summary
================================================================================
Install  102 Packages

Total size: 36 M
Total download size: 32 M
Installed size: 153 M
Is this ok [y/N]: y
Downloading Packages:
(1/76): libldb-2.6.2-1.amzn2023.0.2.x86_64.rpm  1.4 MB/s | 184 kB     00:00    
(2/76): samba-dc-libs-4.17.12-1.amzn2023.0.1.x8 265 kB/s |  35 kB     00:00    
(3/76): libtalloc-2.3.4-1.amzn2023.0.2.x86_64.r 563 kB/s |  31 kB     00:00    
(4/76): krb5-workstation-1.21-3.amzn2023.0.3.x8 6.1 MB/s | 500 kB     00:00    
(5/76): sssd-dbus-2.5.0-1.amzn2023.0.3.x86_64.r 2.8 MB/s | 125 kB     00:00    
(6/76): libsss_certmap-2.5.0-1.amzn2023.0.3.x86 983 kB/s |  66 kB     00:00    
(7/76): dbus-tools-1.12.28-1.amzn2023.0.1.x86_6 1.5 MB/s |  53 kB     00:00    
(8/76): sssd-common-pac-2.5.0-1.amzn2023.0.3.x8 2.4 MB/s |  86 kB     00:00    
(9/76): sssd-common-2.5.0-1.amzn2023.0.3.x86_64  17 MB/s | 1.5 MB     00:00    
(10/76): c-ares-1.19.0-1.amzn2023.x86_64.rpm    3.8 MB/s | 110 kB     00:00    
(11/76): python3-sss-murmur-2.5.0-1.amzn2023.0. 351 kB/s |  13 kB     00:00    
(12/76): samba-4.17.12-1.amzn2023.0.1.x86_64.rp 2.1 MB/s | 950 kB     00:00    
(13/76): samba-client-libs-4.17.12-1.amzn2023.0  35 MB/s | 5.0 MB     00:00    
(14/76): libipa_hbac-2.5.0-1.amzn2023.0.3.x86_6 595 kB/s |  30 kB     00:00    
(15/76): samba-client-4.17.12-1.amzn2023.0.1.x8  10 MB/s | 673 kB     00:00    
(16/76): nss-tools-3.90.0-3.amzn2023.0.3.x86_64  11 MB/s | 433 kB     00:00    
(17/76): libtevent-0.13.0-1.amzn2023.0.2.x86_64 1.8 MB/s |  45 kB     00:00    
(18/76): libdhash-0.5.0-47.amzn2023.0.2.x86_64. 942 kB/s |  29 kB     00:00    
(19/76): python3-samba-4.17.12-1.amzn2023.0.1.x  35 MB/s | 3.3 MB     00:00    
(20/76): oddjob-mkhomedir-0.34.7-2.amzn2023.0.3 861 kB/s |  27 kB     00:00    
(21/76): libsss_autofs-2.5.0-1.amzn2023.0.3.x86 534 kB/s |  31 kB     00:00    
(22/76): samba-libs-4.17.12-1.amzn2023.0.1.x86_ 1.8 MB/s | 127 kB     00:00    
(23/76): libicu-67.1-7.amzn2023.0.3.x86_64.rpm   79 MB/s | 9.6 MB     00:00    
(24/76): sssd-krb5-common-2.5.0-1.amzn2023.0.3. 861 kB/s |  78 kB     00:00    
(25/76): avahi-libs-0.8-14.amzn2023.0.10.x86_64 1.2 MB/s |  68 kB     00:00    
(26/76): cifs-utils-6.15-1.amzn2023.0.2.x86_64. 3.7 MB/s |  95 kB     00:00    
(27/76): python3-libipa_hbac-2.5.0-1.amzn2023.0 794 kB/s |  24 kB     00:00    
(28/76): oddjob-0.34.7-2.amzn2023.0.3.x86_64.rp 1.9 MB/s |  65 kB     00:00    
(29/76): samba-ldb-ldap-modules-4.17.12-1.amzn2 920 kB/s |  33 kB     00:00    
(30/76): samba-winbind-modules-4.17.12-1.amzn20 1.9 MB/s |  66 kB     00:00    
(31/76): cifs-utils-info-6.15-1.amzn2023.0.2.x8 861 kB/s |  20 kB     00:00    
(32/76): sssd-tools-2.5.0-1.amzn2023.0.3.x86_64 3.7 MB/s | 212 kB     00:00    
(33/76): python3-tevent-0.13.0-1.amzn2023.0.2.x 662 kB/s |  20 kB     00:00    
(34/76): authselect-libs-1.2.3-1.amzn2023.0.2.x 3.8 MB/s | 221 kB     00:00    
(35/76): samba-dcerpc-4.17.12-1.amzn2023.0.1.x8  12 MB/s | 691 kB     00:00    
(36/76): samba-tools-4.17.12-1.amzn2023.0.1.x86 886 kB/s |  28 kB     00:00    
(37/76): sssd-krb5-2.5.0-1.amzn2023.0.3.x86_64. 1.3 MB/s |  64 kB     00:00    
(38/76): libwbclient-4.17.12-1.amzn2023.0.1.x86 1.7 MB/s |  47 kB     00:00    
(39/76): augeas-libs-1.13.0-1.amzn2023.0.2.x86_ 7.3 MB/s | 408 kB     00:00    
(40/76): libtdb-1.4.7-1.amzn2023.0.2.x86_64.rpm 2.0 MB/s |  52 kB     00:00    
(41/76): sssd-ipa-2.5.0-1.amzn2023.0.3.x86_64.r 7.6 MB/s | 256 kB     00:00    
(42/76): libkadm5-1.21-3.amzn2023.0.3.x86_64.rp 3.2 MB/s |  80 kB     00:00    
(43/76): python3-cffi-1.14.5-1.amzn2023.0.3.x86 9.7 MB/s | 242 kB     00:00    
(44/76): python3-gssapi-1.6.9-3.amzn2023.0.2.x8 9.6 MB/s | 461 kB     00:00    
(45/76): krb5-pkinit-1.21-3.amzn2023.0.3.x86_64 2.3 MB/s |  62 kB     00:00    
(46/76): tdb-tools-1.4.7-1.amzn2023.0.2.x86_64. 1.2 MB/s |  36 kB     00:00    
(47/76): cyrus-sasl-gssapi-2.1.27-18.amzn2023.0 861 kB/s |  27 kB     00:00    
(48/76): python3-cryptography-36.0.1-1.amzn2023  30 MB/s | 1.1 MB     00:00    
(49/76): python3-ldb-2.6.2-1.amzn2023.0.2.x86_6 1.7 MB/s |  55 kB     00:00    
(50/76): python3-sss-2.5.0-1.amzn2023.0.3.x86_6 1.0 MB/s |  33 kB     00:00    
(51/76): libnetapi-4.17.12-1.amzn2023.0.1.x86_6 4.5 MB/s | 149 kB     00:00    
(52/76): samba-winbind-4.17.12-1.amzn2023.0.1.x 8.8 MB/s | 418 kB     00:00    
(53/76): python3-tdb-1.4.7-1.amzn2023.0.2.x86_6 691 kB/s |  23 kB     00:00    
(54/76): samba-common-tools-4.17.12-1.amzn2023.  11 MB/s | 464 kB     00:00    
(55/76): samba-common-libs-4.17.12-1.amzn2023.0 4.3 MB/s | 106 kB     00:00    
(56/76): authselect-1.2.3-1.amzn2023.0.2.x86_64 3.8 MB/s | 122 kB     00:00    
(57/76): sssd-winbind-idmap-2.5.0-1.amzn2023.0. 638 kB/s |  19 kB     00:00    
(58/76): python3-samba-dc-4.17.12-1.amzn2023.0. 5.3 MB/s | 336 kB     00:00    
(59/76): libsss_sudo-2.5.0-1.amzn2023.0.3.x86_6 935 kB/s |  28 kB     00:00    
(60/76): autofs-5.1.7-21.amzn2023.0.3.x86_64.rp 6.7 MB/s | 360 kB     00:00    
(61/76): cups-libs-2.3.3op2-18.amzn2023.0.7.x86  10 MB/s | 265 kB     00:00    
(62/76): sssd-nfs-idmap-2.5.0-1.amzn2023.0.3.x8 1.0 MB/s |  31 kB     00:00    
(63/76): python3-talloc-2.3.4-1.amzn2023.0.2.x8 698 kB/s |  22 kB     00:00    
(64/76): libsmbclient-4.17.12-1.amzn2023.0.1.x8 2.4 MB/s |  80 kB     00:00    
(65/76): python3-pyasn1-0.4.8-4.amzn2023.0.2.no 3.6 MB/s | 136 kB     00:00    
(66/76): python3-sssdconfig-2.5.0-1.amzn2023.0. 1.7 MB/s |  56 kB     00:00    
(67/76): python3-dns-2.1.0-3.amzn2023.0.3.noarc 9.2 MB/s | 308 kB     00:00    
(68/76): python3-netaddr-0.8.0-3.amzn2023.0.2.n  16 MB/s | 1.5 MB     00:00    
(69/76): python3-tomli-2.0.1-4.amzn2023.noarch. 715 kB/s |  33 kB     00:00    
(70/76): samba-common-4.17.12-1.amzn2023.0.1.no 5.5 MB/s | 153 kB     00:00    
(71/76): python3-pycparser-2.20-3.amzn2023.0.2. 5.2 MB/s | 125 kB     00:00    
(72/76): python3-typing-extensions-3.7.4.3-2.am 1.5 MB/s |  48 kB     00:00    
(73/76): python3-pyasn1-modules-0.4.8-4.amzn202 5.0 MB/s | 215 kB     00:00    
(74/76): policycoreutils-python-utils-3.4-6.amz 2.9 MB/s |  72 kB     00:00    
(75/76): python3-ply-3.11-11.amzn2023.0.2.noarc 4.3 MB/s | 103 kB     00:00    
(76/76): python3-decorator-4.4.2-4.amzn2023.0.2 917 kB/s |  27 kB     00:00    
--------------------------------------------------------------------------------
Total                                            22 MB/s |  32 MB     00:01     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                        1/1 
  Installing       : libtalloc-2.3.4-1.amzn2023.0.2.x86_64                1/102 
  Installing       : libtevent-0.13.0-1.amzn2023.0.2.x86_64               2/102 
  Installing       : libtdb-1.4.7-1.amzn2023.0.2.x86_64                   3/102 
  Installing       : libldb-2.6.2-1.amzn2023.0.2.x86_64                   4/102 
  Running scriptlet: samba-common-2:4.17.12-1.amzn2023.0.1.noarch         5/102 
  Installing       : samba-common-2:4.17.12-1.amzn2023.0.1.noarch         5/102 
  Running scriptlet: samba-common-2:4.17.12-1.amzn2023.0.1.noarch         5/102 
  Installing       : libdhash-0.5.0-47.amzn2023.0.2.x86_64                6/102 
  Installing       : libsss_certmap-2.5.0-1.amzn2023.0.3.x86_64           7/102 
  Installing       : python3-dns-2.1.0-3.amzn2023.0.3.noarch              8/102 
  Installing       : python3-pyasn1-0.4.8-4.amzn2023.0.2.noarch           9/102 
  Installing       : python3-pyasn1-modules-0.4.8-4.amzn2023.0.2.noar    10/102 
  Installing       : python3-ldap-3.4.3-4.amzn2023.x86_64                11/102 
  Installing       : python3-tdb-1.4.7-1.amzn2023.0.2.x86_64             12/102 
  Installing       : python3-talloc-2.3.4-1.amzn2023.0.2.x86_64          13/102 
  Installing       : python3-pyusb-1.2.1-3.amzn2023.noarch               14/102 
  Installing       : freeipa-client-common-4.11.0-7.amzn2023.noarch      15/102 
  Installing       : python3-ply-3.11-11.amzn2023.0.2.noarch             16/102 
  Installing       : python3-sssdconfig-2.5.0-1.amzn2023.0.3.noarch      17/102 
  Installing       : libsss_sudo-2.5.0-1.amzn2023.0.3.x86_64             18/102 
  Installing       : cyrus-sasl-gssapi-2.1.27-18.amzn2023.0.3.x86_64     19/102 
  Installing       : krb5-pkinit-1.21-3.amzn2023.0.3.x86_64              20/102 
  Installing       : augeas-libs-1.13.0-1.amzn2023.0.2.x86_64            21/102 
  Installing       : avahi-libs-0.8-14.amzn2023.0.10.x86_64              22/102 
  Installing       : cups-libs-1:2.3.3op2-18.amzn2023.0.7.x86_64         23/102 
  Installing       : libsss_autofs-2.5.0-1.amzn2023.0.3.x86_64           24/102 
  Installing       : libipa_hbac-2.5.0-1.amzn2023.0.3.x86_64             25/102 
  Installing       : dbus-tools-1:1.12.28-1.amzn2023.0.1.x86_64          26/102 
  Installing       : certmonger-0.79.19-1.amzn2023.x86_64                27/102 
  Running scriptlet: certmonger-0.79.19-1.amzn2023.x86_64                27/102 
  Installing       : python3-libipa_hbac-2.5.0-1.amzn2023.0.3.x86_64     28/102 
  Installing       : python3-pycparser-2.20-3.amzn2023.0.2.noarch        29/102 
  Installing       : python3-cffi-1.14.5-1.amzn2023.0.3.x86_64           30/102 
  Installing       : python3-cryptography-36.0.1-1.amzn2023.0.3.x86_6    31/102 
  Installing       : python3-augeas-1.1.0-10.amzn2023.noarch             32/102 
  Installing       : python3-yubico-1.3.3-13.amzn2023.noarch             33/102 
  Installing       : python3-ldb-2.6.2-1.amzn2023.0.2.x86_64             34/102 
  Installing       : tdb-tools-1.4.7-1.amzn2023.0.2.x86_64               35/102 
  Installing       : python3-tevent-0.13.0-1.amzn2023.0.2.x86_64         36/102 
  Installing       : sssd-winbind-idmap-2.5.0-1.amzn2023.0.3.x86_64      37/102 
  Installing       : python3-wrapt-1.14.1-6.amzn2023.x86_64              38/102 
  Installing       : python3-deprecated-1.2.13-4.amzn2023.noarch         39/102 
  Installing       : python3-jwcrypto-1.4.2-7.amzn2023.noarch            40/102 
  Installing       : python3-decorator-4.4.2-4.amzn2023.0.2.noarch       41/102 
  Installing       : python3-gssapi-1.6.9-3.amzn2023.0.2.x86_64          42/102 
  Installing       : policycoreutils-python-utils-3.4-6.amzn2023.0.2.    43/102 
  Running scriptlet: freeipa-selinux-4.11.0-7.amzn2023.noarch            44/102 
  Installing       : freeipa-selinux-4.11.0-7.amzn2023.noarch            44/102 
  Running scriptlet: freeipa-selinux-4.11.0-7.amzn2023.noarch            44/102 
uavc:  op=setenforce lsm=selinux enforcing=0 res=1uavc:  op=load_policy lsm=seli  Installing       : freeipa-common-4.11.0-7.amzn2023.noarch             45/102 
  Installing       : python3-typing-extensions-3.7.4.3-2.amzn2023.0.2    46/102 
  Installing       : python3-qrcode-7.4.2-7.amzn2023.noarch              47/102 
  Installing       : python3-tomli-2.0.1-4.amzn2023.noarch               48/102 
  Installing       : python3-argparse-manpage-4.5-1.amzn2023.noarch      49/102 
  Installing       : python3-netaddr-0.8.0-3.amzn2023.0.2.noarch         50/102 
  Installing       : sssd-nfs-idmap-2.5.0-1.amzn2023.0.3.x86_64          51/102 
  Installing       : autofs-1:5.1.7-21.amzn2023.0.3.x86_64               52/102 
  Running scriptlet: autofs-1:5.1.7-21.amzn2023.0.3.x86_64               52/102 
  Installing       : libkadm5-1.21-3.amzn2023.0.3.x86_64                 53/102 
  Installing       : krb5-workstation-1.21-3.amzn2023.0.3.x86_64         54/102 
  Running scriptlet: authselect-libs-1.2.3-1.amzn2023.0.2.x86_64         55/102 
  Installing       : authselect-libs-1.2.3-1.amzn2023.0.2.x86_64         55/102 
  Installing       : oddjob-0.34.7-2.amzn2023.0.3.x86_64                 56/102 
  Running scriptlet: oddjob-0.34.7-2.amzn2023.0.3.x86_64                 56/102 
dbus-daemon: no process found

  Installing       : oddjob-mkhomedir-0.34.7-2.amzn2023.0.3.x86_64       57/102 
  Running scriptlet: oddjob-mkhomedir-0.34.7-2.amzn2023.0.3.x86_64       57/102 
dbus-daemon: no process found

  Installing       : libicu-67.1-7.amzn2023.0.3.x86_64                   58/102 
  Installing       : libwbclient-2:4.17.12-1.amzn2023.0.1.x86_64         59/102 
  Installing       : samba-common-libs-2:4.17.12-1.amzn2023.0.1.x86_6    60/102 
  Installing       : samba-client-libs-2:4.17.12-1.amzn2023.0.1.x86_6    61/102 
  Installing       : samba-libs-2:4.17.12-1.amzn2023.0.1.x86_64          62/102 
  Installing       : libnetapi-2:4.17.12-1.amzn2023.0.1.x86_64           63/102 
  Installing       : samba-dcerpc-2:4.17.12-1.amzn2023.0.1.x86_64        64/102 
  Installing       : samba-dc-libs-2:4.17.12-1.amzn2023.0.1.x86_64       65/102 
  Installing       : libsmbclient-2:4.17.12-1.amzn2023.0.1.x86_64        66/102 
  Installing       : python3-samba-2:4.17.12-1.amzn2023.0.1.x86_64       67/102 
  Installing       : cifs-utils-info-6.15-1.amzn2023.0.2.x86_64          68/102 
  Installing       : cifs-utils-6.15-1.amzn2023.0.2.x86_64               69/102 
  Running scriptlet: cifs-utils-6.15-1.amzn2023.0.2.x86_64               69/102 
  Installing       : python3-samba-dc-2:4.17.12-1.amzn2023.0.1.x86_64    70/102 
  Installing       : samba-tools-2:4.17.12-1.amzn2023.0.1.x86_64         71/102 
  Installing       : samba-client-2:4.17.12-1.amzn2023.0.1.x86_64        72/102 
  Running scriptlet: samba-client-2:4.17.12-1.amzn2023.0.1.x86_64        72/102 
  Installing       : samba-winbind-modules-2:4.17.12-1.amzn2023.0.1.x    73/102 
  Installing       : samba-ldb-ldap-modules-2:4.17.12-1.amzn2023.0.1.    74/102 
  Installing       : samba-common-tools-2:4.17.12-1.amzn2023.0.1.x86_    75/102 
  Running scriptlet: samba-winbind-2:4.17.12-1.amzn2023.0.1.x86_64       76/102 
  Installing       : samba-winbind-2:4.17.12-1.amzn2023.0.1.x86_64       76/102 
  Running scriptlet: samba-winbind-2:4.17.12-1.amzn2023.0.1.x86_64       76/102 
  Installing       : authselect-1.2.3-1.amzn2023.0.2.x86_64              77/102 
  Installing       : samba-2:4.17.12-1.amzn2023.0.1.x86_64               78/102 
  Running scriptlet: samba-2:4.17.12-1.amzn2023.0.1.x86_64               78/102 
  Installing       : nss-tools-3.90.0-3.amzn2023.0.3.x86_64              79/102 
  Installing       : python3-sss-murmur-2.5.0-1.amzn2023.0.3.x86_64      80/102 
  Installing       : python3-ipalib-4.11.0-7.amzn2023.noarch             81/102 
  Installing       : python3-ipaclient-4.11.0-7.amzn2023.noarch          82/102 
  Installing       : c-ares-1.19.0-1.amzn2023.x86_64                     83/102 
  Installing       : sssd-common-2.5.0-1.amzn2023.0.3.x86_64             84/102 
  Running scriptlet: sssd-common-2.5.0-1.amzn2023.0.3.x86_64             84/102 
Created symlink /etc/systemd/system/multi-user.target.wants/sssd.service → /usr/lib/systemd/system/sssd.service.

  Installing       : sssd-krb5-common-2.5.0-1.amzn2023.0.3.x86_64        85/102 
  Installing       : sssd-krb5-2.5.0-1.amzn2023.0.3.x86_64               86/102 
  Installing       : sssd-dbus-2.5.0-1.amzn2023.0.3.x86_64               87/102 
  Running scriptlet: sssd-dbus-2.5.0-1.amzn2023.0.3.x86_64               87/102 
  Installing       : sssd-common-pac-2.5.0-1.amzn2023.0.3.x86_64         88/102 
  Installing       : sssd-ipa-2.5.0-1.amzn2023.0.3.x86_64                89/102 
  Installing       : python3-sss-2.5.0-1.amzn2023.0.3.x86_64             90/102 
  Installing       : sssd-tools-2.5.0-1.amzn2023.0.3.x86_64              91/102 
  Installing       : freeipa-client-4.11.0-7.amzn2023.x86_64             92/102 
  Running scriptlet: freeipa-client-4.11.0-7.amzn2023.x86_64             92/102 
  Installing       : freeipa-client-epn-4.11.0-7.amzn2023.x86_64         93/102 
  Running scriptlet: freeipa-client-epn-4.11.0-7.amzn2023.x86_64         93/102 
  Installing       : freeipa-client-samba-4.11.0-7.amzn2023.x86_64       94/102 
  Installing       : freeipa-python-compat-4.11.0-7.amzn2023.noarch      95/102 
  Installing       : argparse-manpage-4.5-1.amzn2023.noarch              96/102 
  Installing       : python3-argparse-manpage+setuptools-4.5-1.amzn20    97/102 
  Installing       : python3-lesscpy-0.14.0-13.amzn2023.noarch           98/102 
  Installing       : python3-rjsmin-1.2.1-4.amzn2023.x86_64              99/102 
  Installing       : python3-pypng-0.0.21-6.amzn2023.noarch             100/102 
  Installing       : python-wrapt-doc-1.14.1-6.amzn2023.x86_64          101/102 
  Installing       : python-rjsmin-docs-1.2.1-4.amzn2023.x86_64         102/102 
  Running scriptlet: freeipa-selinux-4.11.0-7.amzn2023.noarch           102/102 
  Running scriptlet: authselect-libs-1.2.3-1.amzn2023.0.2.x86_64        102/102 
  Running scriptlet: libwbclient-2:4.17.12-1.amzn2023.0.1.x86_64        102/102 
  Running scriptlet: sssd-common-2.5.0-1.amzn2023.0.3.x86_64            102/102 
  Running scriptlet: python-rjsmin-docs-1.2.1-4.amzn2023.x86_64         102/102 
  Verifying        : libldb-2.6.2-1.amzn2023.0.2.x86_64                   1/102 
  Verifying        : samba-dc-libs-2:4.17.12-1.amzn2023.0.1.x86_64        2/102 
  Verifying        : samba-2:4.17.12-1.amzn2023.0.1.x86_64                3/102 
  Verifying        : krb5-workstation-1.21-3.amzn2023.0.3.x86_64          4/102 
  Verifying        : libtalloc-2.3.4-1.amzn2023.0.2.x86_64                5/102 
  Verifying        : libsss_certmap-2.5.0-1.amzn2023.0.3.x86_64           6/102 
  Verifying        : sssd-dbus-2.5.0-1.amzn2023.0.3.x86_64                7/102 
  Verifying        : dbus-tools-1:1.12.28-1.amzn2023.0.1.x86_64           8/102 
  Verifying        : sssd-common-2.5.0-1.amzn2023.0.3.x86_64              9/102 
  Verifying        : sssd-common-pac-2.5.0-1.amzn2023.0.3.x86_64         10/102 
  Verifying        : samba-client-libs-2:4.17.12-1.amzn2023.0.1.x86_6    11/102 
  Verifying        : c-ares-1.19.0-1.amzn2023.x86_64                     12/102 
  Verifying        : python3-sss-murmur-2.5.0-1.amzn2023.0.3.x86_64      13/102 
  Verifying        : libipa_hbac-2.5.0-1.amzn2023.0.3.x86_64             14/102 
  Verifying        : samba-client-2:4.17.12-1.amzn2023.0.1.x86_64        15/102 
  Verifying        : python3-samba-2:4.17.12-1.amzn2023.0.1.x86_64       16/102 
  Verifying        : nss-tools-3.90.0-3.amzn2023.0.3.x86_64              17/102 
  Verifying        : libdhash-0.5.0-47.amzn2023.0.2.x86_64               18/102 
  Verifying        : libtevent-0.13.0-1.amzn2023.0.2.x86_64              19/102 
  Verifying        : oddjob-mkhomedir-0.34.7-2.amzn2023.0.3.x86_64       20/102 
  Verifying        : libsss_autofs-2.5.0-1.amzn2023.0.3.x86_64           21/102 
  Verifying        : libicu-67.1-7.amzn2023.0.3.x86_64                   22/102 
  Verifying        : samba-libs-2:4.17.12-1.amzn2023.0.1.x86_64          23/102 
  Verifying        : sssd-krb5-common-2.5.0-1.amzn2023.0.3.x86_64        24/102 
  Verifying        : avahi-libs-0.8-14.amzn2023.0.10.x86_64              25/102 
  Verifying        : cifs-utils-6.15-1.amzn2023.0.2.x86_64               26/102 
  Verifying        : python3-libipa_hbac-2.5.0-1.amzn2023.0.3.x86_64     27/102 
  Verifying        : oddjob-0.34.7-2.amzn2023.0.3.x86_64                 28/102 
  Verifying        : samba-ldb-ldap-modules-2:4.17.12-1.amzn2023.0.1.    29/102 
  Verifying        : sssd-tools-2.5.0-1.amzn2023.0.3.x86_64              30/102 
  Verifying        : samba-winbind-modules-2:4.17.12-1.amzn2023.0.1.x    31/102 
  Verifying        : cifs-utils-info-6.15-1.amzn2023.0.2.x86_64          32/102 
  Verifying        : authselect-libs-1.2.3-1.amzn2023.0.2.x86_64         33/102 
  Verifying        : python3-tevent-0.13.0-1.amzn2023.0.2.x86_64         34/102 
  Verifying        : samba-dcerpc-2:4.17.12-1.amzn2023.0.1.x86_64        35/102 
  Verifying        : samba-tools-2:4.17.12-1.amzn2023.0.1.x86_64         36/102 
  Verifying        : sssd-krb5-2.5.0-1.amzn2023.0.3.x86_64               37/102 
  Verifying        : augeas-libs-1.13.0-1.amzn2023.0.2.x86_64            38/102 
  Verifying        : libwbclient-2:4.17.12-1.amzn2023.0.1.x86_64         39/102 
  Verifying        : sssd-ipa-2.5.0-1.amzn2023.0.3.x86_64                40/102 
  Verifying        : libtdb-1.4.7-1.amzn2023.0.2.x86_64                  41/102 
  Verifying        : libkadm5-1.21-3.amzn2023.0.3.x86_64                 42/102 
  Verifying        : python3-gssapi-1.6.9-3.amzn2023.0.2.x86_64          43/102 
  Verifying        : python3-cffi-1.14.5-1.amzn2023.0.3.x86_64           44/102 
  Verifying        : krb5-pkinit-1.21-3.amzn2023.0.3.x86_64              45/102 
  Verifying        : tdb-tools-1.4.7-1.amzn2023.0.2.x86_64               46/102 
  Verifying        : cyrus-sasl-gssapi-2.1.27-18.amzn2023.0.3.x86_64     47/102 
  Verifying        : python3-cryptography-36.0.1-1.amzn2023.0.3.x86_6    48/102 
  Verifying        : python3-ldb-2.6.2-1.amzn2023.0.2.x86_64             49/102 
  Verifying        : python3-sss-2.5.0-1.amzn2023.0.3.x86_64             50/102 
  Verifying        : libnetapi-2:4.17.12-1.amzn2023.0.1.x86_64           51/102 
  Verifying        : samba-winbind-2:4.17.12-1.amzn2023.0.1.x86_64       52/102 
  Verifying        : python3-tdb-1.4.7-1.amzn2023.0.2.x86_64             53/102 
  Verifying        : samba-common-tools-2:4.17.12-1.amzn2023.0.1.x86_    54/102 
  Verifying        : samba-common-libs-2:4.17.12-1.amzn2023.0.1.x86_6    55/102 
  Verifying        : authselect-1.2.3-1.amzn2023.0.2.x86_64              56/102 
  Verifying        : python3-samba-dc-2:4.17.12-1.amzn2023.0.1.x86_64    57/102 
  Verifying        : sssd-winbind-idmap-2.5.0-1.amzn2023.0.3.x86_64      58/102 
  Verifying        : autofs-1:5.1.7-21.amzn2023.0.3.x86_64               59/102 
  Verifying        : libsss_sudo-2.5.0-1.amzn2023.0.3.x86_64             60/102 
  Verifying        : cups-libs-1:2.3.3op2-18.amzn2023.0.7.x86_64         61/102 
  Verifying        : sssd-nfs-idmap-2.5.0-1.amzn2023.0.3.x86_64          62/102 
  Verifying        : python3-talloc-2.3.4-1.amzn2023.0.2.x86_64          63/102 
  Verifying        : libsmbclient-2:4.17.12-1.amzn2023.0.1.x86_64        64/102 
  Verifying        : python3-netaddr-0.8.0-3.amzn2023.0.2.noarch         65/102 
  Verifying        : python3-pyasn1-0.4.8-4.amzn2023.0.2.noarch          66/102 
  Verifying        : python3-sssdconfig-2.5.0-1.amzn2023.0.3.noarch      67/102 
  Verifying        : python3-dns-2.1.0-3.amzn2023.0.3.noarch             68/102 
  Verifying        : python3-tomli-2.0.1-4.amzn2023.noarch               69/102 
  Verifying        : samba-common-2:4.17.12-1.amzn2023.0.1.noarch        70/102 
  Verifying        : python3-typing-extensions-3.7.4.3-2.amzn2023.0.2    71/102 
  Verifying        : python3-pycparser-2.20-3.amzn2023.0.2.noarch        72/102 
  Verifying        : python3-pyasn1-modules-0.4.8-4.amzn2023.0.2.noar    73/102 
  Verifying        : policycoreutils-python-utils-3.4-6.amzn2023.0.2.    74/102 
  Verifying        : python3-ply-3.11-11.amzn2023.0.2.noarch             75/102 
  Verifying        : python3-decorator-4.4.2-4.amzn2023.0.2.noarch       76/102 
  Verifying        : argparse-manpage-4.5-1.amzn2023.noarch              77/102 
  Verifying        : certmonger-0.79.19-1.amzn2023.x86_64                78/102 
  Verifying        : freeipa-client-4.11.0-7.amzn2023.x86_64             79/102 
  Verifying        : freeipa-client-common-4.11.0-7.amzn2023.noarch      80/102 
  Verifying        : freeipa-client-epn-4.11.0-7.amzn2023.x86_64         81/102 
  Verifying        : freeipa-client-samba-4.11.0-7.amzn2023.x86_64       82/102 
  Verifying        : freeipa-common-4.11.0-7.amzn2023.noarch             83/102 
  Verifying        : freeipa-python-compat-4.11.0-7.amzn2023.noarch      84/102 
  Verifying        : freeipa-selinux-4.11.0-7.amzn2023.noarch            85/102 
  Verifying        : python-rjsmin-docs-1.2.1-4.amzn2023.x86_64          86/102 
  Verifying        : python-wrapt-doc-1.14.1-6.amzn2023.x86_64           87/102 
  Verifying        : python3-argparse-manpage+setuptools-4.5-1.amzn20    88/102 
  Verifying        : python3-argparse-manpage-4.5-1.amzn2023.noarch      89/102 
  Verifying        : python3-augeas-1.1.0-10.amzn2023.noarch             90/102 
  Verifying        : python3-deprecated-1.2.13-4.amzn2023.noarch         91/102 
  Verifying        : python3-ipaclient-4.11.0-7.amzn2023.noarch          92/102 
  Verifying        : python3-ipalib-4.11.0-7.amzn2023.noarch             93/102 
  Verifying        : python3-jwcrypto-1.4.2-7.amzn2023.noarch            94/102 
  Verifying        : python3-ldap-3.4.3-4.amzn2023.x86_64                95/102 
  Verifying        : python3-lesscpy-0.14.0-13.amzn2023.noarch           96/102 
  Verifying        : python3-pypng-0.0.21-6.amzn2023.noarch              97/102 
  Verifying        : python3-pyusb-1.2.1-3.amzn2023.noarch               98/102 
  Verifying        : python3-qrcode-7.4.2-7.amzn2023.noarch              99/102 
  Verifying        : python3-rjsmin-1.2.1-4.amzn2023.x86_64             100/102 
  Verifying        : python3-wrapt-1.14.1-6.amzn2023.x86_64             101/102 
  Verifying        : python3-yubico-1.3.3-13.amzn2023.noarch            102/102 

Installed:
  argparse-manpage-4.5-1.amzn2023.noarch                                        
  augeas-libs-1.13.0-1.amzn2023.0.2.x86_64                                      
  authselect-1.2.3-1.amzn2023.0.2.x86_64                                        
  authselect-libs-1.2.3-1.amzn2023.0.2.x86_64                                   
  autofs-1:5.1.7-21.amzn2023.0.3.x86_64                                         
  avahi-libs-0.8-14.amzn2023.0.10.x86_64                                        
  c-ares-1.19.0-1.amzn2023.x86_64                                               
  certmonger-0.79.19-1.amzn2023.x86_64                                          
  cifs-utils-6.15-1.amzn2023.0.2.x86_64                                         
  cifs-utils-info-6.15-1.amzn2023.0.2.x86_64                                    
  cups-libs-1:2.3.3op2-18.amzn2023.0.7.x86_64                                   
  cyrus-sasl-gssapi-2.1.27-18.amzn2023.0.3.x86_64                               
  dbus-tools-1:1.12.28-1.amzn2023.0.1.x86_64                                    
  freeipa-client-4.11.0-7.amzn2023.x86_64                                       
  freeipa-client-common-4.11.0-7.amzn2023.noarch                                
  freeipa-client-epn-4.11.0-7.amzn2023.x86_64                                   
  freeipa-client-samba-4.11.0-7.amzn2023.x86_64                                 
  freeipa-common-4.11.0-7.amzn2023.noarch                                       
  freeipa-python-compat-4.11.0-7.amzn2023.noarch                                
  freeipa-selinux-4.11.0-7.amzn2023.noarch                                      
  krb5-pkinit-1.21-3.amzn2023.0.3.x86_64                                        
  krb5-workstation-1.21-3.amzn2023.0.3.x86_64                                   
  libdhash-0.5.0-47.amzn2023.0.2.x86_64                                         
  libicu-67.1-7.amzn2023.0.3.x86_64                                             
  libipa_hbac-2.5.0-1.amzn2023.0.3.x86_64                                       
  libkadm5-1.21-3.amzn2023.0.3.x86_64                                           
  libldb-2.6.2-1.amzn2023.0.2.x86_64                                            
  libnetapi-2:4.17.12-1.amzn2023.0.1.x86_64                                     
  libsmbclient-2:4.17.12-1.amzn2023.0.1.x86_64                                  
  libsss_autofs-2.5.0-1.amzn2023.0.3.x86_64                                     
  libsss_certmap-2.5.0-1.amzn2023.0.3.x86_64                                    
  libsss_sudo-2.5.0-1.amzn2023.0.3.x86_64                                       
  libtalloc-2.3.4-1.amzn2023.0.2.x86_64                                         
  libtdb-1.4.7-1.amzn2023.0.2.x86_64                                            
  libtevent-0.13.0-1.amzn2023.0.2.x86_64                                        
  libwbclient-2:4.17.12-1.amzn2023.0.1.x86_64                                   
  nss-tools-3.90.0-3.amzn2023.0.3.x86_64                                        
  oddjob-0.34.7-2.amzn2023.0.3.x86_64                                           
  oddjob-mkhomedir-0.34.7-2.amzn2023.0.3.x86_64                                 
  policycoreutils-python-utils-3.4-6.amzn2023.0.2.noarch                        
  python-rjsmin-docs-1.2.1-4.amzn2023.x86_64                                    
  python-wrapt-doc-1.14.1-6.amzn2023.x86_64                                     
  python3-argparse-manpage-4.5-1.amzn2023.noarch                                
  python3-argparse-manpage+setuptools-4.5-1.amzn2023.noarch                     
  python3-augeas-1.1.0-10.amzn2023.noarch                                       
  python3-cffi-1.14.5-1.amzn2023.0.3.x86_64                                     
  python3-cryptography-36.0.1-1.amzn2023.0.3.x86_64                             
  python3-decorator-4.4.2-4.amzn2023.0.2.noarch                                 
  python3-deprecated-1.2.13-4.amzn2023.noarch                                   
  python3-dns-2.1.0-3.amzn2023.0.3.noarch                                       
  python3-gssapi-1.6.9-3.amzn2023.0.2.x86_64                                    
  python3-ipaclient-4.11.0-7.amzn2023.noarch                                    
  python3-ipalib-4.11.0-7.amzn2023.noarch                                       
  python3-jwcrypto-1.4.2-7.amzn2023.noarch                                      
  python3-ldap-3.4.3-4.amzn2023.x86_64                                          
  python3-ldb-2.6.2-1.amzn2023.0.2.x86_64                                       
  python3-lesscpy-0.14.0-13.amzn2023.noarch                                     
  python3-libipa_hbac-2.5.0-1.amzn2023.0.3.x86_64                               
  python3-netaddr-0.8.0-3.amzn2023.0.2.noarch                                   
  python3-ply-3.11-11.amzn2023.0.2.noarch                                       
  python3-pyasn1-0.4.8-4.amzn2023.0.2.noarch                                    
  python3-pyasn1-modules-0.4.8-4.amzn2023.0.2.noarch                            
  python3-pycparser-2.20-3.amzn2023.0.2.noarch                                  
  python3-pypng-0.0.21-6.amzn2023.noarch                                        
  python3-pyusb-1.2.1-3.amzn2023.noarch                                         
  python3-qrcode-7.4.2-7.amzn2023.noarch                                        
  python3-rjsmin-1.2.1-4.amzn2023.x86_64                                        
  python3-samba-2:4.17.12-1.amzn2023.0.1.x86_64                                 
  python3-samba-dc-2:4.17.12-1.amzn2023.0.1.x86_64                              
  python3-sss-2.5.0-1.amzn2023.0.3.x86_64                                       
  python3-sss-murmur-2.5.0-1.amzn2023.0.3.x86_64                                
  python3-sssdconfig-2.5.0-1.amzn2023.0.3.noarch                                
  python3-talloc-2.3.4-1.amzn2023.0.2.x86_64                                    
  python3-tdb-1.4.7-1.amzn2023.0.2.x86_64                                       
  python3-tevent-0.13.0-1.amzn2023.0.2.x86_64                                   
  python3-tomli-2.0.1-4.amzn2023.noarch                                         
  python3-typing-extensions-3.7.4.3-2.amzn2023.0.2.noarch                       
  python3-wrapt-1.14.1-6.amzn2023.x86_64                                        
  python3-yubico-1.3.3-13.amzn2023.noarch                                       
  samba-2:4.17.12-1.amzn2023.0.1.x86_64                                         
  samba-client-2:4.17.12-1.amzn2023.0.1.x86_64                                  
  samba-client-libs-2:4.17.12-1.amzn2023.0.1.x86_64                             
  samba-common-2:4.17.12-1.amzn2023.0.1.noarch                                  
  samba-common-libs-2:4.17.12-1.amzn2023.0.1.x86_64                             
  samba-common-tools-2:4.17.12-1.amzn2023.0.1.x86_64                            
  samba-dc-libs-2:4.17.12-1.amzn2023.0.1.x86_64                                 
  samba-dcerpc-2:4.17.12-1.amzn2023.0.1.x86_64                                  
  samba-ldb-ldap-modules-2:4.17.12-1.amzn2023.0.1.x86_64                        
  samba-libs-2:4.17.12-1.amzn2023.0.1.x86_64                                    
  samba-tools-2:4.17.12-1.amzn2023.0.1.x86_64                                   
  samba-winbind-2:4.17.12-1.amzn2023.0.1.x86_64                                 
  samba-winbind-modules-2:4.17.12-1.amzn2023.0.1.x86_64                         
  sssd-common-2.5.0-1.amzn2023.0.3.x86_64                                       
  sssd-common-pac-2.5.0-1.amzn2023.0.3.x86_64                                   
  sssd-dbus-2.5.0-1.amzn2023.0.3.x86_64                                         
  sssd-ipa-2.5.0-1.amzn2023.0.3.x86_64                                          
  sssd-krb5-2.5.0-1.amzn2023.0.3.x86_64                                         
  sssd-krb5-common-2.5.0-1.amzn2023.0.3.x86_64                                  
  sssd-nfs-idmap-2.5.0-1.amzn2023.0.3.x86_64                                    
  sssd-tools-2.5.0-1.amzn2023.0.3.x86_64                                        
  sssd-winbind-idmap-2.5.0-1.amzn2023.0.3.x86_64                                
  tdb-tools-1.4.7-1.amzn2023.0.2.x86_64                                         

Complete!
```

```
[root@tim-amzn-freeipa ~]# /usr/sbin/ipa-client-install \
  --realm IPA.NOPE.COM \
  --principal host_registrar@NOPE.COM \
  --mkhomedir \
  --domain nope.com \
  --no-ntp \
  --unattended \
  --force-join



This program will set up IPA client.
Version 4.11.0

Discovery was successful!
Client hostname: tim-amzn-freeipa.nope.com
Realm: NOPE.COM
DNS Domain: nope.com
IPA Server: ipa01.nope.com
BaseDN: dc=nope,dc=com

Skipping chrony configuration
Successfully retrieved CA cert
    Subject:     CN=Certificate Authority,O=NOPE.COM
    Issuer:      CN=Certificate Authority,O=NOPE.COM
    Valid From:  2016-05-10 16:08:03+00:00
    Valid Until: 2036-05-10 16:08:03+00:00

Enrolled in IPA realm NOPE.COM
Created /etc/ipa/default.conf
Configured /etc/sssd/sssd.conf
Systemwide CA database updated.
Hostname (tim-amzn-freeipa.nope.com) does not have A/AAAA record.
Failed to update DNS records.
Missing A/AAAA record(s) for host tim-amzn-freeipa.nope.com: 10.69.69.69.
Missing reverse record(s) for address(es): 10.69.69.69.
Adding SSH public key from /etc/ssh/ssh_host_rsa_key.pub
Adding SSH public key from /etc/ssh/ssh_host_dsa_key.pub
Adding SSH public key from /etc/ssh/ssh_host_ecdsa_key.pub
Adding SSH public key from /etc/ssh/ssh_host_ed25519_key.pub
Could not update DNS SSHFP records.
SSSD enabled
Cannot get SELinux boolean 'sssd_use_usb': CalledProcessError(Command ['/usr/sbin/getsebool', 'sssd_use_usb'] returned non-zero exit status 255: 'Error getting active value for sssd_use_usb\n')
SELinux does not support SSSD boolean sssd_use_usb, ignoring
Configured /etc/openldap/ldap.conf
Configured /etc/ssh/ssh_config
Configured /etc/ssh/sshd_config.d/04-ipa.conf
Configuring ipa.nope.com as NIS domain.
Configured /etc/krb5.conf for IPA realm NOPE.COM
Client configuration complete.
The ipa-client-install command was successful
```

