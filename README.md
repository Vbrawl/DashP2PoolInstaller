# Description
This repository allows you to easily install dashcore to set up a dash node and p2pool-dash.

They can be installed by running 2 simple commands.

They can also be uninstalled, again by running 2 simple commands.

# Install dashcore and set up a node
```
./setup_node
```

After this completes, dashcore is installed.
The node now needs to synchronize.

Unfortunately, that has to be done manually.

```
cd ~/.dashcore
./dashd
```

Synchronization has started.
This process is going to take a lot of time (depending on your connection and hardware).
Advice: Leave the computer running and check every 1-2 hours the progress by performing the following steps:

```
./dash-cli getblockcount
```
The output of the command should be equal to the number of the current block in dash (https://insight.dash.org/insight/).

After synchronization is complete move on to installing p2pool.

# Install p2pool
```
./setup_p2pool
```

After this completes, p2pool is installed and you only need to start it.

to start p2pool you have to perform the following actions:

```
cd p2pool-dash
source bin/activate
python run_p2pool.py --external-ip <your public ip> -w <port for workers> -f <fee> -a <payout-address> --give-author <donation> --dashd-config-path ~/.dashcore/dash.conf
```


# Uninstall dashcore and dash node
```
chmod +x purge_node
./purge_node
```

Dashcore and node are now removed from the system.


# Uninstall p2pool-dash
```
chmod +x purge_p2pool
./purge_p2pool
```

P2Pool-dash is now removed, but some if it's dependencies are still installed.
You can choose to keep them (as they may be used by other applications)
or you can choose to remove them.

to remove them run:
```
sudo apt remove --purge python2 python2-dev gcc g++ git curl virtualenv python2-setuptools-whl python2-pip-whl
```
