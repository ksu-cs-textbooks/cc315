---
title: "Summary"
weight: 45
pre: "9. "
---
In this section, we discussed more terminology related to trees as well as tree traversals. To recap the new vocabulary: 
- `Ancestor` - The ancestors of a node are those reached from child to parent relationships. We can think of this as our parents and the parents of our parents, and so on. 
- `Depth` - The depth of a node is its distance to the root. Thus, the root has depth zero. `Level` and `depth` are related in that: `level = 1 + depth`.
- `Descendant` - The descendants of a node are those reached from parent to child relationships. We can think of this as our children and our children's children and so on. 
- `Height of a Node` - The height of a node is the **longest** path to a leaf descendant. The height of a leaf is zero.
- `Height of a Tree` - The height of a tree is equal to the height of the root. 
- `Level` - The level of a node characterizes the distance the node is from the root. The root of the tree is considered level 1. As you move away from the tree, the level increases by one. 
- `Path` - a sequence of nodes and edges which connect a node with its descendant.
- `Siblings` - Nodes which share the same parent 
- `Traversal` is a general term we use to describe going through a tree. The following traversals are defined recursively. 
    - Preorder Traversal (Remember: Root Children): 
        1. Access the root
        2. Run the preorder traversal on the children
    - Postorder Traversal (Remember: Children Root): 
        1. Run the postorder traversal on the children
        2. Access the root. 
