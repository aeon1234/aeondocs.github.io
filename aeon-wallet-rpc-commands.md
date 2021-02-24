---
title: "aeon-wallet-rpc Commands"
---

# Wallet RPC Commands

## Usage

`./aeon-wallet-rpc [options]`

## Description

This allows one to interact with a wallet through HTTP requests.
Every request has the following options:

```
IP=127.0.0.1
PORT=5000
METHOD="get_balance"
PARAMS="{"account_index":0,"address_indices":[0,1]}"
```

Then send the information as a request to the server in the following format:

```
curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"get_balance","params":{"account_index":0,"address_indices":[0,1]}}' -H 'Content-Type: application/json'
```

## Authentication 
When a user login is required for the RPC, it follows the HTTP digest authentication scheme specified in [IETF RFC 2617](https://tools.ietf.org/html/rfc2617#page-7).
If using `curl`, these parameters can be specified with the `-u` option as follows:

```
curl http://127.0.0.1:5000/json_rpc -u username:password --digest -d '{"jsonrpc":"2.0","id":"0","method":"get_balance","params":{"account_index":0,"address_indices":[0,1]}}' -H 'Content-Type: application/json'
```

To disable user authentication, use the option `disable-rpc-login` on launch.

## Commands


* [Wallet information](#wallet-information)

* [Addresses and Accounts](#addresses-and-accounts)

* [Transfers](#transfers)

* [Proofs and Signatures](#proofs-and-signatures)

* [Multisig](#multisig)


### Wallet information
#### `get_balance`

*  Params

```
int account_index
int[] address_indices
```

*  Response

```
int balance
int unlocked_balance
bool multisig_import_needed
Subaddress[] per_subaddress
int blocks_to_unlock
```

where `Subaddress` has the following attributes:

```
Subaddress:
  int address_index
  string address
  int balance
  int unlocked_balance
  string label
  int num_unspent_outputs
  int blocks_to_unlock
```


*  Example


```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"get_balance","params":{"account_index":0,"address_indices":[0,1]}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "balance": 1000,
    "blocks_to_unlock": 0,
    "multisig_import_needed": false,
    "per_subaddress": [{
      "address": "W..........",
      "address_index": 0,
      "balance": 500,
      "blocks_to_unlock": 0,
      "label": "Primary account",
      "num_unspent_outputs": 1,
      "unlocked_balance": 500
    },{
      "address": "X...............",
      "address_index": 1,
      "balance": 500,
      "blocks_to_unlock": 0,
      "label": "new-sub",
      "num_unspent_outputs": 1,
      "unlocked_balance": 500
    }],
    "unlocked_balance": 1000
  }
}
```

#### `get_height`

*  Params 

```
```

*  Response

```
int  height
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"get_height"}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "height": 1294237
  }
}
```

#### `start_mining`

*  Params 

```
int    threads_count
bool        do_background_mining
bool        ignore_battery
```

*  Response 

```

```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```


#### `stop_mining`
*  Params 

```
```

*  Response 

```
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```


#### `get_languages`
*  Params 

```

```

*  Response 

```
string[] languages
```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `create_wallet`

*  Params 

```
string filename
string password
string language

```

*  Response 

```
```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `open_wallet`

*  Params 

```
string filename
string password
```

*  Response 

```
```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `close_wallet`
*  Params

```
```

*  Response 

```
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```


#### `change_wallet_password`
*  Params 

```
string old_password
string new_password
```

*  Response 

```
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```


#### `generate_from_keys`
*  Params 

```
int restore_height
string filename
string address
string spendkey
string viewkey
string password
```

*  Response 

```
string address
string info
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```


#### `restore_deterministic_wallet`
*  Params 

```
int restore_height
string filename
string seed
string seed_offset
string password
string language
```

*  Response 

```
string address
string seed
string info
bool was_deprecated
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```


#### `stop_wallet`
*  Params 

```
```

*  Response 

```
```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `rescan_blockchain`
*  Params 

```
```

*  Response 

```
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `set_attribute`
*  Params 

```

string key
string value
```

*  Response 

```
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `get_attribute`

*  Params 

```
string key
```

*  Response 

```

string value
```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `make_uri`

* uri_spec

```
string address
string payment_id
int amount
string tx_description
string recipient_name
```

*  Params 

```
public uri_spec
```

*  Response 

```
string uri

```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```
#### `parse_uri`
*  Params 

```
string uri
```

*  Response 

```
uri_spec uri
string[] unknown_parameters
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `add_address_book_entry`

*  Params 

```
string address
string payment_id
string description
```

*  Response

```
int index
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `get_address_book_entry`

*  Params 

```
int[] entries
```

* entry 

```
int index
string address
string payment_id
string description
```

*  Response 

```
entry[] entries
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `delete_address_book_entry`

*  Params 

```
int index
```

*  Response 

```
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `rescan_spent`

*  Params 

```
```

*  Response 

```
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `get_version`

*  Params 

```
```

*  Response 

```
int version
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```


#### `store`

*  Params 

```
```

*  Response 

```
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"store"}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `refresh`

*  Params 

```
int start_height
```

*  Response 

```
int blocks_fetched
bool received_money
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `set_daemon`

*  Params 

```
string address
bool trusted
bool ssl
#if 0 // to be enabled when ssl support is added
string ssl_support // disabled, enabled, autodetect
string ssl_private_key_path
string ssl_certificate_path
string[] ssl_allowed_certificates
string[] ssl_allowed_fingerprints
bool ssl_allow_any_cert
#endif
#if 0 // to be enabled when ssl support is added
#endif
```

*  Response 

```
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `set_log_level`

*  Params 

```
int8_t level
```

*  Response 

```
```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `set_log_categories`

*  Params 

```
string categories
```

*  Response 

```
string categories
```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

### Addresses and Accounts

#### `get_address`
*  Params 

```
int account_index
int[] address_index
```
*  Response 

```
string address
Address[] addresses
```

where `Address` has the following attributes:

```
Address:
  string address
  string label
  int address_index
  bool used
```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"get_address","params":{"account_index":0,"address_index":[0,1]}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "address": "W.........",
    "addresses": [{
      "address": "W.........",
      "address_index": 0,
      "label": "Primary account",
      "used": true
    },{
      "address": "X.........",
      "address_index": 1,
      "label": "new-sub",
      "used": true
    }]
  }
}
```

#### `get_address_index`

*  Params 

```
string address
```

*  Response 

```
SubaddressIndex index
```

where `SubaddressIndex` has the following attributes:

```
SubaddressIndex:
  int major
  int minor
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"get_address_index","params":{"address":"X.................."}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "index": {
      "major": 0,
      "minor": 1
    }
  }
}
```

#### `get_account_tags`

*  Params 

```
```

*  Response 

```
AccountTagInfo[] account_tags
```

where `AccountTagInfo` has the following attributes:

```
string tag
string label
int[] accounts
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"get_account_tags"}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `get_accounts`

