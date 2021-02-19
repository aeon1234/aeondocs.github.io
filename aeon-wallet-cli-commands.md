---
title: "aeon-wallet-cli Commands"
---

# Wallet CLI Commands

## Usage

  `./aeon-wallet-cli [options] [commands]`

## Description
This is the command line Aeon wallet. It is the perfect tool to manage aeon
transfers and addresses. It needs to connect to an Aeon daemon to 
work correctly.

## Commands

---



### `account`

`account`

Shows all the existing accounts along with their balances.

---



### `account new`

`account new <label text with white spaces allowed>`

Creates a new account with its label initialized by the provided label text (which can be empty).

---



### `account switch`
`account switch <index>`

Switches to the account specified by `<index>`.
  
---


### `account label`
`account label <index> <label text with white spaces allowed>`

Sets the label of the account specified by <index> to the provided label text.
  
---


### `account tag`
`account tag <tag_name> <account_index_1> [<account_index_2> ...]`

A tag `<tag_name>` is assigned to the specified accounts `<account_index_1>`, `<account_index_2>`, ....

---


### `account untag`
`account untag <account_index_1> [<account_index_2> ...]`

The tags assigned to the specified accounts `<account_index_1>`, `<account_index_2>` ..., are removed.

---


### `account tag_description`
`account tag_description <tag_name> <description>`

The tag `<tag_name>` is assigned an arbitrary text `<description>`.


---


### `address`
`address (<index_min> [<index_max>]|all)`

  Shows the default or specified address.

---

### `address new`
`address new <label text with white spaces allowed>`

Creates a new address with the provided label text (which can be empty).

---

### `address label`
`address label <index> <label text with white spaces allowed>`

Sets the label of the address specified by `<index>` to the provided label text.

---


### `address_book`

`address_book`

Print all saved addresses in local storage.

```
>>> address_book
address_book
Index: 0
Address: WmsBWTyNwnbDwjkU1LDTNRaeYK2XNASvHFfHxxxxxxxxxS74f8q3CVwL3RigWN7WTFaFQg6k3SWUFdn2SSaZuidZ2UAyQ9yVo
Payment ID: <0000000000000000000000000000000000000000000000000000000000000000>
Description: test

Index: 1
Address: WmsBWTyNwnbDwjkU1LDTNRaeYK2XNASvHFfHxxxxxxxxxS74f8q3CVwL3RigWN7WTFaFQg6k3SWUFdn2SSaZuidZ2UAyQ9yVo
Payment ID: <0000000000000000000000000000000000000000000000000000000000000000>
Description: test
```

---

### `address_book add`

`address_book add ((<address> [pid <id>])|<integrated address>) [<description possibly with whitespaces>]`

Add an address to the local address book.

```
>>> address_book add WmsBWTyNwnbDwjkU1LDTNRaeYK2XNASvHFfHxxxxxxxxxS74f8q3CVwL3RigWN7WTFaFQg6k3SWUFdn2SSaZuidZ2UAyQ9yVo test
Index: 0
Address: WmsBWTyNwnbDwjkU1LDTNRaeYK2XNASvHFfHcYcQgVsqPS74f8q3CVwL3RigWN7WTFaFQg6k3SWUFdn2SSaZuidZ2UAyQ9yVo
Payment ID: <0000000000000000000000000000000000000000000000000000000000000000>
Description: test
```
---

### `address_book delete`
`address_book delete <index>`

Delete address at `<index>`.

```
>>>  address_book delete 1
```
---


### `balance`
`balance [detail]`

Show the wallet's balance of the currently selected account.

---


### `bc_height`

`bc_height`

Prints the connected daemon's height.

---


### `check_reserve_proof`

`check_reserve_proof <address> <signature_file> [<message>]`

Check a signature proving that the owner of `<address>` holds at least this much, optionally with a challenge string `<message>`.
  
---


### `check_spend_proof`
`check_spend_proof <txid> <signature_file> [<message>]`

Check a signature proving that the signer generated `<txid>`, optionally with a challenge string `<message>`.

---


### `check_tx_key`
`check_tx_key <txid> <txkey> <address>`

Check the amount going to `<address>` in `<txid>`.

---


### `check_tx_proof`
`check_tx_proof <txid> <address> <signature_file> [<message>]`

Check the proof for funds going to `<address>` in `<txid>` with the challenge string `<message>` if any.

