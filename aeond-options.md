---
title: "aeond Options"
---

# aeond Options

Usage
-------------
  `./aeond [options] [commands]`

Description
-------------
These are the options for the Aeon peer-to-peer node. They will configure how the node operates.

Options
-------------

---

### `config-file` 

`config-file=<path>`

Specify a config file to load options from.

An example config file is shown below.

```
# /path/to/file/aeond.conf

daemon-address=192.168.0.1:9149
daemon-login=user:rpcpassword
trusted-daemon=1
password=walletpassword
```

Then launch wallet-cli with the following command:

```
./aeond --config-file=/path/to/file/aeond.conf
```

---


### `help`

`help`

Produce a help message with this list available options.

--- 

### `bootstrap-daemon-address`

`bootstrap-daemon-address=<ip_address>:<port>`

URL of a 'bootstrap' remote daemon that the connected wallets can use 
while this daemon is still not fully synced.  

```
./aeond --bootstrap-daemon-address=127.0.0.1:11180
```

--- 


### `bootstrap-daemon-login`

`bootstrap-daemon-login=<username>:<password>`

Specify `username:password` for the bootstrap daemon login. 

```
./aeond --bootstrap-daemon-address=127.0.0.1:11180 --bootstrap-daemon-login=someuser:theirpassword
```
---



### `data-dir`

`data-dir=<path>`

Specify data directory to store the blockchain data base information.

```
./aeond --data-dir=/path/to/some/directory
```

---



### `db-salvage`

`db-salvage[=<1|0>]`

Try to salvage a blockchain database if it seems corrupted.

---



### `db-sync-mode` 

`db-sync-mode=[safe|fast|fastest]:[sync|async]:[<blocks_per_sync>[blocks]|<bytes_per_sync>[bytes]]`

Specify sync option.

```
./aeond --db-sync-mode=fast:async:250000000bytes
```

---


### `db-type`

`db-type=<type>`

Specify database type, available: `lmdb`.


---


### `fast-block-sync`

`fsat-block-sync[=<1|0>]`

Sync up most of the way by using block hashes stored in source code.

---



### `block-sync-size`

`block-sync-size=<number_of_blocks>`

Limit how many blocks to sync at once during chain synchronization. 0 is an adaptive setting which will change dynamically. 

---


### `max-txpool-weight`

`max-txpool-weight=<number_of_bytes>`

Set maximum pending transaction pool size in bytes.

---



### `in-peers`

`in-peers=<number_of_peers>`

Set the maximum number of incoming peers connecting to your node. 

---


### `out-peers`

`out-peers=<number_of_peers>`

Set the maximum number of outgoing peers you are connecting to.

---



### `limit`

`limit=<kB/s>`

Set both the download and upload limit.

```
>>> limit
limit-down is 8192 kB/s
limit-up is 2048 kB/s
>>> limit 8192
Set limit-down to 8192 kB/s
Set limit-up to 8192 kB/s
```

---



### `limit-rate-down`

`limit-rate-down=<kB/s>`

Set the download limit.

```
>>> limit_down
limit-down is 8192 kB/s
>>> limit_down 2048
Set limit-down to 2048 kB/s
```

---



### `limit-rate-up`

`limit-rate-up=<kB/s>`

Set the upload limit.

```
>>> limit_up
limit_up is 8192 kB/s
>>> limit_up 2048
Set limit_up to 2048 kB/s
```

---



### `max-concurrency`

`max-concurrency=<number_of_cpu_threads>`

Set maximum number of CPU threads used by the daemon process for syncronizing blocks and processing transactions.

---



`prep-blocks-threads=<number_of_cpu_threads>`

### `prep-blocks-threads`

---



### `log-file`

`log-file=<path>`

The path to be used for the log file.

Default argument: `aeon-wallet-cli.log`

---


### `max-log-file-size`

`max-log-file-size=<bytes>`

Maximum log file size in bytes.

Default argument: `104850000`

---


### `max-log-files`

`max-log-files=<number>`

Maximum number of rotated log files to be saved (no limit by setting to 0).  

Default argument: `50`

---


### `log-level`

`log-level=<level|category>`

Aeon source code has five log levels: 0 ERROR, 1 WARN, 2 INFO, 3 DEBUG, 4 TRACE. Each of the higher log levels contains the log levels below them. So for example

```
--log-level=3
``` 

will display levels 0, 1, 2, and 3. To restrict the log to a specific category, you can use the following example

```
--log-level=net.p2p:INFO
```

This will log all ERROR, WARN, and INFO only for net.p2p. To view all net.p2p logs use `net.p2p:TRACE` as that will log all lower levels.

---




### `block-notify`      

`block-notify=<path>`

Run a program for each new block, '%s' will be replaced by the block hash. 

---


### `block-rate-notify`               

`block-rate-notify=<path>`

Run a program when the block rate undergoes large fluctuations. 
This might be a sign of large amounts of hash rate going on and 
off the Aeon network, and thus be of potential interest in predicting 
attacks. %t will be replaced by the number of minutes for the 
observation window, %b by the number of blocks observed within 
that window, and %e by the number of blocks that was expected 
in that window. It is suggested that this notification is used 
to automatically increase the number of confirmations required 
before a payment is acted upon. 


---


### `reorg-notify`                    

`reorg-notify=<path>`

Run a program for each reorg, '%s' will be replaced by the split height, 
'%h' will be replaced by the new blockchain height, '%n' will be replaced 
by the  number of new blocks in the new chain, and '%d' will be replaced 
by the number of blocks discarded from the old chain. 

---


### `p2p-bind-ip`

