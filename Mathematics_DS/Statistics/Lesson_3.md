# **<span style="color:#84a98c">Events and Experiment</span>**

## **<span style="color:#d62828">️⃣ What is an **Experiment**? (from first principles)</span>**

### First principle:

> An **experiment** is a **controlled way to learn how reality behaves**.

You do an experiment when:

- You **don’t know** how something works
- You **change one thing**
- You **observe what changes because of it**

So at its core:

> **Experiment = intentional change + careful observation**

---

## Why experiments exist (deep reason)

Reality does **not** follow our beliefs or intuition.

So instead of asking:

> “What do I think will happen?”

We ask:

> “What actually happens if I do X?”

That’s an experiment.

---

## Simple real-life example

### Question:

Does watering a plant daily make it grow faster?

### Experiment:

- Plant A → water daily
- Plant B → water once a week
- Keep **everything else same** (sunlight, soil, pot)

### Observation:

After 30 days, compare height.

➡️ You changed **one variable** (water frequency)
➡️ You observed the effect

That’s an experiment.

---

## Key properties of an experiment

| Property           | Why it matters    |
| ------------------ | ----------------- |
| Control            | To isolate cause  |
| Repeatable         | To trust results  |
| Measurable outcome | To avoid opinions |

---

## **<span style="color:#d62828">️⃣ What is an **Event**? (from first principles)</span>**

### First principle:

> An **event** is **something that can happen or not happen**.

That’s it.

No math yet.

---

## Everyday intuition

- “It rains today” → event
- “You get selected in interview” → event
- “Server crashes” → event
- “Coin shows heads” → event

An event is just **an outcome or situation**.

---

## Important detail

An event is **not the action**, it’s the **result**.

- Action: toss a coin
- Event: “coin shows heads”

---

## **<span style="color:#d62828">️⃣ Why “Event” matters in probability</span>**

Probability answers only one thing:

> **How likely is an event to occur?**

Without events, probability has **nothing to talk about**.

---

## Example (coin toss)

Sample space = all possible outcomes
`{Heads, Tails}`

Events:

- Event A = “Heads”
- Event B = “Tails”

Probability:

- P(A) = 1/2
- P(B) = 1/2

---

## **<span style="color:#d62828">️⃣ Experiment vs Event (clear separation)</span>**

| Concept        | What it is                     |
| -------------- | ------------------------------ |
| **Experiment** | The **process** you perform    |
| **Event**      | The **outcome** you care about |

### Example:

- Experiment: roll a die
- Event: “number is even”

---

## **<span style="color:#d62828">️⃣ Why ML/AI fundamentally depends on this</span>**

Machine Learning is **just automated experimentation**.

- You change:

- model architecture
- learning rate
- dataset size

- You observe:

- accuracy
- loss
- generalization

Each training run = **experiment**
Each prediction or outcome = **event**

Probability models:

- “Probability that email is spam”
- “Probability user clicks ad”

➡️ These are probabilities of **events**.

---

## **<span style="color:#d62828">️⃣ Ultra-simple mental model (remember forever)</span>**

- **Experiment** = “Let’s try and see”
- **Event** = “What happened”

Or:

> **We run experiments to estimate the probabilities of events.**

---

## Final takeaway (first-principles sentence)

> An **experiment** is a controlled interaction with reality to learn cause-and-effect.
> An **event** is a specific outcome whose occurrence we care about.

---

# **<span style="color:84a98c">Types of Experiments</span>**

# 0️⃣ First Principle (Foundation)

> An **experiment** is any **repeatable interaction with reality** that produces **one outcome from many possible outcomes**.

Mathematically:

- An experiment produces an outcome
- The outcome belongs to a **sample space** Ω

---

# 1️⃣ Deterministic Experiments

### First principle

> If the **same input always gives the same output**, the experiment is deterministic.

### Example

- 2 + 3 = 5
- Compile a C++ program → same binary
- Sorting an array with a fixed algorithm

### Math

There is **only one possible outcome**.

[
|\Omega| = 1
]

No probability needed.

### Key insight

