2017-01-18

So I wanted to try git out as a version control system for code I write, either on my macbook or iMac.  

First, I download and install 'GitHub Desktop'. I already have an account.  

Then, I went to RStudio and tries to create a project and and version control (after it was created) -> No go

Then I read that you need 'git' not 'GitHub'. Go download and install that. Back to RStudio, still no 'git' under Project Options/version control.

Then I see that you need to configure git under Terminal with your username and password. Oh but that doesn't work, I get this:  
```
xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
```

Looking that up I see that maube I need xcode tools, doesn't look like I have that installed. Go to Apple and download [Command Line Tools](https://developer.apple.com/download/more/)

to be continued...
