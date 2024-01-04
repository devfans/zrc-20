# zrc-20

## zrc-20

This standard is fully based on domo-2's [brc-20 standard](https://domo-2.gitbook.io/brc-20-experiment/), with an extension of one extra op code(**delegate)** to introduce brc-20 tokens to bitcoin L2 chains. The purpose is to extend the usability of brc-20 token, so users could port brc-20 tokens into the layer 2 tokens and operate brc-20 tokens same way as erc-20 tokens on L2 chains.​



<figure><img src=".gitbook/assets/Screenshot 2024-01-03 at 16.37.52.png" alt=""><figcaption></figcaption></figure>



Changes:&#x20;

* The deploy operation of the zrc-20 tokens on Bitcoin will be interpreted into erc-20 contract deployment on L2, so each zrc-20 token will have a mirror erc-20 token on L2.&#x20;

```
{ 
  "p": "zrc-20",
  "op": "deploy",
  "tick": "ordi",
  "max": "21000000",
  "lim": "1000",
  "difficulty": "5"
}
```

* Bitcoin account (address A) will have a mapped account (address a) so that: <mark style="color:blue;">`a = keccak(A)[12:]`</mark>, mapped account does not have the permission to operate the token since no one will have the private key of p.&#x20;
* A L2 chain will serve as the ledge of zrc-20 tokens. That means all zrc-20 token operations on the Bitcoin chain will be tracked and interpreted into L2 token contract interactions, so the balance of zrc-20 tokens can be easily checked by calling the mirror erc-20 contract. There’ll be a dedicated module(the indexer module) in Layer 2 node to index the zrc-20 inscriptions, this module works just like brc-20 indexer but with the extended feature supported.&#x20;
* With the op code delegate, a zrc-20 user A could delegate some of the balance to L2 account b, so that the private key holder of account b will be capable of operating these tokens while the balance will be deducted from user A's account. The delegate operation doing the exact operation of transferring tokens to a L2 account. After this operation, the L2 account user could operate the token the same way as erc-20 tokens, no matter if it's a transfer, swap or lock. The inscription should be sent to the sender again as a second step.

```
{ 
  "p": "zrc-20",
  "op": "delegate",
  "tick": "ordi",
  "amt": "100",
  "chain": "l2-chain-a",
  "to": "0x3Ea1756E8Ce21a41E15eC3F026A0eA379Cc3e1A5"
}
```

* If L2 account b transfers some of the balance to a L2 mapped account (address a), that means an operation of un-delegate. After this operation, the transferred balance will be only spendable by the private key holder of the original L1 account A(such that <mark style="color:blue;">`a = keccak(A)[12:]`</mark>).&#x20;
* Each time a newer state of the L2 network is submitted to the Bitcoin and verified in a way(ZKP etc), the afterward transfers which follow un-delegations can be assumed valid.



​With this extension proposal, brc-20 token could be ported to an erc-20 token on Bitcoin L2 chains. Users will need no more to worry about the Bitcoin network congestions or inscriptions since the token will be treated same as erc-20 token on layer 2s. This greatly increases the usability of brc-20 tokens.​ The next page is the original brc20 standard.



The original brc-20 standard: [https://domo-2.gitbook.io/brc-20-experiment/](https://domo-2.gitbook.io/brc-20-experiment/)

