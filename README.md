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
