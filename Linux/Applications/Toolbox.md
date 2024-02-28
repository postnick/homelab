the internet would prefer if we use [[Distrobox|Distrobox]] over toolbox for all and gui applications

Make a new toolbox 

toolbox create -c <name of toolbox>



to make a desktop icon you can
Enter the toolbox and copy the .desktop file from /usr/share/applications to ~/.local/share/applications. Then edit the .desktop file and change the Exec lines to prefix the start command with 'toolbox run -c <container name>'.

You may also want to copy the application icon from the toolbox to somewhere in your home as well and reference it in the local .desktop file.



copy your .desktop file from inside the toolbox /user/share/applications to ~/.local/share/applications

Then edit the .desktop file in ~/.local/share/applications and change the EXEC line to include the text  without quotes "toolbox run -c  <Container name> " before the rest. silv