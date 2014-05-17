This is a tool I made to aid in the process of making mods for Android phones.
I was tired of having multiple tools in different places and wanted to bring everything together with some easy shortcuts. 

This should work on any 64 bit linux distro at the moment, but I have only tested on OpenSuse 13.1 since that is what I use.

Things that are assumed:
you are running on linux 64 bit
you have adb correctly setup and in your $PATH
you have aapt and java setup and in your $PATH
you know how to make changes once you have a decompiled apk

Some general notes for now:
You must always generate a source directory from which files will be used to modify
The source directory always stays untouched, so if you want to start over you can clean your playground and begin again
If you deodex an apk or ar that does not have a .odex it will be basically the same thing as the playWith command
If you have a source dir populated from your phone decompiling will take a while to search for framework files, unless you trim your source dir down


Example usage:

#setup modStudio, only need to do once
git clone https://github.com/miked63017/modStudio.git
cd modStudio

#Need to source this file in your shell everytime you want to use modStudio
. tools/toolbox

#Basic workflow working with a stock odexed system image, must be rooted and have busybox installed
#example given for services.jar but should work with any
cleanSource
cleanPlayGround
pullSystemFromPhone
deodex services.jar
decompile services.jar
#make your changes in playground/system/framework/services.jar.out
build services.jar
odex services.jar
installFromPlayground

#Workflow from zip file, assuming already deodexed ROM
cleanSource
cleanPlayGround
pullSystemFromROM
playWith services.jar
decompile services.jar
#make your changes in playground/system/framework/services.jar.out
build services.jar
installFromPlayground