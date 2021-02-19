---
title: "aeon-wallet-rpc Options"
---

# Wallet RPC Options

Usage
-------------

`./aeon-wallet-rpc [options]`

Description
-------------
This allows one to interact with a wallet through HTTP requests. It is necessary to have a daemon running locally and to specify a wallet file to load using either `wallet-file` or `wallet-dir` along with `password`, `password-file`, or `prompt-for-password`. Additionally a port must be specified through `rpc-bind-port`.  To disable user authentication, use the option `disable-rpc-login` on launch.

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




### `daemon-address`

`daemon-address=<ip_address>:<port>`

Use aeon daemon at ip-address:port. 

```
--daemon-address=192.168.0.1:9149
```
---





### `daemon-host`

`daemon-host=<ip_address>`


Use daemon instance at specific IP address instead of localhost.

```
--daemon-host=192.168.0.1
``` 

---



### `confirm-external-bind`

`confirm-external-bind[=<1|0>]`

Confirm ip value is NOT a loopback (local) IP.

---





### `daemon-login`

`daemon-login=<username>[:<password>]`

`username:password` or `username` credentials for daemon RPC client. 

---




### `daemon-port`

`daemon-port=<port>`

Use daemon instance at specified port. 

Default argument: `11181`

---




### `trusted-daemon`

`trusted-daemon[=<1|0>]`

Enable the following commands which rely on a trusted daemon:

+ `rescan_spent`
+ `import_key_images`
+ `hw_key_images_sync`
+ `start_mining`


A local connection is trusted by default whereas a remote connection is untrusted by default.

---




### `untrusted-daemon`

`untrusted-daemon[=<1|0>]`

Disable the following commands which rely on a trusted daemon:

+ `rescan_spent`
+ `import_key_images`
+ `hw_key_images_sync`
+ `start_mining`

A local connection is trusted by default whereas a remote connection is untrusted by default.

---



### `password`

`password=<password>`

Wallet password (escape/quote as needed). 

---



### `password-file`

`password-file=<path>`

Wallet password file. 

---


### `prompt-for-password`

`prompt-for-password[=<1|0>`

Prompts for password when not provided. 


---


### `rpc-bind-ip`

`rpc-bind-ip=<ip_address>`

Specify IP to bind RPC server.

---




### `rpc-login`

`rpc-login=<username>[:<password>]`

Specify `username[:password]` required for RPC server.

---


### `disable-rpc-login`       

`disable-rpc-login[=<1|0>`

Disable HTTP authentication for RPC connections served by this process.  


---


### `rpc-access-control-origins`

`rpc-access-control-origins=<list,of,comma,separated,urls>`

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


### `wallet-dir`

`wallet-dir=<path>`

Directory for newly created wallets.


---


### `wallet-file`

`wallet-file=<path>`

Use wallet file at `path`.


---


### `generate-from-json`  

`generate-from-json=<path_to_json>`

Generate wallet from JSON format file.  



---


### `shared-ringdb-dir`

`shared-ringdb-dir=<path>`

Set shared ring database path. 


---


### `detach`

`detach[=<0|1>]`
Run as daemon. 


---



### `kdf-rounds`

`kdf-rounds=<number-of-rounds>`

Number of rounds for the key derivation function.  


---



### `max-concurrency`

`max-concurrency=<number_of_cpu_threads>`

Set maximum number of CPU threads used by the daemon process for syncronizing blocks and processing transactions.

---


### `non-interactive`

`non-interactive[=<0|1>]`

Run non-interactive


---




### `tx-notify`                 

`tx-notify=<path>`

Run a program for each new incoming transaction, '%s' will be replaced by the transaction hash. 


---


### `pidfile`

`pidfile=<path_to_file>`

File path to write the rpc's PID to (optional, requires --detach). 


---


### `stagenet`

`stagenet[=<1|0>]`

Run on stagenet. The daemon must be launched with --stagenet flag.


---



### `testnet`

`testnet[=<1|0>]`

Run on testnet. The daemon must be launched with --testnet flag.


---


### `version`                            

`version`

Output version information.
