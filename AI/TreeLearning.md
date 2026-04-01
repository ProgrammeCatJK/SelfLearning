# Tree Learning (week 4)

## Entropy
- Represents the unpredictability of the data lables.
    - **high entropy** --> mixed unvertain dataset
    - **low entropy** --> indicates a pure dataset

- determine the best features of splitting data by measuring **info gain**
    - the entropy change before and after the split

- lost function
    - Cross-Entropy --> Measure the diff between predicted probability distributions and actual traget labels
 - lost function
    - Cross-Entropy --> Measure the diff between predicted probability distributions and actual traget labels

Equations

Entropy (for a discrete distribution p):

$$H(p) = -\sum_{i} p_i \log_b p_i$$

Cross-entropy between true distribution q and predicted distribution p:

$$H(q, p) = -\sum_{i} q_i \log_b p_i$$

### Example: Coin flip
- Coin flip --> Head or tails are equally likely
    - Uncertainty is maximal
    - if the coin is heavily biased **(99% Heads)** --> Outcome predictable --> **Low entropy**


For a fair coin with $P(H)=P(T)=0.5$:

$$
H(X) = -\big[0.5\log_2 0.5 + 0.5\log_2 0.5\big] = 1\ \text{bit}
$$

Unfair coin (99% Heads):

For a coin with $P(H)=0.99,\ P(T)=0.01$:

$$
H(X) = -\big[0.99\log_2 0.99 + 0.01\log_2 0.01\big] \approx 0.0808\ \text{bits}
$$

where $S_t$ and $S_f$ are the subsets of $S$ for which attribute $A_1$ is true/positive and false/negative, respectively.

## Aim
- Decision Tree
- Reproduce basic top-down algo for Top Down Induction Decision Tree TDIDT
- Define entropy
- Define overfitting in decsion trees
- Inductive bias of basic TDIDT algo
- Regression Tree

## Application
- Data mining
- cheap computation, but high variance(Overfit)
- classification

## Tennis Example
- 3 Features --> Outlook, Humidity, Wind
- 1 output --> Play

## **Algo**
Split into subset based on type(Overcast, rain sunny)
if pure: Stop
else repeat

For new data, find the subset the data falls into

### Representation
- Each internal nodes tests an attribute
- Each branch corresponds to attribute value
- Each leaf node assigns a classification

## When to yse DT?
- a mix of numeric features and discrete attribute-value pairs
- traget function is discrete valued(True or False, difference class)
- possibly noisy training data

## TDIDT(ID3 and CaRT)
1. select the best decision attribute for next node to split it
2. Assign A as decision attribute for node
3. For each value of A, create new descendant of node
4. Split traning examples to child node 
5. Perfectly classified, then stop, else new child 
- ID3 --> Categorical target
- CaRT --> Uses both categorical and numerical attributes

## Best Feature Decision?
- Entropy Calculation
    - Info Theory: Amount of info needed to specify the full state of a system
    - Pure, All class is under one category
    
Information gain (for attribute $A_1$):

$$
\mathrm{Gain}(S, A_1) = H(S) - \left(\frac{|S_t|}{|S|} H(S_t) + \frac{|S_f|}{|S|} H(S_f)\right)
$$
## Bias
- info gain is more biased towards attribute with large muber of values
    - Subsets are more likely to be pure if thre is a large number of values
    - Overfitting

- ### Solution 
    - Gain Ratio --> Modificaiton of the info gain value
    - Takes the number and size of branches into account 

## Overfit
- How to know it is overfit? Accuracy on Training vs Test
- Pruning to avoid
    - Pre-pruning: Stop iteration when data split not statistically significant
        - below a certain No. of Leaf (min_samples_leaf)
        - Entropy changes smaller than a lower bound (min_impurity_decrease)
        - max_leaf_nodes
        - min_samples_split
        -max_depth
    - Post-pruning: Grow full tree, then remove sub-trees which are overfitting
        - Error estimation
        - signif testing
        - MDL principle
        1. Reduced-error Pruning(ValidationSet and TrainSet) --> Cutting all child node if the accuray increases/same onvalidation 
        2. Min Error --> Graph of Error against Nodes, Minimum Point
        3. Smallest tree
            - Same as Min Error, but the lowest error node before the lowest error nodes.

    - Early stopping
        - Pre-pruning may suffer from ES: Stop growth of a tree prematurely
            - XOR example:
                - model failed to make it more accuarate than it was. Still the same class for the attribute
                - Dangerous --> data can be useful when combine with other features

## Cross validation
- K fold Cross Validation(Most Common)
    - Model trained on K-1 fold (Subet of K data points)
        - Loops through the K difference combination --> all data is been as a testSet
    -LOOCV(Leave One Out CV)
        - Difference data point is left out until the K iteration
    **Class imbalance issues**
    **Rules can be converted from trees**

## Continue Attribute
- It can have many split in the tree(at most n-1 splits for n values)
- Mid point of the two continous value
- **Computation of all classes can be expensive** 
    - using Gain relative to cost
$$
\frac{Gain^2(S,A)}{Cost(A)}
$$
    - Perference tree with lower cost attributes

## Dealing with missing value of A
- node n tests A, assigned with the most common value of A
- assigm most common value of A among other examples with same target value
- assign probability $p_i$ to each possible value $v_i$ of A
    - assign $p_i$ to each descendant in tree

## Regreeesion Tree
- It is more clear for multiple variables, categorical adn some are real valued
- How to build and find the threshold(The Split point of the features)

### Threshold
**The boundary to split the feature that divides the continuous input to minimize prediction error**

- Using mean squared error: $Avg(y_a-y_p)^2$
- I have a set of data points --> Loop each --> Calculate the min MSE point
- Choose the node based on the lowest MSE
- Split them with the type of result in the atttribute
- choose the node based on the lowest MSE and repeat

## Model Tree
- Splitting the graph with difference part based on the x axis and then lineariase it 
- choose the splitting point based on the reducing the variantion in the data SDR

# Question to ask
- 2 methods: ASK Misclassification with costs means (Page 64)
- Hypothesis Space Search by ID3