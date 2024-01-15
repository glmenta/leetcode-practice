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
# group anagram
# top K freq elements
# Product of Arr Except Self
# Valid Sudoku
# Longest Consecutive Sequence
