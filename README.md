# binary search

Given:

    Input: nums = [1,2,3,4,5], target = 4
    Output: 4

    Pseudocode Approach:
    1. Create pointers that we can start with;
    2. The idea of a binary search => O(logN)
        => Every step divides the search space in half
    3. What I need to do is search thru a number of elements and divide it down to lesser elements every step
    4. The problem gives us a sorted array, so that means left elements are less than right elements
    5. What I can do is take the midpoint of the array and compare it with the target
        => If the target is less than the midpoint, that means the left pointer to the midpoint is our new search space; vice versa for right pointer
            => midpoint is basically the sum of the left + right divided by 2;
        => We can keep checking this way through a loop

    let search = function(nums, target) {
        let left = 0;
        let right = nums.length;

        //edge case: if there is only 1 number, just return that number
        if (nums.length === 1) return 0;

        while(left <= right) {
            let mid = Math.ceil((left + right)/ 2)
            if (nums[mid] === target) {
                return mid
            } else if (nums[mid] > target) {
                left = mid + 1
            } else if (nums[mid] < target) {
                right = mid - 1
            }
        }
        return -1
    }
