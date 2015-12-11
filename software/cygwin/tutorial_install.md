By now Window's users are probably wishing they could have one of those wonderful Linux terminals on their home computer. Cygwin is exactly that, it's a download-able bash shell (terminal). I'm going to quickly walk you through the optimal installation and include some quick-tips.

Installation
1. Download the appropriate set-up file from: https://cygwin.com/install.html

2. Run the set-up file, click the next button, with the radio button on 'Install from Internet' click next again.

3. Select your preferred installation directory in the 'Root Directory' option. Remember where it's installed! We'll need that later. Click next.

4. The 'Local Package Directory' is just where set-up will download files it needs for installation, pick where you want it. I left it in the Downloads folder. Click next.

5. Have the radio dial selected on 'Direct Connection' and click next again.

6. The 'Available Download Sites' is just picking which server you want to download the files from. It doesn't matter too much where you download it - just speed of download. Avoid servers that are hosted overseas, because they'll take longer. I selected 'http://cygwin.mirrors.pair.com'. Click next.

7. Wait for the 'Cygwin Setup - Select Packages' menu to appear. This menu is for downloading the additional tools/software you want to have access too from Cygwin (things like emacs/vim, g++, etc.). By default Cygwin will force you to rerun this entire installation process to get more packages, but we're better than that. We're going to set-up a package manager. This will allow us to in the future download new tools with just a simple terminal command.

8. At the top of the menu there's a search box. In order to install a particular package you should type the name in the search box and the 'Category' options should reduce in the explorer below. You can expand the 'Category' by click the '+' button to see the associated packages. In this case we're going to exemplify with the package 'wget', so if you search for it you end up with four categories. One can infer which 'Category' it actually falls in, but lets assume we don't know where it is. Expand all the categories. Then in the package column you can see the full package name, we want 'wget', which we can see is under the 'Web' 'Category'. Clicking on 'Skip' will change it to the version number to install. In this example it changed to '1.16.3-1' as shown below:


9. Install the following packages: (Web) 'wget', (Base) 'tar', (Archive) 'bzip2', (Editors) 'vim', (Editors) 'emacs'. Click next. Make sure 'Select requied packages' is checked off and click next again. It will now install, this will take a bit. Click Finish when it does.

10. Run Cygwin. Yay a terminal! But we're not done yet, we want a package manager. so run the following commands:
wget rawgit.com/transcode-open/apt-cyg/master/apt-cyg
install apt-cyg /bin

11. You can now install packages using the 'apt-cyg' program, notice how the name is similar to 'apt-get' for Linux. Here's some examples that you'll probably want for 280 & 281:
apt-cyg install gcc-g++
apt-cyg install make
apt-cyg install gdb

There's tons more you can do, but this should allow you to get moving! You should now be able to compile, make, and debug a c++ program from your warm cozy Windows computer.


Quick Tips:
- Cygwin runs a local Linux structured file directory, which you can find in the installation directory of Cygwin. (i.e., "D:\cygwin64\home\USERNAME\" --> "/home/MaxSD_000")

- If you want to open a file with your system's default application run the following command (this example opens up a pdf viewer - Adobe Reader):
cygstart Project5.pdf

- If you want to access a terminal program that you have installed on your main machine but not Cygwin we can create a symbolic link to reference it (read more about this on Google). In this example we're going to get access to a LaTeX compiler. The general structure for a link is:
ln -s SOURCE TARGET
Here the source would be the file you want to link to (e.g., the path to latex.exe), and the target is the file we want to link the source to on Cygwin. It's logical to put things in your bin folder so you can instantly get universal access to the program. Full example:
ln -s 'C:\Program Files (x86)\MiKTeX 2.9\miktex\bin\x64\latex.exe'  /usr/local/bin/latex
Now we can build LaTeX pdfs as follows (in Cygwin):
pdflatex example.tex

- Searching for packages:
apt-cyg searchall SEARCHSTRING


#pin