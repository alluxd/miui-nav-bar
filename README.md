# 🏓 Table Of Contents
[Prerequisites](https://github.com/alluxd/miui-nav-bar/edit/main/README.md#-prerequisites)

[Installing Fluid Navigation Gestures](https://github.com/alluxd/miui-nav-bar/edit/main/README.md#11-fluid-navigation-gestures)

[Installing LADB](https://github.com/alluxd/miui-nav-bar/edit/main/README.md#12-ladb)

[Removing the navigation buttons](https://github.com/alluxd/miui-nav-bar/edit/main/README.md#21-removing-the-buttons)

[Removing the navigation buttons (Alternate Way)](https://github.com/alluxd/miui-nav-bar/edit/main/README.md#221-alternate-way)

[Tasker Setup](https://github.com/alluxd/miui-nav-bar/edit/main/README.md#223-tasker-setup)

[Issues (How to fix them)](https://github.com/alluxd/miui-nav-bar/edit/main/README.md#issues-and-how-to-fix)

[Credits](https://github.com/alluxd/miui-nav-bar/edit/main/README.md#credits)

# 🚀 Prerequisites
- 📱 **A phone with MIUI 12 or higher (You dont need to do this on versions <12)**
- 📁 **USB Debugging**
- 🆕 **A custom launcher, obviously...**

Assuming you have set the default launcher already, let's start...


# 🥇 First Steps
## 1. Installing Apps

### 1.1 Fluid Navigation Gestures
Download an app called "Fluid Navigation Gestures" from the Google Play Store. 
Open it and grant the permissions necessary. After that, open the Security app from your app drawer
and then go to Boost Apps. Click on the gear icon on the top right and select **Locked Apps**, here enable FNG.

Now go to Settings>Apps>Manage Apps>Background Autostart and give FNG the permission.

### 1.2 LADB 

LADB is currently paid but you can download the free builds from here. I would recommend to not download it from an unknown source unless it's Apkvision or ApkMirror...
[Click me to download](https://github.com/hyperio546/ladb-builds/releases/tag/v2.3.1)


# 🥈 The Process

After you setup FNG, you should be able to use the gestures provided by the app. But, the navigation buttons are still there and Xiaomi
does not allow you to change back to Gestures since MIUI 13. On MIUI 12 and MIUI 12.5 you could change back to Gestures without functionallity. 
This is the main reason why we installed LADB. 

### 2.1 Removing the buttons

Open LADB. You will get a notice asking you to provide a port and a pairing code.
For this, go to Settings>Developer Options>Wireless debugging and turn it on.
Click on the option saying "Pair with 6 digit code". 

You will see a dialog simillar to this:


 ![WDD](/images/wirelessdebugging.png)
 The six digit code above your IP is the pairing code and the port is the numbers after your IP.
 
 > **For example, in: 156.69.420.8:34553 <--- is your port**

 Go back to LADB, open your notification panel and enable floating windows.
 Now switch back to the Wireless debugging page and enter the info as I said above. After pairing you should see a message
 saying "Entered adb shell!". Now type in ``pm grant com.fb.fluid android.permission.WRITE_SECURE SETTINGS`` and hit enter.

 Open FNG and then go to hide navigation bar and click on 3 button navigation. And boom! Your navigation bar should be hidden... Well... Not really. On 
 some devices it does not hide the bar. But, luckily there is another method.

 ### 2.2.1 Alternate Way

If the previous way didn't quite work out... Open LADB once again and this time type:

``settings put global force_fsg_nav_bar <value>``

Before we execute the command, let's look into the values first.

> 1 is the value for Button Navigation.

> 2 is for Gesture Navigation. 


During my testing, 2 only lasted a day or so, so I tried -2 according to a reddit comment. It stayed there a lot longer and didn't go away.

Now you can either use -2, -1 or just 2. Try each value out for yourselves, we will use -2 for now:


``settings put global force_fsg_nav_bar -2``


Your buttons should now be replaced with the gesture bar. There's a catch though, it will revert on Reboot. 

What do we do now? Well, you can either type the command on each reboot which is gonna be very annoying. 

For this we're gonna use Tasker.

### 2.2.2 Tasker Installation

Install Tasker from this link: [Click me](https://drive.google.com/file/d/1NQ78QyO3kIeepoISMb_PJudaPnGy8DPa/view?usp=sharing)

The app is paid but here is the link. You can also download it yourself but be careful for fake sites.

Grant it the permissions it needs after installing it. 

Open LADB again, and type ``pm grant net.dinglisch.android.taskerm android.permission.WRITE_SECURE_SETTINGS``. This will grant the permissions it needs to 
enable gestures.

### 2.2.3 Tasker Setup

Open Tasker. Go to **Tasks** and click on the **+** icon. 

Now type in "Enable gestures" and click the check mark. Click the plus button in the new window and go to Settings>Custom Setting.

Type ``force fsg_nav_bar`` in Name and set the value to -2. Scroll down and turn on label and name it
something, preferably "Enable gestures" and then click the arrow on the top left. 

At the bottom click on the 9 squares and select **Application Icon**. Here choose an icon (it can be anything).

Once you're back in the **Task Edit** window, click the three dots on the top right and click **Add to Launcher**. If you're using Nova, click add automatically.

Open your notification panel, go to **Smart devices** and click the pencil icon on the top right. Add the enable gestures toggle in the available window by clicking the green plus icon next to it.

Now this toggle should remain in the Smart devices tab, so you can enable the gesture bar back on every reboot!

### ✅ 3. Finishing up & Troubleshooting

#### Issues (and how to fix)
1. If your gesture bar goes back (without rebooting), open FNG and go to hide navigation bar and disable it. Now use the toggle from Smart Devices to enable it back.
2. Make sure to try the other values by changing them in Tasker if your gesture bar goes away.
3. If you have any other issues, please create an issue in the repository.


#### Credits
I mainly got info from [this post](https://www.reddit.com/r/PocoPhones/comments/11vfhb8/fyi_miui_14_forces_you_to_use_poco_launcher_to/) on the r/PocoPhones subreddit. Thank you to everyone who was in the comments.

I decided to make it a tutorial since there wasn't really any proper ones on YouTube. Full credits goes to the people
in the post's comments! I can't name out everyone since some accounts were deleted.

I will try to make a video about this soon. It will be here once it is uploaded :D


Thanks for reading this, please star this repo if it helped you! =D
