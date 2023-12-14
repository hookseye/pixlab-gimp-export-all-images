### !!! I DID NOT MAKE THIS SCRIPT !!!
### This is based on a post I found on GIMP Forums. Link here: http://gimpchat.com/viewtopic.php?f=9&t=20667


# Export All Images As...

## Purpose.

Batch export all opened images in GIMP at once without the need to export them one by one,
nor the need to interact with the user interface each time an image is exported as everything
can be automated.

**Use case example** : you sliced your image from a guide’s grid of 10x10, and you have 100
new opened images (red rectangle below).

Do you want to export them as JPG or PNG one by one? That’s why this script is for, to batch
export all these opened images at once.

Or simply, like everyday, you just did work on a dozen of images at a time and want them to
be exported ASAP, this script will do the job in a matter of seconds.

**Recommendation** : This script will override existing image with the same name and
extension, even though it will auto-number each exported image to not match an existing
name, it’s better that you create a new folder for the exported images.

![default-export-image-as](https://github.com/hookseye/pixlab-gimp-export-all-images/blob/main/images/1.png)



## 1 - Where to put the script?

The location of the folder can be found in GIMP itself.

**For Linux owners and the users of the Microsoft’s Operating System:**
Go to the top menu **_Edit → Preference_** , a Window opens, then on the left side, go to →
**_Folders → Scripts_** , the location of your scripts folder is written on the right side of this panel.

**For the Apple’s macOS’ users:**
Go to the top menu **_GIMP → Preferences_** , a Window opens, then on the left side, go to →
**_Folders → Scripts_** , the location of your scripts folder is written on the right side of this panel.

Example: (I’m on Linux, thus the paths are written differently than the Microsoft’s OS)

![find-scripts-folder-in-gimp](https://github.com/hookseye/pixlab-gimp-export-all-images/blob/main/images/2.png)


Once you did put the **_pxl-export-all-images-as.scm_** in the scripts folder, you can Refresh all
scripts directly from GIMP without closing GIMP.

To do so, just go to the top menu **_Filters → Script-Fu → Refresh Scripts_**.

**Or** you can restart GIMP if you’re more comfortable with that.


## 2 - Where to find it in the menu?

In the top menu in GIMP, go to **_File → Export All Images As..._** , a window opens, here you
go...

![file-menu-export-images-as](https://github.com/hookseye/pixlab-gimp-export-all-images/blob/main/images/3.png)



## 3 - How to use Export All Images As...?

1. Chose a folder where to export all your opened images.
2. Chose the type of image you want to export (JPG, WebP, PNG, etc...)
3. Input a generic name that you want for your exported images, or you can let the default
    one.
4. Input a starting number, or you can left the default one, the script will auto increment
    the number by 1 for the next image.
    You images will have a name like: IMAGE-00001.jpg, IMAGE-00002.jpg, etc...
5. Select the way you want to interact while exporting your images ( **see below as it’s**
    **very important to understand this step** ).


## 4 - Fully automated or not?

There are 3 options that will define the way you inter-act or not during the exportations of all
your opened images.

```
(1) [1] Default (fully automated) , the one I do recommend
```
```
(2) [2] Full Control (Manual Mode) , if you want to inter-act for each image during
exportation
```
```
(3) [3] Settings From Latest Export , you do need to read my explanation below for this
one to have an understanding about what’s going on, as it can be fully auto, fully
manual, or a mixed of auto and manual mode.
```
### The first option [1] Default (fully automated)

![default-option](https://github.com/hookseye/pixlab-gimp-export-all-images/blob/main/images/4.png)


This option will use **the setting that I did “hard coded” in the script** , it’s the best balance
between good quality and low file size In My Opinion, at least those setting are the one I
usually use.

It’s fully automated, means no question asked, it will run **without you inter-acting** during the
batch exportation.

**You can check the settings in the source code and change them** , but if you are not
familiar with code, below is a screenshot for the JPG settings I did input in the code and what
it looks like from the user interface point of view:


In the red rectangle are those values and options’ settings I did hard-coded (“Not available” is
because I don’t have access to those options via the code)

![export-prompt](https://github.com/hookseye/pixlab-gimp-export-all-images/blob/main/images/5.png)



## The second option [2] Full Control (Manual Mode)

![manual-mode](https://github.com/hookseye/pixlab-gimp-export-all-images/blob/main/images/6.png)


Each time the script will export an image it will ask you to confirm the settings thru the user
interface.

Those settings are default settings from GIMP or the ones you saved as default in GIMP, they
will appear in the user interface for **each image** , thus you will have to just click OK to confirm
or you can change the settings on the fly when the dialog appear for for exporting an image.

In all case it’s way faster than going to **_File → Export..._** each time, as the export dialog will
**automatically pop-ups** each time the script will switch to the next opened image, without any
further actions from you.


## The third option [3] Settings From Latest Export per Image

![setting-from-last-export](https://github.com/hookseye/pixlab-gimp-export-all-images/blob/main/images/7.png)


This is the “tricky” option, because this option can be fully automated, fully manual or a bit of
both depending the conditions in the image history.

1. Case one: **You did not exported any image yet** , selecting this option is like selecting
    the option **_[2] Full Control (Manual Mode)_** , you will have to confirm each exportation
    on each image.
2. Case two: **You have already batch exported your images at least once** , but you
    continue to work on them, and want to export again with the very same settings you did
    your first export. **That’s the option to select** as this time the script will export each
    image with your previous settings, **even** if the previous settings were different from one
    image to another, and this process will be fully automated, no question asking, nor the
    need to confirm on a dialog.
    In this case the export will act as **_[1] Default (fully automated)_** , **but** with a twist, as it
    will use the latest settings you did use **per** image. Thus each image will be exported
    with their own latest export settings.
3. Case three: **A part of opened images** were already exported once, and a part of your
    opened images were never exported, but you want to re-export all at once as it’s
    easier, faster. Images which were already exported at least once will be fully auto with
    their latest export settings, and on the images which never were exported a dialog will
    appear to ask you to confirm or change settings for those newly exported images, thus
    you will have a mix of automated export and manual export.


## Tips and good to know:

**It replaces existing images** : Whatever mode you export your images, it won’t ask you if the
image already exist → what to do, **it will just replace it without any question!**
Thus create a new folder to be sure to not replace the original images.

**You can do animated WebP** if you export in **_[2] Full Control_** , as you will be able to select
“Animation” and other settings in the WebP dialog.
You can even use the option **_[3] Settings From Latest Export per Image_** , if you have to re-
export your animation and want the same settings than the latest export but all automated.

**BigTiff are accessible** via option **_[2] Full Control (Manual Mode)_** ,
then it’s possible to use option **_[3] Settings From Latest Export per Image_** , if you need to
batch export them again.