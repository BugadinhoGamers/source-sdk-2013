# OutSourced
## A modified Source 2013 SDK.
# Get Started
### Setting up the Source SDK Base
Install Source SDK Base 2013 from the links below:
* [Source SDK Base 2013 Multiplayer](steam://rungameid/243750) - The recommended one, works even for singleplayer.
* [Source SDK Base 2013 Singleplayer](steam://rungameid/243730) - The worst one, it's unpatched, only use it if you really need to.
# Setting up
## Source SDK 2013 on Windows
* Download and install [Visual Studio 2013](https://go.microsoft.com/fwlink/?LinkId=532495&clcid=0x409)
* Download and install the [Multibyte MFC Library](https://www.microsoft.com/en-gb/download/details.aspx?id=40770)
* Navigate to ```mp\src\``` or ```sp\src\``` and run ```createallprojects.bat```
* Open ```everything.sln``` from the same folder.
* Select the everything solution, located under the Solution Explorer list, then from the middle menu, right next to the Auto drop down menu (the properties box/pane under the solution explorer), change Debug to Release.
* Right Click on the everything solution, then select Build Solution.
## Source SDK 2013 on macOS
__If you are using macOS Mojave or higher, building the Source SDK 2013 source code will be highly complicated due to Apple deprecating the 32 bits architecture. You will get an error/warning about updating the ```ARCHS``` variable in Xcode to be something else than ```i386```.__
* Install [Xcode 5.0.2](https://developer.apple.com/downloads/more)
* You will also need to have the "Command Line Tools" installed. You can find this in Xcode Preferences -> Downloads -> Components window.
* Run the following scripts to generate project files:
```
cd mp/src
./createallprojects
```
_games.xcodeproj and everything.xcodeproj will be generated in the src folder._
* To compile the tools, server and client libraries open everything.xcodeproj and games.xcodeproj in Xcode and build the projects (Product -> Build).
## Source SDK 2013 on Linux
* Get the basic C/C++ development tools by running the following:
#### __For 32 bit users:__
```
sudo apt-get install build-essential
```
#### __For 64 bit users:__
```
sudo apt-get install build-essential gcc-multilib g++-multilib
```
* Run the following scripts to generate project files:
```
cd mp/src
./createallprojects
```
* Download, install and set up the Steam Client Runtime by running this script:
#### Make sure to replace "[USER]" by your login and "[GROUP]" by your group name
```
cd /
sudo mkdir valve
cd valve
sudo wget http://media.steampowered.com/client/runtime/steam-runtime-sdk_latest.tar.xz
sudo tar xvf steam-runtime-sdk_latest.tar.xz
sudo mv steam-runtime-sdk_2013-09-05 steam-runtime
sudo chown <USER>:<GROUP> * -R
```
* Run the ```./setup.sh``` script in the ```steam-runtime``` directory, select the ```i386``` architecture and one configuration of your choice, say ```Yes``` to everything related to updates.
* Before compiling the SDK, you have to run the sandbox (chroot environement), this is done by running the ```./shell.sh --arch=i386``` script.
* In a terminal (like always), ```cd``` into the ```mp``` (multiplayer) directory of the SDK and the ```src``` directory, just run the following command to compile:
```
make -f everything.mak
```
