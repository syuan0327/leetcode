# 1.Two Sum
### 題目
```

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

```
### 第一次解題
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

所以不同元素用此程式可以，但相同元素就會失效

### 第二次解題
```
class Solution(object):
    def twoSum(self,nums, target):
        for i in range(1,len(nums)):
            fo=nums[:i]#當下數字之前地所有元素
            if target-nums[i] in fo:#如果目標-目前數等於的數在目前數之前的所有元素
                j=fo.index(target-nums[i])
                return([j,i])
    
```
改良了前面雙迴圈以及index問題
1.  使用了單迴圈先記錄當下算出結果的index
比如說nums=[2,3,3],target=6，那首先跑第一次回圈時會是
#### 第一次回圈
```
fo=[2]
target=6
nums[1]=3
6-3=3 不在目前的fo裡[2]，所以不成立
```

#### 第二次回圈
```
fo=[2,3]
target=6
nums[2]=3
6-3=3 有在目前的fo裡[2,3]所以成立
```
這時我的i就會是2,在使用index找出fo中(target-nums[2])=3的值，而3在fo中index為1，因此答案為1,2，這便就解決了相同數元素的問題



