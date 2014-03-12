**NOTE: These instructions don't include installation of drivers for the RTL dongles, and therefore are not very useful.**

### 1. Download and Install a 32 Bit Version of Python

I recommend the Anaconda Python distribution as it has a nice easy installer and comes with almost everything you need. Just [get it here](http://09c8d0b2229f813c1b93-c95ac804525aac4b6dba79b00b39d1d3.r79.cf1.rackcdn.com/Anaconda-1.9.1-Windows-x86.exe) and double click to install.

### 2. Download and Install PyGTK

One package that Anaconda doesn't include that GNURadio depends on is PyGTK. After installing Anaconda, download and install PyGTK from [here](http://ftp.gnome.org/pub/GNOME/binaries/win32/pygtk/2.24/pygtk-all-in-one-2.24.2.win32-py2.7.msi). The default settings are fine.

### 3. Install Python Packages

GNURadio requires a couple of additional Python packages. Open a Command Prompt as administrator by finding "Command Prompt" in the Start menu, right clicking on it, and selecting "Run as administrator". In the new window, execute the command "conda install cheetah". Once that finishes you can close the terminal window. 

### 4. Download and Install GNURadio

Now we're ready to install GNURadio. Grab the [Windows binary here](http://files.ettus.com/binaries/gnuradio/gnuradio_v3.7.2.1/gnuradio_3.7.2.1_Win32.exe) and double click.

### 5. Configure PATH

The last thing you have to do is add GNURadio's libraries to your system PATH and PYTHONPATH. Open the control panel and navigate to "System Properties". Under the "Advanced" tab, click the "Environment Variables" button. Under "System variables", click "New" and add a variable called "PYTHONPATH" with the value C:\Program Files (x86)\gnuradio\lib\site-packages.

### 6. Run GNURadio

You can now run GNURadio Companion from the Start menu (it should be under "gnuradio"). 