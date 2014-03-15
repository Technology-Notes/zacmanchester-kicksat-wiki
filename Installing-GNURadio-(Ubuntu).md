I've written a script that should handle installing GNURadio, the RTL-SDR and Funcube drivers for the USB receiver dongles, the Sprite receiver blocks, and [GQRX](http://gqrx.dk/), on a recent installation of [Ubuntu](http://www.ubuntu.com/) (or [Linux Mint](http://linuxmint.com/)). It's been tested on fresh installs of 64 bit [Ubuntu 12.04, 13.10](http://www.ubuntu.com/download/desktop), and [Linux Mint 16](http://www.linuxmint.com/download.php). Here's what to do:

#### 1. Download Install Script
[Grab the script here](https://raw.github.com/zacinaction/kicksat-groundstation/master/Install-SpriteRadio). Right click the link and "Save As" somewhere convenient (e.g. your home folder).

#### 2. Make The Script Executable
This can be done from the terminal or the GUI. From the terminal, execute the command `chmod +x Install-SpriteRadio`. To use the GUI, right click on the file and click "Properties". At the top of the Properties window, click the "Permissions" tab, then check the box next to "Allow executing file as program".

![Check Box](https://dl.dropboxusercontent.com/u/19178351/GItHub%20Wiki%20Pictures/GNURadio_CheckBox.png)

#### 3. Run The Script
Open a terminal, navigate to the folder containing the script, and run it by typing `./Install-SpriteRadio`. You'll need to be connected to the internet to download the necessary packages and source code. The install process will take a while (possibly up to an hour) and you will have to enter your password a few times.

![Terminal](https://dl.dropboxusercontent.com/u/19178351/GItHub%20Wiki%20Pictures/GNURadio_Term.png)

#### 4. Run GRC
If everything goes well, you should now find a program called "GRC" (which stands for GNURadio Companion) in your applications menu. Download the [Sprite receiver file here](https://raw.github.com/zacinaction/kicksat-groundstation/master/Sprite%20Receiver.grc), then open it in GRC. If you see a block diagram like the one below (with no missing blocks), that means all the necessary software has been installed.

![GRC](https://dl.dropboxusercontent.com/u/19178351/GItHub%20Wiki%20Pictures/GNURadio_GRC.png)