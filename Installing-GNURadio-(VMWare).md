If you are unable to install Ubuntu, VMWare on Windows is another option. Though performance suffers when running in a virtual machine, I've found it's good enough to record .wav files from an RTL dongle or Funcube.

### 1. Install VMWare Player

First, download and install the free [VMWare Player](https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/6_0). If you already have one of the other versions of VMWare (e.g. Workstation or Fusion) you can skip this step.

### 2. Download The KickSat Virtual Machine Image

Next, download the [pre-configured KickSat VMWare image](https://dl.dropboxusercontent.com/u/19178351/KickSatVM.7z). Right click the link and "Save As" somewhere convenient. The image file is compressed with 7-Zip to make the download go faster. If you don't already have a program to decompress it, [download and install 7-Zip](http://www.7-zip.org/).

Once you have the image file downloaded and 7-Zip installed, decompress the image by right clicking and selecting 7-Zip => Extract Here. Decompressing will probably take a few minutes.

### 3. Run VMWare

After decompressing, you should see a folder called "KickSatVM" with two files inside ("KickSat.vmx" and "KickSat.vmdk"). Double click "KickSat.vmx" and VMWare Player should start up and boot the virtual machine. If asked weather the virtual machine was moved or copied, select copied. If asked to download and install guest additions, you can skip it - they're already installed.