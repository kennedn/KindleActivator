# KindleActivator
Older Kindle models, (1, 2, DX, 3 ...) require that a license file (AudibleActivation.sys) be present on the device to allow the playback of audible content. 

As it stands, the Audible/Amazon login flow has changed so much that these old devices can no longer log in and retrive this license by themselves.

KindleActivator is designed to streamline the retrieval of licenses for these devices.

## Features
- Auto-detection of plugged-in Kindles within Linux
- Full CLI wizard
- Install directly to device
- Able to print activation bytes, allowing audio extraction with ffmpeg.

## How to run

### Prerequisites
- Python >=3.6
  
Run pip install from within the project directory to install dependancies:
```bash
python3 -m pip install .
```
This should install all required dependancies, after which the script can be ran:
```bash
python3 kindle_activator.py
```
### Usage

The tool will walk through a Wizard. If one or more Kindles are detected then the only requirement
from the user is to follow the prompts to login to their Audible account to retrieve activation.

#### Serial
If prompted, you can find your Devices serial by Navigating to
Menu --> Settings --> Device Info

Key in the Serial Number field

<img src="images/serial.png" width="300"/>

### Activation Bytes

After Activation has occured you can also `Print activation bytes`. 
These bytes can be used to play .aax files natively or remove DRM entirely, example commands:

Play Natively:
```bash
mpv --demuxer-lavf-o=activation_bytes=XXXXXXXX audiobook.aax
```

Decode to MP3:
```bash
ffmpeg -activation_bytes XXXXXXXX -i audiobook.aax audiobook.mp3
```

### Notes

Kindle auto-detection will not function on Windows and Mac OS systems.
