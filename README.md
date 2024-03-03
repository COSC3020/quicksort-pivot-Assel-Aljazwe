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

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

## Answer:

**Defining a Good Pivot**: A good pivot in quicksort is one that roughly divides the array into two equal parts, which would ideally be the median or something close to it. A good pivot maximizes efficiency by minimizing the depth of the recursive calls.

## First-Element Method:
When we choose the first element:

- The probability of it being the median (ideal pivot) is $1/n$ since any of the $n$ elements can be the median.
- The probability of it being a good pivot (defined as being within the middle 50% of the sorted elements) is $1/2$. This is because there's an equal chance of it falling into the lower half or the upper half of the array.

## Median-of-Three Method:
When using the median-of-three method:

- We select the first, middle and last elements of the array segment being sorted.
- Each of these elements has an independent $1/2$ probability of being a good pivot.
- The median of these three will be considered a good pivot unless all three are in the lower 25% or the upper 25% of the array. 
  

### Probability Analysis for Median-of-Three:
Calculating the probability that the median-of-three is a good pivot choice:
- **All Three Elements Are Good Pivots**: The probability is $\left(\frac{1}{2}\right)^3 = \frac{1}{8}$, because each has a $\frac{1}{2}$ chance of being in the desirable middle 50%.
- **Two Elements Are Good Pivots, One is Bad**: There are three combinations for this, each with a probability of $\left(\frac{1}{2}\right)^2 * \left(\frac{1}{2}\right) = \frac{1}{8}$  With three possible combinations, the total probability is $3 \times \frac{1}{8} = \frac{3}{8}$.
- **One Element is a Good Pivot, Two Are Bad**: The median can still be a good pivot if the single good element is the median among the three. There are three combinations for this, each with a probability of $\left(\frac{1}{2}\right) * \left(\frac{1}{2}\right)^2 = \frac{1}{8}$. However, since the good pivot must be the median, we multiply by $\frac{1}{3}$, giving us $3 * \frac{1}{8} * \frac{1}{3} = \frac{1}{8}$

The combined probability of getting a good pivot with the median-of-three method is $\frac{1}{8} + \frac{3}{8} + \frac{1}{8} = \frac{5}{8}$ or 62.5%. This is a simplification and the actual detailed computation considering the distribution of the 'good' pivots and the fixed positions of the first, middle and last elements would result in a percentage closer to the 68.75% mark. 

**Reference**: https://www.khanacademy.org/computing/computer-science/algorithms/quick-sort/a/analysis-of-quicksort#:~:text=By%20the%20median%2C%20we%20mean,You%20can%20go%20even%20further.

## Conclusion

The median-of-three method statistically increases the efficiency of quicksort by increasing the chances of selecting a centrally located pivot, compared to the first-element method. While the first-element method has a 50% chance of picking a good pivot, the median-of-three method improves this probability to about 62.5%. This approach leads to more balanced partitions and helps quicksort achieve its optimal average-case performance of $Θ(n\ log n)$




