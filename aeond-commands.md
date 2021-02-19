---
title: "aeond Commands"
---
 
# aeond Commands

## Usage
  `./aeond [options] [commands]`

## Description
This is the command line Aeon peer-to-peer node. 
It is a tool to manage network connections. 

## Commands

---




### `alt_chain_info`

`alt_chain_info [<block_hash>]`

Displays alternate competing blockchains and the height at which they differ.

```
>>> alt_chain_info
1 alternate chains found:
1 blocks long, from height 1264997 (5502 deep), diff 1746032035727893: 57519747c6f430928b39aaab4f68515640b219401ed3f8ce147ceadb1ce21e73
```

---



### `ban`

`ban <IP> [<seconds>]`

Ban a given IP for a given amount of seconds. Omit the seconds to ban indefinitely.

```
>>> ban 127.0.0.1
```

---



### `bans`

`bans`

Show the currently banned IPs.

---



### `bc_dyn_stats`

`bc_dyn_stats <number_of_blocks>`

Prints various network related info for the previous `<number_of_blocks>` blocks.

```
>>> bc_dyn_stats 60
Height: 1286123, diff 2948360170310179, cum. diff 227859514661806772567, target 240 sec
Last 60: avg. diff 2966851099331183, 219 avg sec/block, avg num txes 0.533333, avg. reward 2.926493333333, median block weight 255
Block versions: 60 v9
Voting for: 60 v9
```

---



### `diff`

`diff`

Prints the following mining related information at the present moment: pending block height (BH), highest confirmed block hash (TH), network difficulty (DIFF), and estimated network hashrate (HR).

```
>>> diff
BH: 1286123, TH: 5852f84187a1c3a2bb457c8335fba70ce1f608cb835431e3372f07104aef51fb, DIFF: 2948360170310179, HR: 12284834042959 H/s
```

---



### `exit`

`exit`

Stops the daemon process.

---



### `flush_txpool`

`flush_txpool [<tx_id>]`

Removes transactions from the pending transaction pool.

```
>>> flush_txpool
Pool successfully flushed
```
---



### `hard_fork_info`
`hard_fork_info`

Prints information related to hardfork version numbers and what version miners are mining on.

```
>>> hard_fork_info
version 9 enabled, 10039/10080 votes, threshold 0
current version 9, voting for version 9
```

---



### `help`

`help [<cmd>]`

Prints the various commands and their usages.

```
>>> help exit
Command usage: 
  exit

Command description: 
  Stop the daemon.
```
---



### `hide_hr`

`hide_hr`

When mining and hashrate logging is enabled, this can be used to disable the logging print out.

```
>>> hide_hr

Hash rate logging is off
```

---



### `in_peers`

`in_peers <max_number>`

Set the `<max_number>` of peers your daemon has incoming connections with.
```
>>> in_peers 50
Max number of in peers set to 50
```
---



### `is_key_image_spent`

`is_key_image_spent <key_image>`

Print whether a given key image is in the spent key images set.

```
>>> is_key_image_spent 74336412b9707f51cbb8db6b0f7b64c0b79ded67d7daad567368a37d35a5019e
<74336412b9707f51cbb8db6b0f7b64c0b79ded67d7daad567368a37d35a5019e>: spent
```
---



### `limit`

`limit [<kB/s>]`

Get or set the download and upload limit.

```
>>> limit
limit-down is 8192 kB/s
limit-up is 2048 kB/s
>>> limit 8192
Set limit-down to 8192 kB/s
Set limit-up to 8192 kB/s
```

---



### `limit_down`

`limit_down [<kB/s>]`

Get or set the download limit.

```
>>> limit_down
limit-down is 8192 kB/s
>>> limit_down 2048
Set limit-down to 2048 kB/s
```

---



### `limit_up`

`limit_up [<kB/s>]`

Get or set the upload limit.

```
>>> limit_up
limit_up is 8192 kB/s
>>> limit_up 2048
Set limit_up to 2048 kB/s
```

---



### `out_peers`


`out_peers <max_number>`

Set the `<max_number>` of peers your daemon has outgoing connections with.


