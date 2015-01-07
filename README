# Grive 0.3.0
13 October 2014

Command line Google Drive Sync

[http://www.lbreda.com/grive/](http://www.lbreda.com/grive/)

Grive can be considered still beta quality. It simply downloads all the files in your
Google Drive into the current directory. After you make some changes to the local files, run
grive again and it will upload your changes back to your Google Drive. New files created locally
or in Google Drive will be uploaded or downloaded respectively. Deleted files will also be "removed".
Currently Grive will NOT destroy any of your files: it will only move the files to a
directory named .trash or put them in the Google Drive trash. You can always recover them.

There are a few things that Grive does not do at the moment:

- wait for changes in file system to occur and upload. A sync is only performed when you run Grive.
- symbolic links support
- support for Google documents
  
Of course these will be added in the future, possibly the next release.

## Installation
You need the following libraries:

- json-c
- libcurl
- libstdc++
- libgcrypt
- Boost (Boost filesystem and program_option are required)
- yajl

There are also some optional dependencies:
- CppUnit (for unit tests)
- libbfd (for backtrace)
- binutils (for libiberty, required for compilation in OpenSUSE & ubuntu)

Grive uses cmake to build, see the instructions in:

http://www.lbreda.com/grive/installation

...for detailed procedures to compile Grive.

### Installing Grive on Ubuntu 14.04
Instruction on how to build and install Grive from source on Ubuntu 14.04. 
Based on [http://www.lbreda.com/grive/installation](http://www.lbreda.com/grive/installation).

Install most prerequisites from `aptitude`:

	sudo apt-get install --yes git cmake libgcrypt11-dev libjson0-dev libcurl4-openssl-dev libexpat1-dev libboost-filesystem-dev libboost-program-options-dev libboost-all-dev build-essential automake autoconf libtool pkg-config libcurl4-openssl-dev intltool libxml2-dev libgtk2.0-dev libnotify-dev libglib2.0-dev libevent-dev checkinstall

Download, compile and install `yajl` (Another prerequisite):

	git clone git://github.com/lloyd/yajl yajl
	cd yajl
	./configure
	cmake .
	make
	sudo checkinstall
	cd

Expect a confirmation with the text *Done. The new package has been installed and saved to ...*

Obtain the latest version of grive from linwizs branch:
(Alternative: `git clone git@github.com:Grive/grive.git` for the less maintained original)

	DST=~ # Change '~' to the path where you want to download and build grive
	cd $DST
	git clone git@github.com:linwiz/grive.git

Generate make file:

	cd grive
	cmake .

Expect a confirmation with the text *-- Build files have been written to: ...*.

Build the executable: 

	make

Expect a confirmation with the text *[100%] Built target grive_executable*

Create a link on PATH to the grive executable:

	sudo ln -s $DST/grive/grive/grive /usr/bin/grive

Test and verify that that the build time is correct: 

	cd
	grive -v

## Usage

When Grive is run for the first time, you should use the "-a" argument to grant
permission to Grive to access to your Google Drive. A URL should be printed.
Go to the link. You will need to login to your Google account if you haven't
done so. After granting the permission to Grive, the browser will show you
an authenication code. Copy-and-paste that to the standard input of Grive.

If everything works fine, Grive will create .grive and .grive_state files in your
current directory. It will also start downloading files from your Google Drive to
your current directory.

Enjoy!

## Version History:

Grive v0.3.1:
Merge Many forks (bug fixes and features) into linwiz/grive.
Remove useless code: bgrive and qgrive.


Grive v0.3: Bug fix & minor feature release
Fixed bugs:
	#93: missing reference count increment in one of the Json constructors
	#82: retry for HTTP error 500 & 503
	#77: Fixed a bug where grive crashed on the first run.

New features:
	#87: support for revisions
	#86: partial sync (contributed by justin at tierramedia.com)
	
