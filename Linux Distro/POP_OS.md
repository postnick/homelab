POP_OS is a downstream fork of [[Ubuntu]] maintained by System76 in Denver

How to Fix Cosmic so it shows all windows by default rather than having to click a button.
Install Dconf Editor (Debian)

Then Navigate to and change from False to True
```
/org/gnome/shell/extensions/dash-to-dock/default
```

Video Exapmle and Pull request:
(https://github.com/pop-os/cosmic-dock/pull/142)

This PR makes 2 changes

1.  Hides the `All Windows` drop down when an app has no open windows
2.  Adds a gsetting value to automatically open the `All Windows`. requested by [https://twitter.com/postnick/status/1522315015067480070](https://twitter.com/postnick/status/1522315015067480070)  
    Enable: `gsettings set org.gnome.shell.extensions.dash-to-dock default-windows-preview-to-open true`  
    Disable: `gsettings set org.gnome.shell.extensions.dash-to-dock default-windows-preview-to-open false`


NOTE - Dash To Dock - Non cosmic  you need to enable with these settings:
`SETTINGS_SCHEMA_DIR=$HOME/.local/share/gnome-shell/extensions/dash-to-dock@micxgx.gmail.com/schemas gsettings set org.gnome.shell.extensions.dash-to-dock default-windows-preview-to-open true`




## Apt Sucks Use Nala
https://christitus.com/stop-using-apt/


#linux #network 