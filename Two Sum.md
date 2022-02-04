# 1.Two Sum
## 題目
```
英文：
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

中文：
给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那 两个 整数，并返回它们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。

你可以按任意顺序返回答案。

来源：力扣
链接：https://leetcode-cn.com/problems/two-sum
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```
##第一次解題
```
class Solution(object):
    def twoSum(self,nums, target):
        d={'count':0,}
        for i in nums:
            for j in nums[1:]:
                 if i+j == target :
                     d['count']+=1
                     if d['count']==1:
                        a1=nums.index(i)
                        a2=nums.index(j)
                        return(a1,a2)
                        break

```

在看到題目第一個想到的就是使用雙迴圈以及index來找出索引直，但忽略了：

1.  雙迴圈會重複跑同一個index，比如a=[1,2,3]就會跑1,1/1,2/1,3/2,1/2,2.....以此類推
2.  index無法找出同一清單重複的元素