❌ Not useful for probability
❌ Not useful for ML uncertainty
✅ Used in algorithms and logic

---

# 2️⃣ Random (Stochastic) Experiments

### First principle

> If the outcome is **not predictable with certainty**, the experiment is random.

### Example

- Toss a coin
- Roll a die
- User clicks an ad or not

### Sample space

Coin toss:
[
\Omega = {H, T}
]

### Probability

[
P(H) = 0.5,\quad P(T) = 0.5
]

### Why randomness exists

- Hidden variables
- Noise
- Incomplete information

---

# 3️⃣ Simple Experiments

### First principle

> An experiment with **one trial**.

### Example

- Tossing a coin once
- Rolling a die once

### Math

One outcome ω ∈ Ω

### ML analogy

Single prediction:
[
P(y=1|x)
]

---

# 4️⃣ Compound Experiments

### First principle

> An experiment made of **multiple simple experiments**.

### Example

Tossing two coins

### Sample space

[
\Omega = {HH, HT, TH, TT}
]

### Event example

Event A = “at least one head”

[
A = {HH, HT, TH}
]

[
P(A) = \frac{3}{4}
]

---

# 5️⃣ Bernoulli Experiment (Very Important)

### First principle

> An experiment with **exactly two outcomes**: success or failure.

### Outcomes

[
\Omega = {0,1}
]

### Parameter

[
P(X=1)=p,\quad P(X=0)=1-p
]

### Examples

- Coin toss
- Email spam or not
- User clicks ad or not

### ML

Logistic regression models Bernoulli trials.

---

# 6️⃣ Binomial Experiment

### First principle

> Repeating a **Bernoulli experiment n times independently**.

### Conditions

1. Fixed number of trials n
2. Each trial independent
3. Same success probability p

### Random variable

X = number of successes

### Probability mass function

[
P(X=k) = \binom{n}{k} p^k (1-p)^{n-k}
]

### Example

10 coin tosses, probability of exactly 6 heads.

---

# 7️⃣ Multinomial Experiment

### First principle

> Extension of binomial to **more than two outcomes**.

### Example

Roll a die n times.

Outcomes:
[
\Omega = {1,2,3,4,5,6}
]

### Random vector

[
(X_1, X_2, ..., X_6)
]

### Probability

[
P = \frac{n!}{x_1!x_2!...x_6!} \prod_{i=1}^{6} p_i^{x_i}
]

### ML

Softmax classification.

---

# 8️⃣ Continuous Experiments

### First principle

> Outcomes lie on a **continuous range**.

### Example

- Temperature
- Time taken by algorithm
- Stock price

### Sample space

[
\Omega \subset \mathbb{R}
]

### Probability

[
P(X=x) = 0
]

We use **density**:
[
P(a \le X \le b) = \int_a^b f(x) dx
]

---

# 9️⃣ Controlled Experiments

### First principle

> You deliberately control variables to isolate cause.

### Example

A/B testing:

- Group A → old UI
- Group B → new UI

### Hypothesis

[
H_0: \mu_A = \mu_B
]

### Test

t-test, z-test

### ML

Hyperparameter tuning.

---

# 🔟 Observational Experiments

### First principle

> You **observe without intervention**.

### Example

- Medical studies
- User behavior logs

### Problem

Correlation ≠ causation

### Tool

Regression, causal inference.

---

# 1️⃣1️⃣ Thought Experiments

### First principle

> Experiments performed **in the mind** to test logic.

### Example

- Schrödinger’s cat
- Trolley problem

Used to:

- Expose contradictions
- Build theory

---

# 1️⃣2️⃣ Simulation Experiments

### First principle

> Experiments run on **models instead of reality**.

### Example

Monte Carlo simulation.

### Math

Repeat random sampling:
[
\hat{P}(A) = \frac{\text{count(A)}}{N}
]

### ML

Training on synthetic data.

---

# 1️⃣3️⃣ Adaptive Experiments

### First principle

> Experiment design changes **based on previous outcomes**.

### Example

- Multi-armed bandit
- Reinforcement learning

### Update rule

