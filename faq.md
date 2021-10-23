# FAQ

## Mac

### Q
How to fix when Chrome's display is broken?
![Screen Shot 2021-05-27 at 18 05 37](https://user-images.githubusercontent.com/794372/138553580-4829fdf9-ef14-42d1-821f-2486ba1f20c9.png)

### A
Restart your mac OR reset [PRAM](https://techterms.com/definition/pram#:~:text=You%20can%20reset%20or%20%22zap,you%20can%20release%20the%20keys.) OR if it still doesn't work reset [SMC](https://purplecomputing.com/tech-how-to/how-to-reset-the-smc-system-management-controller/).

### Q
How to fix blank icons for Download and Documents stacks in the Dock

### A
Backing up and removing `~/Library/Preferences/com.apple.dock.plist` 
Relaunching the Dock `killall -HUP Dock`

### Q
What to do about the cracking sounds when spotify and the Xcode 12 Simulator is running?

### A
???

### Q
How to Use Apple Diagnostics to Test Your Mac?

### A

#### Apple Silicon
- Turn on your Mac and continue to press and hold the power button as your Mac starts up.
- Release the power button when you see the startup options window (you'll see the internal disk icon and a gear icon labeled Options).
- Press the Command-D key combination on your keyboard.

#### Intel-based Mac
- Press the power button to turn on your Mac, then immediately press and hold the D key on your keyboard as your Mac starts up.
- Release the D key when you see a progress bar or you're asked to choose a language.
- After you've followed the above steps, Apple Diagnostics will begin to run on your Mac. When it's finished testing your machine, the results will be shown, including one or more reference codes to help you identify any potential issues (refer to Apple's support page to learn more about reference codes). To repeat the test, click Run the test again or press Command-R. Alternately, click Restart or Shut Down.
- To get more information about your service and support options, make sure that your Mac is connected to the internet. Then click Get started or press Command-G. Your Mac will restart and open a webpage with more information. When you're done, choose Restart or Shut Down from the Apple menu.

### Q
What to do when bitrise.io login page reloads constantly?

### A
Delete all cookies belonging to this website. Last time I removed all but after that you have to login again everywhere.

### Q
What if gpg says?

``` 
error: gpg failed to sign the data
fatal: failed to write commit object
```

### A
If you use GPG Suite, provide git with the correct gpg tool: `git config --global gpg.program /usr/local/MacGPG2/bin/gpg2`
Alternative: run `killall gpg-agent && gpg-agent --daemon --use-standard-socket --pinentry-program /usr/local/bin/pinentry` (https://stackoverflow.com/a/40066889/971329) 

Also check the trust and expiration of your GPG key!

