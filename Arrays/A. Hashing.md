# HASHING CONCEPTS

## QUESTIONS
| Question | Level | Last Solved | Next Solved |
|----------|-------|-------------|-------------|
| [Identify the largest Outlier in the array (3371)](https://leetcode.com/problems/identify-the-largest-outlier-in-an-array/description/) | Medium | 12-07-2026 | 19-07-2026 |
| [Group Anagrams (49)](https://leetcode.com/problems/group-anagrams/description/) | Medium | 05-08-2026 | 12-08-2026 |
| [Longest Consecutive Sequence (128)](https://leetcode.com/problems/longest-consecutive-sequence/) | Medium | 05-08-2026 | 12-08-2026 |
| [Valid Anagram (217)](https://leetcode.com/problems/valid-anagram/description/) | Easy | 07-08-2026 | 14-08-2026 |


## HASH(SUM, INDEX)
1. This technique is useful when you wish to find longest subarray with sum as K.
2. The idea behind it is to hash (sum, index) during iteration inorder to find the sum K which might exists if totalSum-K exists in the hashmap.
3. Since we need to find the longest subarray there may be a possibility that same sum exists at different indexes. In this case we do not update the (sum, index) entry if the index is higher than the entry's index.