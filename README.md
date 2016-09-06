# Reconnecting Xcode and Learn

From time to time, parts of the mechanism that connects tests in Xcode with the lights on Learn may break. Thankfully, it only takes a few simple steps to get Xcode and Learn to talk to one another again.

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

This will ask for your GitHub username and password, and connect your computer with Learn.

### Check that the lab is properly configured

Each lab you run in Xcode that includes tests should include a special script that calls on the `install.sh` file you just installed.