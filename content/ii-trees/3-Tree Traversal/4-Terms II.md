---
title: "Terms II"
weight: 20
pre: "4. "
---
{{< youtube 86uWWXaanCo  >}}

We can describe the sizes of trees and position of nodes using different terminology, like level, depth, and height. 

![Family Tree](images/3/3Tree_FamilyTree.png)

- `Level` - The level of a node characterizes the distance between the node and the root. The root of the tree is considered level 1. As you move away from the tree, the level increases by one. 
    - For our family tree example, what nodes are in the following levels? Think about the answer and then click corresponding arrow. 
        <details><summary markdown="span">Level 1:</summary><u>Myra</u> - Level 1 is always the root</details>
        <details><summary markdown="span">Level 2:</summary><u>Raju, Joe, Zia</u> - These are the nodes which are 1 edge away from the root.</details>
        <details><summary markdown="span">Level 3:</summary><u>Uzzi, Bert, Uma</u> - These are the nodes which are 2 edges away from the root. </details>
        <details><summary markdown="span">Level 4:</summary><u>Bev, Ava, Ang</u> - These are the nodes which are 3 edges away from the root. </details>
        <details><summary markdown="span">Level 5:</summary><u>Isla</u> - This is the only node which is 4 edges away from the root. </details>
        <details><summary markdown="span">Level 6:</summary><u>Eoin</u> - This is the only node which is 5 edges away from the root. </details>
- `Depth` - The depth of a node is its distance to the root. Thus, the root has depth zero. `Level` and `depth` are related in that: `level = 1 + depth`.
    - For our family tree example, what nodes have the following depths? 
        <details><summary markdown="span">Depth 0:</summary><u>Myra</u> - The root will always be at depth 0.</details>
        <details><summary markdown="span">Depth 1:</summary><u>Raju, Joe, Zia</u> - These are the nodes which are 1 edge away from the root.</details>
        <details><summary markdown="span">Depth 2:</summary><u>Uzzi, Bert, Uma</u> - These are the nodes which are 2 edge away from the root.</details>
        <details><summary markdown="span">Depth 3:</summary><u>Bev, Ava, Ang</u> - These are the nodes which are 3 edge away from the root.</details>
        <details><summary markdown="span">Depth 4:</summary><u>Isla</u> - This is the only node which is 4 edges away from the root.</details>
        <details><summary markdown="span">Depth 5:</summary><u>Eoin</u> - This is the only node which is 5 edges away from the root.</details>
- `Height of a Node` - The height of a node is the **longest** path to a leaf descendant. The height of a leaf is zero.
    - For our family tree example, what nodes have the following heights?
        <details><summary markdown="span">Height 0:</summary><u>Raju, Eoin, Ava, Bert, Ang</u> - The leaves always have height 0. </details>
        <details><summary markdown="span">Height 1:</summary><u>Isla, Uma</u> - `Isla -> Eoin`  and `Uma -> Ang` </details>
        <details><summary markdown="span">Height 2:</summary><u>Bev, Zia</u> - `Bev -> Isla -> Eoin` and `Zia -> Uma -> Ang` </details>
        <details><summary markdown="span">Height 3:</summary><u>Uzzi</u> - `Uzzi -> Bev -> Isla -> Eoin`</details>
        <details><summary markdown="span">Height 4:</summary><u>Joe</u> - `Joe -> Uzzi -> Bev -> Isla -> Eoin`</details>
        <details><summary markdown="span">Height 5:</summary><u>Myra</u> - `Myra -> Joe -> Uzzi -> Bev -> Isla -> Eoin`</details>
- `Height of a Tree` - The height of a tree is equal to the height of the root. 
    - Our family tree would have height 5




