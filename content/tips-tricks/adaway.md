---
title: Android without ads
---
Hey there fellow android users,
- Are you also frustrated with the number of ads you see in almost any app?
- Does skimming through a news article puts you through the misery of navigating through a plethora of banners and popup ads?
- Do you feel annoyed seeing ads in your file explorer? (Yes Xiaomi guys, I have sympathy for you)

Well, then you, my friend, have arrived at a good place where I'll help you out. Stay tuned to the end of the article to know the full story 😉
### Introducing AdAway -  It's all in the name, seriously
AdAway is an app that can literally push almost all the ads 'away' from you. Here's how to install and use it:
- Go to the official repository of AdAway, and download the `.apk` from their latest release. Here is their release page: [https://github.com/AdAway/AdAway/releases](https://github.com/AdAway/AdAway/releases)
- Install the downloaded app. You might get some warnings and stuff that this app is unsafe and all, but you can safely ignore it.
- Open the app, and follow their instructions. You'll most likely use the non root method, so go ahead with it.
- Once you're done with all the steps, you might see a 🔑 symbol on top of your notifications panel, where the wifi and the mobile network icons are present. This indicates that you've started a VPN service.
- That's it. Now go through any app in which shows you ads, and see how the ads disappear 😉 
### But there's a catch!
Do not expect ads to be blocked in subscription based apps like YouTube, Spotify, Hotstar etc. This is not a weakness of AdAway, but the way it works.
### Okay, so how does it work?
Interested for a technical look? Let's dive right in
- AdAway essentially makes use of the `hosts` file that is present in every linux based operating system. It acts as a local DNS resolver for the OS.
- The DNS resolution system has a single job - translate the domain names to the corresponding IP addresses.
- This is where AdAway comes into picture: it creates a local VPN service, which means all the internet traffic going through your phone passes through it. The VPN service can change how DNS resolution works.
- Within AdAway, there's a huge list of community-contributed ad serving domains. The AdAway VPN service does this simple job: it translates every domain to the local IP of your device, which is `127.0.0.1`. Now since you probably won't have any web server running on your phone, the request for ads never reaches the domain it was intended for.
- Hence, the request for serving ads fails, and you don't see any ads at all.
- For apps like YouTube, Spotify, Hotstar etc., their ads are served from the same domain as their content. Hence, the solution provided by AdAway won't work, as if you block the domain `youtube.com`, you won't be able to see the videos either.

Sorry iOS folks, if you're also facing the same problem, there's only one solution: switch to Android first😎 