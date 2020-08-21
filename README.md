# Stage Mac Testing with VMware Fusion #

------------------------------------------------------------------------------------------------------------------------------
These are the step-by-step guide as discussed at the London Apple Admins Conference. For reference here is the video of the conference: https://www.youtube.com/watch?v=nK7c7u1EYqQ

Also here is the link to the Slides:
https://drive.google.com/file/d/1Ajvyf5EkilwYfVNa20QuXC9TI4e9GNAL/view?usp=sharing

**Note**: I have attached two sample JSON files for you to use as examples

##Requirements:## 

    *MDS - https://twocanoes.com/products/mac/mac-deploy-stick/
    *HomeBrew - https://brew.sh/
    *Vfuse - https://github.com/chilcote/vfuse
    *AutoDMG - https://github.com/MagerValp/AutoDMG


------------------------------------------------------------------------------------------------------------------------------
*Install Homebrew with the following command  

```/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)" ```

*Run the following command after Homebrew is installed brew install gemu vfuse
*Once installed, open MDS and navigate to Download macOS and select the OS you require
    **Note:** Here you can change the type of OS you want using the dropdown
*Download  AutoDMG and drag the image you want to create
    *Save As: in location
        *To create a reusable DMG drag and drop the base installer app
        *Uncheck the Apply updates option.
    *In the AutoDMG menu go to Window, then Advanced Options and increase volume size.
        *I personally use 100GB
    *Then click Create DMG
        **Note**: To reuse the DMG, here is a nice guide on this: https://blog.eriknicolasgomez.com/2018/03/26/macOS-testing-tricks-reusing-base-images-and-obtaining-a-root-shell-prior-to-SetupAssistant-with-LanguageChooser/
*Run through one of the following options:
    *Option A: Open terminal and run the following command:
        
        ```/usr/local/vfuse/bin/vfuse -i /path/to/dmg -s real serial number - hw-model real model number```

    *Option B: Open terminal and run the following command:
        
        ```Vfuse -t - /location of template```

*Examples*:
Option A: 

```sudo /usr/local/bin/vfuse -i /Users/Localtion/of image/usr/local/Cellar/qemu/4.1.1/bin/qemu-img -n "macOS10.15.1" -s C0bfajfa2j421 --hw-model Macmini8,1```

Option B: 

```vfuse -t /Users/cdevice/Documents/VM/MacOS10.15_DEP.json```

For examples of templates please see my Non-DEP and DEP (note the dep is linked to my zero-touch workflow just replace the serial number with one in your org whereas the Non-DEP is a generic template. Also, note the templates are reusable.

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



