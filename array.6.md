子集
===
问题
--
给定一组不含重复元素的整数数组 nums，返回该数组所有可能的子集（幂集）。<br>
说明：解集不能包含重复的子集。<br>
示例:<br>
输入: nums = [1,2,3]<br>
输出:<br>
[<br>
  [3],<br>
  [1],<br>
  [2],<br>
  [1,2,3],<br>
  [1,3],<br>
  [2,3],<br>
  [1,2],<br>
  []<br>
]<br>

解决
---
class Solution {<br>
public: <br>   
vector<vector<int>> subsets(vector<int>& nums) {<br>
vector<vector<int> > res(1);<br>
for(int i=0;i<nums.size();i++){    <br>        
int cnt=res.size();     <br>       
for(int j=0;j<cnt;j++){    <br>            
vector<int> tmp=res[j];     <br>           
tmp.push_back(nums[i]);     <br>          
res.push_back(tmp);  <br>          
}   <br>     
}     <br>   
return res; <br>
}<br>
};<br>

