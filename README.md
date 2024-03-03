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
- The median of these three will be considered a good pivot unless all three are in the lower 25% or the upper 25% of the array. The probability of this happening is $(1/4)^3$ + $(1/4)^3$ for the lower and upper extremes.
  
    (**Simplification**: if an array is divided into four equal quartiles. 1/4 represents the probability of any single element to fall into one of the four quartiles. Typically we would want the element to fall into the second or third quartile - the middle 50% - for it to be considered a good pivot.)

### Probability Analysis:
Calculating the probability that the median-of-three is not a good pivot choice:
- Probability that all three elements are in the lower quartile: $(1/4)^3$
- Probability that all three elements are in the upper quartile: $(1/4)^3$
- Combined probability of both scenarios occuring: $2 * (1/4)^3 = 1/32$

This means the probability that the median-of-three method results in a good pivot choice is $1 - 1/32 = 31/32$, which is significantly higher than the $1/2$ probability when choosing the first element.

**Conclusion**:
The median-of-three method has a significantly higher probability of choosing a good pivot in comparison to the first-element method. The median-of-three method increases the likelihood of dividing the array into two equal parts, leading  to a more efficient quicksort with fewer comparisons and swaps on average. Thus allowing quicksort to achieve its average-case complexity of $Θ(nlogn)$.



