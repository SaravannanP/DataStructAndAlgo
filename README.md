# Data Structure and Algorithms in JAVA
Could be doing 75 or 150 qns . Havent decided yet
## Understand the problem dont memorize solutions

1.  Bruteforce method first

2.  Optimizes solution second 

3.  Time and Space Complexity

## Arrays & Hashing
### Contains Duplicate
Given an integer array nums, return true if any value appears more than once in the array,
otherwise return false.

    public static void main(String[] args)
	{
		int [] nums = {1, 2, 3, 3};
		int [] nums2 = {1, 2, 3, 4};
		
		System.out.println(hasDuplicate(nums));
		System.out.println(hasDuplicate(nums2));
	}


Brute Force:

    public class Solution
    {
        public static boolean hasDuplicate(int[] nums)
        {
          // Assume nums Array is unsorted
          for(int i = 0; i < nums.length;i++)
          {
              for(int j = i + 1; j < nums.length;j++)
              {
                  if(nums[i] == nums[j])
                  {
                      return true;
                  }
              }
          }
              return false;
          }        
    }
             
Optimised Solution: 

    public class Solution 
    {
        public static boolean hasDuplicate(int[] nums)
        {
            Set<Integer> dup = new Set<>();
            for(int num : nums)
            {
              if(dup.contains(num))
              {
                  return true;
              }
              dup.add(num);
            }
            return false;
        }
    }

### Valid Anagram
Given two strings s and t, return true if the two strings are anagrams of each other, otherwise return false.

An anagram is a string that contains the exact same characters as another string, but the order of the characters can be different.

### Two Sum 
### Group Anagrams
### Top K Frequent Elements 
### Encode and Decode Strings 
### Product of Array Except Self 
### Longest Consecutive Sequence  










