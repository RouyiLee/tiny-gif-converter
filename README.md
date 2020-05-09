![License Badge](https://img.shields.io/badge/FFmpeg-4.2.2-ff69b4) ![License Badge](https://img.shields.io/badge/PySimpleGUI-4.18.2-orange) ![License Badge](https://img.shields.io/badge/python-3.5%2B-blue) ![License Badge](https://img.shields.io/badge/platform-osx--64-lightgrey) ![License Badge](https://img.shields.io/badge/license-Apache--2.0-green)<br>



<p align="center">
  <img width="500" src="./assets/icon.png">
</p>

<h2 align=center>Tiny GIF Converter</h2>
 
This is a tiny gif converter for WeChat official account writers or bloggers. This converter takes in a video or gif file, then it converts or compresses the file to a gif image, which is compatible with WeChat official account. The program has been tested on the Mac OS X with Python 3.6 environment. Both [FFmpeg](https://github.com/FFmpeg/FFmpeg) and [PySimpleGUI](https://github.com/PySimpleGUI/PySimpleGUI) are cross-platform libraries, so it should be worked well on other OS theoretically. Please let me know if something went south in Windows or Linux.

## Requirements 

- FFmpeg
- PySimpleGUI

## Setup

Here is an installation guidance for Mac users. Windows and Linux are following the same setup procedure.

### Mac OS X

The simplest way to install FFmpeg on Mac is using [Homebrew](https://brew.sh). Run the following command in macOS Terminal (zsh) to install it:

```bash
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

Once it is done, use the following command to install FFmpeg:

```bash
$ brew install ffmpeg
```

The last step is installing PySimpleGUI:

```bash
$ pip install pysimplegui
```

Here [Miniconda](https://docs.conda.io/en/latest/miniconda.html) is recommended, which provides a lightweight virtual environment for us.

Now you are all set!

## Run

Use the following command to run the program:

```bash
$ python main.py
```

I may release an executable file in the future, sorry for the inconvenience for now.

Some files are provided in the sample folder just for testing. They are from [T.E.D.D. 1104](https://github.com/ikergarcia1996/Self-Driving-Car-in-Video-Games) and an [ICLR 2020 paper](https://openreview.net/pdf?id=SyxrxR4KPS) respectively.

## Overview

```python
// main.py

import PySimpleGUI as sg

from convert_to_gif import gif_converter

# ---------------------- Window Layout ---------------------- #
layout = [***]

# ---------------------- Create Window ---------------------- #
window = sg.Window('Tiny GIF Converter', layout)

# Event Loop to process "events" and get the "values" of the inputs
while True:
    event, values = window.read()
    if event in (None, 'Cancel'):  # if user closes window or clicks cancel
        break
    elif event == 'Convert':
        # Converting
        if gif_converter(**kwargs) == 'Done':
            break
```

```python
// convert_to_gif.py

import subprocess

# Convert file
subprocess.call([
                'ffmpeg',
                '-ss', start_time,  # start time
                '-t', duration,  # duration
                '-i', load_path,  # original file dir
                '-pix_fmt', 'yuv420p',  # pixel formats
                '-r', fps,  # fps
                '-s', frame_size,  # resolution
                # output file dir
                '-y', os.path.join(save_path, out_file_name),
                ])
```

## Appearance

Here is what the GUI looks like. You can change the theme which you like.

DarkTeal2 | DarkPurple | LightBrown3
:-----:|:-----:|:-----:
<img width="300" src="./assets/screen_shot_0.png"> | <img width="300" src="./assets/screen_shot_1.png">|<img width="300" src="./assets/screen_shot_2.png">


## Sample

<img width="640" src="./assets/demo.gif">

## License

[Apache License 2.0](LICENSE)









