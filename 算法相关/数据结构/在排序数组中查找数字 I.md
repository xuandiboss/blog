# 描述
统计一个数字在排序数组中出现的次数。
## 示例 1:
输入: nums = [5,7,7,8,8,10], target = 8

输出: 2

## 示例 2:
输入: nums = [5,7,7,8,8,10], target = 6

输出: 0

## 提示：
* 0 <= nums.length <= 10^5
* -10^9 <= nums[i] <= 10^9
* nums 是一个非递减数组
* -10^9 <= target <= 10^9

# 代码实现（二分查找+前后计数）
```
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var search = function(nums, target) {
    let count = 0;
    let left = 0;
    let right = nums.length - 1;
    let targetIdx = -1;
    while(left <= right) {
        let middle = parseInt((left + right) / 2);
        if(nums[middle] === target){
            targetIdx = middle;
            break;
        }
        if(nums[middle] < target) {
            left = middle + 1;
        } else if(nums[middle] > target) {
            right = middle - 1;
        } else {
            break;
        }
    }
    let i = targetIdx;
    while(nums[i]=== target) {
        count++;
        i--;
    }
    i = targetIdx;
    while(nums[i + 1] === target) {
        count++;
        i++;
    }
    return count;
};
```