*  Params

```
string tag      // all accounts if empty, otherwise those accounts with this tag
```

*  Response 

```
int total_balance
int total_unlocked_balance
SubaddressAccount[] subaddress_accounts
```

where `SubaddressAccount` has the following attributes:

```
SubaddressAccounts:
  int account_index
  int balance
  string base_address
  string label
  string tag
  int unlocked_balance
```

*  Example

```
curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"get_accounts"}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "subaddress_accounts": [{
      "account_index": 0,
      "balance": 0,
      "base_address": "W...................................",
      "label": "Primary account",
      "tag": "",
      "unlocked_balance": 0
    },{
      "account_index": 1,
      "balance": 0,
      "base_address": "X.......................................",
      "label": "",
      "tag": "",
      "unlocked_balance": 0
    }],
    "total_balance": 0,
    "total_unlocked_balance": 0
  }
}
```

#### `create_address`

*  Params 

```
int account_index
string label
```

*  Response 

```
string   address
int      address_index
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"create_address","params":{"account_index":0,"label":"test"}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "address": "X.......................",
    "address_index": 2
  }
}
```

#### `make_integrated_address`

*  Params 

```
string standard_address
string payment_id
```

*  Response 

```
string integrated_address
string payment_id
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"make_integrated_address","params":{"standard_address":"...","payment_id":"..."}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "integrated_address":"...",
    "payment_id":"..."
  }
}
```

