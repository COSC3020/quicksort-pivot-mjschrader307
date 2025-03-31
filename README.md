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

I happen to be taking a Probability course right now, which is good for this.

I am going to define a "good" pivot as one that falls in the middle 50% of the distribution of elements in the array. This is because those values should be fairly close to the median value of the array, which should split the array roughly in half as a pivot.

I would guess that for an arbitrary, uniformly-random array of numbers, about half of the elements would be considered "good" pivots, because that many would be in the middle 50% of the distribution.

I'm going to let the event G be the event that the element is a good pivot, and the event N be the event that it is not. With my definition of a "good" pivot, the probability of any element being a good pivot is given by $P(G) = \frac{1}{2}$ and, since the element is either good or it's not, the probability that it is not is given by $P(N) = 1 - P(G) = \frac{1}{2}$. These probabilities apply to all elements.

Therefore, the probability of having the first element of the array be a good pivot is $\frac{1}{2}$, assuming the array is random. 

If picking three elements at random from the array, there are $2^3$ or 8 possible outcomes, in terms of whether each of them individually are good pivots or not:

${(G, G, G), (N, G, G), (G, N, G), (G, G, N), (N, N, G), (N, G, N), (G, N, N), (N, N, N)}$

The probabilities of having a certain amount of good pivots, using the above set:

| Number of good pivots | Probability |
| --- | --- |
| 0 | $\frac{1}{8} = 12.5$ % |
| 1+ | $\frac{7}{8} = 87.5$ % |
| 2+ | $\frac{4}{8} = 50$ % |
| 3 | $\frac{1}{8} = 12.5$ % |

I'm not sure how to calculate the exact theoretical probability of having the median of any of those orderings be a good pivot, but I would imagine it falls between 50% and 87.5%. 

Either way, that value (representing the probability that the median of three is a good pivot) is higher than the probability of picking one random element and hoping it is a good pivot. 

--- 

**I certify that I have listed all sources used to complete this exercise, including the use
of any Large Language Models. All of the work is my own, except where stated
otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is
suspected, charges may be filed against me without prior notice.**