```shell
[Storage]
	path = /home/nick/share
	writable = yes
	browsable = yes
	guest okay = yes
	read only = no
	create mask = 0755 Comment: describe the share.
```

Don't forget to chown nick:nick the folder you want to share. 


Veto Not sure where this fits in. 
```shell
veto files = /._*/.DS_Store/ delete veto files = yes
```
