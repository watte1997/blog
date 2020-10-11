
# 数组中重复的数字
**题目：**  在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

**实例**  `输入：[2, 3, 1, 0, 2, 5, 3]输出：2 或 3`

**思路1：**  利用hash表特性，使用stl库的set模板，当set中没有该数字时，将该数字加入到set当中(标记为true)，当set有该数字时，表明有重复，返回该数字。

代码1：
  

```cpp
  class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
        unordered_map<int ,bool> hash;
        for(int i=0;i<nums.size();++i)
        {
            if(hash[nums[i]]) return nums[i];
            hash[nums[i]]=true;
        }
        return -1;
    }
};
```

**思路2** 由于nums 里的所有数字都在 0～n-1 的范围内，所以可以先将每个num填到对应的第num个位置上，当num个位置上已经有相同数字时，即为重复。

**代码2** 

```cpp

    class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
        int i;
        for(int i=0;i<nums.size();++i)
        {
            if(nums[i]==i) continue;
            if(nums[nums[i]]==nums[i])  return nums[i];
            swap(nums[nums[i]],nums[i]);
        }
    
     return -1;
    }
   
    };


```
