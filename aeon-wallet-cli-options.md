---
title: "aeon-wallet-cli Options"
---

# Wallet CLI Options

## Usage

  `./aeon-wallet-cli [options] [commands]`

## Description
This is the command line Aeon wallet. It is the perfect tool to manage aeon
transfers and addresses. It needs to connect to an Aeon daemon to 
work correctly.

## Options

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




### `daemon-login`

`daemon-login=<username>[:<password>]`

`username:password` or `username` credentials for daemon RPC client. 

---



### `do-not-relay`

`do-not-relay[=<1|0>]`

Newly created transactions received by this daemon will not be relayed to the Aeon network.

Default argument: `0`

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




### `allow-mismatched-daemon-version`

`allow-mismatched-daemon-version[=<1|0>]`

Allow communicating with a daemon that uses a different RPC version. 

---



### `restore-deterministic-wallet`

`restore-deterministic-wallet[=<1|0>]`

Recover wallet using mnemonic seed. 

---



### `restore-multisig-wallet`

`restore-multisig-wallet[=<1|0>]`

Recover multisig wallet using seed.

---



### `generate-new-wallet`

`generate-new-wallet=<path>`

Generate new wallet and save it to a file set by the argument. 
```
./aeon-wallet-cli --generate-new-wallet=/path/to/file/mynewwallet
```
This will create two new files: mynewwallet and mynewwallet.keys

---



### `create-address-file`

`create-address-file=<path>`

Create an address file for new wallets. 

---



### `wallet-file`

`wallet-file=<path>`

Use wallet file at path.

---



### `generate-from-json`

`generate-from-json=<path_to_json>`

Generate wallet from JSON format file with content.

```
{
  "version": 1,
  "filename": "aeonwallet",
  "scan_from_height": 1796000,
  "password": "pass",
  "seed": "some valid seed ..."
}
```
---



### `generate-from-keys`

`generate-from-keys=<path_to_new_wallet>`

Generate wallet from private keys 

---



### `electrum-seed`

`electrum-seed=<seed>`

Specify Electrum seed for wallet recovery/creation. 

---



### `generate-from-spend-key`

`generate-from-spend-key=<path_to_new_wallet>`

Generate deterministic wallet from spend key. 

---



### `generate-from-view-key`

`generate-from-view-key=<path_to_new_wallet>`

Generate incoming-only wallet from view key. 

---



### `restore-height`

`restore-height=<height>`

Restore from specific blockchain height. 

---



### `mnemonic-language`

`mnemonic-language=<language>`

Language for mnemonic.  

---



### `wallet-non-deterministic`

`wallet-non-deterministic[=<1|0>]`

Generate non-deterministic view and spend keys

---



### `generate-from-multisig-keys`

`generate-from-multisig-keys=<path_to_new_wallet>`

Generate a master wallet from multisig wallet keys.

---



### `password`

`password=<password>`

Wallet password (escape/quote as needed). 

---



### `password-file`

`password-file=<path>`

Wallet password file. 

---



### `shared-ringdb-dir`

`shared-ringdb-dir=<path>`

Set shared ring database path. 

---



### `use-english-language-names`

`use-english-language-names[=<1|0>]`

Display English language names. 

---



### `kdf-rounds`

`kdf-rounds=<number-of-rounds>`

Number of rounds for the key derivation function.  

---



### `max-concurrency`

`max-concurrency=<number_of_cpu_threads>`

Set maximum number of CPU threads used by the daemon process for syncronizing blocks and processing transactions.

---



### `tx-notify`                 

`tx-notify=<path>`

Run a program for each new incoming transaction, '%s' will be replaced by the transaction hash. 


---


### `stagenet`

`stagenet[=<1|0>]`

Run on stagenet. The daemon must be launched with --stagenet flag.


---



### `subaddress-lookahead`

`subaddress-lookahead=<num_accounts>:<num_subaddresses>`

When pair with a new wallet, creates a lookup table of `num_accounts` each with `num_subaddresses`. In total, `num_accounts * num_subaddresses` addresses.

---


### `testnet`

`testnet[=<1|0>]`

Run on testnet. The daemon must be launched with --testnet flag.

---


### `version`                            

`version`

Output version information.

---
