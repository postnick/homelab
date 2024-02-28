`find` can do that. Just add `-delete`:

```shell
find . -name ".DS_Store" -delete
```

Extend it even further to also print their relative paths

```shell
find . -name ".DS_Store" -print -delete
```

For extra caution, you can exclude directories and filter only for files

```shell
find . -name ".DS_Store" -type f -delete
```


VETO from [[Samba]]
```shell
veto files = /._*/.DS_Store/  
delete veto files = yes
```

Delete on Windows CMD Terminal
```shell
del /s /q /f /a .DS_STORE
```