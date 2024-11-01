# Running i3WM with XFCE4

## Installation

Install i3 and the official Qubes-specific i3 settings in dom0 from the official Qubes repositories:

`$ sudo qubes-dom0-update i3 i3-settings-qubes`

Next, we modify Xfce4 settings to replace xfwm with i3wm. 

Under Qubes Menu > Gear > System Settings > Session & Startup

* Go to the Application Autostart tab and add an entry for i3:
  * Name: `i3wm`
  * Description: `i3 Window Manager`
  * Command: `i3`
  * Trigger: `on login`
  * [OK]
* On the Current Session tab:
  * Change the `Restart Style` column for `xfwm4` to `Never`
  * Change the `Restart Style` column for `xfdesktop` to `Never`

Now you should be able to log out and log back in, and XFWM should have been replaced by i3wm, with the rest of XFCE4 still in place.

## Issues

* The workspaces will be a little broken. They should still somewhat work in the way that they normally do, they just won't display properly in the Menu bar. There is a package i3-workspaces that is designed to fix this issue, but I don't believe it's available for dom0 update in Qubes, and I haven't had a chance to try it. You can optionally leave in i3-bar if you wish, but that's up to you. 
* You'll need to install a compositer to get a background image other than the default Qubes background. 

References:
* https://wwwtest.qubes-os.org/fr/doc/i3/
* https://www.youtube.com/watch?v=nZTBxJ_gr8w
