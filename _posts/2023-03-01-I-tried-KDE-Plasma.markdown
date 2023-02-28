---
layout: post
title:  I tried KDE Plasma
subtitle: It was... interesting to say at least
tags: [software, KDE]
comments: true
---
KDE Plasma is often regarded as one of the most customizable and powerful Desktop Environment and there's no doubt about it.
In around January, I switched my main desktop to Debian Testing along with KDE Plasma just to get a taste of how it actually feels like.
It took me a while to get this thing actually running and understand everything but well at least I've learnt a lot of stuff along the way and now we're here.

## Bugs, lots of them
I really want to put "The Goods" on the top as I think plasma is very capable, unfortunately right after the initial installation I was hit with a devastating multi-monitor bug.

![KDE Plasma 5.26.5 with no icon, no window title](/assets/img/2023-03-01/plasma-broken.jpg)

Introduced in Plasma 5.26, if you start the plasma session with 2 monitor under X11, all icons across the entire shell will disappear, window title will disappear and the context menu is oversized.
The worst part is probably the oversized context menu and it pretty much just means I can't right click anywhere.

For a long time I was pretty much stuck with single monitor as Wayland works rather "terribly" on my machine.
However when Plasma 5.27 came around Wayland seems to be much smoother, along with the new multi-monitor refactor I can now comfortably switch to Wayland and finally use my second monitor. (Also my current monitor only works well with limited RGB Range, props to KDE devs for making this easy to switch under Display Settings).

However Wayland also has its own set of issues (Window thumbnail on the panel may not always show, clipboard is a bit wonky etc), and for many Wayland may still not be a viable option, and this rather odd multi-monitor bug might just throws alot of new potential user away from Plasma or even Linux in general.