#### `split_integrated_address`

*  Params 

```
string integrated_address
```

*  Response 

```
string standard_address
string payment_id
bool is_subaddress
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `label_address`

*  Params 

```
SubaddressIndex index
string label
```

where `SubaddressIndex` has the following attributes:

```
SubaddressIndex:
  int major
  int minor
```

*  Response 

```

```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"label_address","params":{"index":{"major":0,"minor":2},"label":"test14314312"}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"get_address","params":{"account_index":0,"address_index":[2]}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "address": "W.............................",
    "addresses": [{
      "address": "X.................................",
      "address_index": 2,
      "label": "test14314312",
      "used": false
    }]
  }
}
```


#### `create_account`

*  Params 

```
string label
```

*  Response 

```
int account_index
string address      // the 0-th address for convenience
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"create_account"}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "account_index": 1,
    "address": "X....................."
  }
}
```

#### `label_account`

*  Params 

```
int account_index
string label
```

*  Response 

```
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"label_account","params":{"account_index":0,"label":"mywallet"}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `tag_accounts`

*  Params 

```
string tag
int[] accounts
```

*  Response 

```
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"tag_accounts","params":{"tag":"mywallet","accounts":[0]}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `untag_accounts`

*  Params 
```
int[] accounts
```

*  Response 

```
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"untag_accounts","params":{"accounts":[0]}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `set_account_tag_description`

*  Params 

```
string tag
string description
```

*  Response 

```
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"set_account_tag_description","params":{"tag":"mywallet","description":"mydescription"}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `validate_address`

*  Params

```
string address
bool any_net_type
bool allow_openalias
```

*  Response 

