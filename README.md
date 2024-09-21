#### Work-In-Progress (rearranging things and adding more lesser known PKI softwares)

# Awesome Cryptography GUI Tools
Making the list of available OS tools for cryptography and user-friendly cryptography GUI tools.

## Categories
* [Windows](#windows)
* [Linux](#linux)
* [Mac OS](#mac-os)
* [Android](#android)
* [Cross-Platform](#cross-platform)

## Windows
These utilities only run on Windows (not cross-platform).

### Windows Certificate Manager Snap-In
![Freeware and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) ![No homepage is available.](https://img.shields.io/badge/No_Homepage-gray)

![certmgr.msc running on Windows 8.1.](https://user-images.githubusercontent.com/415502/271792055-2332fd61-8b82-4890-94be-4fcaf09002e1.png)

Microsoft's built-in solution for managing the Windows operating system's certificate stores.

It only supports x509 certificates and the available certificate stores are defined by Microsoft (**Root**, **Enterprise**, **Personal** ...). It's not intended to sign or encrypt data (cryptographic operations), it only manages the certificates themselves.

No support for PGP certificates either. Such certificates are decentralized without a Certificate Authority, so it would make no sense for Microsoft to support them in the Certificate Manager snap-in.

Windows 8.1 & earlier uses **certmgr.msc** while Windows 10 & later uses **certmgmt.msc** as the filename.


### SignGUI
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://www.briggsoft.com/signgui.htm)

![SignGUI running on Windows 7.](https://user-images.githubusercontent.com/131653305/284413619-44b181f3-b6d0-4ba5-a129-cc03d714a4f5.png)

This is the most reliable GUI frontend for Microsoft's **signtool.exe** program (from the Windows SDK Tools). It supports signtool.exe version 6.3 or later, and cans handle SHA2 signatures with dual-signing.

This software doesn't ship with the Windows Signtool utility that you can get separately from the [Wayback Machine](https://archive.org/details/windowssdk). The official download for the Windows 8.1 SDK is now broken because Microsoft removed its required setup files from their servers.

### MGTEK SmartCard Tools
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://www.mgtek.com/smartcard)

![MGTEK SmartCard Tools running on Windows 10.](https://user-images.githubusercontent.com/131653305/284414889-b4d9701f-4697-4b7a-b3f3-60c0312689eb.png)

An alternative to the [Gemalto MiniDriver Manager](#gemalto-minidriver-manager) that supports running Microsoft's signtool.exe with pre-configured smartcard PINs.

It provides both a command-line **ScSigntool.exe** utility and a graphical smartcard minidriver manager (that additionally allows renaming certificate slots on a smartcard compared to Gemalto's).

### Gemalto MiniDriver Manager
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://supportportal.thalesgroup.com/csm?id=kb_article_view&sysparm_article=KB0017162)

![MGTEK SmartCard Tools running on Windows 7.](https://i.postimg.cc/N048XWzw/Gemalto-Mini-Driver-Manager-2-4-6.png)

This is the most famous minidriver manager online for smartcards. It allows essential functionality in order to make use of PKI smartcards, since Windows has no built-in facilities for managing them.

Albeit coming from Gemalto (now Thales (now Entrust)), it supports all brands of PKI cards. Actually it's only a few specific sensitive operations such as **Card Factory Reset** & **PIN Policy Management** that are unsupported with HID Global's Crescendo PKI products (requires [ActivClient](#activclient) which is not free).
