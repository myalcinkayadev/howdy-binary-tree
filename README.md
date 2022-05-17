# howdy-binary-tree
keywords: root, node, leaf node, edge, child, parent

Rules:
- A binary tree is a tree where every node has at most two children. 
- Exactly 1 root
- Exactly 1 path b/w root and any node
- We should consider any empty tree as actually being a binary tree.

## Binary Tree Node Class
```javascript
class Node {
  constructor(val) {
    this.val = val;
    this.left = null;
    this.right = null;
  }
}


// Static Representation
const a = new Node('a');
const b = new Node('b');
const c = new Node('c');
const d = new Node('d');
const e = new Node('e');
const f = new Node('f');

a.left = b;
a.right = c;
b.left = d;
b.right = e;
c.right = f;

      a
    /   \
   b     c
  / \     \
 d   e     f
```

## depth first values problem
## breadth first values problem
