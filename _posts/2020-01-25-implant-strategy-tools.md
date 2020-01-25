---
layout: post
title: "Deciding on a Cyborg Implant: Exploring NFC Smartcard Tools"
subtitle: "Exploring and testing tools for reading/writing/cloning smartcards to eventually implant them in my hand."
description: Exploring and testing tools for reading/writing/cloning smartcards to eventually implant them in my hand.
permalink: adventures-into-nfc
image: /img/implant-icon.jpg
tags: [nfc, rfid, smartcard, implant, acr122u, linux, dangerous things, i am robot, cyborg]
published: true
---

I have been toying with the idea of getting an implant for a few years for access control and other NFC-coolness such as storing business cards or medical records.
Nothing quite like being to key to your house or never forgetting your gym card.
Those fantasies have recently been kicked into gear by a group of close friends who want to group-buy implants and arranged a professional body modder to do the job.
So the time is ripe to jump into the world of RFID and NFC implants and determine what options are out there for the nacant cyborg.
I have never modded my body in any way before and am really apprehensive of the idea.
I have no tattoos, no piercings, not even an earring.
In this post I weigh all the options, the risks, and mainly functionality that these implants can provide before pulling the trigger.
Functionality will decide which implant chip I buy and even IF I get one at all.

# Desired Functionality
In order for these RFID implants to work well, they cannot be placed on top of eachother (generally).
In use the most practical locations for RFID/NFC implants are in the hand and on the upper wrist.
For access control, this is specifically limited to the hand and the right hand is preferable as many card readers are located to the right.
You don't want to akwardly have to twist your body in order to open a door. 
Any practical implant strategy is thus inherently limited to the subdermal surface area on your hands and wrists.

1. Access control: Right hand implant.

2. NFC applications/data storage: Wrist. Side TBD.

Today we will focus on Acces control.
. 

# Exploring Requirements

The goal: Collecting data and identifying the make and model of my most use smartcards.
This is needed to determine which implant to get from many vendors such as Dangerous Things and I Am Robot.

1. Collect info on all my smartcards currently in use.
2. If most-used smartcards are cloneable/emulatable: research implant option. Find one which can emulate your most-used card(s)`
    Else: I will not get an Acces Control implant yet, since there is limited daily-use and I am not planning on changing out my locks for electronic ones.

## Hardware and System
- ACS ACR122U-A9 USB2.0: This is a smartcard reader/writer that I saw recommended everywhere.
This is the latest model (which will cause some issues for tooling down the line).
It was discounted on Amazon.de so I got it for 29EUR.

We will use the reader to read and identify all my smartcards.

- OS: Ubuntu 18.04 (Linux Mint)
- Dell Latitude E7450

# Software

## pcsc-tools: A good quick start

1. Download and install pcscd:
`sudo apt-get install pcscd pcsc-tools`

2. Test your card reader with: `pcsc_scan`

3. If this fails with the message:
'''
Scanning present readers…
Waiting for the first reader...
'''

You will have to blacklist pre-installed drivers.
Add these lines to `/etc/modprobe.d/blacklist.conf`:
'''
install nfc /bin/false
install pn533 /bin/
'''

## ACR122U smartcard terminal drivers
First we need to install the reader's drivers:

Go to https://www.acs.com.hk/en/driver/3/acr122u-usb-nfc-reader/ and select the latest Linux driver package.
These are updated regularly so it's worth checking for the latest package.

1. Unplug your reader when installing drivers.

2. Download & unzip:
`wget https://www.acs.com.hk/download-driver-unified/11929/ACS-Unified-PKG-Lnx-118-P.zip && unzip ACS-Unified-PKG-Lnx-118-P && cd ACS-Unified-PKG-Lnx-118-P`

3. Select the right directory for your Linux distribution. Mine is Ubuntu 18.04 Bionic Beaver:
`cd ACS-Unified-PKG-Lnx-118-P/acsccid_linux_bin-1.1.3/ubuntu/bionic`

4. Install package. This will depend on the package manager on your system. For Ubuntu 64bit:
`sudo dpkg -i libacsccid1_1.1.3-1~ubuntu14.04.1_amd64.deb`

5. Restart the pcscd service daemon:
`sudo service pcscd restart`

## pcsc_scan
Now we start scanning cards and identifying them with the `pcsc_scan` command.
Cool!
We can start collecting make and model of all our smartcards now!
Here is what I got:
- Enter overview table of SCs: description (non-conf), chipset candidate, ART

Note that pcsc_scan uses the ART of the card to select potential candidate models.
Some more research will be needed to determine the exact card with certainty.

Seems like my most-used card is probably a Mifare Classic 1K, which is good news as these are crackable and emulatable.
These legacy cards have a proprietary cryptographic function called Crypto1 which has been cracked long ago.
There are even some tools for cracking these cards' keys. Nice!

# Setting up lib-nfc
In order to be absolutely 
lib-nfc provides a lot of tools and functionality for interacting with NFC smartcards.
It is also required by many other tools such as `mfoc` which we will use for cracking 4byte Mifare Classic 1k cards.
