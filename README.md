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

The role of pivot selection in the quicksort algorithm's performance is vital. A well-chosen pivot can significantly improve the efficiency of quicksort, ensuring a balanced partition and ensuring the algorithm operates at it's typical average-case time complexity of $O(n\ log n)$. On the other hand, a consistently poor pivot choice can worsen quicksort's performance to $O(n^2), particularly found in arrays that are already sorted or nearly sorted.

### Pivot Selection Methods:
**Leftmost Element as Pivot**:
Opting for the leftmost element as the pivot is the simplest strategy. It's straightforward to implement and requires minimal computation.

- **Pros**: It's incredibly fast to determine since it involves no additional logic or calculations.
- **Cons**: Its major drawback is its vulnerability to the array's initial order. In nearly sorted arrays, this method can lead to highly unbalanced partitions, significantly slowing down the sorting process.

**Median-of-Three Method**:
This approach involves examining the first, middle, and last elements of the array (or subarray) and selecting the median of these three values as the pivot.

- **Pros**: By considering three strategically positioned elements, this method reduces the likelihood of selecting an extreme value as the pivot, allowing more balanced partitions.
- **Cons**: While this method is better at avoiding bad choices for the pivot compared to just picking the first item, it does introduce a slight computational overhead due to the additional steps required to identify the median of the three.

### Probability Analysis:
- **First Element as Pivot**: The probability that the first element is a good pivot is 50%. This is based on the equal chance of the first element falling into the less desirable extremes or the more advantageous middle range of values in a randomly ordered array.
- **Median-of-Three**: This method has a higher probability of achieving a good pivot, at a 68.75% probability, thus significantly increasing the chances of a balanced partition. This is largely due to the method's design of considering three strategically placed elements in the array (first, middle, last) to reduce the chances of an extreme value as a pivot.

### Comparing the Methods:
The median-of-three method;s higher probability of selecting a good pivot, at 68.75%, compared to the 50% chance with the first element, shows its effectiveness in improving quicksort's performance. This improved probability is a result of the method's design to avoid choosing a pivot from the array's extremes, thus reducing the likelihood of unbalanced partitions that lead to increased recursion depth and worse performance.

Choosing the median from three points (first, middle and last elements) maintains a good balance between keeping things simple and ensuring the sort works well. Even though it takes a bit longer to pick the pivot this way than just taking the first element, the extra step proves to be worth it as it helps avoid the slowdowns that occur with bad pivots. 

We can make the process of picking a pivot in quicksort even better by increasing the number of elements from which we select the median pivot. For example, if you pick 5 elements at random and use the middle one as the pivot, your chances of getting a good, balanced split go up to about 79.3% (203 out of 256 chances). Choose 7 elements, and those chances increase to around 85.9% (1759 out of 2048 chances). With 9 elements, the likelihood goes up to about 90.2% (59123 out of 65536 chances), and with 11 elements, it reaches roughly 93.1% (488293 out of 524288 chances).

**Reference**: https://www.khanacademy.org/computing/computer-science/algorithms/quick-sort/a/analysis-of-quicksort#:~:text=By%20the%20median%2C%20we%20mean,You%20can%20go%20even%20further.

This shows that the more elements you consider for picking the median, the better your odds of splitting the list evenly, which helps quicksort work more efficiently. **However**, you also need to think about the extra time it takes to pick and calculate the median from more elements. As the number of elements increases, so does the computational effort required, which could potentially offset the benefits of more balanced partitions.  Finding the right balance is key: this means carefully weighing the benefits of a potentially perfect pivot through a larger sample against the additional computational time it requires, to maintain the overall efficiency of the sorting operation.

### Conclusion: 
In summary, choosing the median-of-three method as the pivot selection method in quicksort turns out to be a pretty smart choice. It finds a good middle ground between simplicity of implementation and ensuring time-efficient array partitioning. By sampling three points within the array to determine the pivot, it reduces the risk of running into problems caused by bad pivot choices. The median-of-three approach doesn't just make it more likely to split the list evenly but also helps quicksort handle different kinds of input conditions (randomly sorted, nearly sorted arrays etc.), thus making it a solid choice for fast and dependable sorting.






