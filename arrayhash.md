# contains dupe
Given:
    nums = [1,2,3,1]
    True
    nums = [1,2,3,4]
    False

    1. Given a nums arr, we need to check every element to see if exists more than once
    2. We can use a hash map to store a value to check to see if it exists already
    3. while iterating, save that value to the hash, if it already exists, then its a dupe, return true
    4. if it does not exist, add it to the hash
    5. if we exit the loop/iteration, that means none of the numbers are dupes, return false

    var containsDupe = function(nums) {
        let hash = {};

        for (let i = 0; i < nums.length; i++) {
            let num = nums[i];
            if (hash[num]) {
                return true
            } else {
                hash[num] = true
            }
        }
        return false;
    }

# valid anagram
Given:
    s = 'anagram'
    t = 'nagaram'
    True

    s = 'rat'
    t = 'car'
    False

    0. check first if both string lengths match
    1. given two strings, we need to check to see if each char in both strings are the same
    2. I need to iterate through s or t first and store the chars inside a hash
    3a. Then I need to iterate through the other string and check whether it exists in the hash
    3b. the value must add for each char since they can be used multiple times
    3c. when checking the second string, we could check if it exists and then deduct 1
    3d. that would remove multiples of the same char until there is none left,
    4. if theres a char that doesnt exist, then they are not anagrams, return false
    5. if i exit the loop, then all the chars matched, must be true

    var validAnagram = function(s,t) {
        if (s.length !== t.length) return false;

        let hash = {}

        for (let i = 0; i < s.length; i++) {
            let letter = s[i];

            if (letter in hash) {
                hash[letter] += 1
            } else {
                hash[letter] = 1
            }
        }

        for (let i = 0; i < t.length; i++) {
            let letter = t[i];
            if (letter in hash) {
                if (hash[letter] > 0) {
                    hash[char] -= 1
                } else {
                    return false;
                }
            } else {
                return false;
            }
        }
        return true;
    }

# two sum
Given:
    nums = [2,7,11,15] target = 9;
    [0,1] (indexes for 2 and 7)

    1. I need to definitely iterate through the nums array
    2. I also need to use a hash to store some value using the elements in the nums array
    3. The problem uses a target value, that must match two elements added up together to reach that target value sum
    4. Since its a sum, that means subtracting the element's value from the target gives us the other pair for the sum
    5. I can save that value inside my hash using the index as a value and the difference as a key
    6. if that difference already exists, then we found the other match for our sum
    7. I can take the index for both numbers and return it as an array with two num elements
    8. if we exit the loop, that means we couldnt find any match for our target

    var twoSum = function(nums,target) {
        let hash = {};
        for (let i = 0; i < nums.length; i++) {
            let num = nums[i];
            let difference = target - num;
            if (difference in hash) {
                return [hash[difference], i]
            } else {
                hash[num] = i
            }
        }
        return []
    }

# group anagram
# top K freq elements
# Product of Arr Except Self
# Valid Sudoku
# Longest Consecutive Sequence