```
>>> out_peers 50
Max number of out peers set to 50
```

---



### `output_histogram`

`output_histogram ([@<amount>]|[<lower_bound> [<upper_bound>]])`

Print the output histogram of transaction outputs. The first column is the frequency of the output and the second column is the amount in aeon.

```
>>> output_histogram 500000
570813  1.000000000000
807641  0.500000000000
891168  10.000000000000
>>> output_histogram @400000000000
376944  0.400000000000
```
---



### `print_bc`

`print_bc <begin_height> [<end_height>]`

Print the blockchain info in a given blocks range.

```
>>> print_bc 100 103
height: 100, timestamp: 1402081081, size: 310, weight: 310 (long term 310), transactions: 0
major version: 1, minor version: 0
block id: 6dd13aaab16679f49ee6b2b75c7dc99b1fd09ab2282b18cb4b55b73110655742, previous block id: b81ad1606a80d2e29fe2cf7b1a3dbd232614cf73f50036b0f4eee35d83eb12c9
difficulty: 2104944, nonce 2648661871, reward 17.590508402013

height: 101, timestamp: 1402081079, size: 346, weight: 346 (long term 346), transactions: 0
major version: 1, minor version: 0
block id: df3a804ec1164436f875816e6936ddb75e592bee86a9aeca46b5a144ae0a00e8, previous block id: 6dd13aaab16679f49ee6b2b75c7dc99b1fd09ab2282b18cb4b55b73110655742
difficulty: 2108005, nonce 1955249155, reward 17.590491626397

height: 102, timestamp: 1402081110, size: 347, weight: 347 (long term 347), transactions: 0
major version: 1, minor version: 0
block id: 35908ffaef2fa8b54f81778df495ab2bfecc6a346575c9eecb95b939f00ed570, previous block id: df3a804ec1164436f875816e6936ddb75e592bee86a9aeca46b5a144ae0a00e8
difficulty: 2144783, nonce 800540195, reward 17.590474850797

height: 103, timestamp: 1402081172, size: 347, weight: 347 (long term 347), transactions: 0
major version: 1, minor version: 0
block id: 62fd2e1c1c7e6a2fceba8e76f8f81178c0e5cba936bc46525af2a6d0c784f040, previous block id: 35908ffaef2fa8b54f81778df495ab2bfecc6a346575c9eecb95b939f00ed570
difficulty: 2163955, nonce 1954583209, reward 17.590458075213

```
---



### `print_block`

`print_block <block_number>`

Prints raw information about a given block.

```
>>> print_block 100
timestamp: 1402081081
previous hash: b81ad1606a80d2e29fe2cf7b1a3dbd232614cf73f50036b0f4eee35d83eb12c9
nonce: 2648661871
is orphan: 0
height: 100
depth: 1286027
hash: 6dd13aaab16679f49ee6b2b75c7dc99b1fd09ab2282b18cb4b55b73110655742
difficulty: 2104944
POW hash: 5105c0d305fa2db326330c583647762fc76e3f08c820b55a9d0921d4de050000
block size: 310
block weight: 310
long term weight: 310
num txes: 0
reward: 17.590508402013
{
  "major_version": 1, 
  "minor_version": 0, 
  "timestamp": 1402081081, 
  "prev_id": "b81ad1606a80d2e29fe2cf7b1a3dbd232614cf73f50036b0f4eee35d83eb12c9", 
  "nonce": 2648661871, 
  "miner_tx": {
    "version": 1, 
    "unlock_time": 160, 
    "vin": [ {
        "gen": {
          "height": 100
        }
      }
    ], 
    "vout": [ {
        "amount": 402013, 
        "target": {
          "key": "81ce0f45c10bce3d6ff85fc318933cbe6e456f80891ccf410b3b0c26f8abf45d"
        }
      }, {
        "amount": 8000000, 
        "target": {
          "key": "f6ba955736ec1d6a603c26fc39624ecc6814201de1e9bd76cb40237df97a9d74"
        }
      }, {
        "amount": 500000000, 
        "target": {
          "key": "18a7eeeb235fecbead4cdc47e017cbe560934c605a7b5696673bb255c5932015"
        }
      }, {
        "amount": 90000000000, 
        "target": {
          "key": "e4a881761a5a3b3aa83eabe329f97a3918fe0d3045a0af58bb260cb9677f62d6"
        }
      }, {
        "amount": 500000000000, 
        "target": {
          "key": "ba3c12abe756f9294e11170a154a15798505baeebdf4f1f1ae2240cc4140d4ce"
        }
      }, {
        "amount": 7000000000000, 
        "target": {
          "key": "4965688f9fe2d925785f9a77177a11aa15f81aa47fd2ffa443bb528161760db7"
        }
      }, {
        "amount": 10000000000000, 
        "target": {
          "key": "ddccdd7016d44335525a98729c685b9abb78ebc5f409591426b965f9a54d52b4"
        }
      }
    ], 
    "extra": [ 1, 211, 183, 59, 244, 246, 74, 155, 242, 110, 74, 9, 6, 164, 186, 214, 213, 16, 85, 232, 90, 205, 30, 158, 37, 243, 123, 55, 171, 145, 3, 33, 194
    ], 
    "signatures": [ ]
  }, 
  "tx_hashes": [ ]
}
```

