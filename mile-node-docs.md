# Mile Node Ducumentation 

* [Introduction](#introduction)
* [Node Setup](#node-setup)
* [Minting Premium](#minting-premium)
* [Mile Shell Commands](#mile-shell-commands)
* [Join Mile Testnet](#join-mile-testnet)
* [FAQ](#faq)

## Introduction
Basically there are two types of nodes: active and passive nodes.

### Active (Consensus) Node

Registered with 10 000—100 000 XDR node that takes part in blockchain consensus (that keeps blockchain operation on). 

Active nodes can vote for MILE/XDR rate and can receive [minting premium](#minting premium).

### Passive Node

Unregistered node. It doesn't take part in blockchain consensus, doesn't receive minting premium, it can't vote for MILE/XDR rate, but it stores the full blockchain. 

## Node Setup

To run a node your node host must comply with certain [requirements](#requirements).

To set up [active (consesus) node](#active-consensus-node) you need to go trough these steps:

1. [Download and install Mile Node And Mile Shell](#download-and-install-mile-node-and-mile-node-shell)
2. [Launch Mile Node And Mile Shell](#launch-mile-node-and-mile-shell)
3. [Register node](#node-registration) 

To set up [passive node](#passive-node) you need only steps 1—2.

**Note:** As soon as [minting premium](#minting-premium) for running an consesus node depends on the amount of blocks in the blockchain your node closed, to receive the maximum possible premium your node have to stay active and online permanently. To do so you might want to use web hosting services. 

### Requirements

* OS Supported: Linux Centos 7.x

* System:

 | Minimum | Recommended |
 |:-------:| :----------:|
 |2 GB RAM|8 GB RAM|
 |1 CPU core|8 CPU cores|
 |60GB HDD|512GB SDD|
 
* Static IP address (only for active nodes).

### Download And Install Mile Node And Mile Shell

You can install Mile Node and Mile Shell using package managers like [RPM](#RPM) or [YUM](#YUM).

To get the latest Mile Node and Mile Shell versions check [GitHub repository](https://github.com/mile-core/mile-files). 

Main-net Genesis Block is included in the package.

#### RPM 

##### Install Mile Node

Domnload and install Mile Node:

```
$ rpm -ivh https://github.com/mile-core/mile-files/blob/master/mile-<version>.x86_64.rpm?raw=true
```
Where `<version>` is the version of Mile Node.

***Example:***

```
$ rpm -ivh https://github.com/mile-core/mile-files/blob/master/mile-0.4x-56.x86_64.rpm?raw=true
```
install Mile Node ver. 0.4x-56
<br>
<br>

Check Mile Node installations:

```
$ rpm -qi mile
```
___
###### Other Options

Mile Node download only: 

```
$ wget -O mile-<version>.x86_64.rpm https://github.com/mile-core/mile-files/blob/master/mile-<version>.x86_64.rpm?raw=true
```

Install previously downloaded Mile Node:

```
$ rpm -ivh mile-<version>.x86_64.rpm
```

Update Mile Node (in case Mile Node was installed before):

```
$ rpm -Uvh https://github.com/mile-core/mile-files/blob/master/mile-<version>.x86_64.rpm?raw=true
```

**In this section** `<version>` **is the version of Mile Node** (e.g. ver. `0.4x-56`)

Unistall Mile Node:

```
$ rpm -e mile
```
##### Install Mile Shell 

Domnload and install Mile Shell:

```
$ rpm -ivh https://github.com/mile-core/mile-files/blob/master/mileshell-<version>.x86_64.rpm?raw=true
```

Where `<version>` is the version of Mile Shell.

***Example:***

```
$ rpm -ivh https://github.com/mile-core/mile-files/blob/master/mileshell-0.4x-4.x86_64.rpm?raw=true
```
will install Mile Shell ver. 0.4x-4
<br>
<br>

Check Mile Shell installations:

```
$ rpm -qi mileshell
```
___
###### Other Options

Mile Shell download only: 

```
$ wget -O mileshell-<version>.x86_64.rpm https://github.com/mile-core/mile-files/blob/master/mileshell-<version>.x86_64.rpm?raw=true
```

Install previously downloaded Mile Shell:

```
$ rpm -ivh mileshell-<version>.x86_64.rpm
```

Update Mile Shell (in case Mile Shell was installed before):

```
$ rpm -Uvh https://github.com/mile-core/mile-files/blob/master/mileshell-<version>.x86_64.rpm?raw=true
```
**In this section** `<version>` **is the version of Mile Shell** (e.g. ver. `0.4x-4`)

Unistall Mile Shell:

```
$ rpm -e mileshell
```

#### YUM

##### Add YUM Repo

```
$ vi /etc/yum.repos.d/mile.repo
```

##### Edit mile.repo file

Open mile.repo file and write the following content to the file:

```
[mile]
name=Mile Unity Foundation
gpgcheck = 0
enabled=1 
baseurl=https://repo.mile.global/mainnet/
``` 

##### Install/Update Mile Node

```
$ yum install mile
```

##### Install Mile Shell

```
$ yum install mileshell
```

### Launch Mile Node And Mile Shell

#### Launch Mile Node

Start Mile Node:

```
$ systemctl start mile
```
___
###### Other Options

Check Mile Node status:

```
$ systemctl status mile
```

Stop Mile Node:

```
$ systemctl stop mile
```

#### Launch Mile Shell  

You can either start Mile Shell on node host or on remote host.

Start Mile Shell on node host: 

```
$ shell.chaos
```

Start Mile Shell on node host:

```
$ shell.chaos -i <your.node.address>
```
___
###### Other Options

Exit from Mile Shell:

```
[chaos@mile]> exit
```

For full list of available commands see [Mile Shell Commads](#mile-shell-help).

### Node Registration 

To register node you need to lock **10 000—100 000 XDR** on your node. That is, you have to have [wallet](#create-wallet) with proper amount in XDR or [MILE](#issue-xdr-with-mile) deposited. You can buy MILE on the [open market](https://github.com/mile-core/mile-docs/wiki/faq#how-i-can-buy-mile).   

#### Create Wallet
You can create new wallet or add your existing wallet to database.

##### Create New Wallet

```
[chaos@mile]> create local wallet <wallet_name> [password <password>]
```
Where:<br>
`<wallet_name>` – wallet name you want to set<br>
`<password>` – wallet password you want to set (password is optional, but it is highly recommended)<br>

This command will generate private and public keys and create a new wallet with them. File wallet_name.wallet will be created in the current directory.

Output:

```
Private Key: "xxxxxxxxxxxxxxx"
Public Key : "xxx"
```

##### Add Existing Wallet

If you already have a wallet:

```
create local wallet from keys <wallet_name> public key <public_key> private key <private_key> [password <password>]
```
Where:<br>
`<wallet_name>` – wallet name you want to set<br>
`<public_key>` – public key of your existing wallet<br>
`<private_key>` – private key of your existing wallet<br>
`<password>` – wallet password you want to set (password is optional, but it is highly recommended)<br>

This command will create a new wallet from your existing public and private keys. File wallet_name.wallet will be created in the current directory.

##### Check Wallet State

To check your wallet state in Mile Shell use one of two commands:

* Get local wallet state command

 ```
[chaos@mile]> get local wallet state <wallet-name>
``` 
Where:<br>
`<wallet_name>` – your wallet name

* Get local wallet state command

 ```
[chaos@mile]> get wallet state key <public_key>
``` 
Where:<br>
`<public_key>` – public key of your wallet

Output:

```
Wallet                  : "<your wallet name>" or "<your wallet public key>" 
xdr                     : "<your wallet XDR balance>"
Freeze XDR              : "<amount of XDR locked for node registration>"
mile                    : "<your wallet MILE balance>"
Freeze MILE             : "<amount of MILE locked XDR emission>"
Tags                    : "Node"
Node address            : "your node IP address"
Last transaction id     : "xxxxxxx"
Is transactions exist   : "yes"

``` 
`Freeze XDR`, `Tags`, `Node address` – appear only if you have a registered node.<br>
`Freeze MILE` - appear only if you made emission transaction to issue XDR with MILE. 

**Note:** You can also check your wallet state on [Wallet](https://wallet.mile.global/wallet_info) or [Explorer](https://explorer.mile.global/wallet) websites.

#### Issue XDR with MILE
If you have no XDR but you have MILE you can issue XDR with MILE with no commission fee for this transaction:

```
[chaos@mile]> emission transaction mile local <wallet_names> [password <password>]
```
Where:<br>
`<wallet_names>` – your local wallet name<br>
`<password>` – your local wallet password (if there is one)

This command will lock MILE and emit XDR in your wallet in amount corresponding to current MILE/XDR rate (check [current rate](#blockchain-state)). Upon completion check your [wallet state](#check-wallet-state) to make sure XDR appear in the wallet. Otherwise repeat the operation as transaction can be rejected by blockchain.

**NOTE:** All MILE assets in your wallet will be locked. You will be able to unlock MILE by submitting proper XDR amount according to current MILE/XDR rate (reverse emission of MILE with XDR). 0,2% in XDR is charged for that [operation](#update-emission). 

You can start emission with any amount in MILE. You will not be able to issue XDR with MILE if you have already locked MILE in this wallet. 

For more information about *emission transaction* command see [Mile Shell Commands](#emission). 

#### Register Node

```
[chaos@mile]> register node with amount transaction local wallet <wallet_name> address <address> amount <amount> [password <password>]
```
Where:<br>
`<wallet_name>` – your local wallet name with proper XDR amount<br>
`<address>` – your node static IP address<br> 
`<amount>` – amount of XDR (10 000 — 100 000 XDR) you wish to deposit to register your node<br> 
`<password>` – your local wallet password (if there is one)

This command will register an active node on specified IP address with selected amount of XDR as a deposit with no commission fee for this transaction. 

The amount of XDR you set during registration will be locked in you wallet, therefore you will not be able to make any transactions with this amount unless you [unregister the node](#unregister-node) (commission fee of 1 XDR is charged for that operation).

**Note:** The amount of XDR deposited to register the node can only be set once and can not be updated for this node. To update the amount of XDR you need to unregister node (a commission fee of 1 XDR is charged for that operation and then register it again).

For more information about *register node* command see [Mile Shell Commands](#register-node). 

Upon completion of registration check your wallet state to make sure tag "Node" and node IP address appeared in your wallet:

```
[chaos@mile]> get local wallet state <name-of-your-wallet>
Wallet                  : "<your wallet name>"
xdr                     : "<your wallet XDR balance>"
mile                    : "<your wallet MILE balance>"
Tags                    : "Node"
Node address            : "<your node IP address>"
Last transaction id     : "xxxxx"
Is transactions exist   : "yes"
Freeze mile             : "0"
```

## Minting Premium

Minting premium is provided for operating [active (consensus) node](#active-consensus-node). The amount is **8,5—13%** of deposited volume of XDR per annum depending on two factors:

* amount of XDR deposited to register a node (the dependence is parabolic — the closer the 100 000 XDR deposit, the faster the % is growing)
* how many times the node participated in consensus (i.e. was the node operating permanently)   

The minting premium is delivered once in 1-2 days to node-associated wallet. 

## Mile Shell Commands

* [Help](#help)
* [Settings](#settings)
* [Node Wallet](#node-wallet)
* [Local Wallet](#local-wallet)
* [Blockchain Operations](#blockchain-operations)
* [Blockchain Transactions](#blockchain-transactions)


### Help

To see Mile Shell help commands type: 

```
help
```

Output:

```
| N: | Section name:        | Content:                         |
|----+----------------------+----------------------------------|
|  0 | settings             | Settings for shell               |
|  1 | node wallet          | Settings for node wallet         |
|  2 | local wallet         | Settings for local wallet        |
|  3 | blockchain           | Blockchain operations            |
|  4 | transaction          | Binary transaction               |
|----+----------------------+----------------------------------|

Type 'help <N>' or 'help <Section name>' to see commands

```
Type:<br>
`help 0` or `help settings` – show help on [settings](#settings) commands <br>
`help 1` or `help node wallet` – show help on [node wallet](#node-wallet) commands (**not recommended** to use this commands as node wallet commands are for blockchain developer purposes only)<br> 
`help 2` or `help local wallet` – show help on [local wallet](#local-wallet) commands<br>
`help 3` or `help blockchain` – show help on [blockchain operations](#blockchain-operations) commands<br>
`help 4` or `help transaction` – show help on [blockchain transactions](#blockchain-transactions) commands<br>

### Settings

* [`shell version`](#shell-version)
* [`shell set block event disable|enable`](#blockchain-event-enable-disable)
* [`shell set show transaction digest disable|enable`](#transaction-digest-enable-disable)
* [`shell settings`](#shell-settings)

#### Shell Version

```
shell version
```
Example output:

```
Blockchain verion   : chaos
Shell version       : 0.31
Git branch          : develop
Git commit hash     : 4427215
Build date          : 2018-11-25
Network lib version : 0.90

```

#### Blockchain event enable/disable

```
shell set block event disable|enable
```
`disable` or `enable` event message when new block is created.

#### Transaction digest enable/disable

```
shell set show transaction digest disable|enable
```
`disable` or `enable` event message when transaction is created.

#### Shell settings

```
shell settings
```

Show status of shell settings.

Example output:

```
New block event is      : disable
Show transaction digest : enable
```

### Node Wallet

**Node wallet commands are intended for developer purposes only**

### Local Wallet

* [`create local wallet <wallet_name> [password <password>]`](#create-local-wallet)
* [`create local wallet from keys <wallet_name> public key <public_key> private key <private_key> [password <password>]`](#create-local-wallet-from-keys)

#### Create local wallet

```
create local wallet <wallet_name> [password <password>]
```
Where:<br>
`<wallet_name>` – wallet name you want to set<br>
`<password>` – wallet password you want to set<br>

Create new local wallet.

#### Create local wallet from keys


### Blockchain Operations

#### Blockchain state

```
get blockchain state
```

Example output:

```
Blockchain state
Block count               : "73284"
Last block digest         : "2kdCssVgJk5adv2rVtRuykU8STHdTzbPTCFrMwcLgzcmaGeDr3"
Last block merkle root    : "111111111111111111111111111111115RyRTN"
Transaction count         : "19193"
Node count                : "12"
Local node                : "yes"
Non empty wallet count    : "2043"
Voting transaction count  : "0"
Pending transaction count : "0"
Blockchain state          : "Active"
Consensus round           : "0"
Mile courses              : "1.21"
```
Where:<br> 
`Block count` – number of blocks in blockchain<br>
`Last block digest` – digest of the last block<br>
`Last block merkle root` – **?????**<br>
`Transaction count` – number of transaction in the blockchain<br>
`Node count` – number of active node in the blockchain<br>
`Local node` – **?????**<br>
`Non empty wallet count` – number of wallets in blockchain with nonzero balance<br>
`Voting transaction count` – **?????**<br>
`Pending transaction count` – number of pending transactions<br>
`Blockchain state` – **????? (can be "Active" or "Escort")**<br>
`Consensus round` – **?????**<br>
`Mile courses` – current MILE/XDR rate

### Blockchain Transactions

#### Register Node

```
unregister node transaction local|node wallet <wallet_name> [password <password>]
```

#### Unregister Node

```
unregister node transaction local|node wallet <wallet_name> [password <password>]
```
____


#### Emission

```
emission transaction [mile|xdr] local|node <wallet_names> [password <password>]
```
_____

#### Update Emission

```
update emission transaction local|node wallet <wallet_name> [password <password>]
```
In case MILE/XDR rate has grown this command will emit additional XDR with your locked MILE in amount of the difference between current MILE/XDR rate and the rate as of your previous emission. 

**Note:** Commission fee for update emission transaction is 0,2% in XDR. The fee is charged even if MILE/XDR rate drops.  
____
### Exit shell

## Join Mile Testnet

Download testnet genesis block:

```
$ wget -O genesis_block_testnet.txt https://github.com/mile-core/mile-files/blob/master/genesis_block_testnet.txt?raw=true 
```

Replace existing mainnet genesis block:

```
$ cp ./genesis_block_testnet.txt  /etc/mile/genesis_block.txt 
```

You can use Mile Shell to manage your test node. [Test Wallet]( https://wallet.testnet.mile.global) for managing your wallet as well as [test Explorer](https://explorer.testnet.mile.global) for blockchain monitoring are also avaliable in testnet.

## FAQ

### Can I run a node if I don't have MILE or XDR?

### Can I move node from one host to another?

### Can I run a node if I have MILE, but I don't have XDR?

### Do I have to run a node if I want to make transactions with MILE or XDR?

### Are there any commissions for transactions?
