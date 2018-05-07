# Guide to GNU Privacy Guard (Win / MacOS / Linux / UNIX)

PGP is the forward-secrecy encryption for message and file. Developed by Phil Zimmerman in 1991 from his activist root in hope for secure communication by-design. PGP is by far the most secure method of communication and has no known crypto attack against its cryptographic design. PGP was open-sourced to OpenPGP implementation, with GNU Foundation developed free software version GNU Privacy Guard, GnuPG or simply referred to as gpg. GnuPG will be the software this guide mainly focuses, along with Thunderbird extension Enigmail.

## 1.  SETUP

GPG is available on all major Linux distribution and their core package repository. To install on Debian/Ubuntu/Mint and similar Debian-based distros: `sudo apt install -y -f gnupg`. To install in Fedora/Red Hat: `sudo yum install gnupg`. [Windows](https://gpg4win.org/download.html) and [MacOS](https://sourceforge.net/p/gpgosx/docu/Download/)

On MacOS you can install [Homebrew](https://brew.sh) package manager:

Open your Terminal and paste this:

    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    
 Then install GPG with Brew:
 
     brew install gnupg

## 2.  USAGE

To generate key we are going to use the flag `--full-gen-key` or complete command `gpg --full-gen-key`

It will prompt you:

    Please select what kind of key you want:
       (1) RSA and RSA (default)
       (2) DSA and Elgamal
       (3) DSA (sign only)
       (4) RSA (sign only)
    Your selection? 

Type `1` and enter. This is the best option.

It then asks you:

    RSA keys may be between 1024 and 4096 bits long.
    What keysize do you want? (3072) 

Your choice should be `4096`, maximum key size is recommended, as shown in [here](https://www.eff.org/deeplinks/2015/10/how-to-protect-yourself-from-nsa-attacks-1024-bit-DH) RSA 1024 no longer secure.

Next:

    Please specify how long the key should be valid.
             0 = key does not expire
          <n>  = key expires in n days
          <n>w = key expires in n weeks
          <n>m = key expires in n months
          <n>y = key expires in n years
    Key is valid for? (0)

You are recommended to set your key to certain expire time. 2 to 3 years are the best. set `2y` for 2 years. Unexpired keys are dangerous and should be revoked if you had them.

Then:

    Key expires at Thu 14 Dec 2017 01:01:01 AM EST
    Is this correct? (y/N)

Type `y` and press Enter

Then:

    GnuPG needs to construct a user ID to identify your key.

    Real name:
    Email address:
    Comment:

DO NOT EVER PUT YOUR REAL NAME IF YOU ARE NOT REQUIRED. You are not required to put actual name. YOU ARE NOT ALSO REQUIRED TO PUT COMMENT!

Next:

    You selected this USER-ID:
        "abcdef <abc@me.com>"

    Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit?

If this was correct, type `O` and press Enter

It will ask you for password. DICEWARE IS RECOMMENDED.

    We need to generate a lot of random bytes. It is a good idea to perform
    some other action (type on the keyboard, move the mouse, utilize the
    disks) during the prime generation; this gives the random number
    generator a better chance to gain enough entropy.
    We need to generate a lot of random bytes. It is a good idea to perform
    some other action (type on the keyboard, move the mouse, utilize the
    disks) during the prime generation; this gives the random number
    generator a better chance to gain enough entropy.
    gpg: key 971EF8CF1B32D507 marked as ultimately trusted
    gpg: revocation certificate stored as '/home/icarus/.gnupg/openpgp-revocs.d/597B64C318F8749DE66CF69B971EF8CF1B32D507.rev'
    public and secret key created and signed.
    
    pub   rsa4096 2017-12-14 [SC] [expires: 2017-12-15]
          597B64C318F8749DE66CF69B971EF8CF1B32D507
    uid                      abcdef <abc@me.com>
    sub   rsa4096 2017-12-14 [E] [expires: 2017-12-15]

The diagram below shows what and how to read the fingerprints

    [type] [cipher] [created date]    [expire date]
     |      |           |                   |
     V      V           V                   V
    pub   rsa4096 2017-12-14 [SC] [expires: 2017-12-15]
          597B64C318F8749DE66CF69B971EF8CF1B32D507 <-- [fingerprint]
    uid                      abcdef <abc@me.com>  <== name / email
    sub   rsa4096 2017-12-14 [E] [expires: 2017-12-15]

`597B64C318F8749DE66CF69B971EF8CF1B32D507` shall be your fingerprint/keyID
or in this format `597B 64C3 18F8 749D E66C  F69B 971E F8CF 1B32 D507`

To export your key `gpg --export --armor abc@me.com`

This will be your public key

    -----BEGIN PGP PUBLIC KEY BLOCK-----
    
    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
    =f0Cr
    -----END PGP PUBLIC KEY BLOCK-----

### IT IS IMPORTANT TO PAIR YOUR PUBLIC KEY WITH YOUR FINGERPRINT WHEN YOU SHARE THEM.

## 3.  USEFUL COMMANDS

To change passphrase:

    gpg --change-passphrase abc@me.com

To upload key to keyserver:

    gpg --send-keys abc@me.com

To import keys

    gpg --import key.asc

To import from keyserver

    gpg --recv-keys bdf@you.com

To search public keys from key server

    gpg --search-keys bdf@you.com

To delete keys on public key-ring **WARNING IRREVERSE IT IF DELETED**

    gpg --delete-keys bdf@you.com

To delete keys on secret key-ring **WARNING IRREVERSE IT IF DELETED**

    gpg --delete-secret-keys bdf@you.com


ALWAYS VERIFY FINGERPRINT!!!

## 4.  ENCRYPT, SIGN & DECRYPT

To list all signatures in keyring

    gpg --list-signatures

To list signature from specific key

    gpg --list-signatures bdf@you.com

To check and list all signatures in keyring

    gpg --check-signatures

To check and list signature from specific key

    gpg --check-signatures bdf@you.com

**Always sign your messages!**

To encrypt your message:

    cat file.txt | gpg -e -a --recipient bdf@you.com --sign -u abc@me.com

To encrypt your message on Windows

    type file.txt | gpg -e -a --recipient bdf@you.com --sign -u abc@me.com

To encrypt file:

    gpg -e -a --recipient bdf@you.com --sign -u abc@me.com file.txt

To decrypt message

    gpg -d file.asc

**REMEMBER! - ALWAYS VERIFY EACH OTHER'S SIGNATURES !!!**

To encrypt file using symmetrical crypto:

    gpg -c --cipher-algo aes256 --armor file.txt

### NOTE - YOU SHOULD ALWAYS SPECIFY --cipher-algo flag! SOME VERSION OF GPG ON WINDOWS MIGHT USE CAST5 AS DEFAULT, CANADIAN-DESIGNED CIPHER AND IT IS KNOWN TO BE BROKEN BY CSE/CSIS. OTHER SECURE CIPHERS ARE TWOFISH, BLOWFISH, AES and AES192. AES256 IS THE BEST RECOMMENDATION.

**THINGS TO NOTE** PGP is not perfect end to end encryption. PGP only **encrypts content**, and *not metadata* - this means that when you send an encrypted message to a recipient, anyone intercepting your message will not see the content, but still able to see its date, time, location, email... To minimize your metadata, you and your recipient can use fully encrypted services like [Tutanota](https://tutanota.de) and [Protonmail](https://protonmail.ch). It's not perfect forward secrecy, by compromising secret key and password on targeted machine or device can and will compromise your secret contents!

## [BACK TO HOME PAGE](index.md)
