# Apple testing Workflow

------------------------------------------------------------------------------------------------------------------------------
Step by Step guide as discussed at London Apple admins https://www.youtube.com/watch?v=nK7c7u1EYqQ
I have attached two sample Json files for you to play about with

Requirements

MDS -https://twocanoes.com/products/mac/mac-deploy-stick/

HomeBrew-https://brew.sh/

Vfuse-https://github.com/chilcote/vfuse

AutoDMG-https://github.com/MagerValp/AutoDMG

Link to Slides
https://drive.google.com/file/d/1Ajvyf5EkilwYfVNa20QuXC9TI4e9GNAL/view?usp=sharing

Link to Youtube 00:00 to 12:00
https://www.youtube.com/watch?v=nK7c7u1EYqQ


------------------------------------------------------------------------------------------------------------------------------
1- 
install home-brew  /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

2- 
Run Brew Install qemu vfuse

3-
Once installed Open MDS and navigate to  Download macOS and select the OS you require
(Note here you can change the type of OS you want using the drop down)

4-
Download  Auto DMG and Drag the image you want to create
Save As: in location
(to create a resuable DMG
Drag and drop the base installer app.
Uncheck the Apply updates option.
In the AutoDMG menu, go to Window -> Advanced Options and increase the Volume Size. I personally use 100GB.
Create the DMG.

(nice note)
To Reuse the DMG
Drag and drop the resulting dmg.
Check the Apple updates option.
Add any custom pkgs you wish to install.
Create the DMG.
Guide on this is https://blog.eriknicolasgomez.com/2018/03/26/macOS-testing-tricks-reusing-base-images-and-obtaining-a-root-shell-prior-to-SetupAssistant-with-LanguageChooser/
)

5-

Option a- Open terminal and run using the format
/usr/local/vfuse/bin/vfuse -i /path/to/dmg

Example 

sudo /usr/local/bin/vfuse  -i/Users/Localtion/of image/usr/local/Cellar/qemu/4.1.1/bin/qemu-img -n "macOS10.15.1" -s C0afajf2j421 --hw-model Macmini8,1

Option b

Call Template using Vfuse -t - /location of template


Example

vfuse -t /Users/cdevice/Documents/VM/MacOS10.15_DEP.json


For examples of templates please see my Non DEP and My DEP (note the dep is linked to my zero touch workflow just replace Serialnumber with one in your org where as my Non DEP is a generic template. Also note the templates are reuseable








------------------------------------------------------------------------------------------------------------------------------
Useful links and Credits

https://kb.vmware.com/s/article/1003746

https://github.com/chilcote/vfuse

https://soundsnw.wordpress.com/?ref=spelling

https://www.modtitan.com/

https://soundsnw.wordpress.com/2019/01/23/creating-macos-mojave-vmware-images-for-testing-machines-enrolled-in-apples-device-enrollment-program/

https://scriptingosx.com/2019/10/download-a-full-install-macos-app-with-softwareupdate-in-catalina/

https://github.com/chilcote/vfuse/wiki/Templates

https://www.vmware.com/uk/products/fusion/fusion-evaluation.html

https://travellingtechguy.eu/macos-10-15-catalina-and-esxi/

