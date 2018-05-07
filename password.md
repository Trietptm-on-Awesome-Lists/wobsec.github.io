# Guides to Creating and Using Secure Passwords

Because passwords are almost always the weakest link in any security system where they are used, the first step to better security is better password practice.

The goal when creating a password is to pick one that is part of a large class of equally likely alternatives. This way, it is not possible to guess your password without (potentially) trying all of these other possibilities, which is important as a computer can typically test billions of possibilities every second. The strength of a password is often measured with something called entropy, which is the logarithm of the size of this class of other similar passwords.

### Things to avoid

Don’t pick a dictionary word or a proper noun! Passwords are often easy to crack because most people pick a password that is a variation on a word in the dictionary. There are simply not that many wordscharacters in human languages: it is trivial for a computer to try them all! This includes words where you have replaced some letters with numbers. For example, “L0V3” is just as easy to crack as “LOVE”. Don’t use the same password for all your accounts. If you use a password one place, never use it again anywhere else, since that allows compromise of one login to compromise every other login you’ve reused that password with. Also, it can be better to write down your passwords in a secure place rather than use the same one everywhere. Don’t forget to change your password. You should change your password immediately if you have even the slightest feeling someone else could have possibly seen any part of it, or a service provider is compromised. Never tell anyone your password, especially if they ask for it.

How do you create a password that is strong and yet easy to remember? This can be really tough. There is one generally approved methods:

## Passphrases

Pick a few random words you can easily remember. Mixing in words from different languages and non-dictionary words is a good idea (just like it's a good idea to use unusual characters in a password). String these together into a long passphrase. This will be longer, but easier to type. There is software available to make these easily called Diceware.

## Diceware

Diceware is password generator by random methods by dice or random number generator (RNG) and randomly picking words or phrases from set of wordlists. Diceware method is often preferred over traditional password generating due to its strong entropy and easy to remember phrases. The method of using a dice is often difficult and time-consuming, however fortunately there is software that could ease the problem.

[Diceware](https://github.com/ulif/diceware) is an open-source Python program can be used to generate complex diceware passphrase.

Python 2.7.x is required. [Windows](https://www.python.org/downloads/windows/), [MacOS](https://www.python.org/downloads/mac-osx/). Python is available on across all Linux platforms, can be installed from their package manager.

To install diceware: `pip install diceware` (use sudo if asked for permission)

Use `--help` flag for manual.

To run diceware with 5 words: `diceware -n 5`

To generate 5 words with 5 special characters: `diceware -n 5 -s 5`

diceware can be paired with using a real dice to generate words. `diceware -r realdice --dice-sides 6`

To make it easier to memorize, you could even come up with a humorous memory aid. The sillier and more unusual it is, the more likely it is that you will remember it. [See also: XKCD: Password Strength]: https://www.xkcd.com/936/

### THINGS TO CONSIDER WHEN GENERATING DICEWARE

Weak entropy diceware could be generated from words coincidentally combined into a single dictionary word.

The minimum secure number for words should be 5 words. On iPhone and other iOS device, diceware word numbers can be minimized to 3 words if maximum tries for login password enabled. On Android device, minimum numbers should be 5 words. Recommended number for words on Full Disk Encryption and other device must be 7 words.

***WARNING**: Never use TouchID, Fingerprint Scanning, or Facial recognition for unlocking your devices. Not only can biometrics be coerced out of you, spoofed, copied, and enjoy none of the legal protections against self-incrimination, but they also prove your ownership of the device and prevent you from denying ownership of the device should you be find yourself on the wrong side of a questioning table or the wrong side of a gavel, and be subpoenaed to unlock it!

## Password Managers

You will, over the course of your life end up with a large number of passwords, and it will be impossible to remember them all. You should consider installing a password manager, such as KeePass2 or KeePass X. Some Linux installations come with KeePass2 by default. KeePass will keep your passwords in an easily manageable password database, which is then encrypted using a password. This has the effect of reducing the number of passwords you will need to memorize.

For the best security, you should keep your KeePass file on a separate computer you can keep that has had its network adapters physically removed and that. An old desktop running Linux, even one with only 512MB of RAM and and old Pentium processor works well for this, since you won’t be using it for anything else.

(TBA KEEPASS INSTALLATION SECTIONS!)

## Passwords

If you can only use a limited number of characters, start with multiple words you can easily remember. Convert these words to non-words (for example, by taking the first letter of each word). Add a few random uppercase letters, numbers, or symbols (which increases the number of possible characters in each position and therefor entropy), and you are done.

For example:

You could turn “The Revolution Will Not Be Televised” into “trwNbt” and then add a few random characters for “trwNbt!42”.

### DISCLAIMER: The intro section here are not from mine, originally from /r/Cyberzine Wiki that I contributed to, later merged with Socialist Rifle Association (SRA). THIS PAGE WILL BE REVISED WHEN I HAVE MORE TIME.
