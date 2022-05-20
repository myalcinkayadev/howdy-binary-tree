# howdy-binary-tree
keywords: root, node, leaf node, edge, child, parent

**Rules:**
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

/*
  What we want to do is take in a binary tree, and in particular,a function is going to take in the root of the binary tree.
  And recall that given the root node of a binary tree, we know that that node is going to have pointers 
  to its left and right children, which may point to other nodes. 
  However, if let's say a node does not have a left or right child, then its point is going to be set to null. 
  So that's how we represent our binary tree programmatically.
*/

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
```javascript
/*
  If I'm doing a depth first traversal, I need to go deeper in the tree before I move laterally.
  The really important characteristic is we must go deeper in the tree 
  until we can't anymore and then we can go across the tree.
  values: a,b,d,e,c,f
*/
```

#### How can we manage to implement this algorithm?
> It's going to use a data structure like a stack.

#### Time-space complexity
***n = # of nodes***
- Time:  O(n)
- Space: O(n)

#### Iterative solution
```javascript
 const depthFirstValues = (root) => {
   if (root === null) return [];
   const result = [];
   const stack = [root];
   while (stack.length > 0) {
     const current = stack.pop();
     result.push(current.val);
     if (current.right) stack.push(current.right);
     if (current.left) stack.push(current.left);
   }
   return result;
 };
``` 

#### Recursive solution
```javascript
const depthFirstValues = (root) => {
  if (root === null) return [];
  const leftValues = depthFirstValues(root.left);
  const rightValues = depthFirstValues(root.right);
  return [root.val, ...leftValues, ...rightValues]; 
}
```

## breadth first values problem
``` javascript
//      a
//    /   \
//   b     c
//  / \     \
// d   e     f
//    /       \
//   g         h

//   -> ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']
```

#### How can we manage to implement this algorithm?
> It's going to use a queue data structure.

#### Time-space complexity
***n = # of nodes***
- Time: O(n) -> best 
- Space: O(n)

#### Iterative solution
```javascript
const breadthFirstValues = (root) => {
  if (root === null) return [];

  const values = [];
  const queue = [root];

  while (queue.length > 0) {
    const current = queue.shift();
    values.push(current.val);

    if (current.left !== null) queue.push(current.left);
    if (current.right !== null) queue.push(current.right);
  }

  return values;
}
```

## tree includes problem
```javascript
const treeIncludes = (root, target) => {
  if (root === null) return false;
  
  const queue = [ root ];
  while (queue.length > 0) {
    const current = queue.shift();
    if (current.val === target) return true;
    if (current.left) queue.push(current.left);
    if (current.right) queue.push(current.right);
  }
  return false;
}
```