```
bool valid
bool integrated
bool subaddress
string nettype
string openalias_address
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

### Transfers

#### `transfer`

*  Params 

```
TransferDestination[] destinations
int account_index
int[] subaddr_indices
int priority
int mixin
int ring_size
int unlock_time
string payment_id
bool get_tx_key
bool do_not_relay
bool get_tx_hex
bool get_tx_metadata
```

where `TransferDestination` has the following attributes:

```
int amount
string address
```

`amount` is in atomic units. 

*  Response 

```
string tx_hash
string tx_key
int amount
int fee
string tx_blob
string tx_metadata
string multisig_txset
string unsigned_txset
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"transfer","params":{"destinations":[{"amount":10000,"address":"W..."}], "account_index":0, "subaddress_indices": [0], "priority":0, "mixin":0, "ring_size":0, "unlock_time":0, "payment_id":"", "get_tx_key":true, "do_not_relay":false,"get_tx_hex":true,"get_tx_metadata":true}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "amount": 10000,
    "fee": 1199990000,
    "multisig_txset": "",
    "tx_blob": "...",
    "tx_hash": "...",
    "tx_key": "...",
    "tx_metadata": "...",
    "unsigned_txset": ""
  }
}
```

#### `transfer_split`

*  Params 

```
transfer_destination[] destinations
int account_index
int[] subaddr_indices
int priority
int mixin
int ring_size
int unlock_time
string payment_id
bool get_tx_keys
bool do_not_relay
bool get_tx_hex
bool get_tx_metadata
```

`amount` is in atomic units. 

*  Response 

```
string[] tx_hash_list
string[] tx_key_list
int[] amount_list
int[] fee_list
string[] tx_blob_list
string[] tx_metadata_list
string multisig_txset
string unsigned_txset
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"transfer_split","params":{"destinations":[{"amount":10,"address":"W..."}], "account_index":0, "subaddress_indices": [0], "priority":0, "mixin":0, "ring_size":0, "unlock_time":0, "payment_id":"", "get_tx_key":true, "do_not_relay":false,"get_tx_hex":true,"get_tx_metadata":true}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "amount_list": [1,2,3,4]
    "fee_list": [1,1,1,1],
    "multisig_txset": "",
    "tx_blob_list": ["...","...","...","..."],
    "tx_hash_list": ["...","...","...","..."],
    "tx_key_list": ["...","...","...","..."],
    "tx_metadata_list": ["...","...","...","..."],
    "unsigned_txset": ""
  }
}
```

#### `sign_transfer`
*  Params 

```
string unsigned_txset
bool export_raw
```

*  Response 

```
string signed_txset
string[] tx_hash_list
string[] tx_raw_list
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"sign_transfer","params":{"unsigned_txset":"....","export_raw":true}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "signed_txset":"...",
    "tx_hash_list":["...","..."],
    "tx_raw_list":["...","..."]
  }
}
```

#### `submit_transfer`
*  Params 

```
string tx_data_hex
```

*  Response 

```
string[] tx_hash_list
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"submit_transfer","params":{"tx_data_hex":"...."}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "tx_hash_list":["...","..."]
  }
}
```

#### `sweep_dust`

*  Params 

```
bool get_tx_keys
bool do_not_relay
bool get_tx_hex
bool get_tx_metadata
```

*  Response 

```
string[] tx_hash_list
string[] tx_key_list
int[] amount_list
int[] fee_list
string[] tx_blob_list
string[] tx_metadata_list
string multisig_txset
string unsigned_txset
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"sweep_dust","params":{"get_tx_key":true, "do_not_relay":false,"get_tx_hex":true,"get_tx_metadata":true}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "amount_list": [1,2,3,4]
    "fee_list": [1,1,1,1],
    "multisig_txset": "...",
    "tx_blob_list": ["...","...","...","..."],
    "tx_hash_list": ["...","...","...","..."],
    "tx_key_list": ["...","...","...","..."],
    "tx_metadata_list": ["...","...","...","..."],
    "unsigned_txset": "..."
  }
}
```

#### `sweep_all`
*  Params 

```
string address
int account_index
int[] subaddr_indices
int priority
int mixin
int ring_size
int unlock_time
string payment_id
bool get_tx_keys
int below_amount
bool do_not_relay
bool get_tx_hex
bool get_tx_metadata
```

*  Response 

```
string[] tx_hash_list
string[] tx_key_list
int[] amount_list
int[] fee_list
string[] tx_blob_list
string[] tx_metadata_list
string multisig_txset
string unsigned_txset
```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"sweep_all","params":{"address":"W...", "account_index":0, "subaddress_indices": [0], "priority":0, "mixin":0, "ring_size":0, "unlock_time":0, "payment_id":"", "get_tx_key":true, "do_not_relay":false,"get_tx_hex":true,"get_tx_metadata":true}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "amount_list": [1,2,3,4]
    "fee_list": [1,1,1,1],
    "multisig_txset": "...",
    "tx_blob_list": ["...","...","...","..."],
    "tx_hash_list": ["...","...","...","..."],
    "tx_key_list": ["...","...","...","..."],
    "tx_metadata_list": ["...","...","...","..."],
    "unsigned_txset": "..."
  }
}
```

#### `sweep_single`

*  Params 

```
string address
int priority
int mixin
int ring_size
int unlock_time
string payment_id
bool get_tx_key
string key_image
bool do_not_relay
bool get_tx_hex
bool get_tx_metadata
```

*  Response 

```
string tx_hash
string tx_key
int amount
int fee
string tx_blob
string tx_metadata
string multisig_txset
string unsigned_txset
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"sweep_all","params":{"address":"W...", "account_index":0, "subaddress_indices": [0], "priority":0, "mixin":0, "ring_size":0, "unlock_time":0, "payment_id":"", "get_tx_key":true, "key_image":"...","do_not_relay":false,"get_tx_hex":true,"get_tx_metadata":true}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "amount": 10000,
    "fee": 1199990000,
    "multisig_txset": "",
    "tx_blob": "...",
    "tx_hash": "...",
    "tx_key": "...",
    "tx_metadata": "...",
    "unsigned_txset": ""
  }
}
```

