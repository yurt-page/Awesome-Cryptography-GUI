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

### Microsoft TPM Virtual Smartcard
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://learn.microsoft.com/en-us/windows/security/identity-protection/virtual-smart-cards/virtual-smart-card-tpmvscmgr)

*(The tpmvscmgr.exe command-line utility doesn't have a GUI)*

The **tpmvscmgr.exe** is a virtual smartcard utility shipped by default with Windows 10 & later operating systems by Microsoft.
It allows you to make use of your TPM with CAPI-enabled applications (CAPI standing for smartcard API), that includes Windows logon and protecting passwords in password managers or for use with non-System Bitlocker drives.

The virtual smartcard that gets created by this utility will inherit the TPM's lockout policy for failed authentication attempts. It's nonetheless recommended to always keep a backup of the material you use to encrypt data in the virtual smartcard.

Make sure to always prefer using *Admin Key* instead of *PUK* for unblocking your smartcard (*/AdminKey* switch) and your own Admin Key.

You will be able to unblock your virtual smartcard with the [Microsoft PIN Tool](#Microsoft-PIN-Tool) and unique challenge-response codes rather than a static *PUK*.
The response code cans be computed with your Admin Key the Gemalto Response Code Calculator which is part of [Gemalto MiniDriver Manager](#Gemalto-MiniDriver-Manager).

### VersaSec vSEC_TOOL_K
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://versasec.com/products/vsec-tool-k/)

![VersaSec vSEC_TOOL_K running on Windows 7.](https://i.postimg.cc/85g0tQ1X/v-SEC-TOOL-K.png)

VersaSec's free utility for advanced PKI smartcard management, with the ability to change PIN, unblock PIN and also change the Admin key.

It as well allows on supported smartcards (many actually) to set their Security Policy such as the maximum PIN try count and character restrictions (e.g. no letters).

Very useful for hardening the Security Policy of your digital signature tokens and e.g. block them upon the first failed PIN attempt.

### VersaSec vSEC_CMS_K
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://versasec.com/products/vsec-cms/)

![VersaSec vSEC_CMS_K running on Windows 7.](https://i.postimg.cc/Y9VjJ3sP/v-SEC-CMS-K.png)

This utility is a more advanced version of the vSEC_TOOL_K from VersaSec for PKI smartcards. It even supports Biometric Policies if your PKI smartcard (here USB Token) has a fingerprint reader.

It nonetheless stays free unlike what the official homepage says, since only the vSEC_CMS_T & vSEC_CMS_S products require a license to be purchased before using them.

The utility runs for free in a 'limited' *Tool* mode albeit it doesn't appear to be limited much if at all, with some hidden functionalities being revealed if you purchase its *Operator Token* from a reseller.

The VersaSec vSEC_CMS_K cans also be downloaded freely as part of the [Taglio PIVKey Administrator Kit](https://pivkey.zendesk.com/hc/en-us/articles/360003283491-The-vSEC-CMS-Utility) (you don't need a Taglio product to use it).

### Crypto Stuff
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](http://jacquelin.potier.free.fr/CryptoStuff/)

![Crypto Stuff running on Windows 7.](https://i.postimg.cc/gjqZZ7sZ/Crypto-Stuff.png)

A full-featured cryptography software for trying out symmetric & asymmetric ciphers such as AES, RSA, Blowfish, Twofish, and so on.

You can do hashing, encryption, decryption, signing and verification using this tool. It's literally as if it was a GUI frontend for .NET Framework's System.Cryptography namespace, if you want a developer joke.

It's pure gold. It's even useful for reverse-engineering cryptographic ciphers & proprietary file formats.

### Crypware Virtual Cryptoki
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://ncryptoki.com/download.aspx)

![Crypware Virtual Cryptoki running on Windows 7.](https://i.postimg.cc/RhLqYFnw/Crypware-Virtual-Cryptoki-Explorer.png)

A masterfully crafted PKCS11 Token/HSM emulator that supports the PKCS11 2.20 specification, compatible with any PKCS11-enabled application.

Its default PIN codes are *1234* but they can be changed to anything you like, including alphanumeric letters (since smartcard PINs aren't SIM card PINs).

This emulator is powered by a core library named **vcki.dll** available for both 32 & 64-bit Windows systems. You basically just have to provide your PKCS11 application with the *vcki.dll* file to start using the virtual PKCS11 token.

### PKI Solutions ASN1 Editor
![Free and Open-Source software.](https://img.shields.io/badge/Free-Open--Source-green) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://github.com/PKISolutions/Asn1Editor.WPF)

![PKI Solutions ASN1 Editor running on Windows 10.](https://user-images.githubusercontent.com/131653305/284415784-5b7b69e0-93f1-4fde-a658-611e48f0a906.png)

Forensic-grade ASN.1 object inspector, it cans handle PKCS#12, PKCS#7, PEM, DER or Hex dumps. It cans also surgically edit certificates & CSR requests, it allows arbitrary data modifications.

This tool is gold for debugging faulty certificates & public or private keys in binary format. It also contains a built-in DER/PEM data converter for switching between binary & text file formats.

### Pkcs11Admin
![Free and Open-Source software.](https://img.shields.io/badge/Free-Open--Source-green) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://www.pkcs11admin.net/)

![Pkcs11Admin running on Windows 10.](https://i.postimg.cc/ZYQnNLwh/pkcs11admin.png)

A fully featured PKCS11 Token management utiltiy that allows specifying the card reader to use, and which Token to connect to.
Once connected to a Token, it cans be used to initialize or unblock the User PIN, or it cans be used to log into the PKCS11 Token and import or export data from it.

Pkcs11Admin offers the ability to log into the Tokens as Administrator (SO PIN) which allows exporting most (if not all) of the PKCS11 private data elements (p11 folder's datXX files).
We can however notice that it's currently not possible to select many PKCS11 data elements at once (multi-selection) for import & export, so you will have to do it one by one.

### OpenSSLUI
![Free and Open-Source software.](https://img.shields.io/badge/Free-Open--Source-green) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://github.com/A9G-Data-Droid/OpenSSLUI)

![OpenSSLUI running on Windows 10.](https://i.postimg.cc/XvbqnnNq/128235989-164f4c8e-394f-46ec-8f4b-83cbb4d68859.jpg)

OpenSSLUI is a GUI frontend for OpenSSL that allows you to easily create a Root CA and generate then sign certificate requests with it (CSR requests).
This utility cans be used to create your own CSRs or just for generating a self-signed certificate.

This utility is mostly intended for creating your own SSL Root CA (e.g. for HTTPS) rather than being a full-featured GUI for OpenSSL ([imagine if it actually was](https://smallstep.com/blog/if-openssl-were-a-gui/)).
It does provide utilities for converting PEM private keys & certificate files to PFX (PKCS12 file) but doesn't allow you to use your own certificate usage policies (EKUs) so you will be limited to 'SSL client' and 'SSL server'.

### OpenSSL Wizard
![Free and Open-Source software.](https://img.shields.io/badge/Free-Open--Source-green) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://github.com/deviousasti/openssl-wizard)

![OpenSSL Wizard running on Windows 10.](https://i.postimg.cc/pdS2pxRK/75088352-07941780-5572-11ea-9ac5-a078a2faf6a7.png)

A compact OpenSSL GUI frontend for generating a Root CA that uses either RSA or ECDSA.
It cans generate CSRs (certificate requests) in a more advanced form than OpenSSLUI since it allows you to insert a SubjectAltName (DNS attribute) and IP address (IP attribute).

It has a builtin facility to convert files between PEM & DER (binary encoded) formats, it's able to also split a PFX file (PKCS12) into two separate PEM & CRT files.
Finally it's able to combine a PEM or DER private key & a certificate into one PKCS12 (PFX) file.

And lastly, this utility is written in C# and cans be installed with the Chocolatey package manager.

### SignFiles.com Signer Tools
![Paid and Proprietary software.](https://img.shields.io/badge/Paid-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://www.signfiles.com/signature-software/)

![P7S Signer running on Windows 10.](https://www.signfiles.com/resources/P7SSigner.jpg)

A proprietary suite of paid digital signature GUI tools for Windows. They support CAdES, eIDAS, QSCD and other norms.

It uses .NET Framwork and the software suite features a **PDF**, **P7S**, **XML** & **DOCX Signer**.

## Cross-Platform
These programs can run of multiple operating systems (generally thanks to QtFramework or Java).

### Fortra Open PGP Studio
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://www.goanywhere.com/products/open-pgp-studio)

![Fortra Open PGP Studio running on Windows 7.](https://user-images.githubusercontent.com/131653305/284412737-c7629a8e-5db1-4e94-b6a0-b0356dd43ee4.png)

Simple and efficient PGP management software, with a good user interface. It has the ability to both manage PGP keys and also do cryptographic operations (namely decrypting, encrypting, verifying & signing data).

This utility also supports creating new PGP keys, additionally to importing and exporting them.

Windows versions of [Open PGP Studio v1.2.2 (x64)](https://web.archive.org/web/20231120223315/https://static.goanywhere.com/releases/goanywhere/openpgpstudio/gapgpstudio1_2_2_windows-x64.exe) and [Open PGP Studio v1.2.1 (x86/x64)](https://web.archive.org/web/20231120223425/https://static.goanywhere.com/releases/goanywhere/openpgpstudio/gapgpstudio1_2_1_windows.exe) are available for direct download as well (so no need for a good temporary email service).

### XCA
![Free and Open-Source software.](https://img.shields.io/badge/Free-Open--Source-green) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://hohnstaedt.de/xca/)

![XCA running on Windows 7.](https://i.postimg.cc/WbfqB0dg/XCA.png)

This is the singlehandedly most useful certificate management utility known to date for a GUI *OpenSSL* utility. This is the most complete one in terms of managing a full *Certificate Authority* with certificate revocation lists.

It features an extraordinary set of supported public & private keys, ranging from PKCS1 to PKCS8 encoding for x509 authentication or SSH connection. Its feature set for PGP is however limited to managing and converting only the public & private keys instead of managing the PGP certificates as well.

It finally also supports PKCS12 keystores among others alongwith PKCS11 if you provide it with the proper PKCS11 library of your smartcard manufacturer (*OpenSC* rarely works unless your card is very popular).

### KeyStore Explorer
![Free and Open-Source software.](https://img.shields.io/badge/Free-Open--Source-green) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://github.com/kaikramer/keystore-explorer)

![KeyStore Explorer running on Windows 10.](https://raw.githubusercontent.com/kaikramer/kaikramer.github.io/main/images/win10_mykeystore.png)

Very useful and complete utility for managing PKCS12 & Java Keystores. While it's mostly known for managing certificates it also possesses less talked-about features such as the ability to sign JAR files and sign JWT tokens.

Its feature set is now considerably better than the Java keytool program that it initially wanted to be a GUI frontend for.

KeyStore Explorer has now climbed to being a full Java KeyStore manager, that also offers the ability to do cryptographic operations and convert public/private keys between different formats.

### Kleopatra
![Free and Open-Source software.](https://img.shields.io/badge/Free-Open--Source-green) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://apps.kde.org/kleopatra/)

![Kleopatra running on Linux.](https://i.postimg.cc/MHgG8WnG/kleopatra.png)

Cross-platform certificates & keypairs manager. It supports managing x509 certificates and PGP keys, including the ability to generate a revocation certificate for PGP keys.

It cans be used to generate & verify PGP keys. It cans also perform cryptographic operations such as signing, encryption and decryption. It's finally able to retrieve certificates from LDAP servers and PGP keys from PGP-keyservers.

You can use it on Windows with [Gpg4win](https://gpg4win.org/index.html).

### ActivClient
![Paid and Proprietary software.](https://img.shields.io/badge/Paid-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://www.hidglobal.com/products/activclient)

![ActivClient running on Windows 7.](https://i.postimg.cc/k4h72gNR/Activ-Client.png)

HID Global's PKI middleware for Crescendo smartcard products, it also supports many more PKI smartcard brands.

Its price is nonetheless highly expensive for the little it brings compared to using the already existing & free minidriver managers found online. Its main selling point appears to be the ability to use its PKCS11 library (*acpkcs11.dll*) & import Root certificates into smartcards of its own brand.

It's highly difficult if not impossible to purchase it from HID Global, if you wish to buy it you will only be able to get it from third-party resellers.

ActivClient is mostly known for its Windows versions, albeit Linux & Mac OS versions also exist. It's currently unknown where the average customer should go to purchase a Linux or Mac OS version of ActivClient.

## Linux
These programs only run on Linux OS distros.

### GNOME Seahorse
![Free and Open-Source software.](https://img.shields.io/badge/Free-Open--Source-green) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://wiki.gnome.org/Apps/Seahorse)

![GNOME Seahorse running on Linux.](https://upload.wikimedia.org/wikipedia/commons/5/5b/Gnome_Seahorse_3.12.2.png)

GUI for SSH keys, X509 certs, PGP/GPG. Linux only.

### Pyrite
![Free and Open-Source software.](https://img.shields.io/badge/Free-Open--Source-green) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://github.com/stokito/pyrite)

![Pyrite running on Linux](http://b19.org/linux/pyrite/1enc_txt.png)

GnuPG/OpenSSL encryption/signing GUI for Linux implemented with Python & PyGTK.

### a7crypt
![Free and Open-Source software.](https://img.shields.io/badge/Free-Open--Source-green) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://github.com/ryran/a7crypt)

![a7crypt running on Linux](http://b19.org/linux/a7crypt/menuA.png)

GUI frontend for symmetric encryption/decryption.

Bash, Zenity, Linux

## Mac OS

### Cypt
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://en.freedownloadmanager.org/Mac-OS/Cypt-FREE.html)

![Cypt running on Mac OS.](https://1786035589.rsc.cdn77.org/s_mac/502/502872_4.png)

Nice and clean PGP GUI for Mac OS. Proprietary.

## Android
These are applications that run only on Android.

### Root Certificate Manager
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://apkpure.com/root-certificate-manager-root/net.jolivier.cert.Importer)

![Root Certificate Manager running on Android.](https://i.postimg.cc/nhW3dsKh/Root-Certificate-Manager.png)

This is the equivalent of the **Windows Certificate Manager Snap-In** but for Android instead. This application requires *Root* access (just like regular Linux systems) and cans import custom Root certificates into your system's trusted keystore.

This allows you to entirely bypass user-imported CA restrictions added in Android 7.0 Nougat up to Android 9.0 Pie, with Android 10 permanently locking the Android system partition in read-only mode.

The user-imported CA restrictions impose that your custom certificates aren't trusted by default for intercepting Android apps' network traffic, requiring you to recompile them with a flag that explicitly allows custom user-imported CA certificates.

This utility is therefore a Trusted Root Certificate import utility just like Windows's own and will only work up to Android 9.0 due to newer Android OS versions' limitations.

### Dory Cert
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://apkpure.com/dory-certificate-rsa-csr-x5/io.tempage.dorycert)

![Dory Cert running on Android.](https://i.postimg.cc/bw6w4PdJ/Dory-Cert.png)

This application is a keystore manager that supports PKCS12 and x509 certificates. It also supports both public & private keys in both PEM & binary formats (PGP is however not supported).

It as well includesthe ability to inspect certificates & cryptographic keyfiles, additionally to creating new certificates and private keys. Most of the rest is common functionaliy such as importing & exporting certificates & keys.

### x509 Certificate KeyStore Generator
![Free and Proprietary software.](https://img.shields.io/badge/Free-Proprietary-red) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://apkpure.com/x509-certificate-keystore-gene/main.scheka.ew.certificatgenerator)

![x509 Certificate KeyStore Generator running on Android.](https://i.postimg.cc/MpXSMQK6/x509-Certificate-Key-Store-Generator.png)

Describing the features of this app would be pretty long, it's basically **makecert.exe** but for Android. Additionally, it supports all OpenSSL certificate generation options.

You can generate *Root certificates* and your own TLS certificates directly from your mobile phone with it.

### OpenKeyChain
![Free and Open-Source software.](https://img.shields.io/badge/Free-Open--Source-green) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://www.openkeychain.org/)

![OpenKeyChain running on Android.](https://www.openkeychain.org/public/images/screen1.png)

Simple and efficient PGP key management software, it allows other Android applications to do PGP cryptographic operations with its own API and is supported by many Android email clients & messaging apps.

It features the basic functionalities of encryption & decryption, digital signature & their verification in the OpenKeyChain application itself. You should nonetheless think of it as a *Secure PGP Framework for other Android applications*.

Example applications using it are [K9 Mail](https://f-droid.org/en/packages/com.fsck.k9/) and [Conversations.im](https://f-droid.org/en/packages/eu.siacs.conversations/). One more lesser talked-about feature of OpenKeyChain is the ability to use a *YubiKey* NFC device for secure cryptographic operations.

### Android PIN Unblocker
![Free and Open-Source software.](https://img.shields.io/badge/Free-Open--Source-green) [![Visit the Homepage.](https://img.shields.io/badge/Homepage-blue)](https://github.com/gdmeunier/android-pin-unblocker/)

![Android PIN Unblocker running on Android.](https://i.postimg.cc/jq1LZKLP/1-main-app-screen.png)

This application allows you to generate unblock codes for PKI smartcards using your Admin key and phone. These are used incase you accidentally (or intentionally) block your smartcard PIN codes.

So its purpose is to generate smartcard unblock codes using your Admin key and phone instead of requiring a computer, incase you cannot accept to type your Admin key while being observed by nearby employees of staff, for example.

The purpose of the QR Code scanning functionality is to allow quick unblocking of smartcards, since you can then simply:
- make a QR Code for the Request code (e.g. using [CodeTwo QR Code Desktop Reader & Generator](https://www.codetwo.com/freeware/qr-code-desktop-reader/)),
- click on Generate to get your Response Code,
- click on the Share button and share it to a QR Code generator app,
- on the computer scan the Response QR Code from your webcam,
- the rest is a matter of copy-pasting text.

## See Also

* [cryptool](https://www.cryptool.org): set of GUI tools and some of them are open-source like [jcryptool](https://github.com/jcryptool/core).
  - The compamy also has a good YouTube channel ([Cryptography for Everybody](https://www.youtube.com/@CryptographyForEverybody))
* [GnuPG (GPG) Frontends](https://www.gnupg.org/software/frontends.html): list of GnuPG frontends
* [PGP-GUI](https://github.com/stokito/PGP-UI): a Java Swing app based on Bouncy Castle
* [oSSLSignCode](https://github.com/mtrojnar/osslsigncode): a free alternative to Microsoft Signtool, it's also cross-platform