---



### `print_cn`

`print_cn`

Shows peer connection information.

```
>>> print_cn
Remote Host                   Peer id             Support Flags       Recv/Sent (inactive,sec)      State                    Livetime(sec)       Down (kB/s) Down(now)     Up (kB/s) Up(now)      

OUT xxx.xxx.xxx.xxx:11180     a619756425250d4e    1                   24441(97)/1033(8)             normal                   98                  0           2             0         0            
OUT xxx.xxx.xxx.xxx:11180     82fce994b2232ba7    1                   25102(8)/1654(10)             normal                   99                  0           0             0         0            
OUT xxx.xxx.xxx.xxx:20111     574b999fa8fc68c3    1                   8702(8)/2165(8)               normal                   99                  0           0             0         0      
```

---



### `print_coinbase_tx_sum`

`print_coinbase_tx_sum <start_height> <block_count>`

Print the sum of coinbase transactions.
  
```
>>> print_coinbase_tx_sum 100 3
Sum of coinbase transactions between block heights [100, 103) is 52.771474879207 consisting of 52.771474879207 in emissions, and 0.000000000000 in fees
```

---



### `print_height`

`print_height`

Prints the total number of mined blocks.
  
```
>>> print_height
1286130
```

---



### `print_pl`

`print_pl`

Peer list historical information. Column headers are: `white/gray peer|Peer ID|IP address|elapsed time since last seen`. White peers are online and reachable and grey peers are offline. 

```
>>> print_pl
...
white      ef7e60xxxxxxx881          xxx.110.xxx.146:11180     d79.h0.m22.s20                                                                                                                                                                                                                                                
white      9eae3xxxx3b32ed4          xxx.63.xxx.22:11180        d79.h7.m38.s6                                                                                                                                                                                                                                                 
white      ad9xxxxxxfe6a73e          xxx.45.xxx.241:32404        d79.h9.m11.s29                                                                                                                                                                                                                                                
white      70da0187xxxx7656          xxx.142.xxx.104:11180       d79.h15.m37.s36                                                                                                                                                                                                                                               
gray       2ddac6xxxx8cc587          xxx.201.xxx.248:11180      d0.h0.m4.s59                                                                                                                                                                                                                                                  
gray       9125218xxxx065bd          xxx.145.xxx.4:11180         d0.h1.m36.s6                                                                                                                                                                                                                                                  
gray       e40da7xxxx21f7b1          xxx.126.xxx.94:11180        d1.h3.m40.s2                                                                                                                                                                                                                                                  
gray       d6b4738bxxxx3c7f          xxx.160.xxx.83:11180      d1.h13.m34.s25   
...
```

---



### `print_pl_stats`

`print_pl_stats`

Print peer list counts and limits.

```
>>> print_pl_stats
White list size: 235/1000 (23.5%)
Gray list size: 486/5000 (9.72%)
```

---



### `print_pool`