[
Q_{t+1} = Q_t + \alpha(R_t - Q_t)
]

---

# 1️⃣4️⃣ Causal Experiments

### First principle

> Designed to answer **“what caused what?”**

### Tools

- Randomized controlled trials
- Do-calculus

### Notation

[
P(Y|do(X))
]

---

# Mental Summary Table

| Type          | Key idea          |
| ------------- | ----------------- |
| Deterministic | No uncertainty    |
| Random        | Uncertain outcome |
| Bernoulli     | Yes/No            |
| Binomial      | Many Bernoulli    |
| Multinomial   | Many outcomes     |
| Continuous    | Infinite outcomes |
| Controlled    | Intervention      |
| Observational | Passive           |
| Simulation    | Artificial        |
| Adaptive      | Learns            |
| Causal        | Cause–effect      |

---

# Final First-Principles Insight

> **All experiments exist to map actions → outcomes → uncertainty.**
> Probability quantifies uncertainty.
> Statistics estimates truth from experiments.
> ML automates experiments at scale.

---

# <span style="color:#84a98c"> Types of Events</span>\*\*

# 0️⃣ First Principle: What is an Event?

> An **event** is a **set of outcomes** we care about.

That’s it.

Not magic.
Not random by itself.
Just a **subset** of possible outcomes.

---

## Mathematical foundation

Let:

- Ω = **sample space** (all possible outcomes)
- ω = a **single outcome**
- E ⊆ Ω = **event**

If the outcome ω ∈ E → the event **occurs**.

---

# 1️⃣ Simple (Elementary) Event

### First principle

> An event containing **exactly one outcome**.

### Math

[
|E| = 1
]

### Example (die roll)

[
\Omega = {1,2,3,4,5,6}
]

Event:
[
E = {4}
]

[
P(E) = \frac{1}{6}
]

### Meaning

“One very specific thing happens.”

---

# 2️⃣ Compound Event

### First principle

> An event containing **more than one outcome**.

### Math

[
|E| > 1
]

### Example

Event = “even number”

[
E = {2,4,6}
]

[
P(E) = \frac{3}{6} = \frac{1}{2}
]

---

# 3️⃣ Certain (Sure) Event

### First principle

> An event that **must happen**.

### Math

[
E = \Omega
]

[
P(E) = 1
]

### Example

Rolling a die gives a number ≤ 6.

---

# 4️⃣ Impossible Event

### First principle

> An event that **cannot happen**.

### Math

[
E = \varnothing
]

[
P(E) = 0
]

### Example

Rolling a 7 on a die.

---

# 5️⃣ Complementary Event

### First principle

> “Event does NOT happen.”

### Math

If E is an event:
[
E^c = \Omega \setminus E
]

[
P(E^c) = 1 - P(E)
]

### Example

Event: Even number
Complement: Odd number

---

# 6️⃣ Mutually Exclusive (Disjoint) Events

### First principle

> Two events **cannot happen together**.

### Math

[
A \cap B = \varnothing
]

[
P(A \cup B) = P(A) + P(B)
]

### Example

Event A = “roll 2”
Event B = “roll 5”

---

# 7️⃣ Non-Mutually Exclusive Events

### First principle

> Events that **can happen together**.

### Math

[
A \cap B \neq \varnothing
]

[
P(A \cup B) = P(A) + P(B) - P(A \cap B)
]

### Example

A = “even number”
B = “number > 3”

Intersection:
[
A \cap B = {4,6}
]

---

# 8️⃣ Independent Events

### First principle

> One event **does not affect** the probability of the other.

### Math

[
P(A \cap B) = P(A)P(B)
]

### Example

Two coin tosses:

- A = “first toss is head”
- B = “second toss is head”

---

# 9️⃣ Dependent Events

### First principle

> One event **changes the probability** of another.

### Math

[
P(A \cap B) = P(A)P(B|A)
]

### Example

Drawing cards **without replacement**.

---

# 🔟 Conditional Event

### First principle

> Probability of an event **given** another event occurred.

### Math

