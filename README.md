# Apple_VM_Testing
Step by Step guide as discussed at London Apple admins https://www.youtube.com/watch?v=nK7c7u1EYqQ
I have attached two sample Json files for you to play about with

Requirements -DOWNLOAD AND INSTALL THE 
MDS -https://twocanoes.com/products/mac/mac-deploy-stick/
HomeBrew-https://brew.sh/
Vfuse-https://github.com/chilcote/vfuse
AutoDMG-https://github.com/MagerValp/AutoDMG
Vfuse template example-https://github.com/chilcote/vfuse/wiki/Templates
VM Fusion -https://www.vmware.com/uk/products/fusion/fusion-evaluation.html
travellingtechguy-https://travellingtechguy.eu/macos-10-15-catalina-and-esxi/
Useful links and Credits to 
VM hardware list https://kb.vmware.com/s/article/1003746 for template HW_Version
https://github.com/chilcote/vfuse
https://soundsnw.wordpress.com/?ref=spelling
https://www.modtitan.com/
https://soundsnw.wordpress.com/2019/01/23/creating-macos-mojave-vmware-images-for-testing-machines-enrolled-in-apples-device-enrollment-program/
https://scriptingosx.com/2019/10/download-a-full-install-macos-app-with-softwareupdate-in-catalina/

1- install home-brew  /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

2- Run Brew Install qemu vfuse

4-Once installed Open MDS and navigate to  Download macOS and select the OS you require
(Note here you can change the type of OS you want using the drop down)

Step 4
Download  Auto DMG and Drag the image you want to create
Save As: in location
(to create a resuable DMG
Drag and drop the base installer app.
Uncheck the Apply updates option.
In the AutoDMG menu, go to Window -> Advanced Options and increase the Volume Size. I personally use 100GB.
Create the DMG.

To Reuse the DMG
Drag and drop the resulting dmg.
Check the Apple updates option.
Add any custom pkgs you wish to install.
Create the DMG.
Guide on this is https://blog.eriknicolasgomez.com/2018/03/26/macOS-testing-tricks-reusing-base-images-and-obtaining-a-root-shell-prior-to-SetupAssistant-with-LanguageChooser/
)
Step 7: 

Step 8 option a- Open terminal and run using the format
/usr/local/vfuse/bin/vfuse -i /path/to/dmg

example 
sudo /usr/local/bin/vfuse  -i/Users/Localtion/of image/usr/local/Cellar/qemu/4.1.1/bin/qemu-img -n "macOS10.15.1" -s C0afajf2j421 --hw-model Macmini8,1

Option b
Call Template using Vfuse -t - \location of template




