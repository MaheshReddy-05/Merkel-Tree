# Java-Theory-Digital-Assignment-Merkel-Tree
## Introduction To Merkel Tree

A Merkle tree is a data structure with unique properties which make it useful for Bitcoin. Merkle trees are used to store all transactions in a given block. The advantage of this system is that one node can easily prove to another that a given transaction was contained in a specific block. This is useful for SPV nodes and light clients, who do not store the entire blockchain and are only interested in certain transactions or blocks.

## Architecture to Merkel Tree

As you can see in the above image, The data is broken up into blocks D1, D2, D3 and D4. These blocks are hashed using hash functions. Then each pair of nodes are hashed recursively until we reach the root node. Hash 0-0 contains the hash of D1 and hash 0-1 contains the hash of D2. Hash 0 contains hash of the sum of its children( hash(hash 0-0 + hash 0-1)). Similarly, all non-leaf nodes are a hash of their child nodes and the root node contains the hash of all nodes below it.
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Hash_Tree.svg/1920px-Hash_Tree.svg.png" />
## Algorithm

### **Algorithm of find function in Merkle tree**

- **Step 1:** We will take tree and key as parameters.
- **Step 2:** If the tree is null then we will return null.
- **Step 3:** If the tree->key is equal to the key we will return the tree.
- **Step 4:** If the key is smaller than tree->key then we will return find(tree->left, key)
- **Step 5:** else return find(tree->right, key)

### **Algorithm to add a node in Merkle tree.**

- **Step 1:** We will take key and value as parameters.
- **Step 2:** Take the hash(key) and store it in a variable called index.
- **Step 3:** store (struct node*) arr[index].head in a pointer called tree of datatype node.
- **Step 4:** create a new node with its key as key and value as value and both links as null.
- **Step 5:** If the tree is null then assign the new node to the head and increment the size by 1.
- **Step 6:** If the tree is not null then we will check if the key is already present in the tree using the find function.
- **Step 7:** If the key is already present in the tree then we will update the value.
- **Step 8:** If it is not present in the tree then we will use the insert function to insert the element.

### **Algorithm of insert function.**

- **Step 1:** It will take tree and item pointers of node data type as parameters.
- **Step 2:** If item->key is smaller than tree->key and tree->left is null then assign the item to tree->left.
- **Step 3:** If item->key is smaller than tree->key and tree->left is not null then call insert function with tree->left and item as parameters.
- **Step 4:** If item->key is greater than tree->key and tree->right is null then assign the item to tree->right.
- **Step 5:** If item->key is greater than tree->key and tree->right is not null then call insert function with tree->right and item as parameters.

### **Algorithm to delete a node in Merkle tree.**

- **Step 1:** We will take a key as a parameter.
- **Step 2:** Take the hash(key) and store it in a variable called index.
- **Step 3:** store (struct node*) arr[index].head in a pointer called tree of datatype node.
- **Step 4:** If the tree is null then the key is not present.
- **Step 5:** If the tree is not null then we will check if the key is already present in the tree using the find function.
- **Step 6:** If the find function returns null then the key is not present in the tree.
- **Step 7:** If it is not null then we will use the remove function to delete the elemen

### **Algorithm of remove function.**

- **Step 1:** It will take tree and key as parameters.
- **Step 2:** If the tree is null then return null.
- **Step 3:** If the key is smaller than the tree->key then tree->left is equal to remove(tree->left, key) and return tree.
- **Step 4:** If the key is greater than the tree->key then tree->right is equal to remove(tree->right, key) and return tree.
- **Step 5:** else if the tree->left is equal to null and the tree->right is equal to null then decrement the size and return tree->left.
- **Step 6:** else if the tree->left is not equal to null and the tree->right is equal to null then decrement the size and return tree->left.
- **Step 7:** else if tree->left is equal to null and tree->right is not equal to null then decrement the size and return tree->right.
- **Step 8:** else assign tree->left to a pointer called left of data type node.
- **Step 9:** While left->right is not equal to null, left is equal to left->right.
- **Step 10:** tree->key is equal to left->key.
- **Step 11:** tree->value is equal to left->value.
- **Step 12:** tree->left is equal to remove(tree->left, tree->key).
- **Step 13:** Return tree.
# **Time and Space complexity of Merkle Tree**

- The time complexity for searching is `O(log n)` because the time complexity for searching in a binary tree is `O(log n)`.
- The time complexity for insertion is `O(log n)`.
- The time complexity for deletion is `O(log n)`.
- The space complexity is `O( n )`.
# **Applications of Merkle tree**

- Apache Cassandra uses Merkle Trees to detect inconsistencies.
- Git uses a merkle tree to store its data.
- Ethereum uses a Merkle Patricia Trie.
- It is a fundamental part of the blockchain.
# References

- [https://iq.opengenus.org/merkle-tree/](https://iq.opengenus.org/merkle-tree/)
- https://decentralizedthoughts.github.io/2020-12-22-what-is-a-merkle-tree/
