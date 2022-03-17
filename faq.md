# FAQ

## Mac

### How to fix when Chrome's display is broken?

<img src="https://user-images.githubusercontent.com/794372/138553580-4829fdf9-ef14-42d1-821f-2486ba1f20c9.png" width=30% />

#### Answer
Restart your mac OR reset [PRAM](https://techterms.com/definition/pram#:~:text=You%20can%20reset%20or%20%22zap,you%20can%20release%20the%20keys.) OR if it still doesn't work reset [SMC](https://purplecomputing.com/tech-how-to/how-to-reset-the-smc-system-management-controller/).

### How to fix non-rendered preview icons in the file stacks of macOS's Dock?

Open `Activity Monitor`, search for the service `com.apple.quicklook.ThumbnailsAgent` and terminate it.

### What to do about the cracking sounds when spotify and the Xcode 12 Simulator is running?

???

### How to Use Apple Diagnostics to Test Your Mac?

#### Apple Silicon
- Turn on your Mac and continue to press and hold the power button as your Mac starts up.
- Release the power button when you see the startup options window (you'll see the internal disk icon and a gear icon labeled Options).
- Press the Command-D key combination on your keyboard.

#### Intel-based Mac
- Press the power button to turn on your Mac, then immediately press and hold the D key on your keyboard as your Mac starts up.
- Release the D key when you see a progress bar or you're asked to choose a language.
- After you've followed the above steps, Apple Diagnostics will begin to run on your Mac. When it's finished testing your machine, the results will be shown, including one or more reference codes to help you identify any potential issues (refer to Apple's support page to learn more about reference codes). To repeat the test, click Run the test again or press Command-R. Alternately, click Restart or Shut Down.
- To get more information about your service and support options, make sure that your Mac is connected to the internet. Then click Get started or press Command-G. Your Mac will restart and open a webpage with more information. When you're done, choose Restart or Shut Down from the Apple menu.

### What to do when Bitrise login page reloads constantly?

Delete all cookies belonging to this website. Last time I removed all but after that you have to login again everywhere.

### What if gpg says
``` 
error: gpg failed to sign the data /
fatal: failed to write commit object
```

#### Answer
If you use GPG Suite, provide git with the correct gpg tool: `git config --global gpg.program /usr/local/MacGPG2/bin/gpg2`
Alternative: run `killall gpg-agent && gpg-agent --daemon --use-standard-socket --pinentry-program /usr/local/bin/pinentry` (See [stack overflow post](https://stackoverflow.com/a/40066889/971329))

Also check the trust and expiration of your GPG key!

### Why are rolling builds turned off on Bitrise?

Because it can happen that when merging a PR and directly after starting the release that the lokalization upload (the respective build on the CI) is cancelled and the apps are built with missing translations.

### How can I have custom, per-developer scheme settings

Just copy the scheme in question and don't make it **shared**. Then it is stored in `<project_root>/<project>.xcodeproj/xcuserdata/`. Now you can add custom environment variables or launch arguments and configure the scheme as you like.

### Screenshot tests are not working anymore. What can I do? 

The second iteration (where the dark-mode screens are generated) fails on CI • Running **swift run snap...** locally works excellent

#### Answer

- Switch to fast mode temporarily
- Try [this fix](https://github.com/fastlane/fastlane/pull/19344) fastlane implemented
- Try this followup to last fix[ https://github.com/fastlane/fastlane/pull/19380](https://github.com/fastlane/fastlane/pull/19380)
- Try to call sudo **killall -10 com.apple.CoreSimulator.CoreSimulatorService** before updating the style and/or statusbar
- Try to erase content and settings before updating the style and/or statusbar
- Have a look on [this build](https://app.bitrise.io/build/93b703f3-fd45-41f4-897e-6f8f2ecf6d63#?tab=log) where I ignored the Xcodebuild errors and kill all simulators before changing appearance and status bar. Tests run incredible long but all images are generated ✅ 
- Here is another [build](https://app.bitrise.io/build/6524dc74-47bf-410a-9882-512074bbc6c6#?tab=log) which failed
- Make the CI Build fail when snap fails!!!
- Try to do the full screenshots again after Monterey is on Bitrise CI
