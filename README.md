# Vagrant and Ansible stuff for LimeSDR

- Quick and dirty way to get the LimeSDR up and running on OSX.

  This installs the following software:
    - LimeSuite
    - Soapy modules
    - Gnuradio
    - GQRX

## Requirements
* VirtualBox and VirtualBox extension pack (https://www.virtualbox.org/wiki/Downloads)
* vagrant (brew install vagrant)
* ansible (brew install ansible)

## Instructions
1. Install VirtualBox, vagrant, and ansible
2. Clone this repo
3. Run `vagrant up`
    * This will setup an ubuntu VM with most prerequirements as well as create shortcuts for things

## Test
* Test if LimeSDR is recognized and USB filter works correct:

```dmesg|egrep -i '(lime|myriad)'```

expected output: something like:
```
[  468.079086] usb 3-1: Product: LimeSDR-USB
[  468.079087] usb 3-1: Manufacturer: Myriad-RF
```   

* Test SoapySDR:

```SoapySDRUtil --find=filter=lime```

expected output: something like:
```
######################################################
## Soapy SDR -- the SDR abstraction library
######################################################

Found device 0
  addr = 1d50:6108
  driver = lime
  media = USB
  module = STREAM
  name = USB 3.0 (LimeSDR-USB)
  serial = <xxxxxxxxxxxxxxxx>
```

* Test LimeSDR-stuff

  Follow guide on https://wiki.myriadrf.org/LimeSDR-USB_Quick_Test .

## Known issues
- This is in fact not the recommended way to use an SDR due to USB limitations on Virtualbox.  However, it is a quick way to have a working Lime-configuration on OSX.   Please do not use in production.
- Please select the correct antenna in GQRX.  Default is 'none'.  It took me some time to figure this out... :)
- This works for me.  (MacOS 10.12.3, Virtualbox 5.1.14, Vagrant 1.9.1, Ansible 2.2.1.0) Results may vary...

## More info
- https://wiki.myriadrf.org/LimeSDR_Quick_Start
- http://wiki.myriadrf.org/Packaging#GNU_Radio_PPA
- https://myriadrf.org/blog/limesdr-application-ecosystem/
- https://myriadrf.org/blog/limesuite-driver-architecture/
- https://wiki.myriadrf.org/Lime_Suite
- https://github.com/pothosware/SoapySDR/wiki
- https://github.com/pothosware/pothos-sdr/wiki/Tutorial