`print_pool`

Print the transaction pool using a long format.
```
```

---



### `print_pool_sh`

`print_pool_sh`

Print transaction pool using a short format.
```
```
---



### `print_pool_stats`

`print_pool_stats`

Print various transaction pool information.

```
>>> print_pool_stats
0 tx(es), 0 bytes total (min 0, max 0, avg 0, median 0)
fees 0.000000000000 (avg 0.000000000000 per tx, 0.000000000000 per byte)
0 double spends, 0 not relayed, 0 failing, 0 older than 10 minutes (oldest -), no backlo
```
---



### `print_status`

`print_status`

`status` for non-interactive mode.

---



### `print_tx`
`print_tx <tx_hash> [+hex] [+json]`

Find a transaction by hash and show information using `+hex` or `+json`.
```
>>> print_tx 0b3aef5340883a313522df41a6534ce05c43c62abfb8861b804727dfd89d57c6 +hex +json
Found in blockchain at height 1286136
01b4c04e01fff8bf4e058090bcfd02028bc55b44ca98800e93fc2aae1fce11cc37c8be36940d1fa2d85c3d7f03e156b8808cee891a029c4a1ed54864faf461feef6677e246de5b13a2b17aa3d34c3a477894c091569b80d88ee16f025cd087417aa17ccd4b8baead77780ed9b9132c4875480a0f012c4553ddff96418080dd9da41702116cb270c89667ee374011fb77bc0af813e9fed7e41db91c0d938a06087dff5280c0a8ca9a3a02a50b58d5ff5c87b1d87ad6d5af31b3975251b77751b4898b1c51e1ab58fc5d7634011a83442004f6ce96d32ff3129d721d9bdcc790164c3801b0285deec44f47e91e02110000000306d0ef9f000000000000000000

{
  "version": 1, 
  "unlock_time": 1286196, 
  "vin": [ {
      "gen": {
        "height": 1286136
      }
    }
  ], 
  "vout": [ {
      "amount": 800000000, 
      "target": {
        "key": "8bc55b44ca98800e93fc2aae1fce11cc37c8be36940d1fa2d85c3d7f03e156b8"
      }
    }, {
      "amount": 7000000000, 
      "target": {
        "key": "9c4a1ed54864faf461feef6677e246de5b13a2b17aa3d34c3a477894c091569b"
      }
    }, {
      "amount": 30000000000, 
      "target": {
        "key": "5cd087417aa17ccd4b8baead77780ed9b9132c4875480a0f012c4553ddff9641"
      }
    }, {
      "amount": 800000000000, 
      "target": {
        "key": "116cb270c89667ee374011fb77bc0af813e9fed7e41db91c0d938a06087dff52"
      }
    }, {
      "amount": 2000000000000, 
      "target": {
        "key": "a50b58d5ff5c87b1d87ad6d5af31b3975251b77751b4898b1c51e1ab58fc5d76"
      }
    }
  ], 
  "extra": [ 1, 26, 131, 68, 32, 4, 246, 206, 150, 211, 47, 243, 18, 157, 114, 29, 155, 220, 199, 144, 22, 76, 56, 1, 176, 40, 93, 238, 196, 79, 71, 233, 30, 2, 17, 0, 0, 0, 3, 6, 208, 239, 159, 0, 0, 0, 0, 0, 0, 0, 0, 0
  ], 
  "signatures": [ ]
}
```
---



### `relay_tx`

`relay_tx <txid>`

Relay a transaction based on its id.


---



### `save`
`save`

Save the blockchain.
```
>>> save
Blockchain saved
```
---



### `set_log`
`set_log <level>|<{+,-,}categories>`

Aeon source code has five log levels: `0 ERROR, 1 WARN, 2 INFO, 3 DEBUG, 4 TRACE`. Each of the higher log levels contains the log levels below them. So for example `set_log 3` will display levels 0, 1, 2, and 3. To restrict the log to a specific category, you can use the following example `set_log net.p2p:INFO`. This will log all ERROR, WARN, and INFO only for net.p2p. To view all net.p2p logs use `net.p2p:TRACE` as that will log all lower levels.

