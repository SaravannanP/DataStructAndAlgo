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

Example 1:

 	Input: nums = [1, 2, 3, 3]
	Output: true
Example 2:

	Input: nums = [1, 2, 3, 4]
	Output: false

Main Method:

    public static void main(String[] args)
	{
		int [] nums = {1, 2, 3, 3};
		int [] nums2 = {1, 2, 3, 4};
		
		System.out.println(hasDuplicate(nums));
		System.out.println(hasDuplicate(nums2));
	}


Brute Force:

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
    
             
Optimised Solution: 

        public static boolean hasDuplicate(int[] nums)
        {
            Set<Integer> dup = new HashSet<>();
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
    

### Valid Anagram
Given two strings s and t, return true if the two strings are anagrams of each other, otherwise return false.

An anagram is a string that contains the exact same characters as another string, but the order of the characters can be different.

Example 1: 

	Input: s = "racecar", t = "carrace"
	Output: true

Example 2:

	Input: s = "jar", t = "jam"
	Output: false

Constraints: 

	s and t consist of lowercase English letters.

Main Method:

Brute Force(Sorting):

Optimised Solution:


### Two Sum

Given an array of integers nums and an integer target, return the indices i and j such that nums[i] + nums[j] == target and i != j.

You may assume that every input has exactly one pair of indices i and j that satisfy the condition.

Return the answer with the smaller index first.

Example 1:

	Input: nums = [3,4,5,6], target = 7
	Output: [0,1]
Explanation: nums[0] + nums[1] == 7, so we return [0, 1].

Example 2:

	Input: nums = [4,5,6], target = 10
	Output: [0,2]

Example 3: 

	Input: nums = [5,5], target = 10
	Output: [0,1]


Constraints: 

	2 <= nums.length <= 1000
	-10,000,000 <= nums[i] <= 10,000,000
	-10,000,000 <= target <= 10,000,000

Main Method:

	public static void main(String[] args)
	{
	int [] nums = {3,4,5,6};
	int target = 7;
	int [] nums2 = {4,5,6};
 	int target 2 = 10;
  	int [] nums2 = {5,5};
 	int target 2 = 10;
	
	System.out.println(hasDuplicate(nums));
	System.out.println(hasDuplicate(nums2));
	}

Brute Force(Sorting):

	public int[] twoSum(int[] nums, int target) 
    {
    	for(int i = 0 ; i < nums.length;i++)
      {
        for(int j = i + 1; j < nums.length;j++)
        {
            if(nums[i]+nums[j] == target)
            {
                return new int []{i,j};
            }
        }
      }
      return new int[0];  
    }

Optimised Solution:

	public int[] twoSum(int[] nums, int target) 
    {
		HashMap<Integer,Integer> Map = new HashMap<>();
	        for(int i =0 ; i < nums.length;i++)
	        {
	            int num = nums[i];
	            int diff = target - nums[i];
	
	            if(Map.containsKey(diff))
	            {
	                return new int [] {Map.get(diff),i};
	            }
	            Map.put(num,i); 
	        } 
	
	        return new int[] {}; 
	}


### Group Anagrams
### Top K Frequent Elements 
### Encode and Decode Strings 
### Product of Array Except Self 
### Longest Consecutive Sequence  










