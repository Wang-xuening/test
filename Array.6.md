螺旋矩阵
==
给定一个正整数 n，生成一个包含 1 到 n2 所有元素，且元素按顺时针顺序螺旋排列的正方形矩阵。<br>
示例:<br>
输入: 3<br>
输出:<br>
[<br>
 [ 1, 2, 3 ],<br>
 [ 8, 9, 4 ],<br>
 [ 7, 6, 5 ]<br>
]<br>

思路
--
1.既然是螺旋矩阵，那么可以一圈一圈地来看，每一圈都有相应的边界，每走一圈边界都向内缩1<br>
2.每一圈都按照从左到右，从上到下，从右到左，再从下到上的顺序进行<br>

解决
---
class Solution {<br>
public:<br>    
vector<vector<int>> generateMatrix(int n)   {  <br>      
int l = 0, r = n - 1, t = 0, b = n - 1;    <br>    
vector<vector<int>> mat(n);   <br>     
for (int i = 0; i < mat.size(); i++)    <br>        
mat[i].resize(n);      <br>  
int num = 1, tar = n * n;     <br>   
while(num <= tar){  <br>          
for(int i = l; i <= r; i++) mat[t][i] = num++; // left to right. <br>           
t++; <br>           
for(int i = t; i <= b; i++) mat[i][r] = num++; // top to bottom. <br>           
r--;  <br>          
for(int i = r; i >= l; i--) mat[b][i] = num++; // right to left.<br>            
b--;  <br>          
for(int i = b; i >= t; i--) mat[i][l] = num++; // bottom to top. <br>           
l++;<br>        
} <br>       
return mat; <br>   
}<br>
};<br>


