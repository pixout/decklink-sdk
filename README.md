# Blackmagic DeckLink SDK

[![Contributors](https://img.shields.io/github/contributors/pixout/decklink-sdk.svg)](https://github.com/pixout/decklink-sdk/graphs/contributors)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Last Commit](https://img.shields.io/github/last-commit/pixout/decklink-sdk.svg)](https://github.com/pixout/decklink-sdk/commits/master)

---

An **unofficial repository** containing openly licensed SDK files from Blackmagic's Desktop Video Software Development Kit.  
These files were originally distributed in a ZIP archive that was once publicly available at:  
<https://www.blackmagicdesign.com/developer/products/capture-and-playback/sdk-and-software>

---

## DeckLink Driver Installation (Linux)

### 1. Download Desktop Video
Download Desktop Video from the [Blackmagic website](https://www.blackmagicdesign.com/support/family/capture-and-playback).

### 2. Extract the tar archive
```sh
tar -xf Blackmagic_Desktop_Video_Linux.tar
```

### 3.Install the .deb package

In the subfolder of the extracted Blackmagic Desktop Video Linux folder, enter the following subfolder:
deb/x86_64 (for 64-bit systems).

Then run:
```sh
cd deb/x86_64
sudo apt install libegl1-mesa
sudo dpkg -i
```
(This helped in my case.)

P.S.
If, after running sudo apt install libegl1-mesa, errors still appear, try installing libgl1-mesa-glx and then run:
sudo apt --fix-broken install

Here is a forum thread on the same tutorial:
[Das Werkstatt Forum – DeckLink SDK Installation](http://www.das-werkstatt.com/forum/werkstatt/viewtopic.php?t=2656)