[
P(A|B) = \frac{P(A \cap B)}{P(B)}
]

### ML

Posterior probability.

---

# 1️⃣1️⃣ Equally Likely Events

### First principle

> All outcomes have **same probability**.

### Math

[
P(E) = \frac{|E|}{|\Omega|}
]

### Example

Fair dice.

---

# 1️⃣2️⃣ Exhaustive Events

### First principle

> A set of events that **covers the entire sample space**.

### Math

[
\bigcup_i E_i = \Omega
]

### Example

Odd or even.

---

# 1️⃣3️⃣ Favorable Events

### First principle

> Outcomes that **support your goal**.

### Math

[
P = \frac{\text{favorable outcomes}}{\text{total outcomes}}
]

### Example

Getting a head.

---

# 1️⃣4️⃣ Random Event

### First principle

> Event whose occurrence is **uncertain**.

### Math

[
0 < P(E) < 1
]

---

# 1️⃣5️⃣ Rare Event

### First principle

> Event with **very small probability**.

### Example

System failure.

---

# 1️⃣6️⃣ Joint Event

### First principle

> Multiple events occurring together.

### Math

[
A \cap B
]

### ML

Joint distribution.

---

# 1️⃣7️⃣ Marginal Event

### First principle

> Probability of one event **ignoring others**.

### Math

[
P(A) = \sum_B P(A,B)
]

---

# 1️⃣8️⃣ Continuous Events

### First principle

> Event defined over **intervals**.

### Math

[
P(a \le X \le b) = \int_a^b f(x)dx
]

### Important

[
P(X=x) = 0
]

---

# 🔚 Ultimate First-Principles Summary

> **Events are just sets.**
> Probability is a **measure on sets**.
> All rules come from **set theory + logic**.

---

## One sentence to remember forever

> **If you understand sets, you understand events.**

---

# **<span style="color:#84a98c">Counting Principle</span>**

# 1️⃣ First Principle: Why counting exists at all

Probability always starts with this ratio:

[
P(\text{event}) = \frac{\text{number of favorable outcomes}}{\text{number of possible outcomes}}
]

So the **core problem** is:

> How many outcomes are possible?

**Counting principles exist to answer that question efficiently.**

---

# 2️⃣ What is a Counting Principle (from first principles)

> A **counting principle** is a logical rule that lets us count outcomes **without listing them one by one**.

Counting is about **structure**, not numbers.

---

# 3️⃣ Fundamental Counting Principle (Product Rule)

### First principle idea

> If a process happens in **stages**, and
> each stage has **independent choices**,
> then total outcomes = product of choices.

---

### Mathematical statement

If:

- Step 1 has ( n_1 ) choices
- Step 2 has ( n_2 ) choices
- …
- Step k has ( n_k ) choices

Then:
[
\text{Total outcomes} = n_1 \times n_2 \times \cdots \times n_k
]

---

### Example (simple)

Outfit selection:

- Shirts: 3
- Pants: 2

Total outfits:
[
3 \times 2 = 6
]

Why this works:

- For **each shirt**, you can pair **every pant**
- Choices don’t restrict each other

---

### Experiment view

Experiment = “choose shirt → choose pant”
Each path is a **distinct outcome**

---

# 4️⃣ Sum Rule (Addition Principle)

### First principle idea

> If outcomes come from **mutually exclusive cases**, add them.

---

### Mathematical statement

If:

- Case A has ( n_1 ) outcomes
- Case B has ( n_2 ) outcomes
- A and B **cannot happen together**

Then:
[
\text{Total outcomes} = n_1 + n_2
]

---

### Example

Choose transport:

- Bus: 5 routes
- Train: 3 routes

Total:
[
5 + 3 = 8
]

Why not multiply?
Because you **choose only one**, not both.

---

# 5️⃣ Why counting principles work (deep reason)

Counting principles rely on **two hidden assumptions**:

1. **Clear structure** (steps or cases)
2. **No overlap or ambiguity**

If either breaks → counting breaks.

---

# 6️⃣ Where counting CAN be applied (conditions)

Counting works **if and only if** all of these are true:

