# Tree-Based Methods

These involve stratifying or segmenting the predictor space into a number of simple regions.

Tree-based methods are simple and useful for interpretation. However, they typically are not competitive with the best supervised learning approaches. Hence in this chapter we also introduce bagging, random forests, and boosting. Each of these approaches involves producing multiple trees which are then combined to yield a single consensus prediction. We will see that combining a large number of trees can often result in dramatic improvements in prediction accuracy, at the expense of some loss in interpretation.

### Regression Trees

In keeping with the tree analogy, the regions R1, R2, and R3 are known as terminal nodes or leaves of the tree.

The points along the tree where the predictor space is split are referred to as internal nodes. We refer to the segments of the trees that connect the nodes as branches.

#### Prediction via Stratification of the Feature Space

How do we construct the regions?

we choose to divide the predictor space into high-dimensional rectangles, or boxes, for simplicity and for ease of interpretation of the resulting predictive model.

It is computationally infeasible to consider every possible partition of the feature space into J boxes. For this reason, we take a top-down, greedy approach that is known as recursive binary splitting.

It is greedy because at each step of the tree-building process, the best split is made at that particular step, rather than looking ahead and picking a split that will lead to a better tree in some future step.

##### Tree Pruning

The process described above may produce good predictions on the training set, but is likely to overfit the data, leading to poor test set performance. This is because the resulting tree might be too complex. A smaller tree with fewer splits (that is, fewer regions R1, . . . , RJ) might lead to lower variance and better interpretation at the cost of a little bias. 

One possible alternative to the process described above is to build the tree only so long as the decrease in the RSS due to each split exceeds some (high) threshold. This strategy will result in smaller trees, but is too short-sighted since a seemingly worthless split early on in the tree might be followed by a very good split—that is, a split that leads to a large reduction in RSS later on.

Therefore, a better strategy is to grow a very large tree T0, and then prune it back in order to obtain a subtree.

How do we determine the best way to prune the tree?

Cost complexity pruning—also known as weakest link pruning—gives us a way to do just this. Rather than considering every possible subtree, we consider a sequence of trees indexed by a nonnegative tuning parameter α.

