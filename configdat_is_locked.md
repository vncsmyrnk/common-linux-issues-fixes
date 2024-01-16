# configdat is locked

## Context

Sometimes when using `sudo apt update` or `sudo apt upgrade` to run app updates, a error message "debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable" is visible. This situation is usually caused when a process is using the file mentioned.

## More info

[Stack Overflow](https://askubuntu.com/questions/136881/debconf-dbdriver-config-config-dat-is-locked-by-another-process-resource-t)

## How to solve it

To solve it you will need to stop the process holding the lock. To do so, run a script simillar to this:

```bash
#!/bin/bash

process_number=$(fuser -v /var/cache/debconf/config.dat)
kill $process_number
```
