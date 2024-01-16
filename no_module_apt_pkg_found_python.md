# configdat is locked

## Context

When upgrading a python version to a new one, some errors on running `apt update` and `apt upgrade` occurs. The following message is returned:

```
Traceback (most recent call last):
  File "/usr/bin/apt-listchanges", line 30, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'
```

This is caused by the absence of a expected module, "apt_pkg".

## More info

[Stack Overflow](https://stackoverflow.com/questions/13708180/python-dev-installation-error-importerror-no-module-named-apt-pkg)

## How to solve it

To solve it you will need to reinstall the python apt package and create a symbolic link to reference the "apt_pkg" module. First, execute the following:

```
sudo apt-get install python3-apt --reinstall
```

After that, create a symbolic link as the example below:

```
sudo ln -s apt_pkg.cpython-{your-version-number}-x86_64-linux-gnu.so apt_pkg.s
```
