---
layout: post
title: Sharing encrypted files using Encfs and Drobox (or whatever cloud storage you are using)
---

I recently needed to share some sensitive data files with a colleague. We wanted something that would allow us to analyse the same set of files simultaneously even when those files changed. For various reasons our preferred solution was syncing encrypted files using a shared directory on dropbox. I'm running OSX 10.9 and my colleague is using Windows 8 so we also needed a cross-platform solution. 

Our initial idea was to create an encrypted volume using [TrueCrypt](http://truecrypt.sourceforge.net) but we abandoned ths given last year's [security warning](http://truecrypt.sourceforge.net).  Besides changes to files in an encrypted volume do not seem to propagate to dropbox  until the volume is unmounted (please correct me if I'm wrong), which would be a major annoyance. 

So, we decided on an alternative solution which used the open source [EncFS](http://www.arg0.net/#!encfs/c1awt) (encrypted filesystem) project. This solution appeals to my paranoid side since you can explicitly see the files you are sharing are encrypted.

(This is the important bit:)

The latest stable version of EncFS is 1.7.5. However, if you intend on syncing your files with a windows machine  **you will want to install EncFS 1.7.4**. This is because the windows port ([encfs4win](http://members.ferrara.linux.it/freddy77/encfs.html)) is based on 1.7.4 and files encrypted with 1.7.4 are incompatible with those using 1.7.5. 

##### Installation

Here are the steps to install EncFS 1.7.4.

- **OSX 10.9 (Mavericks)**  
  1. Install osxfuse with macfusion compatibility layer, available from  https://osxfuse.github.io/
  2. Install the wonderful [Homebrew package manager](http://brew.sh) (if you don't have it already) and run from a terminal:
```brew install https://raw.githubusercontent.com/jollyjinx/encfs.macosx/master/encfs.rb```

- **Windows 7/8**  
There is a windows port called [encfs4win](http://members.ferrara.linux.it/freddy77/encfs.html) which is based on encfs 1.7.4.

- **Linux**  
For Ubuntu at least installation is pretty straight forward. Follow the instructions here: https://help.ubuntu.com/community/FolderEncryption.

##### Usage

Once you have EncFS up and running you can pretty much just follow the instructions given here:  
https://www.bestvpn.com/blog/11385/protect-cloud-storage-files-encfs/
 