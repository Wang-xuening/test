划分为k个和相等的子集
===============
问题
---
给定一个整数数组  nums 和一个正整数 k，找出是否有可能把这个数组分成 k 个非空子集，其总和都相等。<br>
示例 1：<br>
输入： nums = [4, 3, 2, 3, 5, 2, 1], k = 4<br>
输出： True<br>
说明： 有可能将其分成 4 个子集（5），（1,4），（2,3），（2,3）等于总和。<br>
 注意:<br>
1 <= k <= len(nums) <= 16<br>
0 < nums[i] < 10000<br>

解决
--
class Solution {<br>
public: <br>   
bool canPartitionKSubsets(vector<int>& nums, int k) {  <br>     
int n = nums.size();      <br>  
int target = 0;       <br> 
for(auto x:nums) target += x;      <br>  
if(target % k) return false;    <br>   
target /= k;   <br>             
vector<int> h;   <br>      
for(int i = 0 ; i < 1<<n ; i++) {           <br> 
int s = 0;     <br>       
for(int j = 0 ; j < n ; j++)     <br>           
if(i>>j&1)    <br>                
s += nums[j];    <br>       
if(s==target) h.push_back(i);    <br>    
}      <br>          
function<bool(int,int)> dfs = [&] (int u, int p) {    <br>        
if(u==h.size()) return p == (1<<n)-1;    <br>                    
return dfs(u+1,p) || !(h[u]&p) && dfs(u+1,p|h[u]);       <br> 
};    <br>    
return dfs(0,0);    <br>
}<br>
};<br>

