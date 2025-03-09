# Lab-1
Prefix Sum Array: Find the sum of elements in a given range [L, R] using a prefix sum array.


python code: 
def prefix_sum_and_range_sums(arr, ranges):
    """
    Constructs the prefix sum array and calculates sums for given ranges.

    Args:
        arr: The input array.
        ranges: A list of tuples, where each tuple represents a range (start, end).

    Returns:
        A tuple containing:
            - The prefix sum array.
            - A list of sums for the given ranges.
    """

    n = len(arr)
    prefix_sum = [0] * n  # Initialize prefix_sum array with zeros

    # Construct the prefix sum array
    prefix_sum[0] = arr[0]  # The first element is the same
    for i in range(1, n):
        prefix_sum[i] = prefix_sum[i - 1] + arr[i]

    range_sums = []
    # Calculate sums for each range
    for start, end in ranges:
        # Note: Adjust indices for 0-based indexing (Python)
        start -= 1  # Subtract 1 to adjust to 0-based indexing
        end -= 1    # Subtract 1 to adjust to 0-based indexing

        if start == 0:
            range_sum = prefix_sum[end]  # Sum from the beginning to 'end'
        else:
            range_sum = prefix_sum[end] - prefix_sum[start - 1] # Sum from 'start' to 'end'

        range_sums.append(range_sum)

    return prefix_sum, range_sums
# Example Usage
arr = [1, 2, 3, 4, 5, 6]
ranges = [(1, 3), (2, 4)]  # Ranges are given as 1-based indices

prefix_sum_array, sums = prefix_sum_and_range_sums(arr, ranges)

print("Prefix Sum Array:", prefix_sum_array)
print("Range Sums:", sums)



