# xidel
Xidel for MacOS 12+. 

A copy of `xidel-0.9.9.201903.mac.bykonings.zip`, from https://sourceforge.net/projects/videlibri/files/Xidel/Xidel%20development/

Xidel is mainly intended for older Macs and Linux/Windows.

Someone published a 0.9.9 binary that runs on MacOS 12 Monterey:

https://sourceforge.net/projects/videlibri/files/Xidel/Xidel%20development/xidel-0.9.9.201903.mac.bykonings.zip/download

Download it and run it with:

```
cd path/to/xidel/binary
./xidel\ 2 <commands>
```

To use the alias 'xidel', download the file above to wherever you
want to keep the tool, then add that path to your PATH in `.bashrc`:

`export PATH="/Path/to/folder/:$PATH"`

Then add an alias like this:

`alias xidel=xidel\ 2`
