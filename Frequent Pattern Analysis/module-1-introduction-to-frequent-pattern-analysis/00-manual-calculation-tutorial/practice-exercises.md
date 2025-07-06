# Practice Exercises: Manual Frequent Pattern Analysis

## Exercise 1: Basic Support Calculation

Given the following transaction database:

```
T1: {A, B, C}
T2: {A, B}
T3: {A, C}
T4: {B, C}
T5: {A, B, C}
```

**Questions:**
1. Calculate the support for each individual item (A, B, C)
2. Calculate the support for each 2-itemset: {A,B}, {A,C}, {B,C}
3. Calculate the support for the 3-itemset: {A,B,C}
4. If minimum support = 0.6, which itemsets are frequent?

**Solutions:**
<details>
<summary>Click to reveal answers</summary>

1. Individual item support:
   - A: appears in T1, T2, T3, T5 → 4/5 = 0.8
   - B: appears in T1, T2, T4, T5 → 4/5 = 0.8  
   - C: appears in T1, T3, T4, T5 → 4/5 = 0.8

2. 2-itemset support:
   - {A,B}: appears in T1, T2, T5 → 3/5 = 0.6
   - {A,C}: appears in T1, T3, T5 → 3/5 = 0.6
   - {B,C}: appears in T1, T4, T5 → 3/5 = 0.6

3. 3-itemset support:
   - {A,B,C}: appears in T1, T5 → 2/5 = 0.4

4. Frequent itemsets (min_support = 0.6):
   - L1: {A}, {B}, {C}
   - L2: {A,B}, {A,C}, {B,C}
   - L3: {} (empty, {A,B,C} has support 0.4 < 0.6)

</details>

---

## Exercise 2: Apriori Algorithm Execution

Using the same database from Exercise 1, manually execute the Apriori algorithm with minimum support = 0.4.

**Steps to complete:**
1. List all candidate 1-itemsets and their support
2. Determine frequent 1-itemsets (L1)
3. Generate candidate 2-itemsets (C2) from L1
4. Calculate support for C2 and determine L2
5. Generate candidate 3-itemsets (C3) from L2
6. Calculate support for C3 and determine L3
7. Try to generate C4 - explain why this stops

**Solution:**
<details>
<summary>Click to reveal step-by-step solution</summary>

**Step 1: Candidate 1-itemsets**
- C1 = {{A}, {B}, {C}}
- Support: A=0.8, B=0.8, C=0.8

**Step 2: Frequent 1-itemsets**
- L1 = {{A}, {B}, {C}} (all ≥ 0.4)

**Step 3: Generate C2**
- C2 = {{A,B}, {A,C}, {B,C}}

**Step 4: Support for C2 and L2**
- {A,B}: 0.6 ≥ 0.4 ✓
- {A,C}: 0.6 ≥ 0.4 ✓  
- {B,C}: 0.6 ≥ 0.4 ✓
- L2 = {{A,B}, {A,C}, {B,C}}

**Step 5: Generate C3**
- C3 = {{A,B,C}} (only one possible combination)

**Step 6: Support for C3 and L3**
- {A,B,C}: 0.4 ≥ 0.4 ✓
- L3 = {{A,B,C}}

**Step 7: Generate C4**
- Cannot generate C4 because we need at least 2 frequent 3-itemsets to create 4-itemsets
- Algorithm terminates

</details>

---

## Exercise 3: Association Rule Generation

Using the frequent itemsets from Exercise 2 (min_support = 0.4), generate all possible association rules with minimum confidence = 0.5.

**For each rule, calculate:**
1. Support
2. Confidence  
3. Lift
4. Determine if the rule meets the minimum confidence threshold

**Itemsets to work with:**
- L2: {{A,B}, {A,C}, {B,C}}
- L3: {{A,B,C}}

**Solution:**
<details>
<summary>Click to reveal detailed calculations</summary>

**From {A,B} (support = 0.6):**
1. A → B: 
   - Confidence = 0.6/0.8 = 0.75 ≥ 0.5 ✓
   - Lift = 0.75/0.8 = 0.9375
2. B → A:
   - Confidence = 0.6/0.8 = 0.75 ≥ 0.5 ✓  
   - Lift = 0.75/0.8 = 0.9375

**From {A,C} (support = 0.6):**
3. A → C:
   - Confidence = 0.6/0.8 = 0.75 ≥ 0.5 ✓
   - Lift = 0.75/0.8 = 0.9375
4. C → A:
   - Confidence = 0.6/0.8 = 0.75 ≥ 0.5 ✓
   - Lift = 0.75/0.8 = 0.9375

**From {B,C} (support = 0.6):**
5. B → C:
   - Confidence = 0.6/0.8 = 0.75 ≥ 0.5 ✓
   - Lift = 0.75/0.8 = 0.9375
6. C → B:
   - Confidence = 0.6/0.8 = 0.75 ≥ 0.5 ✓
   - Lift = 0.75/0.8 = 0.9375