```
>>> check_tx_proof txid WmsxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxVo aeon_tx_proof yes
Good signature
WmsxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxVo received 10.000000000 in txid <e2xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx>
This transaction has 359 confirmations
```

---


### `donate`
`donate [index=<N1>[,<N2>,...]] [<priority>] [<ring_size>] <amount> [<payment_id>]`

Donate `<amount>` to the development team (`donate.aeon.cash`).
  
---


### `encrypted_seed`

`encrypted_seed`

Display the encrypted Electrum-style mnemonic seed.

---


### `exchange_multisig_keys `

`exchange_multisig_keys <string> [<string>...]`

Performs extra multisig keys exchange rounds. Needed for arbitrary M/N multisig wallets. See [MultiSig Guide](https://monero.stackexchange.com/questions/5646/how-to-use-monero-multisignature-wallets-2-2-2-3).

---


### `export_key_images`

`export_key_images <file>`

Export a signed set of key images to a `<file>`.

```
>>> export_key_images key_file
Wallet password: ***************************
Signed key images exported to key_file
```

---


### `export_multisig_info `

`export_multisig_info <filename>`

Export multisig info for other participants. See [MultiSig Guide](https://monero.stackexchange.com/questions/5646/how-to-use-monero-multisignature-wallets-2-2-2-3).

---


### `export_outputs`

`export_outputs <file>`

Export the set of outputs owned by this wallet.

```
>>> export_outputs file
Wallet password: ***************************
Outputs exported to file
```

---


### `export_raw_multisig_tx `

`export_raw_multisig_tx <filename>`

Export a signed multisig transaction to a file. See [MultiSig Guide](https://monero.stackexchange.com/questions/5646/how-to-use-monero-multisignature-wallets-2-2-2-3).
  
---


### `export_transfers`

`export_transfers [in|out|all|pending|failed|coinbase] [index=<N1>[,<N2>,...]] [<min_height> [<max_height>]] [output=<filepath>]`

Export to CSV the incoming/outgoing transfers within an optional height range.

```
>>> export_transfers
CSV exported to output0.csv
```
---


### `finalize_multisig`

`finalize_multisig <string> [<string>...]`

Turn this wallet into a multisig wallet, extra step for N-1/N wallets. See [MultiSig Guide](https://monero.stackexchange.com/questions/5646/how-to-use-monero-multisignature-wallets-2-2-2-3).
  
---


### `get_description`

`get_description`

Get the description of the wallet.

```
>>> get_description
description found: My Favorite Wallet
```
---


### `get_reserve_proof `
`get_reserve_proof (all|<amount>) [<message>]`

Generate a signature proving that you own at least this much, optionally with a challenge string `<message>`.  If `all` is specified, you prove the entire sum of all of your existing accounts' balances.
Otherwise, you prove the reserve of the smallest possible amount above `<amount>` available in your current account.
  
```  
>>> get_reserve_proof 10 I-have-ten-coins
Wallet password: ****************
signature file saved to: aeon_reserve_proof
```

---


### `get_spend_proof`

`get_spend_proof <txid> [<message>]`


Generate a signature proving that you generated `<txid>` using the spend secret key, optionally with a challenge string `<message>`.


---


### `get_tx_key `
`get_tx_key <txid>`

Get the transaction private key. This can be used to prove coins have been sent but does not prove who sent the transaction. 

---


### `get_tx_note `
`get_tx_note <txid>`

Get the note attached to a transaction id.

---


### `get_tx_proof `

`get_tx_proof <txid> <address> [<message>]`

Generate a signature proving funds sent to `<address>` in `<txid>`, optionally with a challenge string `<message>`, using either the transaction secret key (when `<address>` is not your wallet's address) or the view secret key (otherwise), which does not disclose the secret key.

```
>>> get_tx_proof e2xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx WmsxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxVo yes
Wallet password: 
signature file saved to: aeon_tx_proof
```

---


### `help `

`help [<command>]`

Get documentation information.

```
>>> help get_tx_key
Command usage: 
  get_tx_key <txid>

Command description: 
  Get the transaction key (r) for a given <txid>
```

---


### `import_key_images`

`import_key_images <file>`

Import a signed key images list and verify their spent status. This could be used to verify a cold wallet balance. 

---


### `import_multisig_info`

`import_multisig_info <filename> [<filename>...]`

Import multisig info from other participants.  See [MultiSig Guide](https://monero.stackexchange.com/questions/5646/how-to-use-monero-multisignature-wallets-2-2-2-3).

---


### `import_outputs`

`import_outputs <file>`

Import a set of outputs owned by this wallet. This could be used to load transactions to an offline wallet. 


---


### `incoming_transfers`

`incoming_transfers [available|unavailable] [verbose] [index=<N1>[,<N2>[,...]]]`

Show the incoming transfers, all or filtered by availability and address index.

---


### `integrated_address`
`integrated_address [<payment_id> | <address>]`

Encode a payment ID into an integrated address for the current wallet public address (no argument uses a random payment ID), or decode an integrated address to standard address and payment ID.
  
---


### `is_output_spent`

`is_output_spent <amount>/<key_offset>`

Checks whether an output is marked as spent.

```
>>> mark_output_spent 500/2657
>>> is_output_spent 500/2657
Spent: 500/2657
>>> mark_output_unspent 500/2657
>>> is_output_spent 500/2657
Not spent: 500/2657
```
---


### `locked_sweep_all`

`locked_sweep_all [index=<N1>[,<N2>,...]] [<priority>] [<ring_size>] <address> <lockblocks> [<payment_id>]`

Send all unlocked balance to an address and lock it for `<lockblocks>` (max. 1000000). If the parameter `index<N1>[,<N2>,...]` is specified, the wallet sweeps outputs received by those address indices. `<priority>` is the priority of the sweep. The higher the priority, the higher the transaction fee. Valid values in priority order (from lowest to highest) are: unimportant, normal, elevated, priority. If omitted, the default value (see the command `set priority`) is used. `<ring_size>` is the number of inputs to include for untraceability.

---


### `locked_transfer`
`locked_transfer [index=<N1>[,<N2>,...]] [<priority>] [<ring_size>] (<URI> | <addr> <amount>) <lockblocks> [<payment_id>]`

Transfer `<amount>` to `<address>` and lock it for `<lockblocks>` (max. 1000000). If the parameter `index=<N1>[,<N2>,...]` is specified, the wallet uses outputs received by addresses of those indices. `<priority>` is the priority of the transaction. The higher the priority, the higher the transaction fee. Valid values in priority order (from lowest to highest) are: unimportant, normal, elevated, priority. If omitted, the default value (see the command `set priority`) is used. `<ring_size>` is the number of inputs to include for untraceability. Multiple payments can be made at once by adding URI_2 or `<address_2> <amount_2>` etc. (before the payment ID, if it's included).

---


### `make_multisig`
`make_multisig <threshold> <string1> [<string>...]`

  Turn this wallet into a multisig wallet. See [MultiSig Guide](https://monero.stackexchange.com/questions/5646/how-to-use-monero-multisignature-wallets-2-2-2-3).

---


### `mark_output_spent`
`mark_output_spent <amount>/<offset> | <filename> [add]`
  Mark output(s) as spent so they never get selected as fake outputs in a ring.

```
>>> mark_output_spent 500/2657
>>> is_output_spent 500/2657
Spent: 500/2657
>>> mark_output_unspent 500/2657
>>> is_output_spent 500/2657
Not spent: 500/2657
```
---


### `mark_output_unspent`
`mark_output_unspent <amount>/<offset>`

  Marks an output as unspent so it may get selected as a fake output in a ring.

```
>>> mark_output_spent 500/2657
>>> is_output_spent 500/2657
Spent: 500/2657
>>> mark_output_unspent 500/2657
>>> is_output_spent 500/2657
Not spent: 500/2657
```
---


### `password`
`password`

Change the wallet's password.

---


### `payment_id`
`payment_id`

Generate a new random full size payment id. These will be unencrypted on the blockchain, see `integrated_address` for encrypted short payment ids.
```
>>> payment_id
Random payment ID: <3b9c33d3444a1e8f489f9669f0c83cc72a6fef93c5133dfea3401d976dba32ec>
```
---


### `payments`

`payments <PID_1> [<PID_2> ... <PID_N>]`

Show the payments for the given payment IDs.

---


### `prepare_multisig`

`prepare_multisig`

  Export data needed to create a multisig wallet. See [MultiSig Guide](https://monero.stackexchange.com/questions/5646/how-to-use-monero-multisignature-wallets-2-2-2-3).

---


### `print_ring`

`print_ring <key_image> | <txid>`

Print the ring(s) used to spend a given key image or transaction (if the ring size is > 1).

---


### `refresh`

`refresh`

Synchronize with daemon. 

---


### `rescan_bc`

`rescan_bc`

Rescan the blockchain from scratch, losing any information which can not be recovered from the blockchain itself.


---


### `rescan_spent`

`rescan_spent`

Rescan the blockchain for spent outputs.

---


### `save`

`save`

Save the wallet data including key images, transaction history, etc.


---


### `save_bc`

 `save_bc`

  Save the current blockchain data.

---


### `save_known_rings`

 `save_known_rings`

  Save known rings to the shared rings database

---


### `save_watch_only`

 `save_watch_only`
 
  Save a watch-only keys file.

---


### `seed`

`seed`

  Display the Electrum-style mnemonic seed

---


### `set`

`set <option> [<value>]`

This command is used to set a variety of options in the wallet CLI.

Available options:

* `seed language` Set the wallet's seed language.
* `always-confirm-transfers <1|0>` Whether to confirm unsplit txes.
* `print-ring-members <1|0>` Whether to print detailed information about ring members during confirmation.
* `store-tx-info <1|0>` Whether to store outgoing tx info (destination address, payment ID, tx secret key) for future reference.
* `default-ring-size <n>` Set the default ring size (obsolete).
* `auto-refresh <1|0>` Whether to automatically synchronize new blocks from the daemon.
* `refresh-type <full|optimize-coinbase|no-coinbase|default>` Set the wallet's refresh behaviour.
* `priority [0|1|2|3|4]` Set the fee to default/unimportant/normal/elevated/priority.
* `confirm-missing-payment-id <1|0>`
* `ask-password <0|1|2   (or never|action|decrypt)>`
* `unit <aeon|milliaeon|microaeon|nanoaeon|picoaeon>` Set the default aeon (sub-)unit.
* `min-outputs-count [n]` Try to keep at least that many outputs of value at least min-outputs-value.
* `min-outputs-value [n]` Try to keep at least min-outputs-count outputs of at least that value.
* `merge-destinations <1|0>` Whether to merge multiple payments to the same destination address.
* `confirm-backlog <1|0>` Whether to warn if there is transaction backlog.
* `confirm-backlog-threshold [n]` Set a threshold for confirm-backlog to only warn if the transaction backlog is greater than n blocks.
* `refresh-from-block-height [n]` Set the height before which to ignore blocks.
* `auto-low-priority <1|0>` Whether to automatically use the low priority fee level when it's safe to do so.
* `segregate-pre-fork-outputs <1|0>` Set this if you intend to spend outputs on both Aeon AND a key reusing fork.
* `key-reuse-mitigation2 <1|0>` Set this if you are not sure whether you will spend on a key reusing Aeon fork later.
* `subaddress-lookahead <major>:<minor>` Set the lookahead sizes for the subaddress hash table.
* `segregation-height <n>` Set to the height of a key reusing fork you want to use, 0 to use default.
*  `ignore-outputs-above <amount>` Ignore outputs of amount above this threshold when spending. Value 0 is translated to the maximum value (18 million) which disables this filter.
*  `ignore-outputs-below <amount>` Ignore outputs of amount below this threshold when spending.

---


### `set_daemon`
`set_daemon <host>[:<port>] [trusted|untrusted]`

Set another daemon to connect to.

---


### `set_description`
`set_description [free text note]`

```
>>> set_description My Favorite Wallet
>>> get_description
description found: My Favortite Wallet
```
---


### `set_log`

`set_log <level>|{+,-,}<categories>`

Aeon source code has five log levels: 0 ERROR, 1 WARN, 2 INFO, 3 DEBUG, 4 TRACE. Each of the higher log levels contains the log levels below them. So for example

```
set_log 3
```

will display levels 0, 1, 2, and 3. To restrict the log to a specific category, you can use the following example

```
set_log net.p2p:INFO
```

This will log all ERROR, WARN, and INFO only for net.p2p. To view all net.p2p logs use `net.p2p:TRACE` as that will log all lower levels.

---


### `set_ring`
`set_ring <filename> | ( <key_image> absolute|relative <index> [<index>...] )`

Set the ring used for a given key image, so it can be reused in a fork.


---


### `set_tx_key`
`set_tx_key <txid> <tx_key>`

  Set the transaction key `r` for a given `<txid>` in case the tx was made by some other device or 3rd party wallet.

---


### `set_tx_note`
`set_tx_note <txid> [free text note]`

Set an arbitrary string note for a `<txid>`.

---


### `show_transfer`
`show_transfer <txid>`

Show information about a transfer to/from this address.


---


### `show_transfers`
`show_transfers [in|out|pending|failed|pool|coinbase] [index=<N1>[,<N2>,...]] [<min_height> [<max_height>]]`

Show the incoming/outgoing transfers within an optional height range.


---


### `sign`
`sign <file>`

  Sign the contents of a file.

---


### `sign_multisig`

`sign_multisig <filename>`

  Sign a multisig transaction from a file. See [MultiSig Guide](https://monero.stackexchange.com/questions/5646/how-to-use-monero-multisignature-wallets-2-2-2-3).

---


### `sign_transfer`

`sign_transfer [export_raw]`

Sign a transaction from a file. If the parameter "export_raw" is specified, transaction raw hex data suitable for the daemon RPC /sendrawtransaction is exported.


---


### `spendkey`
  
`spendkey`

Display the private spend key.


---


### `start_mining`

`start_mining [<number_of_threads>] [bg_mining] [ignore_battery]`

Start mining thread. 

---


### `status`

 `status`

Show synchronization status

---


### `stop_mining`

`stop_mining`

Kills mining threads.

---


### `submit_multisig`

`submit_multisig <filename>`

  Submit a signed multisig transaction from a file

---


### `submit_transfer`

`submit_transfer`

  Submit a signed transaction from a file.


---


### `sweep_all`

`sweep_all [index=<N1>[,<N2>,...]] [<priority>] [<ring_size>] <address> [<payment_id>]`

Send all unlocked balance to an address.  If the parameter `index<N1>[,<N2>,...]` is specified, the wallet sweeps outputs received by those address indices. If omitted, the wallet sweeps outputs received by all address indices.


---


### `sweep_below `

`sweep_below <amount_threshold> [index=<N1>[,<N2>,...]] [<priority>] [<ring_size>] <address> [<payment_id>]`

Send all unlocked outputs below an amount to an address. If the parameter `index<N1>[,<N2>,...]` is specified, the wallet sweeps outputs received by those address indices. If omitted, the wallet sweeps outputs received by all address indices.

---


### `sweep_single`

`sweep_single [<priority>] [<ring_size>] <key_image> <address> [<payment_id>]`

Send a single output to an address. 

---


### `sweep_unmixable`

 `sweep_unmixable`

  Send all unmixable outputs to yourself with ring_size 1

---


### `transfer`

`transfer [index=<N1>[,<N2>,...]] [<priority>] [<ring_size>] (<URI> | <address> <amount>) [<payment_id>]`


Transfer `<amount>` to `<address>`. If the parameter `index=<N1>[,<N2>,...]` is specified, the wallet uses outputs received by addresses of those indices. `<priority>` is the priority of the transaction. The higher the priority, the higher the transaction fee. Valid values in priority order (from lowest to highest) are: unimportant, normal, elevated, priority. If omitted, the default value (see the command `set priority`) is used. `<ring_size>` is the number of inputs to include for untraceability. Multiple payments can be made at once by adding URI_2 or `<address_2> <amount_2>` etc. (before the payment ID, if it's included)

---


### `unspent_outputs`

`unspent_outputs [index=<N1>[,<N2>,...]] [<min_amount> [<max_amount>]]`


Show the unspent outputs of a specified address within an optional amount range.

```
[wallet WXXXX]: unspent_outputs

Amount: 0.000000010000, number of keys: 2
124698 129240 

...

...

Amount: 2000.000000000000, number of keys: 1
129626 

Min block height: 124698
Max block height: 129240
Min amount found: 0.000000010000
Max amount found: 2000.000000000000
Total count: ###

Bin size: ....
Outputs per *: 2.9
count
  ^
  |                                   *              |
  |                                   *              |
  |                                   *              |
  |                                   *              |
  |                                   *              |
  |                                   *              |
  |                                *  *     *        |
  |       *                        *  **    *        |
  |*  *   *                        *  **    *    ** *|
  |*  *   *      *  * *      *     *  **   **  * ** *|
  +--------------------------------------------------+--> block height
   ^                                                ^
  124698                                          129240

```
---


### `verify`

`verify <filename> <address> <signature>`

  Verify a signature on the contents of a file.

---


### `version`

`version`

  Returns version information

---


### `viewkey`

`viewkey`

  Display the private view key.

---


### `wallet_info`

 `wallet_info`
 
  Show the wallet's information.

---


