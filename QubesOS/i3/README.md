# Running i3WM with XFCE4

## Installation

Install i3 and the official Qubes-specific i3 settings in dom0 from the official Qubes repositories:

`$ sudo qubes-dom0-update i3 i3-settings-qubes`

Next, we modify Xfce4 settings to replace xfwm with i3wm. 

Under Qubes Menu > Gear > System Settings > Session & Startup:

* Go to the Application Autostart tab and add an entry for i3:
  * Name: `i3wm`
  * Description: `i3 Window Manager`
  * Command: `i3`
  * Trigger: `on login`
  * [OK]
* On the Current Session tab:
  * Change the `Restart Style` column for `xfwm4` to `Never`
  * Change the `Restart Style` column for `xfdesktop` to `Never`

In Qubes Menu > Gear > System Settings > Keyboard:

* Go to the Application Shortcuts tab, highlight all shortcuts and click Remove. Just use i3's config file to manage your keyboard shortcuts from now on, to avoid the risk of a conflict.

Now you should be able to log out and log back in, and XFWM should have been replaced by i3wm, with the rest of XFCE4 still in place.

When you log in for the first time, you'll notice that the auto-generated i3 config will be set to load the i3-bar loading at the bottom of the screen in addition to the Xfce menu at the top. From dom0, you can optionally edit the config file to remove the i3-bar (personally, I don't mind having both, so I just leave it, but here's how to get rid of it):

Use $mod+Return to open a terminal in dom0

Use your favorite editor to edit the i3 config file (I'll assume it's vi, because you're a tiling window manager-loving hipster weirdo like me):

`sudo vim ~/.config/i3.config`

Comment out (add `#` to the beginning of each line) the section at the bottom that starts with `bar {` until the matching closing bracket `}`:

```
#bar {
#    position top
#
#    < etcetera... >
#
#}
```

Save and exit, then the next time you log out/back in the i3-bar should be gone. 

## ToDos:

[ ] I need to add my i3/config file to Github, along with some scripts that I wrote to make i3 work a little better with Qubes.
[ ] I need to figure out a good/secure way to get i3 and XFCE workspaces to work nicer together. 

## Issues

* The workspaces will be a little broken. They should still somewhat work in the way that they normally do, they just won't display properly in the Menu bar. There is a package i3-workspaces that is designed to fix this issue, but I don't believe it's available for dom0 update in Qubes, and I haven't had a chance to try it. You can optionally leave in i3-bar if you wish, but that's up to you. 
* You'll need to install a compositer to get a background image other than the default Qubes background. 

References:
* https://wwwtest.qubes-os.org/fr/doc/i3/
* https://www.youtube.com/watch?v=nZTBxJ_gr8w
