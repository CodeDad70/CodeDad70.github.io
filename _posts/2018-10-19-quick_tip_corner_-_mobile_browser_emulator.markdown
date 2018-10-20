---
layout: post
title:      "Quick Tip Corner - Mobile Browser Emulator"
date:       2018-10-20 01:51:45 +0000
permalink:  quick_tip_corner_-_mobile_browser_emulator
---


I have been building responsive layouts for a site I'm making.  I would keep dropping into developer mode in Chrome, switching to mobile,  and use the drop down to test various mobile sizes to make sure my layouts were still working okay. 

After about the 500th time doing this I began wondering if there was an easier way. I did some googling and after wading through a bunch of sites trying to sell me apps I found a chrome extension that is free called Mobile Browser Emulator:

https://chrome.google.com/webstore/detail/mobile-browser-emulator/lbofcampnkjmiomohpbaihdcbjhbfepf?hl=en 

You bascially click on the extension from the page you are builiding, set up your computer's screen resolution, and click either mobile or tablet. It will open 4 browser windows sized to 4 popular phones. You can also resize the windows by just dragging with the mouse, it will show you the size as you drag which is very useful.  There is a bunch of information on the settings page for the extension explaining its' accuracy. 

It's not perfect. When you double click to select phone or tablet the new windows open hidden behind your main browser. I actually thought the extension wasn't working for a minute until I reaized what was going on. It also doesn't seem to be able to open phone and tablet windows at once for some reason - it's one or the other which is strange.  Updating your css file will update all four phone screens at once, but refreshing your main page will not - you need to generate them again, which is a pain.  I saw complaints of video and some functionality not working, but I haven't tested that myself. All my React components seem to function fine in the previews so I can't speak to functionality problems. 

All that being said I found this little extension really helpful for opening up four different phone aspect ratios tweaking my css file and seeing how the layout looked in all four at once. It was a real time saver and made figuring out my break points way easier. If you are working up responsive layouts I would recommend giving it a shot !

