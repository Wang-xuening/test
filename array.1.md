问题：
给定一个整数数组和一个整数 k，你需要找到该数组中和为 k 的连续的子数组的个数。
示例 1 :
输入:nums = [1,1,1], k = 2
输出: 2 , [1,1] 与 [1,1] 为两种不同的情况。
说明 :
数组的长度为 [1, 20,000]。
 数组中元素的范围是 [-1000, 1000] ，且整数 k 的范围是 [-1e7, 1e7]。
思路：
本题首先需要数组中和为k的所有子数组，这里两次遍历数组，保证所有和为k的数组都被取到
解决：
int subarraySum(int* nums, int numsSize, int k){
    int i,j;int sum=0;int n=0;
    for(i=0;i<numsSize;i++){
        sum=0;
        for(j=i;j<numsSize;j++){
            sum=sum+nums[j];
            if(sum==k) n++;
        }
    }    
    return n;
}