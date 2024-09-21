#### Work-In-Progress (rearranging things and adding more lesser known PKI softwares)
In order: freeware-proprietary / paid-proprietary / free-opensource

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

![SignGUI running on Windows 7.](https://i.postimg.cc/NMZWh97D/SignGUI.png)

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

### Microsoft PIN Tool
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://www.catalog.update.microsoft.com/Search.aspx?q=KB909520)

![Microsoft PIN Tool running on Windows 7.](https://i.postimg.cc/HnsTx77g/Microsoft-PIN-Tool.png)

This is a lesser known utility since it's very old (originally for Windows XP) that cans be used standalone to change PKI smartcard PIN codes & also unblock PINs with Admin keys. It does for the end-user the same basic job as popular & expensive card management softwares from big companies (PIN change & PIN unblock).

The Microsoft PIN Tool is also available unofficially with the ability to handle [ActivClient](#activclient) cards, as my [Microsoft PIN Tool ActivID Mod](#microsoft-pin-tool-activid-mod).

### Microsoft PIN Tool ActivID Mod
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://github.com/gdmeunier/microsoft-pin-tool)

![Microsoft PIN Tool ActivID Mod running on Windows 7.](https://i.postimg.cc/NMdWdCL3/Microsoft-PIN-Tool-Activ-ID-Mod.png)

The Microsoft PIN Tool modified for ActivClient-initialized PKI smartcards (HID Global cards with a static unblock code). It successfully unblocks ActivClient Crescendo cards without using the official ActivClient PIN Initialization Tool.

Your static unblock code is always the Response code to unblock the card and set a new User PIN. This modification means there's no need to use [ActivClient](#activclient) anymore for unblocking HID Crescendo cards.

### VersaSec vSEC_TOOL_K
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://versasec.com/products/vsec-tool-k/)

![VersaSec vSEC_TOOL_K running on Windows 7.](https://i.postimg.cc/85g0tQ1X/v-SEC-TOOL-K.png)

VersaSec's free utility for advanced PKI smartcard management, with the ability to change PIN, unblock PIN and also change the Admin key.

It as well allows on supported smartcards (many actually) to set their Security Policy such as the maximum PIN try count and character restrictions (e.g. no letters).

Very useful for hardening the Security Policy of your digital signature tokens and e.g. block them upon the first failed PIN attempt.

### ActivClient
![Paid and Proprietary software.](https://img.shields.io/badge/Paid-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://www.hidglobal.com/products/activclient)

![ActivClient running on Windows 7.](https://i.postimg.cc/k4h72gNR/Activ-Client.png)

HID Global's PKI middleware for Crescendo smartcard products, it also supports many more PKI smartcard brands.

Its price is nonetheless highly expensive for the little it brings compared to using the already existing & free minidriver managers found online. Its main selling point appears to be the ability to use its PKCS11 library (*acpkcs11.dll*) & import Root certificates into smartcards of its own brand.

It's highly difficult if not impossible to purchase it from HID Global, if you wish to buy it you will only be able to get it from third-party resellers.