**From {A,B,C} (support = 0.4):**
7. A → {B,C}:
   - Confidence = 0.4/0.8 = 0.5 ≥ 0.5 ✓
   - Lift = 0.5/0.6 = 0.833
8. B → {A,C}:
   - Confidence = 0.4/0.8 = 0.5 ≥ 0.5 ✓
   - Lift = 0.5/0.6 = 0.833
9. C → {A,B}:
   - Confidence = 0.4/0.8 = 0.5 ≥ 0.5 ✓
   - Lift = 0.5/0.6 = 0.833
10. {A,B} → C:
    - Confidence = 0.4/0.6 = 0.667 ≥ 0.5 ✓
    - Lift = 0.667/0.8 = 0.833
11. {A,C} → B:
    - Confidence = 0.4/0.6 = 0.667 ≥ 0.5 ✓
    - Lift = 0.667/0.8 = 0.833
12. {B,C} → A:
    - Confidence = 0.4/0.6 = 0.667 ≥ 0.5 ✓
    - Lift = 0.667/0.8 = 0.833

**All 12 rules meet the minimum confidence threshold!**

</details>

---

## Exercise 4: Threshold Impact Analysis

Consider this transaction database:

```
T1: {Bread, Milk}
T2: {Bread, Eggs}  
T3: {Milk, Eggs}
T4: {Bread, Milk, Eggs}
T5: {Bread}
T6: {Milk}
T7: {Eggs}
T8: {Bread, Milk, Eggs, Butter}
```

**Analysis Tasks:**
1. Calculate support for all possible itemsets
2. Compare results using minimum support thresholds of 0.25, 0.5, and 0.75
3. For each threshold, determine:
   - Which itemsets are frequent
   - How many association rules can be generated (confidence ≥ 0.6)
4. Discuss the trade-offs between different thresholds

**Solution Framework:**
<details>
<summary>Click for guidance on approach</summary>

**Step 1: Calculate all supports**
- Individual items: Bread, Milk, Eggs, Butter
- 2-itemsets: All combinations of items that appear together
- 3-itemsets: {Bread,Milk,Eggs}
- 4-itemsets: {Bread,Milk,Eggs,Butter}

**Step 2: Apply thresholds**
- min_support = 0.25 (2/8 transactions)
- min_support = 0.5 (4/8 transactions)  
- min_support = 0.75 (6/8 transactions)

**Step 3: Count rules**
- For each frequent itemset size ≥ 2, count possible rules
- Check confidence ≥ 0.6 for each rule

**Step 4: Trade-off analysis**
- Higher threshold: Fewer, more reliable patterns
- Lower threshold: More patterns, potentially noisy
- Business context determines optimal threshold

</details>

---

## Exercise 5: Real-World Application

You're analyzing shopping cart data for a small bookstore:

```
T1: {Python_Book, Data_Science_Book, Coffee}
T2: {Python_Book, Coffee, Notebook}
T3: {Data_Science_Book, Coffee, Pen}
T4: {Python_Book, Data_Science_Book, Notebook, Pen}
T5: {Coffee, Notebook}
T6: {Python_Book, Data_Science_Book, Coffee, Notebook}
T7: {Data_Science_Book, Pen}
T8: {Python_Book, Coffee}
```

**Business Questions:**
1. Which items are frequently bought together?
2. If someone buys a Python book, what else are they likely to buy?
3. What product placement recommendations would you make?
4. Which items could be bundled for promotions?

**Analysis Steps:**
1. Calculate frequent itemsets (choose appropriate minimum support)
2. Generate high-confidence association rules
3. Interpret rules for business value
4. Make specific recommendations

**Solution Approach:**
<details>
<summary>Click for business analysis framework</summary>

**Step 1: Choose minimum support**
- Consider: 8 transactions, small bookstore
- Suggested: min_support = 0.375 (3/8) to capture meaningful patterns

**Step 2: Business-focused rule interpretation**
- Look for rules with high confidence AND business sense
- Consider profit margins, inventory turnover
- Identify cross-selling opportunities

**Step 3: Actionable recommendations**
- Product placement: Put frequently associated items near each other
- Bundles: Create packages from strong association rules  
- Inventory: Stock complementary items proportionally
- Marketing: Target customers based on purchase patterns

**Step 4: Monitor and iterate**
- Track success of implemented recommendations
- Adjust thresholds based on business outcomes
- Regularly update analysis with new data

</details>

---

## Challenge Exercise: Algorithm Optimization

**Advanced Challenge:** Implement an optimization to the basic Apriori algorithm.

Choose one optimization to implement:

1. **Hash Tree**: Use hash trees to efficiently count candidate support
2. **Transaction Reduction**: Remove transactions that don't contain frequent itemsets
3. **Subset Checking**: Optimize the subset checking operation
4. **Vertical Data Format**: Use transaction IDs instead of horizontal scanning

**Requirements:**
- Implement your chosen optimization in Python
- Compare performance with the basic algorithm
- Document the trade-offs of your approach
- Test with larger datasets

This challenge helps you understand how frequent pattern mining scales to real-world applications!