```
>>> set_log net.p2p:TRACE
Log categories are now net.p2p:TRACE
2020-11-29 17:08:11.624 [P2P0]  DEBUG   net.p2p contrib/epee/src/connection_basic.cpp:177      
2020-11-29 17:08:11.625 [P2P0]  INFO    net.p2p src/p2p/net_node.inl:941       
2020-11-29 17:08:11.625 [P2P0]  DEBUG   net.p2p src/p2p/net_node.inl:1140       
2020-11-29 17:08:11.625 [P2P0]  DEBUG   net.p2p src/p2p/net_node.inl:1122       
2020-11-29 17:08:11.625 [P2P0]  DEBUG   net.p2p src/p2p/net_node.inl:1137      
2020-11-29 17:08:11.625 [P2P0]  DEBUG   net.p2p src/p2p/net_node.inl:925        
2020-11-29 17:08:11.625 [P2P0]  DEBUG   net.p2p contrib/epee/src/connection_basic.cpp:169  
2020-11-29 17:08:16.626 [P2P0]  DEBUG   net.p2p contrib/epee/src/connection_basic.cpp:177   
2020-11-29 17:08:16.626 [P2P0]  INFO    net.p2p src/p2p/net_node.inl:941      
2020-11-29 17:08:16.626 [P2P0]  DEBUG   net.p2p src/p2p/net_node.inl:1140     
2020-11-29 17:08:16.626 [P2P0]  DEBUG   net.p2p src/p2p/net_node.inl:1122      
2020-11-29 17:08:16.626 [P2P0]  DEBUG   net.p2p src/p2p/net_node.inl:1137      
2020-11-29 17:08:16.626 [P2P0]  DEBUG   net.p2p src/p2p/net_node.inl:925       
2020-11-29 17:08:16.627 [P2P0]  DEBUG   net.p2p contrib/epee/src/connection_basic.cpp:169 
>>> set_log net.p2p:NONE
Log categories are now net.p2p:NONE
```
---



### `show_hr`

`show_hr`

If mining, hashrate info will begin to be printed to the console at a regular interval.

```
>>> show_hr
Hash rate logging is on
hashrate: 321685.937540986
```
---



### `start_mining`

`start_mining <addr> [<threads>]`

Spawns mining process.

```
>>> start_mining WmtFPiaD2d4gM2TbrU1vYdZABqoVzYBicGPfXfSRMY2QYWRscJPDPDy67y1oiU3CYNhXCnKwn6aDpVGuX2nqcp5D1HWr2N7mg 1
2020-11-29 15:18:26.411     7f65467fc700        WARN    miner   src/cryptonote_basic/miner.cpp:325      Mining has started with 1 threads, good luck!
2020-11-29 15:18:26.411 [miner 0]       INFO    global  src/cryptonote_basic/miner.cpp:441      Miner thread was started [0]
```
---



### `status`

`status`

Prints various network related information.

```
>>> status
Height: 1286128/1286128 (100.0%) on mainnet, not mining, net hash 12.23 TH/s, v9, 0(out)+0(in) connections, uptime 0d 0h 1m 9s
```

---



### `stop_daemon`

`stop_daemon`

Stops the daemon process.

---



### `stop_mining`

`stop_mining`

Halts the mining process.

```
>>> stop_mining
2020-11-29 15:41:12.639 [miner 0]       INFO    global  src/cryptonote_basic/miner.cpp:510      Miner thread stopped [0]
Mining stopped
```

---



### `sync_info`

`sync_info`
  
Prints network sychronization information.
  
```
>>> sync_info
Height: 1286139, target: 1286139 (100%)
Downloading at 0 kB/s
1 peers
168.119.38.182:49802      22591ed177acf57b  normal            1286139  0 kB/s, 0 blocks / 0 MB queued
0 spans, 0 MB
```
---



### `unban`

`unban <IP>`

Unban a given IP.

```
>>> unban 127.0.0.1
```

---



### `version`
`version`

Print the software version you are using.

```
>>> version
Aeon 'Chronos' (v0.14.1.0-release)
```
---
