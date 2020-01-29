有效三角形的个数
==============
问题：<br>
----------

  给定一个包含非负整数的数组，你的任务是统计其中可以组成三角形三条边的三元组个数。<br>
  示例 1:<br>
  输入: [2,2,3,4]<br>
输出: 3<br>
解释:<br>
有效的组合是:<br> 
2,3,4 (使用第一个 2)<br>
2,3,4 (使用第二个 2)<br>
2,2,3<br>
注意:<br>
数组长度不超过1000。<br>
数组里整数的范围为 [0, 1000]。<br>


思路：<br>
---------

满足任意两边之和大于第三边即为有效三角形，实际上只要满足最小的两边大于第三边即可，故可先排序，只要满足前面两个数之和大于第三边即可，且一旦出
现前面两边之和小于等于第三边的情况即可停止循环。<br>

解决：<br>
----------

int triangleNumber(int* nums, int numsSize){<br>
    int i,j,k,t;<br>
    int count=0;<br>
    //暴力解法,用时太长了，但也算通过<br>
    for(i=0;i<numsSize;i++)<br>
      for(j=i+1;j<numsSize;j++)<br>
        if(nums[i]>nums[j]){<br>
            t=nums[i];<br>
            nums[i]=nums[j];<br>
            nums[j]=t;<br>
        }<br>
    for(i=0;i<numsSize-2;i++)<br>
      for(j=i+1;j<numsSize-1;j++)<br>
         for(k=j+1;k<numsSize;k++){<br>
            if(nums[i]+nums[j]<=nums[k])<br>
               break;<br>
            else<br>
               count++;<br>
         }<br>
    return count;<br>
    //换一种，先排序，再用二分法求出a+b>c的最大范围<br>
    /*for(i=0;i<numsSize;i++)<br>
      for(j=i+1;j<numsSize;j++)<br>
        if(nums[i]>nums[j]){<br>
            t=nums[i];<br>
            nums[i]=nums[j];<br>
            nums[j]=t;<br>
        }
    for(i=0;i<numsSize-2;i++)<br>
      for(j=i+1;j<numsSize-1;j++){<br>
          k=j+1;<br>
          while(nums[i]+nums[j]>nums[k]) k++;<br>
          count=count+k-j-1;<br>
      }<br>
    return count;*/<br>
}<br>

