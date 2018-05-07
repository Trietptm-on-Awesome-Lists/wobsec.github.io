# Guide to METADATA

Metadata is the contextual information trails of everything you do and act in the modern world, as of who/what/where/when/why/how they came about, it does not distinguish whether it was physical or digital actions. An example of metadata would be your snail mail in the post office. The stamp, location, identity and the envelope you used for your mail would be the metadata. Although the fact that you can never completely remove all metadata, there are certain metadata types of metadata which is are dangerous to be leaked from content such as files or communication shared, and they can be linked back to you even if your initial communication method was secure. With enough metadata of any type, you can create a sizable profile of your intended target. Also known as as doxing. Something as simple as camera serial or printer's dot, to build enough of these unique patterns, potential attacker could link your public activity with your personal activity.

To simply explain what is metadata: they are the data about what, where, when, who and which that could identify you by linking to your different identities from unique patterns, fingerprints and behaviours by analyzing the metadata. Although the fact that you can never completely remove all metadata, there are certain metadata types which are dangerous to be leaked from content such as files or communication shared, and they can be linked back to you even if your initial communication method was secure. The mentioned metadata types are EXIF from picture and document files. Examples of such data are time and date created/modified, creator's machine, encoded fingerprint, encoder type, to more critical metadata such as camera model serial, GPS coordinates and sometime geography location, usually embedded from pictures taken with location service enabled. These media files sometime embedded with full name or machine's name of the device used to create the media.

With enough metadata of any type, you can create a sizable profile of your intended target. The official term for this type of metadata profiling, OSINT, open-source intelligence. Also known as as doxing. Even with something as simple as camera serial or printer's dot, to build enough of these unique patterns, potential attacker could link your public activity with your personal activity. This was a tactic by law enforcement to single out protesters from public rally or riot, not by face recognition or other believed-CSI magics but metadata embedded in media files uploaded to the web that shared similar metadata to the media files on their personal profile, thus compromising their own identity and/or real location. This method of metadata connection is called linkability.

There are tools were developed to strip these specific metadata. Tools such as *MAT* and *pdf-redact-tools* are important to anonymizing your files you share in public. However, they are not silver bullets and there will never be a tool that could completely strip all metadata. The goal to have these tools is to minimize your metadata footprints, where you fail to practice opsec and further with bad security culture can foil any attempt to anonymize your metadata even with the best tools. No amount of security and privacy could protect you without your own common sense and awareness.

### MAT

MAT stood for Metadata Anonymisation Tool, it automatically strips all harmful metadata from media, archive, torrent and document files. MAT is built-in to Tails OS and could be installed from Debian default repository on Debian-based distributions (Debian, Ubuntu, Mint, Trisquel...) with the follow command: `sudo apt install -y -f mat`

Although its default version is on CLI, MAT could be used as GUI version by launching from Alt-F2 or terminal/konsole then to type in `mat-gui`. In this guide will be focused on the CLI version for its complete features. To see its manual you can either printing it by `mat -h` or with `--help` flag, and `man mat`. Note that MAT will strip metadata and overwrite newly stripped file(s) over existing file(s) so if you preferred to keep the original file(s), use `-b` or `--backup` flag.

To strip a single file: `mat file.jpg`

To strip a file and keep its original backup (back up will be copied to file.jpg*.bak*): `mat -b file.jpg` or `mat --backup file.jpg`

To strip all files in a folder with same extension: `mat *.jpg`

To strip all files in a folder regardless of extension (MAT will show error on unstrippable files): `mat *`

To check if the file is stripped of harmful metadata: `mat -c file.jpg` or `mat --check file.jpg`

To list of existing metadata on unstripped file: `mat -d file.jpg` or `mat --display file.jpg`

To reduce/resize PDF quality: `mat -L file.pdf` or `mat --low-pdf-quality file.pdf`

To list all supported formats: `mat -l` or `mat --list`

### pdf-redact-tools

pdf-redact-tools was developed by The Intercept staff to redact and stripp metadata from their leaked documents and protecting their source. Recently, one of their leaks were exposed by unexplored metadata type, printer's yellow dots that contain laser printer's serial numbers and date/time of the printed papers, and thus their source was exposed and caught. The said tool set has since been updated and included the feature of stripping printer's dots from scanned PDF document.

It can be installed from added repository on Ubuntu or from sources on supported platforms.

To install on Ubuntu from its repository:

    sudo add-apt-repository ppa:micahflee/ppa
    sudo apt-get update && sudo apt-get install -y -f pdf-redact-tools

To install from sources on other platform (requirement: git):

    git clone https://github.com/micahflee/pdf-redact-tools.git
    cd pdf-redact-tools

Debian and Debian-based distributions:

    sudo apt-get install imagemagick libimage-exiftool-perl python-stdeb python-all fakeroot build-essential
    ./build_deb.sh
    sudo dpkg -i deb_dist/pdf-redact-tools_*-1_all.deb

Fedora and Red Hat based distros:

    sudo dnf install rpm-build ImageMagick perl-Image-ExifTool
    ./build_rpm.sh
    sudo dnf install dist/pdf-redact-tools-*-1.noarch.rpm

Mac OSX:

    brew install imagemagick exiftool gs
    sudo cp pdf-redact-tools /usr/local/bin

For Arch, [it was packaged here.](https://aur.archlinux.org/packages/pdf-redact-tools/)

We only use pdf-redact-tools to strip metadata and not redacting information, we can run the tool with following command `pdf-redact-tools --sanitize file.pdf` or `pdf-redact-tools -s file.pdf`

To remove printer's dot by converting to black and white, `pdf-redact-tools --achromatic file.pdf` or `pdf-redact-tools -a file.pdf`

**WARNING**: Work cautiously with PDF files as they can be embbedded with malicious codes or binded malware into the file and compromise your system. In the case of pdf-redact-tools, one of its dependency is ImageMagick, has been known for critical vulnerabilities that could be used take over your machine triggered by malicious PDFs from using any ImageMagick version (6.x). Recommended working environment for PDF would be on live distro such as Tails OS, in VM, or under sandboxed environments such as Qubes OS.

If necessary, convert PDF document to raw text, or using another metadata stripping tool: [Qubes PDF Converter](https://github.com/QubesOS/qubes-app-linux-pdf-converter)

TIPS: You can check if scanned document in your device by overlaying pure blue layer under GIMP and set it to opaque value, then zoom it, it will reveal the yellow dots.

Unmentioned tools below will be discussed further in the future for advanced anonymizing metadata:

[pdfparanoia](https://github.com/kanzure/pdfparanoia) - PDF watermarking removal

[anonymouth](https://github.com/psal/anonymouth) - stylometric & linguistic analysis and anonymizing

## [BACK TO HOME PAGE](index.md)
