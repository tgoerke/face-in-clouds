
# Scaling Ethereum Hackathon 2024

face-in-clouds is a storage application running on Filecoin IPC that leverages ZK proofs

Towards a data commons for open educational resources leveraging IPC & ZK.


Filecoin on it's mission to create decentralized storage, safeguard humanity's data and bring compute **to** the data has a huge potential to put things right for OER. Open educational resources (OER) aim to be teaching, learning, and research materials intentionally created and licensed to be free for the end user to own, share, and in most cases, modify. The reality is that in a person-centric data economy most resources are actually hosted on platforms and reputation is build by resource providers to build a followership there. Web3 still lacks of decentralized reputation system that could offer a practical alternative to platforms right now.  This hackathon projects has a focus on the data availability layer combined with some ideas to setup light incentive structures.

Filecoin & IPC 
Using IPC, a scalability framework from Filecoin & IPFS creators, protocol labs
decentralized apps bootstrap their own recursively scalable subnets tailored to dev requirements. 

It enables the creation of flexible, living networks of customizable sidechains or "subnets", which can achieve massive scaling by running parallel chains that interoperate with one another. 


Hack: Deploy a IPC subnet and run RISC Zero proofs on Ethereum

1) https://docs.ipc.space/quickstarts/deploy-a-subnet

	use case: DAO governance 
	-> vote for exam pass/fail using provable result of exam_score but without revealing personal data



Historically, the only method for confirming the correct execution of a software application was through redundant computation. ZK introduces a new option: verifiable computation. It's now possible to pair a program's output with a self-certifying receipt, allowing a skeptical third party to verify correct execution — and the verifier doesn't need to repeat the original computation or even see the inputs to the program!

For the second part of the hack we just assumed that OER are available and fairly shared on the storage network and implemented a simple use case how to leverages ZK technology to achieve verifiable computation using that data.  

How it's made: 

In the JSON example provided by risc0 we can prove that we know some "critical data" inside a JSON without revealing the other records in the same JSON. In the context of OER the Dapp proves completion of a certain assessment task by a person without revealing other personal data. 

https://docs.rs/risc0-zkvm/latest/risc0_zkvm/
https://dev.risczero.com/api/zkvm/examples

follow the JSON code and video tutorial from  workshop at ZK HACK III.

# Deploy a IPC subnet

Tutorial to deploy your first custom IPC subnet
see https://docs.ipc.space/quickstarts/deploy-a-subnet

Step 1: Prepare your system -> not shown here

Step 2: Initialise your config


Step 3: Set up your wallets


# Step 3: Set up your wallets

Output of `ipc-cli wallet new --wallet-type evm`

````
2024-04-19T13:24:16Z INFO  ipc_wallet::evm::persistent] key store does not exist, initialized to empty key store
"0x5ad2fa0996f7c25b446c5722f7254006616db509"
tgoerke@pad:~/src/face-in-clouds/ipc$ ipc-cli wallet new --wallet-type evm
"0x34fb473c5fc21958c6d2bb9d7bd1c8a080b0ae26"
tgoerke@pad:~/src/face-in-clouds/ipc$ ipc-cli wallet new --wallet-type evm
"0x9e19dbe0334a752e6dfa493af096ce07557cffdf"
tgoerke@pad:~/src/face-in-clouds/ipc$ ipc-cli wallet new --wallet-type evm
"0xbf225578ec98224b0757049d03b15f1542a2d0a7"
````



tgoerke@pad:~/src/face-in-clouds/ipc$ ipc-cli subnet create --parent /r314159 --min-validator-stake 1 --min-validators 4 --bottomup-check-period 300 --from 0x34fb473c5fc21958c6d2bb9d7bd1c8a080b0ae26 --permission-mode collateral --supply-source-kind native
[2024-04-19T14:34:00Z INFO  ipc_cli::commands::subnet::create] created subnet actor with id: /r314159/t410fe6ota3cu4msgpwbwkkcx4j5j35267nj6rrs4iga
tgoerke@pad:~/src/face-in-clouds/ipc$ 



fund wallets. 

explorer
https://calibration.filfox.info/en/address/0xbf225578ec98224b0757049d03b15f1542a2d0a7

:wq

