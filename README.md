# Proxmark3

### What is proxmark 
Proxmark is an open-source tool used by security researchers to interact with and analyze RFID (Radio-Frequency Identification) technology. It can read, emulate, and test RFID tags and systems, making it valuable for understanding and assessing RFID security. However, it can also be misused for unauthorized access or fraud, so it must be used responsibly and legally. 
### RFID
RFID stands for Radio-Frequency Identification. It's a technology that uses radio waves to wirelessly identify and track objects, people, or animals. RFID systems consist of RFID tags or chips that store information and RFID readers or scanners that communicate with the tags. RFID has various applications, including inventory management, access control, payment cards, and tracking systems in logistics and transportation. 

## Installation
[proxspace.7z](https://github.com/Gator96100/ProxSpace/releases/download/v3.11/ProxSpace.7z) (from the [source](https://forum.dangerousthings.com/t/getting-started-with-the-proxmark3-easy/9050))


Extract the 7z file

```
cd proxmark3
```

git clone

```
git clone https://github.com/RfidResearchGroup/proxmark3.git
```

```
cp Makefile.platform.sample Makefile.platform
```

```
notepad Makefile.platform
```

Notice the lines;

PLATFORM=PM3RDV4

#PLATFORM=PM3GENERIC


#PLATFORM=PM3RDV4
PLATFORM=PM3GENERIC

**In this case we are using PM3RDV4 so there is no # before PM3RDV4**

The compile commands in Linux are bundled into a simple make command. Now we just tell ProxSpace to compile the firmware and client software.

```
make clean && make -j8 all`
```

With your Proxmark3 connected and showing as a new virtual com port in the device manager, it’s time to flash the new firmware updates (bootloader and full image). Start with the bootloader by typing

```
./pm3-flash-bootrom
```
Now we need to flash the full image by typing…

```
./pm3-flash-fullimage
```

With the firmware updated to the current version, now it’s time to run the client. To do this just run the pm3 command in the /proxmark3 directory

```
pm3
```

```
exit
```

```
cd ..
```

```
ls -la
```

```
notepad .bashrc
```

In this file add ``proxmark3/pm3`` in the last line

```
runme64
```


**We are all set**

Tune low frequency card

```
lf tune
```

tune high frequency card 

```
hf tune
```


Identify High Frequency cards
```
pm3 --> hf search
```

Identify Low Frequency cards
```
pm3 --> lf search
```

Measure antenna characteristics, LF/HF voltage should be around 20-45+ V
```
pm3 --> hw tune
```

Check versioning
```
pm3 --> hw version
```

Check overall status
```
pm3 --> hw status
```

``lf search`` will only detect low card which have any data in it, else it wont detect

we can add data by 

```
lf hid clone -r aaaaaa
```

 to wipe data,

```
lf t5 wipe
```