---

## ✅ Condition 1: Finite outcomes

Counting requires:
[
|\Omega| < \infty
]

### Example

- Dice rolls
- Passwords of fixed length

❌ Not valid:

- Time
- Real numbers
- Continuous measurements

---

## ✅ Condition 2: Well-defined outcomes

Each outcome must be:

- Distinct
- Counted exactly once

Example:

- “HT” ≠ “TH” (order matters)

If outcomes blur → counting fails.

---

## ✅ Condition 3: Independence OR controlled dependence

You must know whether:

- Choices are independent
- Or restricted (and how)

Example:

- With replacement → independent
- Without replacement → restricted

If restrictions exist but are **known**, counting still works.

---

## ✅ Condition 4: Equal likelihood (for probability use)

Counting alone gives **counts**, not probabilities.

To use:
[
P = \frac{\text{count}}{\text{total}}
]

You need **uniform probability**.

---

# 7️⃣ Counting techniques (when conditions hold)

### Permutations (order matters)

[
nPr = \frac{n!}{(n-r)!}
]

Example:
Arranging 3 students out of 5.

---

### Combinations (order doesn’t matter)

[
nCr = \frac{n!}{r!(n-r)!}
]

Example:
Choosing a committee.

---

### With repetition allowed

Passwords, sequences, etc.

[
n^r
]

---

# 8️⃣ Where counting FAILS (constraints & limitations)

Now the **most important part**.

---

## ❌ Limitation 1: Outcomes are infinite

### Example

Pick a random real number between 0 and 1.

How many outcomes?
[
\infty
]

Counting gives:
[
\frac{1}{\infty} \quad \text{(meaningless)}
]

### Why counting fails

Counting assumes **discrete outcomes**.
Here outcomes are **continuous**.

👉 We use **integration**, not counting.

---

## ❌ Limitation 2: Outcomes are not equally likely

### Example

Rolling a biased die.

Counting says:

- 6 outcomes → probability = 1/6

Reality:

- Outcomes have different weights

### Why counting fails

Counting assumes **uniform probability**.

👉 Use **probability distributions**, not counting.

---

## ❌ Limitation 3: Dependencies are unknown or complex

### Example

Human behavior:

- Clicking ads
- Stock movement

You cannot say:
[
\text{choices} = n_1 \times n_2
]

Because choices influence each other in unknown ways.

👉 Use statistics / ML.

---

## ❌ Limitation 4: Overlapping cases (double counting)

### Example

Students who play:

- Cricket: 30
- Football: 25
- Both: 10

Naive count:
[
30 + 25 = 55 \quad ❌
]

Correct:
[
30 + 25 - 10 = 45
]

### Root problem

Counting assumes **disjoint sets**.
Overlap breaks naive addition.

---

## ❌ Limitation 5: Outcomes not clearly defined

### Example

“How many ways can a company succeed?”

Ambiguous.
No fixed sample space.
No clear outcomes.

👉 Counting is impossible.

---

# 9️⃣ Why counting is still foundational

Even with limitations:

- Probability starts with counting
- Distributions generalize counting
- ML replaces counting with estimation

Counting is **discrete probability’s backbone**.

---

# 🔚 Ultimate First-Principles Summary

### Counting works when:

- Outcomes are **finite**
- Outcomes are **clearly defined**
- Probabilities are **uniform**
- Dependencies are **known**

### Counting fails when:

- Outcomes are infinite
- Probabilities differ
- Dependencies are unknown
- Overlaps exist
- Outcomes are vague

---

## One sentence to remember forever

> **Counting is probability without uncertainty — once uncertainty appears, counting alone collapses.**

---

# **<span style="color:#84a98c">Addition and Multiplicaton Rule</span>**

# 0️⃣ First Principle Behind Counting Rules

Before rules, understand this:

> **Counting is about partitioning reality into non-overlapping possibilities.**

Everything comes down to:

- **Are choices alternative (OR)?**
- **Are choices sequential (AND)?**

That’s it.

---

# 1️⃣ Addition Rule (Sum Rule)

## First-Principles Idea