#### `relay_tx`

*  Params 

```
string hex
```

*  Response 

```
string tx_hash
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"relay_tx","params":{"hex":"..."}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "tx_hash": "..."
  }
}
```

#### `get_payments`

*  Params
 
```
string payment_id
```

*  Response
 
```
PaymentDetails[] payments
```
where `PaymentDetails` has the following attributes:
```
string payment_id
string tx_hash
int amount
int block_height
int unlock_time
SubaddressIndex subaddr_index
string address
```
where `SubaddressIndex` has the following attributes:

```
SubaddressIndex:
  int major
  int minor
```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"get_payments","params":{"payment_id":"..."}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    [
      "payment_id": "...",
      "tx_hash": "...",
      "amount": 10000,
      "block_height": 10000,
      "unlock_time": 10000,
      "subaddr_index": {"major":0,"minor":0},
      "address": "..."
    ] ,
    [
      "payment_id": "...",
      "tx_hash": "...",
      "amount": 10000,
      "block_height": 10000,
      "unlock_time": 10000,
      "subaddr_index": {"major":0,"minor":0},
      "address": "..."
    ]
    }
}
```
#### `get_bulk_payments`

*  Params
 
```
string[] payment_ids
int min_block_height
```
*  Response
 
```
PaymentDetails[] payments
```
where `PaymentDetails` has the following attributes:
```
string payment_id
string tx_hash
int amount
int block_height
int unlock_time
SubaddressIndex subaddr_index
string address
```
where `SubaddressIndex` has the following attributes:

```
SubaddressIndex:
  int major
  int minor
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"get_bulk_payments","params":{"payment_id":["...","...","..."],"min_block_height":1500000}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    [
      "payment_id": "...",
      "tx_hash": "...",
      "amount": 10000,
      "block_height": 10000,
      "unlock_time": 10000,
      "subaddr_index": {"major":0,"minor":0},
      "address": "..."
    ] ,
    [
      "payment_id": "...",
      "tx_hash": "...",
      "amount": 10000,
      "block_height": 10000,
      "unlock_time": 10000,
      "subaddr_index": {"major":0,"minor":0},
      "address": "..."
    ]
    }
}
```
#### `incoming_transfers`

*  Params
 
```
string transfer_type
int account_index
int[] subaddr_indices

```

*  Response
 
```
TransferDetails[] transfers
```
where `TransferDetails` has the following attributes:
```
int amount
bool spent
int global_index
string tx_hash
SubaddressIndex subaddr_index
string key_image
```
where `SubaddressIndex` has the following attributes:
```
SubaddressIndex:
  int major
  int minor
```

*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"incoming_transfers","params":{"transfer_type":"...","account_index":0,"subaddr_indices:[0]}}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "transfers": [
      "amount": 100,
      "spent": false,
      "global_index": 1,
      "tx_hash": "...",
      "subaddr_index": {"major": 1, "minor":0},
      "key_image": "...",
    ] , 
    [
      "amount": 100,
      "spent": false,
      "global_index": 1,
      "tx_hash": "...",
      "subaddr_index": {"major": 1, "minor":0},
      "key_image": "...",
    ]
  }
}
```
#### `query_key`

*  Params
 
```
string key_type
```

*  Response
 
```
string key
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"query_key","params":{"key_type":"..."}]}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "key":"..."
  }
}
```
#### `set_tx_notes`

*  Params
 
```
string[] txids
string[] notes

```


*  Response
 
```
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `get_tx_notes`

*  Params
 
```
string[] txids
```

*  Response
 
```
string[] notes
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `get_transfers`

*  Params
 
