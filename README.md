# Reconnecting Xcode and Learn

From time to time, parts of the mechanism that connects tests in Xcode with the lights on Learn may break. Thankfully, it only takes a few simple steps to get Xcode and Learn to talk to one another again. The first section will only have to be followed one time. The second section should be followed every time thereafter your lab's tests aren't recognized on Learn.co.

### Ensure your environtment is properly configured

Copy, paste, and run the following code in your terminal. It should only have to be run once.

```
curl https://raw.githubusercontent.com/flatiron-school/dotfiles/master/.bash_profile -o ~/.bash_profile
source ~/.bash_profile
```

These two lines of code download the Flatiron School `bash_profile` to your home directory (indicated by the `~`), then reload your terminal to show the new configuration. There should now be a heart at the start of your command line, which indicates the new profile was loaded successfully.

Next, run the following line in your terminal. This, too, should only have to be run one time.

```
bash <(curl -s https://raw.githubusercontent.com/flatiron-school/ios-setup/master/install.sh)
```

This will ask for your GitHub username and password, and connect your computer with GitHub and Learn.

### Check that the lab is properly configured

Each lab you run in Xcode that includes tests should include a file called `test_runner.sh`, which captures the results of your Xcode activity log for the lab and passes those results to Flatiron. This file is called from a script that is included in your Xcode project's scheme. For some older labs, this script wasn't included and may prevent the results of your tests from being recorded on Learn.

To configure your lab to include the script, follow these steps:

* Open your Xcode project file, or if using pods, open the Xcode workspace file.
* Located at the top of Xcode (when open), to the right of the play and stop buttons, should be a button with the name of your project. In the example image below, the name of our project is LoveNotWar. If you don't see the name of your project here, click the button and a dropdown will appear that should contain your project's name. Select your project first to ensure that's the scheme with which you're working.

![theRealFirst](http://i.imgur.com/ODB44nI.png)  
-

* Next, open the dropdown menu again and this time select "Manage Schemes..." 

![first](http://i.imgur.com/kZnlEaM.png)  
-  

* You should be presented with a screen that looks something like this.

![second](http://i.imgur.com/p5HvRmx.png)  
-

* Select your project's name, which is usually the top item. In this example it's "LoveNotWar". Hit "Edit..."

![third](http://i.imgur.com/KdG8Clb.png)  
- 

* Expand the Test (Debug) section and select "Post-actions". These are actions taken after tests have been run in your project. Your screen should look like this:

![fourth](http://i.imgur.com/U2s1j38.png)  
-

* You should see a `+` symbol in the lower left of the "No Actions" window. Select the `+` symbol to be presented with two options and then select "New Run Script Action".

![fifth](http://i.imgur.com/HmyikHz.png)  
- 

* Open the drop down menu where it states "Provide build settings from" and select your project.

![sixth](http://i.imgur.com/FynWI0R.png)  
-

* Copy and paste the following lines into the text field below the drop down menu:  

```
LOG_PATH=`echo "${BUILD_DIR}" | sed "s/Build\/Products/Logs\/Test/"`
"${SRCROOT}/test_runner.sh" "$LOG_PATH" "${SRCROOT}"
```

![seventh](http://i.imgur.com/0OfusZ7.png)  

* Close the window and run the lab's tests. All the things should now work. You did it.

![congrats](https://media.giphy.com/media/daUOBsa1OztxC/giphy.gif)
