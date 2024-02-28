How to upgrade everything in PIP on Linux. I'm not sure why this is so complicated. 

[LINK](https://www.activestate.com/resources/quick-reads/how-to-update-all-python-packages/)
```shell
pip3 list -o | cut -f1 -d' ' | tr " " "\n" | awk '{if(NR>=3)print}' | cut -d' ' -f1 | xargs -n1 pip3 install -U
```


