# midiExperimentsWithRaspberryPi
Using MIDI over UART with Raspberry Pi

Examples are using the py-midi library: https://pypi.org/project/py-midi/

If using MIDI over UART with a Pi 3 or 4 on Stretch or Buster, you'll need to make the following edits:

sudo nano /boot/cmdline.txt

    # delete: 
  
console=serial0, 115200
  
    # save & exit

sudo nano /boot/config.txt

    # add:
    
enable_uart=1
dtoverylay=pi3-miniuart-bt
dtoverlay=midi-uart0
     
    # Check raspi.config to make sure logging in over UART is disabled

sudo reboot

    # Checking settings after reboot

vcgencmd measure_clock uart 

    # checks UART clock speed

ls -lh /dev/* 

    # lists all devices /serial0 should be on AMA0; /serial1 should be ttyS0
