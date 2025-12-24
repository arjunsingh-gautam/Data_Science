# **<span style="color:#84a98c">Permutation and Combination</span>**

## **<span style="color:#d62828">First-principle view: what are we actually counting?</span>**

Before formulas, reduce everything to this idea:

Counting problems ask
“How many distinct outcomes are possible **given rules**?”

The rules decide whether:

- order matters → permutation
- order does not matter → combination

All formulas come from **counting choices step by step**.

---

## **<span style="color:#d62828">Permutation from first principles</span>**

### Core question

How many ways can we **arrange** objects?

Order changes the outcome.

ABC ≠ BAC

---

## **<span style="color:#d62828">Deriving permutation formula</span>**

### Example setup

You have n distinct objects.
You want to arrange r of them.

---

### Step-by-step reasoning

First position
You can choose any of the n objects

Second position
One object is used, so n−1 remain

Third position
n−2 remain

Continue until r positions are filled

---

### Multiply choices

By the multiplication principle:

Number of permutations
= n × (n−1) × (n−2) × ... × (n−r+1)

---

### Writing it using factorials

Recall
n! = n × (n−1) × (n−2) × ... × 1

So,

nPr = n! / (n−r)!

This is not a magic formula
It is just removing the extra terms beyond r selections.

---

## **<span style="color:#d62828">Mathematical permutation example</span>**

### Example

How many ways to arrange 3 students out of 5?

Students: A B C D E

Apply formula:

5P3 = 5! / (5−3)!
= 5! / 2!
= (5 × 4 × 3 × 2 × 1) / (2 × 1)
= 5 × 4 × 3
= 60

Order matters
ABC and CBA are counted separately

---

## **<span style="color:#d62828">Combination from first principles</span>**

### Core question

How many ways can we **select** objects?

Order does not matter.

ABC = CBA

---

## **<span style="color:#d62828">Why permutations overcount combinations</span>**

Suppose you select r objects.

For each selection:

- you can arrange them in r! different orders
- but all represent the same combination

So permutations count the same group r! times.

---

## **<span style="color:#d62828">Deriving combination formula</span>**

### Start from permutation count

Permutations of r objects from n:

nPr = n! / (n−r)!

But each combination appears r! times due to orderings.

---

### Remove overcounting

Number of combinations:

nCr = nPr / r!

Substitute permutation formula:

nCr = n! / (r! (n−r)!)

This division removes ordering redundancy.

---

## **<span style="color:#d62828">Mathematical combination example</span>**

### Example

How many ways to choose 3 students from 5?

Apply formula:

5C3 = 5! / (3! 2!)
= (5 × 4 × 3 × 2 × 1) / ((3 × 2 × 1)(2 × 1))
= (5 × 4) / (2 × 1)
= 10

Order does not matter
ABC, BAC, CBA are all the same group

---

## \*\*<span style="color:#d62828">Direct comparison example</span>

### Same data

5 students
Choose 3

Permutation
5P3 = 60
Different arrangements matter

Combination
5C3 = 10
Only the group matters

---

## **<span style="color:#d62828">First-principle summary</span>**

Permutation
Counting sequences
Order matters
Derived by multiplying available choices

Combination
Counting groups
Order does not matter
Derived by removing permutation overcounting

---

## **<span style="color:#d62828">Final mental model</span>**

Permutation asks
“How many different **orders**?”

Combination asks
“How many different **groups**?”

---
