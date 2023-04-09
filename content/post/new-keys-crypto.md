+++
categories = ["general"]
tags = ["security"]
images = ["images/security-ny.jpg"]
banner = "images/security-ny.jpg"
date = "2020-07-26T13:47:00-04:00"
title = "GPG, SSH: New Keys"
menu = ""
description = "Updating my cryptographic keys for GPG and SSH after over a decade of not thinking about it much!"

+++

I recently changed jobs, and decided that this was probably also a good opportunity to revisit cryptography and keys. My SSH and GPG keys were created many years ago, I made a new SSH key recently but can't remember all the options I used. I know in the time since I made my GPG keys some of the algorithms I used back then have become deprecated, and new SSH key types have been added that are better than what was available. In general it is advisable to use bigger keys, and better hashing algorithms too.

GPG Key
-------

I have been a little mixed on my GPG key for a while as it has been signed at a number of key signing parties as part of my long history of open source development. I have decided to keep my old key around, sign my new key but create something new using the best advice. After looking around I thought this [blog post][gpg-post] had a lot of good advice including limiting information leaked, and preferring currently accepted algorithms. I edited my gpg.conf, and generated my key as advised.

I did as recommended using RSA, 4096 bit keys, and edited they key to add subkeys for each purpose. I also added a uid for my active email addresses that I want to be able to use. I also added a portrait photograph at 240x288 in the JPEG format as seems to be the common recommendation. It warned me about the size being large, but I added it anyway. The public key is pretty big, I am undecided on whether that will end up being an issue.

I then signed my new key with my (now very) old key, generated revocation certificates, and uploaded it:
```bash
$ gpg2 --default-key CE046C697D4117BD --sign-key 3F33E7859E24E2E9
$ gpg2 --output 3F33E7859E24E2E9.rev --gen-revoke 3F33E7859E24E2E9
$ gpg2 --send-keys 3F33E7859E24E2E9
$ gpg2 --export --armor 3F33E7859E24E2E9 > 3F33E7859E24E2E9.pub.asc
```

I then added the key to GitHub so that I could use it to verify tags/commits. I used the following to see a summary of the private keys I had available:
```bash
$ gpg --list-secret-keys --fingerprint --keyid-format long
```

Then I needed to configure Git to use my new signing key, so I checked in on the ID of the signing subkey, and added that to my global Git configuration:
```bash
$ git config --global user.signingKey FE4AFB8A22E09BB7
```

SSH Key
-------

For the SSH key things are much simpler, I don't have any legacy systems to worry about, and so just use the latest algorithm:
```bash
$ ssh-keygen -o -a 100 -t ed25519
```

This uses the new OpenSSH format rather than the old PEM format (-o), and 100 KDFs (Key Derivation Functions) to increase the resistance to brute-force password cracking. If your private key is stolen it is pretty much done, but you may as well makes things harder, it will make password verification slower though so you don't want to make that number too high.

Done
----

There you have it, my short search on current best practices, and then trying to make sure I have updated my keys on the different services I use.

[gpg-post]: https://blog.eleven-labs.com/en/openpgp-almost-perfect-key-pair-part-1/
