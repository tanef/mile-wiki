# Mile Node Ducumentation 

* [Introduction](#introduction)
* [Node Setup](#node-setup)
* [Minting Premium](#minting-premium)
* [Mile Shell Help](#mile-shell-help)
* [Join Mile Testnet](#join-mile-test-net)
* [FAQ](#faq)

## Introduction
There are two types of nodes in the blockchain:

### Active (Consensus) Node

The minting premium for running a consensus node depends on two factors:

* how many blocks you closed 
* ammount of XDR with wich you registered your node

is 8,5—13% per annum depending on deposit volume and  you receive depends on the 

### Passive Node

## Node Setup

To run a node your node host must comply with certain [requirements] (#requirements).

To set up [active (consesus) node](#active-consensus-node) you need to go trough these steps:

1. [Download and install Mile Node](#download-and-install-mile-node)
2. [Download and install Mile Shell](#download-and-install-mile-shell)
3. [Run node shell](#run-node-shell)
3. [Register node] (#node-registration) 

To set up [passive node] (#passive) you need only steps 1—3.

### Requirements

* OS Supported: Linux Centos 7.x

* System:

 | Minimum | Recommended |
 |:-------:| :----------:|
 |2 GB RAM|8 GB RAM|
 |1 CPU core|8 CPU cores|
 |60GB HDD|512GB SDD|
 
* Static IP address (only for active nodes).

### Download And Install Mile Node

You can install Mile Node ode using RPM or YUM.

#### RPM 

**Domnload and install**

```
$ rpm -ivh https://github.com/mile-core/mile-files/blob/master/mile-0.4x-46.x86_64.rpm?raw=true # install binaries
$ rpm -qi mile # check installations
```

**Download only** 

```
$ wget -O mile-0.4x-46.x86_64.rpm https://github.com/mile-core/mile-files/blob/master/mile-0.4x-46.x86_64.rpm?raw=true
```

**Update**

In case Mile node was installed before.

```
$ rpm -Uvh https://github.com/mile-core/mile-files/blob/master/mile-0.4x-46.x86_64.rpm?raw=true
```

**Unistall**

```
$ rpm -e mile
```

#### YUM

### Download And Install Mile Shell 

#### RPM
#### YUM

### Run Node Shell  

### Node Registration 

To register node you need to lock **10 000 — 100 000 XDR** on your node. That is, you have to have [wallet] (#create-wallet) with proper amount in XDR or [MILE] (#issuing-xdr-with-mile) deposited. You can buy MILE on the [open market] (https://github.com/mile-core/mile-docs/wiki/faq#how-i-can-buy-mile).

As soon as [minting premium] (#minting-premium) depends on the amount of blocks in the blockchain your node closed (i.e. 

**Note:** A node should have a static IP address.   

#### Create Wallet
You can create new wallet or add your existing wallet to database.

##### Create New Wallet
**Note:** Password is optional, but it is highly recommended. 

##### Add Existing Wallet

##### Check Wallet State

You can check your wallet state 

#### Issuing XDR with MILE
If you have no XDR but you have MILE you can issue XDR with MILE with no commission fee for this transaction:

```
[chaos@mile]> emission transaction mile local <wallet_names> [password <password>]
```
Where:<br>
`<wallet_names>` – your local wallet name<br>
`<password>` – your local wallet password (if there is one)

This command will lock MILE and emit XDR in your wallet in amount corresponding to current MILE/XDR rate (check [current rate](#blockchain-state)). Upon completion check your [wallet state] (#check-wallet-state) to make sure XDR appear in the wallet. Otherwise repeat the operation as transaction can be rejected by blockchain.

**NOTE:** All MILE assets in your wallet will be locked. You will be able to unlock MILE by submitting proper XDR amount according to current MILE/XDR rate (reverse emission of MILE with XDR). 0,2% in XDR is charged for that operation. 

You can start emission with any amount in MILE. You will not be able to issue XDR with MILE if you have already locked MILE in this wallet. 

For more information about *emission transaction* command see [Mile Shell Help] (#emission). 

#### Register Node

```
[chaos@mile]> register node with amount transaction local wallet <wallet_name> address <address> amount <amount> [password <password>]
```
Where:<br>
`<wallet_name>` – your local wallet name with proper XDR amount<br>
`<address>` – your node static IP address<br> 
`<amount>` – amount of XDR (10 000 — 100 000 XDR) with which you register your node<br> 
`<password>` – your local wallet password (if there is one)

This command will register an active node on specified IP address with selected amount of XDR with no commission fee for this transaction. 

The amount of XDR you set during registration will be locked in you wallet, therefore you will not be able to make any transactions with this amount unless you [unregister the node] (#unregister-node) (commission fee of 1 XDR is charged for that operation).

**Note:** The amount of XDR with which you register node can only be set once and can not be updated for this node. To update the amount of XDR you need to unregister node a commission fee of 1 XDR is charged for that operation and then register it again.

For more information about *register node* command see [Mile Shell Help] (#register-node). 

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

## Mile Shell Help
_____

**Blockchain State**

```
get blockchain state
```

Output:

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
Where: 

Mile courses – current MILE/XDR rate
____
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


## Join Mile Testnet

## FAQ

### Can I run a node if I don't have 10 000 XDR?

### Can I move node from one host to another?

### What are commissions for transactions?