## Join the subne## Join the subnett
tgoerke@pad:~/src/face-in-clouds/ipc$ sh j
[2024-04-19T14:36:07Z INFO  ipc_cli::commands::subnet::join] pre-funding address with 1
[2024-04-19T14:36:10Z INFO  ipc_provider] joining subnet with public key: "0410bf3d915abfea20f3b9bb09f1f29aca9da5f2b8592476ccb215c0c78823f02a415e614e71d11508c6dd2b2eb536e789389d0ba5a96dfbf1c9256c6f96967c69"
joined at epoch: 1540367
[2024-04-19T14:37:00Z INFO  ipc_cli::commands::subnet::join] pre-funding address with 1
[2024-04-19T14:37:03Z INFO  ipc_provider] joining subnet with public key: "0453f99398e2432e1d1d75f8b7baf1732cd43fb48285b83b54b5609fb9b73cde7b49ca86328b246333773ea692f173747e4419122bc8fd2c3fc35832dc5bb6e3ec"
joined at epoch: 1540369
[2024-04-19T14:38:01Z INFO  ipc_cli::commands::subnet::join] pre-funding address with 1
[2024-04-19T14:38:04Z INFO  ipc_provider] joining subnet with public key: "0498a5cc9eb9b995ae3b679009ba4b95a58e6ff37bfe55e6372adde2038c864423217771fd02e4617ef4fbacfdc053dff5d3fdf1d1b7e1f586dd400364a4e4a243"
joined at epoch: 1540371
[2024-04-19T14:39:01Z INFO  ipc_cli::commands::subnet::join] pre-funding address with 1
[2024-04-19T14:39:04Z INFO  ipc_provider] joining subnet with public key: "0403de9ef515b87236ecd6e5e37dfe38088c2e78e45f2bb42e4e602b1b49a5dab33c5ca7ed1c7e9d58a63905b5a603d900d26388855b07882f98cfe1c89d86ebe7"
joined at epoch: 1540373


## Deploy the infrastructure

Start validator 1

sh s1


#################################
#                               #
# Subnet node ready! 🚀         #
#                               #
#################################

Subnet ID:
        /r314159/t410fe6ota3cu4msgpwbwkkcx4j5j35267nj6rrs4iga

Eth API:
        http://0.0.0.0:8545

Chain ID:
        0

Fendermint API:
        http://localhost:26658

CometBFT API:
        http://0.0.0.0:26657

CometBFT node ID:
        39d354193227fe1fce14783c51ff0255fa81b624

CometBFT P2P:
        http://0.0.0.0:26656

IPLD Resolver Multiaddress:
        /ip4/0.0.0.0/tcp/26655/p2p/16Uiu2HAmCgVTL4PcPmW6YU92TBUQAoKvjGBFFgsDXMikETJB11Va
[cargo-make] INFO - Build Done in 30.79 seconds.




---

We need the peer_id, last part of IPLD Resolver Multiaddress : 16Uiu2HAmCgVTL4PcPmW6YU92TBUQAoKvjGBFFgsDXMikETJB11Va
and we need the CometBFT node ID:
	ca644ac3194d39a2834f5d98e141d682772c149b


sh s2

#################################
#                               #
# Subnet node ready! 🚀         #
#                               #
#################################

Subnet ID:
        /r314159/t410fe6ota3cu4msgpwbwkkcx4j5j35267nj6rrs4iga

Eth API:
        http://0.0.0.0:8645

Chain ID:
        2722837839937549

Fendermint API:
        http://localhost:26658

CometBFT API:
        http://0.0.0.0:26757

CometBFT node ID:
        1fe7b2ba86d6f13ca853a94c4dcdf552ad80be2a

CometBFT P2P:
        http://0.0.0.0:26756

IPLD Resolver Multiaddress:
        /ip4/0.0.0.0/tcp/26755/p2p/16Uiu2HAmUAJ6t3GjEEPApWDfHt57858ppcXRFsGYRwcG6ReCSZpK
[cargo-make] INFO - Build Done in 63.64 seconds.










## Step 7: Interact with your subnet using the IPC CLI

tgoerke@pad:~/src/face-in-clouds/ipc$ ipc-cli wallet balances --wallet-type evm --subnet=/r314159/t410fe6ota3cu4msgpwbwkkcx4j5j35267nj6rrs4iga
0x5ad2fa0996f7c25b446c5722f7254006616db509 - Balance: 1.0
0xbf225578ec98224b0757049d03b15f1542a2d0a7 - Balance: 1.0
0x34fb473c5fc21958c6d2bb9d7bd1c8a080b0ae26 - Balance: 1.0
0x9e19dbe0334a752e6dfa493af096ce07557cffdf - Balance: 1.0