```
bool in
bool out
bool pending
bool failed
bool pool

bool filter_by_height
int min_height
int max_height
int account_index
int[] subaddr_indices
```
* transfer_entry
```
string txid
string payment_id
int height
int timestamp
int amount
int fee
string note
transfer_destination[] destinations
string type
int unlock_time
cryptonote::subaddress_index subaddr_index
cryptonote::subaddress_index[] subaddr_indices
string address
bool double_spend_seen
int confirmations
int suggested_confirmations_threshold
```

*  Response
 
```
transfer_entry[] in
transfer_entry[] out
transfer_entry[] pending
transfer_entry[] failed
transfer_entry[] pool
```




*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```
#### `get_transfer_by_txid`

*  Params
 
```
string txid
int account_index
```

*  Response
 
```
transfer_entry transfer
transfer_entry[] transfers
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `export_outputs`

*  Params
 
```
```

*  Response
 
```
string outputs_data_hex
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `import_outputs`

*  Params
 
```
string outputs_data_hex
```

*  Response
 
```
int num_imported
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `export_key_images`

*  Params
 
```
```
* signed_key_image 
```
string key_image
string signature
```

*  Response
 
```
signed_key_image[] signed_key_images
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `import_key_images`
* signed_key_image 
```
string key_image
string signature
```

*  Params
 
```
signed_key_image[] signed_key_images
```

*  Response
 
```
int height
int spent
int unspent
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```
### Proofs and Signatures
#### `sign`

*  Params
 
```
string data
```

*  Response
 
```
string signature
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `verify`

*  Params
 
```
string data
string address
string signature
```

*  Response
 
```
bool good
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `get_tx_key`

*  Params
 
```
string txid
```

*  Response
 
```
string tx_key
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `check_tx_key`

*  Params
 
```
string txid
string tx_key
string address
```

*  Response
 
```
int received
bool in_pool
int confirmations
```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```


#### `get_tx_proof`

*  Params
 
```
string txid
string address
string message
```

*  Response

```
string signature
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `check_tx_proof`


*  Params
 

```
string txid
string address
string message
string signature
```


*  Response
 


```
bool good
int received
bool in_pool
int confirmations

```


*  Example



```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```
#### `get_spend_proof`

*  Params
 


```
string txid
string message
```


*  Response
 


```
string signature
```



*  Example



```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `check_spend_proof`

*  Params
 


```
string txid
string message
string signature
```


*  Response
 


```
bool good
```



*  Example



```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `get_reserve_proof`

*  Params
 


```
bool all
int account_index     // ignored when `all` is true
int amount            // ignored when `all` is true
string message
```


*  Response
 


```
string signature
```



*  Example



```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `check_reserve_proof`

*  Params
 
```
string address
string message
string signature
```

*  Response
 
```
bool good
int total
int spent
```




*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```
### Multisig
#### `is_multisig`

*  Params
 
```
```

*  Response
 
```
bool multisig
bool ready
int threshold
int total
```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```


#### `prepare_multisig`

*  Params
 
```
```

*  Response
 
```
string multisig_info
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `make_multisig`

*  Params

```
string[] multisig_info
int threshold
string password
```

*  Response
 
```
string address
string multisig_info
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `export_multisig`

*  Params
 
```
```

*  Response
 
```
string info
```




*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `import_multisig`

*  Params
 
```
string[] info
```


*  Response
 
```
int n_outputs
```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```


#### `finalize_multisig`

*  Params
 
```
string password
string[] multisig_info
```

*  Response
 
```
string address
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `exchange_multisig_keys`

*  Params
 
```
string password
string[] multisig_info
```

*  Response
 
```
string address
string multisig_info
```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `sign_multisig`

*  Params
 
```
string tx_data_hex
```

*  Response
 
```
string tx_data_hex
string[] tx_hash_list
```



*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```

#### `submit_multisig`

*  Params
 
```
string tx_data_hex
```

*  Response
 
```
string[] tx_hash_list
```


*  Example

```
>>> curl http://127.0.0.1:5000/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"","params":}' -H 'Content-Type: application/json'
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
  }
}
```


