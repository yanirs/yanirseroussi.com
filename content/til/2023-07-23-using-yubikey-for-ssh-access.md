---
title: Using YubiKey for SSH access
author: Yanir Seroussi
type: til
date: 2023-07-23T00:07:15+00:00
url: /til/2023/07/23/using-yubikey-for-ssh-access/
summary: Some pointers for setting up SSH access with YubiKey on Ubuntu 22.04.
showBreadcrumbs: true
tags:
  - DevOps
  - GitHub
  - security
---

I've been getting increasingly paranoid about computer security over the years. There's always plenty to improve as new threats and technologies keep evolving. For example, dependency chain compromises like [the one disclosed by PyTorch in December 2022](https://www.bleepingcomputer.com/news/security/pytorch-discloses-malicious-dependency-chain-compromise-over-holidays/) show that even a seemingly-benign action like installing a well-known package can result in exposure of secrets, including private SSH keys.

As part of improving my security stance, I bought a couple of YubiKeys a couple of years ago and started using them wherever possible (either directly on supported sites or indirectly via [Yubico Authenticator](https://www.yubico.com/products/yubico-authenticator/)). At some point, I realised that YubiKeys may be used for SSH access as well, but I only got around to setting it up today. Turns out it's pretty simple.

One problem with YubiKeys is that they often offer more than one way of doing things, and SSH access is no exception. [Andrej Friesen covered the options for SSH in an accessible post](https://www.ajfriesen.com/yubikey-ssh-key/), which led me to [the official Yubico page on securing SSH with FIDO2](https://developers.yubico.com/SSH/Securing_SSH_with_FIDO2.html). I went with the discoverable key option along with `ed25519` as the algorithm (see [this post](https://www.cryptsus.com/blog/how-to-secure-your-ssh-server-with-public-key-elliptic-curve-ed25519-crypto.html) for a short explanation of the different algorithms).

Following the official guide was straightforward, but then I hit this error: `sign_and_send_pubkey: signing failed for ED25519-SK "..." from agent: agent refused operation`. The common cause of this error is having the wrong permissions on the private key file, but that wasn't the case for me. After a bit of digging, I found [this Reddit thread](https://www.reddit.com/r/yubikey/comments/wip57i/ubuntu_ssh_sign_and_send_pubkey_signing_failed/) that points to a [gnome-keyring issue as the root problem](https://gitlab.gnome.org/GNOME/gnome-keyring/-/issues/101) (I use Ubuntu 22.04 on my laptop). As suggested on the Reddit thread, adding `IdentityAgent none` to the relevant hosts in my SSH config sorted out the issue. It seems like a reasonable workaround for now &ndash; I'm happy that I now have my SSH access tied to my YubiKey.