`p2p-bind-ip=<ip_address>`

Interface for p2p network protocol. 

---


### `offline`

`offline[=<1|0>]`

Do not listen for peers, nor connect to any.

---


### `p2p-bind-port` 

`p2p-bind-port=<port>`

Port for p2p network protocol. 

---



### `hide-my-port`

`hide-my-port[=<1|0>]`

Do not announce yourself as peerlist candidate.

---



### `p2p-external-port`

`p2p-external-port=<port>`

External port for p2p network protocol (if port forwarding used with NAT).   

---


### `confirm-external-bind`

`confirm-external-bind[=<1|0>]`

Confirm ip value is NOT a loopback (local) IP.

---



### `add-peer`

`add-peer=<ip_address>:<port>`

Manually add peer to local peerlist. 

---



### `add-exclusive-node`

`add-exclusive-node=<ip_address>:<port>`

Specify list of peers to connect to only. If this option is given the options 
add-priority-node and seed-node are ignored. 


---


### `peer-priority`
`peer-priority=<ip_address>:<port>`

Specify list of peers to connect to and attempt to keep the connection open.

---



### `rpc-bind-ip`

`rpc-bind-ip=<ip_address>`

Specify IP to bind RPC server.

---



### `rpc-login`

`rpc-login=<username>[:<password>]`

Specify `username[:password]` required for RPC server.

---


### `rpc-access-control-origins`

Specify a comma separated list of origins to allow cross origin resource sharing.

---



### `rpc-bind-port`

`rpc-bind-port=<port>`

Specify IP to bind RPC server.

---


### `restricted-rpc`

`restricted-rpc[=<1|0>]`

Restrict RPC to view only commands and do not return privacy sensitive data in RPC calls.

---



### `rpc-restricted-port`

`rpc-restricted-port=<port>`

Port for restricted RPC server. 

---



### `zmq-rpc-bind-ip`

`zmq-rpc-bind-ip=<ip_address>`

IP for ZMQ RPC server to listen on. 


---



### `zmq-rpc-bind-port`

`zmq-rpc-bind-port=<port>`

Port for ZMQ RPC server to listen on. 


---



### `test-dbg-lock-sleep`

`test-dbg-lock-sleep[=<1|0>]`

 Sleep time in ms, defaults to 0 (off), used to debug before/after locking mutex. Values 100 to 1000 are good for tests.


---


### `test-drop-download`

`test-drop-download[=<1|0>]`

For net tests: in download, discard ALL blocks instead checking/saving them (very fast).

---


### `test-drop-download-height`

`test-drop-download-height[=<1|0>]`

Like test-drop-download but discards only after around certain height.

---


### `fixed-difficulty`

`fixed-difficulty=<difficulty>`

Fixed difficulty used for testing. 


---



### `fluffy-blocks`

`fluffy-blocks[=<1|0>]`

Relay blocks as fluffy blocks (obsolete, now default).



---


### `no-fluffy-blocks`

`no-fluffy-blocks[=<1|0>]`

Relay blocks as normal blocks. 


---


### `allow-local-ip`

`allow-local-ip[=<1|0>]`

Allow local ip add to peer list, mostly in debug purposes.



---


### `bg-mining-enable`

`bg-mining-enable[=<1|0>]`

Enable/disable background mining.


---


### `bg-mining-ignore-battery`

`bg-mining-ignore-battery[=<1|0>]`

If true, assumes plugged in when unable to query system power status.



---


### `bg-mining-min-idle-interval`

`bg-mining-min-idle-interval=<seconds>`

Specify min lookback interval in seconds for determining idle state.


---


### `bg-mining-idle-threshold`

`bg-mining-min-idle-interval=<percentage>`

Specify minimum avg idle percentage over lookback interval.



---



### `bg-mining-miner-target`

`bg-mining-miner-target=<percentage>`

Specify maximum percentage cpu use by miner(s).


---


### `start-mining`

`start-mining=<address>`

Specify wallet address to mining for.


---



### `mining-threads`

`mining-threads=<number>`

Specify mining threads count. 


---



### `regtest`

`regtest[=<1|0>]`

Run in a regression testing mode. 


---



### `coinbase-message` 

`coinbase-message=<message>`

Specify file for extra messages to include into transactions.

---


### `detach`

`detach[=<1|0>]`

Run as background process.

---


### `enforce-dns-checkpoints`

`enforce-dns-checkpoints[=<1|0>]`

checkpoints from DNS server will be enforced.


---


### `disable-dns-checkpoints`     

`disable-dns-checkpoints[=<1|0>]`   

Do not retrieve checkpoints from DNS.



---


### `non-interactive`

`non-interactive[=<1|0>]`

Run non-interactive.



---


### `pidfile`

`pidfile=<path>`

File path to write the daemon's PID to a file. 


---


### `stagenet`

`stagenet[=<1|0>]`

Run on stagenet. The daemon must be launched with --stagenet flag.



---


### `testnet`

`testnet[=<1|0>]`

Run on testnet. The wallet must be launched with --testnet flag.



---



### `show-time-stats`

`show-time-stats[=<1|0>]`

Show time-stats when processing blocks/txs and disk synchronization.



---


### `tos-flag`

`tos-flag[=<1|0>]`

Set terms of service flag.



---



### `check-update` 

`check-update[=<1|0>]`

Check for new versions of Aeon.


---


### `no-idg`

`no-idg[=<1|0>]`

Disable UPnP port mapping. 



---


### `version`                            

`version`

Output version information.


---



### `os-version`                             

`os-version`
             
OS for which this executable was compiled.


---