Something unrelated, but another rather "funny bug" I found is that plasmashell will [crash if a window title is too long under Wayland](https://bugs.kde.org/show_bug.cgi?id=465775).
This shouldn't be a very big problem as the limit is like 4000 characters or something, but in theory you can make a webpage with a very long &lt;title> and crash someone's plasmashell under Wayland whenever they visit your site (Please don't however). This IMO is kinda a powerful bug although I can also understand why this isn't getting prioritized.

Setting aside all the "X11 and Wayland" bugs, there are still more bugs waiting for me, mostly relating to random crashes (Even more so in Wayland, there's rarely a single day where I don't have to restart plasmashell), and it doesn't help that Dr Konqi keeps saying that the crash report is not useful, or doesn't even pop up at all.
I have used Kubuntu previously (Which runs an slightly older version of plasma), and that was way more stable than the current Plasma (As in, >= 5.26).
Sure some will say "Plasma works flawless here" but my experience unfortunately tells me otherwise, and it can get very painful especially if you're still relatively new to Linux.

Now don't get me wrong, I am not trying to bash against the developer or question the direction plasma is heading. Plasma is complex software and I appreciate those who voluntarily contributes to KDE.
I am just here documenting my experience and how one might be easily discouraged from using Plasma/Linux in general, and I sincerely hope most of them will be fixed in Plasma 6. (Although given the timeframe I don't have too much hope&lt;?>).

## UX
Another thing about plasma is that the UX can get a bit questionable. (UI is absolutely fine and consistent, even if "slightly" dated)
For example if you want to add an application to the Application Launcher (Start menu), the most average computer users would just drag the app from the panel to the Application Launcher.

Nope that doesn't work. Ok I see a "settings" icon on the top left, given how obviously placed it is surely I can add it from there right?

![KDE Application Launcher, with mouse hovered over the settings icon on top right](/assets/img/2023-03-01/plasma-start.jpg)

Nope it just configures the behavior of the Application Launcher, not the menu itself. So I tried right clicking the empty space in hopes that there will be a context menu that I can modify the menu, but nothing happens either. At this point I am really puzzled, so I gave a google search and turns out you need to right click the Application Launcher from the Panel (Taskbar), then you can click "Edit Applications".

That is just "kinda" hidden? Ideally it should be as follows:
1. Drag and Drop
2. If drag and drop can't be implemented due to technicial reasons, right clicking should bring up a way to Add/Edit applications.
3. If neither of these are feasible, instead of putting the Settings button (Where the user will most likely only configure this 1 or few times), it's probably more sensible to just replace it with an Edit Application button instead?

Bonus: I think the Menu editor (KMenuEdit) are not quite well designed either? It's just overwhelming complex with all the button laid on top in the same style.
![KMenuEdit](/assets/img/2023-03-01/kmenuedit.png)
IMO some of the button like re-arranging should be offloaded to the treeview, Environment Variable should be put into "Advanced", and a lack of tooltips doesn't help explaining to user what that option actually does.

It also requires the user to save the configuration manually (Good on paper, but in practice it's not that good with something as simple as a menu editor). There's also no indication on whether the current configuration is modified or not, so the user would have expected it to be saved automatically, and you would risk losing the new configuration when the Editor crashes, which has happended to me at least 3 times now.

Another thing that I wished Plasma does better is the handling of hidden files. (Very nitpicking I know).
In most cases I think Plasma just ignores hidden files on the front end, this can lead to confusion especially with dot-files where, for example, the user are trying to add a `.startup.sh` as an Autostart item. This would not get reflected in the Autostart Settings even when in reality it is added already, leading to confusions where "I am unable to add my script to startup and it does nothing".

This also goes for other aspects of KDE apps in general.
For example when adding an account in KMail (Yes it's not actively worked on, but given how they are shipped with the standard KDE Installation you would expect it to have better integration with Plasma than any other apps), you are greeted with this screen.

![KMail Add Account Wizard, with all info entered correctly. The "Next" button is highlighted](/assets/img/2023-03-01/kmail.png)

Clicking the "Next" option will bring you into a loading screen for a split second, then bring you back to this screen with absolutely no indication on what to do, and it turns out you need to click "Add Accounts".

Ideally, the "Add Account" button should be highlighted, and the Next button should be disabled when it can't actually do anything. Better yet, get rid of the Add Account all together and do that automatically when clicking Next.

Some options are also just rather hard to discover, for example the "Show Desktop" widget, to toggle between "Minimize all window" and "Peek at Desktop" you have to switch to an alternative widgets.
These 2 widgets have the exact same apperance but only different behaviors, given how other widgets also use the Configure Window to configure the behavior it should be the same in this widget as well.

These UX issues generally isn't a problem for existing Plasma users as they usually know the way around, and in all fairness most of them aren't located in 50 submenu so it's very straightforward once you know it, but it creates sort of a barrier for new users who are just trying Plasma out.
Sure you can Google it but the user should be able to discover these options by themselves.

With that being said, it seems that these UX issues are being worked on and newly developed KDE apps are usually pretty good, along with the [redesign of Spectacle](https://pointieststick.com/2022/12/09/this-week-in-kde-new-spectacle/), moving items to a more sensible group in System Settings it is heading towards a good direction, but there are just many of these issues across different areas, and especially with the amount of apps KDE has, it will probably take a good while for most of it to be resolved.

## The good
It is pretty much as "advertised", just an extremely customizable and adaptable (And with that also comes with a cost of well, slightly more bugs) desktop environment.
As a more traditional desktop user, KDE's default workflow works well and I don't have to tinker too much to get it right, at the same time offering some comfort features hidden piles of options. I also love KDE's Widget as they all are deeply customizable and flexible. This means I can make use of my smallish empty space on my second monitor to display informations that are relevant to me.

And of course I have to mention KRunner, sometimes you just want to just run some quick terminal command, calculations, currency conversion, dictionary and spelling lookup, KRunner can do it all out of the box.
You can also [browse more KRunner Plugins/Runners](https://store.kde.org/browse?cat=628) and see what goodies are on the shelf.
If you know a bit about python scripting/C++, you can also just make your own plugin to suits your need. (Although there's not alot of documentation).

## Overall
Plasma will remain as my primary DE on my main Desktop. It's a DE where "It works very well... when it does"
For me there's a large amount of crashes and bugs but it still is a powerful and customizable desktop environment and with the right configuration it can appeal to lots of people.

However if you are new to Linux then Plasma probably won't be my choice. You're pretty much always better off with Linux Mint + Cinnamon.
Yes they don't have Wayland, looks dated by default (But theme exists), not as customizable as KDE Plasma, but it's rock stable and are generally very good just to get your feet wet before going any further.

Or you could also stick with an older version of Plasma and hope these nasty issues don't chase after you, although they probably will go out of support soon and that's not really a viable choice.

I apologize if this post sounds just like me nitpicking KDE Plasma's weakness, but I really wanted to share on what a normal user may find fustrating, and what could be improved for a more pleasent experience. I do respect all KDE contributors and to get us to where we are today.
