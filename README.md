[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/IF3rQO50)

# Quicksort Pivots

in the lectures I only briefly mentioned strategies for determining a good pivot
for quicksort. The implementation on the slides simply picks the leftmost
element in the part of the array that we consider as a pivot. I also mentioned a
few other ways of picking a good pivot, e.g. randomly.

Median-of-three is also a good way of picking a pivot -- inspect the first,
middle, and last elements of the part of the array under consideration and
choose the median value. Using the probabilities for picking a pivot in a
particular part of the array (in the same way as we did on slide 34), argue
whether this method is more or less (or equally) likely to pick a good pivot
compared to simply choosing the first element. Assume that all permutations are
equally likely, i.e. the input array is ordered randomly.

Your answer must derive probabilities for choosing a good pivot and
quantitatively reason with them.

## Analysis

### Given Info

From the slide in **01-sorting.pdf pg34** we know that the probability of selecting a random element which is a **good** pivot is simply $1/2 = 0.5$. We also know that the probability of selecting a random pivot which is **large** is $1/4 = 0.25$ and the same is true for **small** pivot being selected.

| Method                                     | Probability              |
| ------------------------------------------ | ------------------------ |
| Probability of selecting a **good** pivot  | $ P(G) = \frac12 = 0.50$ |
| Probability of selecting a **small** pivot | $ P(S) = \frac14 = 0.25$ |
| Probability of selecting a **large** pivot | $ P(L) = \frac14 = 0.25$ |

### Leftmost Selection

The probability of selecting a **good** pivot point is given as $P(G) = 0.5 = 50$%. This is the probability of selecting the leftmost pivot and it being good aswell.

### Median-Of-Three Selection

The **median-of-three** requires us to select 3 specific pivot positions in the array we are considering. This means we will always select the **first**, **middle**, and **last** index as the possible pivot positions. We then select the median value between the three as the new pivot position.

To analize the probability let's consider all the possible outcomes of ordering these 3 pivot combinations.

1. We can have an ordering of _all_ **good** orderings. There is only one way to do this.

   $G \times G \times G$

1. We can have an ordering of _mostly_ **good** with a single _small_ or _large_. There are a total of 6 possible orderings for this.

   $S \times G \times G$

   $G \times S \times G$

   $G \times G \times S$

   $L \times G \times G$

   $G \times L \times G$

   $G \times G \times L$

1. Lastly there is the case where there exists only one ordering with a single **good** pivot position. The rest are either **small** or **large**. There exist 6 ways to generate these orderings.

   $G \times S \times L$

   $G \times L \times S$

   $S \times L \times G$

   $S \times G \times L$

   $L \times S \times G$

   $L \times G \times S$

Therefore the probability of selecting a good pivot position is the sum of the three cases:

$P(G) = P(Case1) + P(Case2) + P(Case3)$

$P(G) = 1(\frac12)(\frac12)(\frac12) + 6(\frac12)(\frac14)(\frac12) + 6(\frac14)(\frac12)(\frac14)$

$P(G) = 0.125 + 0.375 + 0.1875$

$P(G) = 0.6875 = 68.75$%

Therefore we can conclude that between the methods **median-of-three** and **first-element**, on average the best choice for selecting a pivot point is by using **median-of-three**.
