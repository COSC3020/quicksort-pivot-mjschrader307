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

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

---

I am going to define a "good" pivot as one that falls in the middle 50% of the distribution of elements in the array. This is because those values should be fairly close to the median value of the array, which should split the array roughly in half as a pivot.

I would guess that for an arbitrary, uniformly-random array of numbers, about half of the elements would be considered "good" pivots, because that many would be in the middle 50% of the distribution.

I'm going to let the event G be the event that the element is a good pivot, and the event N be the event that it is not. With my definition of a "good" pivot, the probability of any element being a good pivot is given by $P(G) = \frac{1}{2}$ and, since the element is either good or it's not, the probability that it is not is given by $P(N) = 1 - P(G) = \frac{1}{2}$. These probabilities apply to all elements.

Therefore, the probability of having the first element of the array be a good pivot is $\frac{1}{2}$, assuming the array is random. 

If picking three elements at random from the array, there are $2^3$ or 8 possible outcomes, in terms of whether each of them individually are good pivots or not:

$S =$ {$(G,G,G), (G,G,N), (G,N,G), (N,G,G), (G,N,N), (N,N,G), (N,G,N), (N,N,N)$}

Four scenarios of a certain number of good pivots in sample of three elements:

| Exact Number of Good Pivots | Probability           |
| ------------ | --------------------- |
| 0            | $\frac{1}{8} = 12.5$% |
| 1            | $\frac{3}{8} = 37.5$% |
| 2            | $\frac{3}{8} = 37.5$% |
| 3            | $\frac{1}{8} = 12.5$% |

### Case 1: No Good Pivots in Sample

Fix elements like so: A = N, B = N, C = N

Obviously, there is no ordering of A, B, and C where the middle value is a good pivot, so the probability for this case is 0%

### Case 2: One Good Pivot in Sample

Fix elements: A = G, B = N, C = N

Six possible orderings:

| Ordering  | Middle Value |
| --------- | ------------ |
| A < B < C | B = N        |
| A < C < B | C = N        |
| B < A < C | A = G        |
| B < C < A | C = N        |
| C < A < B | A = G        |
| C < B < A | B = N        |
2 ways out of 6 that the middle value is a good pivot: probability is $\frac{1}{3}$

This end probability is the same for if B = G and if C = G.

### Case 3: Two Good Pivots in Sample

Fix elements: A = G, B = G, C = N

Same 6 orderings:

| Ordering  | Middle Value |
| --------- | ------------ |
| A < B < C | B = G        |
| A < C < B | C = N        |
| B < A < C | A = G        |
| B < C < A | C = N        |
| C < A < B | A = G        |
| C < B < A | B = G        |

4 ways out of 6 that the middle value is good pivot: probability is $\frac{2}{3}$

### Case 4: All Three are Good Pivots

Obviously, if all three elements are good pivots, the median should be good also. Probability is 100%


### Conclusion

Using the Law of Total Probability:

$P(\text{Good Pivot using Median of Three}) = \frac{1}{8}(0) + \frac{3}{8}(\frac{1}{3}) + \frac{3}{8}(\frac{2}{3}) + \frac{1}{8}(1) = 0 + \frac{3}{24} + \frac{6}{24} + \frac{3}{24} = \frac{15}{24} = \frac{5}{8} = 0.625$

Therefore, I have come to the conclusion that for a random array, there is a 62.5% chance that the Median of Three procedure produces a good pivot element, which is quite better than just picking one element and hoping it's good (50% chance)

---

**I certify that I have listed all sources used to complete this exercise, including the use
of any Large Language Models. All of the work is my own, except where stated
otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is
suspected, charges may be filed against me without prior notice.**