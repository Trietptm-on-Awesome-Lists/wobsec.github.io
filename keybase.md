# Guide to Using Keybase

**[Keybase](https://keybase.io)** is a cross-platform OpenPGP key directory for linking social media services. This is the best user-friendly alternative to GNUPG.

## 1.  SETUP

### ANDROID

https://play.google.com/store/apps/details?id=io.keybase.ossifrage

### iOS

https://itunes.apple.com/us/app/keybase-crypto-for-everyone/id1044461770

### WINDOWS

Download and install Keybase [here](https://prerelease.keybase.io/keybase_setup_386.exe)

Confirm there's a Keybase icon in your system tray.

### MACOS

[Download the DMG here](https://prerelease.keybase.io/Keybase.dmg)

### LINUX

Debian 64 bit:

    curl -O https://prerelease.keybase.io/keybase_amd64.deb
    sudo dpkg -i keybase_amd64.deb
    sudo apt install -f
    run_keybase

Debian 32 bit:

    curl -O https://prerelease.keybase.io/keybase_i386.deb
    sudo dpkg -i keybase_i386.deb
    sudo apt install -f
    run_keybase

Fedora 64 bit:

    sudo yum install https://prerelease.keybase.io/keybase_amd64.rpm
    run_keybase

Fedora 32 bit:

    sudo yum install https://prerelease.keybase.io/keybase_i386.rpm
    run_keybase

Arch:

    pacaur -S keybase-bin
    run_keybase

## 2.  USAGE

### BASIC COMMANDS

To register:

    keybase signup

To update (ONLY WORKS ON WINDOWS):

    keybase update

To see help:

    keybase help

To see help on specific command:

    keybase help tor

In command line, log into your Keybase account:

    keybase login username

You will be asked to name your device:

    $ keybase login wobsec
    
    
    ************************************************************
    * Name your new device!                                    *
    ************************************************************
    
    
    
    Enter a public name for this device: wobsec
    
    
    
    ✔ Success! You provisioned your device wobsec.
    
    You are logged in as wobsec
      - type `keybase help` for more info.

To logout:

    keybase logout username

### GENERATE KEYS

To generate your first key

    keybase pgp gen
    Enter your real name, which will be publicly visible in your new key: WobSec 
    Enter a public email address for your key: abc@def.com
    Enter another email address (or <enter> when done): def@zxc.com
    Enter another email address (or <enter> when done): 
    Push an encrypted copy of your new secret key to the Keybase.io server? [Y/n] y
    When exporting to the GnuPG keychain, encrypt private keys with a passphrase? [Y/n] y
    ▶ INFO PGP User ID: EXAMPLE <abc@def.com> [primary]
    ▶ INFO PGP User ID: EXAMPLE <def@zxc.com> 
    ▶ INFO Generating primary key (4096 bits)
    ▶ INFO Generating encryption subkey (4096 bits)
    
    ▶ INFO Generated new PGP key:
    ▶ INFO   user: WobSec <abc@def.com>
    ▶ INFO   4096-bit RSA key, ID EXAMPLE, created 2018-05-07

Voila! Now your key is generated!

To list your keys:

    keybase pgp list

To export your public key:

    keybase pgp export

### ENCRYPT AND DECRYPT MESSAGE & FILE

To encrypt message:

LINUX/MACOS: `cat file.txt | keybase pgp encrypt`

WINDOWS: `type file.txt | keybase pgp encrypt`

To encrypt and sign:

LINUX/MACOS: `cat file.txt | keybase pgp sign`

WINDOWS: `type file.txt | keybase pgp sign`

To decrypt

    cat file.asc | keybase pgp decrypt

    type file.asc | keybase pgp decrypt

### VERIFY AND LINK SOCIAL MEDIA

Example, to verify proof on Github:

    keybase prove github

## [BACK TO HOME PAGE](index.md)
