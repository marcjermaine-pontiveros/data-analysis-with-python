# Association Rules Tutorial

## Overview
This tutorial demonstrates how to create association rules using the Apriori algorithm. You'll learn to identify relationships between items in transactional data and calculate key metrics like support, confidence, and lift.

## Prerequisites
- Python 3.x
- Basic understanding of data analysis concepts
- Familiarity with pandas and data manipulation

## Learning Objectives
By the end of this tutorial, you will be able to:
1. Understand the concept of association rules
2. Implement the Apriori algorithm using mlxtend
3. Calculate and interpret support, confidence, and lift metrics
4. Generate actionable insights from transaction data

## Tutorial Structure

### Step 1: Setup and Installation
Install the required mlxtend library which provides efficient Apriori implementation.

### Step 2: Data Preparation
- Create a sample transactional dataset
- Convert data to one-hot encoded format using TransactionEncoder
- Understand the data structure required for association rule mining

### Step 3: Frequent Itemset Mining
- Apply the Apriori algorithm with minimum support threshold
- Identify frequent itemsets in the dataset
- Interpret support values and their significance

### Step 4: Association Rule Generation
- Generate rules from frequent itemsets
- Apply minimum confidence threshold
- Calculate lift values for rule evaluation

### Step 5: Results Interpretation
- Analyze rule metrics (support, confidence, lift)
- Identify strong associations
- Understand business implications

## Key Concepts

### Support
- Percentage of transactions containing the itemset
- Indicates how frequently items appear together
- Higher support = more frequent occurrence

### Confidence
- Probability that consequent occurs given antecedent
- Measures rule reliability
- Range: 0 to 1 (higher is better)

### Lift
- Ratio of observed support to expected support
- Indicates strength of association
- Lift > 1: positive association
- Lift < 1: negative association
- Lift = 1: independence

## Sample Dataset
The tutorial uses a grocery store transaction dataset with items:
- Milk
- Bread
- Eggs
- Butter

## Expected Outputs
- Frequent itemsets with support values
- Association rules with confidence and lift metrics
- Insights about item relationships

## Next Steps
After completing this tutorial, you can:
- Apply the techniques to your own datasets
- Experiment with different support and confidence thresholds
- Explore advanced association rule mining algorithms
- Implement in real-world business scenarios

## Files
- `C9-M1-Demo Association Rules.ipynb`: Complete implementation notebook
- `README.md`: This tutorial guide