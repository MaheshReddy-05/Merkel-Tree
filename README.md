# Java-Theory-Digital-Assignment-Merkel-Tree
## Introduction To Merkel Tree

A Merkle tree is a data structure with unique properties which make it useful for Bitcoin. Merkle trees are used to store all transactions in a given block. The advantage of this system is that one node can easily prove to another that a given transaction was contained in a specific block. This is useful for SPV nodes and light clients, who do not store the entire blockchain and are only interested in certain transactions or blocks.

## Architecture to Merkel Tree

As you can see in the above image, The data is broken up into blocks D1, D2, D3 and D4. These blocks are hashed using hash functions. Then each pair of nodes are hashed recursively until we reach the root node. Hash 0-0 contains the hash of D1 and hash 0-1 contains the hash of D2. Hash 0 contains hash of the sum of its children( hash(hash 0-0 + hash 0-1)). Similarly, all non-leaf nodes are a hash of their child nodes and the root node contains the hash of all nodes below it.
