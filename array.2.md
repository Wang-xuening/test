问题：
给定一个包含非负整数的数组，你的任务是统计其中可以组成三角形三条边的三元组个数。
示例 1:
输入: [2,2,3,4]
输出: 3
解释:
有效的组合是: 
2,3,4 (使用第一个 2)
2,3,4 (使用第二个 2)
2,2,3
注意:
数组长度不超过1000。
数组里整数的范围为 [0, 1000]。
思路：
满足任意两边之和大于第三边即为有效三角形，实际上只要满足最小的两边大于第三边即可，故可先排序，只要满足前面两个数之和大于第三边即可，且一旦出
现前面两边之和小于等于第三边的情况即可停止循环。
解决：
int triangleNumber(int* nums, int numsSize){
    int i,j,k,t;
    int count=0;
    //暴力解法,用时太长了，但也算通过
    for(i=0;i<numsSize;i++)
      for(j=i+1;j<numsSize;j++)
        if(nums[i]>nums[j]){
            t=nums[i];
            nums[i]=nums[j];
            nums[j]=t;
        }
    for(i=0;i<numsSize-2;i++)
      for(j=i+1;j<numsSize-1;j++)
         for(k=j+1;k<numsSize;k++){
            if(nums[i]+nums[j]<=nums[k])
               break;
            else
               count++;
         }
    return count;
    //换一种，先排序，再用二分法求出a+b>c的最大范围
    /*for(i=0;i<numsSize;i++)
      for(j=i+1;j<numsSize;j++)
        if(nums[i]>nums[j]){
            t=nums[i];
            nums[i]=nums[j];
            nums[j]=t;
        }
    for(i=0;i<numsSize-2;i++)
      for(j=i+1;j<numsSize-1;j++){
          k=j+1;
          while(nums[i]+nums[j]>nums[k]) k++;
          count=count+k-j-1;
      }
    return count;*/
}