> Use the **Addition Rule** when **only ONE of several alternatives can happen**.

In plain language:

- “This **OR** that”
- Not “this **AND** that”

---

## Mathematical Statement

If:

- Set A has |A| outcomes
- Set B has |B| outcomes
- A and B are **mutually exclusive**

Then:
[
|A \cup B| = |A| + |B|
]

---

## Why this is true (deep logic)

Because:

- No outcome belongs to both A and B
- No outcome is counted twice

Counting = safe addition.

---

## Example 1: Simple (transport)

You travel **either** by:

- Bus (4 routes)
- Train (3 routes)

Total ways:
[
4 + 3 = 7
]

Why not multiply?
Because you choose **one mode only**, not both.

---

## Example 2: Mathematical (dice)

Die roll:
[
\Omega = {1,2,3,4,5,6}
]

Let:

- A = even numbers = {2,4,6}
- B = odd numbers = {1,3,5}

[
|A \cup B| = 3 + 3 = 6
]

---

## When Addition Rule FAILS

### Overlapping sets

Example:

- A = multiples of 2 = {2,4,6}
- B = multiples of 3 = {3,6}

Naive:
[
3 + 2 = 5 \quad ❌
]

Correct:
[
|A \cup B| = |A| + |B| - |A \cap B|
]

[
= 3 + 2 - 1 = 4
]

This leads to **inclusion–exclusion**.

---

# 2️⃣ Multiplication Rule (Product Rule)

## First-Principles Idea

> Use the **Multiplication Rule** when an outcome is formed by **sequential independent choices**.

In plain language:

- “This **AND** that”
- Step-by-step construction

---

## Mathematical Statement

If:

- Step 1 has (n_1) choices
- Step 2 has (n_2) choices
- …
- Step k has (n_k) choices

Then:
[
\text{Total outcomes} = n_1 \times n_2 \times \cdots \times n_k
]

---

## Why this is true (deep logic)

For **every choice** in step 1,
you can pair **every choice** in step 2,
and so on.

This creates a **Cartesian product**.

---

## Example 1: Outfit selection

- Shirts: 3
- Pants: 2
- Shoes: 2

Total outfits:
[
3 \times 2 \times 2 = 12
]

Each outfit is:
[
(\text{shirt}, \text{pant}, \text{shoe})
]

---

## Example 2: Dice (two throws)

Die has 6 outcomes.

Two throws:
[
6 \times 6 = 36
]

Each outcome:
[
(1,1), (1,2), ..., (6,6)
]

---

## Restricted Multiplication (Without replacement)

Example:
Arrange 3 students from 5.

- First position: 5 choices
- Second: 4
- Third: 3

[
5 \times 4 \times 3 = 60
]

Dependence exists, but **known**.

---

# 3️⃣ Addition vs Multiplication (Decision Rule)

Ask this ONE question:

> **Am I choosing between alternatives, or building a sequence?**

| Situation   | Rule           |
| ----------- | -------------- |
| A **OR** B  | Addition       |
| A **AND** B | Multiplication |

---

# 4️⃣ Combined Use (Real problems)

### Example: Password

- Must start with letter (26)
- Then 3 digits (10 each)

Total:
[
26 \times 10^3 = 26{,}000
]

Multiplication inside
Addition only if alternative formats exist.

---

# 5️⃣ Common Mistakes (very important)

### Mistake 1: Multiplying alternatives

“Bus or Train” → ❌ multiply

### Mistake 2: Adding sequential choices

“Shirt AND pant” → ❌ add

### Mistake 3: Ignoring overlap

For addition, always check:
[
A \cap B = \varnothing ?
]

---

# 6️⃣ First-Principles Summary

### Addition Rule:

> Use when **choices are mutually exclusive alternatives**

[
|A \cup B| = |A| + |B|
]

---

### Multiplication Rule:

> Use when outcomes are formed by **sequential choices**

[
|\Omega| = \prod n_i
]

---

## One sentence to remember forever

> **OR → add. AND → multiply.**
> (Only when outcomes don’t overlap.)

---
