# Mile Node Ducumentation 

* [Introduction](#introduction)
* [Node Setup](#node-setup)
* [Minting Premium](#minting-premium)
* [Mile Shell Help](#mile-shell-help)
* [Other Ways To Manage And Monitor Wallets And Transactions](#other-ways-to-manage-and-monitor-wallets-and-transactions)
* [Join Mile Testnet](#join-mile-testnet)
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

To run a node your node host must comply with certain [requirements](#requirements).

To set up [active (consesus) node](#active-consensus-node) you need to go trough these steps:

1. [Download and install Mile Node And Mile Node](#download-and-install-mile-node-and-mile-node-shell)
2. [Launch Mile Node And Mile Node Shell](#launch-mile-node-and-mile-node-shell)
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

### Download And Install Mile Node And Mile Node Shell

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
will install Mile Node ver. 0.4x-56

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
Where `<version>` is the version of Mile Node (e.g. ver. <0.4x-56>). 
<br>
<br>

Install previously downloaded Mile Node:

```
$ rpm -ivh mile-<version>.x86_64.rpm
```
Where `<version>` is the version of Mile Node (e.g. ver. <0.4x-56>).
<br>
<br>

Update Mile Node (in case Mile Node was installed before):

```
$ rpm -Uvh https://github.com/mile-core/mile-files/blob/master/mile-<version>.x86_64.rpm?raw=true
```
Where `<version>` is the version of Mile Node (e.g. ver. <0.4x-56>).
<br>
<br>


Unistall Mile Node:

```
$ rpm -e mile
```
##### Install Mile Shell 

Domnload and install Mile Shell:

```
$ rpm -ivh https://github.com/mile-core/mile-files/blob/master/mileshell-0.4x-1.x86_64.rpm?raw=true
```
Check Mile Shell installations:

```
$ rpm -qi mileshell
```
___
###### Other Options

Mile Shell download only: 

```
$ wget -O mileshell-0.4x-1.x86_64.rpm https://github.com/mile-core/mile-files/blob/master/mileshell-0.4x-1.x86_64.rpm?raw=true
```

Install previously downloaded Mile Shell:

```
$ rpm -ivh mileshell-0.4x-1.x86_64.rpm
```

Update Mile Shell (in case Mile Shell was installed before):

```
$ rpm -Uvh https://github.com/mile-core/mile-files/blob/master/mileshell-0.4x-1.x86_64.rpm?raw=true
```

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

##### Install Mile Node

```
$ yum install mile
```

##### Install or update Mile Node from downloaded local rpm package

перед этим wget!!! также как в описании rpm ===
```
$ yum localinstall ./mileshell-0.4x-4.x86_64.rpm 
```


##### Install Mile Shell

```
$ yum install mileshell
```

##### Install or update Mile Shell from downloaded local rpm package

перед этим wget только для shell уже!!! также как в описании rpm ===
```
$ yum localinstall ./mileshell-0.4x-4.x86_64.rpm 
```

### Launch Mile Node And Mile Node Shell

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

To register node you need to lock **10 000 — 100 000 XDR** on your node. That is, you have to have [wallet](#create-wallet) with proper amount in XDR or [MILE](#issue-xdr-with-mile) deposited. You can buy MILE on the [open market](https://github.com/mile-core/mile-docs/wiki/faq#how-i-can-buy-mile).   

#### Create Wallet
You can create new wallet or add your existing wallet to database.

##### Create New Wallet
**Note:** Password is optional, but it is highly recommended. 

##### Add Existing Wallet

##### Check Wallet State

You can check your wallet state 

#### Issue XDR with MILE
If you have no XDR but you have MILE you can issue XDR with MILE with no commission fee for this transaction:

```
[chaos@mile]> emission transaction mile local <wallet_names> [password <password>]
```
Where:<br>
`<wallet_names>` – your local wallet name<br>
`<password>` – your local wallet password (if there is one)

This command will lock MILE and emit XDR in your wallet in amount corresponding to current MILE/XDR rate (check [current rate](#blockchain-state)). Upon completion check your [wallet state](#check-wallet-state) to make sure XDR appear in the wallet. Otherwise repeat the operation as transaction can be rejected by blockchain.

**NOTE:** All MILE assets in your wallet will be locked. You will be able to unlock MILE by submitting proper XDR amount according to current MILE/XDR rate (reverse emission of MILE with XDR). 0,2% in XDR is charged for that operation. 

You can start emission with any amount in MILE. You will not be able to issue XDR with MILE if you have already locked MILE in this wallet. 

For more information about *emission transaction* command see [Mile Shell Commands](#emission). 

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

The amount of XDR you set during registration will be locked in you wallet, therefore you will not be able to make any transactions with this amount unless you [unregister the node](#unregister-node) (commission fee of 1 XDR is charged for that operation).

**Note:** The amount of XDR with which you register node can only be set once and can not be updated for this node. To update the amount of XDR you need to unregister node a commission fee of 1 XDR is charged for that operation and then register it again.

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

## Mile Shell Commands

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

### Node Wallet

### Local Wallet

### Blockchain Operations

#### Blockchain State

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
Where: 

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

## Other Ways To Manage And Monitor Wallets And Transactions

## Join Mile Testnet

## FAQ

### Зачем нужна нода?

### Can I run a node if I don't have MILE or XDR?

### Can I move node from one host to another?

### Can I run a node if I have MILE, but I don't have XDR?

### Do I have to run a node if I want to make transactions with MILE or XDR?

### Are there any commissions for transactions?
