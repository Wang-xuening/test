最长的斐波那契子序列的长度
=======================

问题：
-----

如果序列 X_1, X_2, ..., X_n 满足下列条件，就说它是 斐波那契式 的子序列：<br>
n >= 3;<br>
对于所有 i + 2 <= n，都有 X_i + X_{i+1} = X_{i+2};<br>
给定一个严格递增的正整数数组形成序列，找到 A 中最长的斐波那契式的子序列的长度。如果一个不存在，返回  0 。<br>
（回想一下，子序列是从原序列 A 中派生出来的，它从 A 中删掉任意数量的元素（也可以不删），而不改变其余元素的顺序。例如， [3, 5, 8] 是 [3, 4, 5, 6, 7, 8] 的一个子序列）<br>
示例 1：<br>
输入: [1,2,3,4,5,6,7,8]<br>
输出: 5<br>
解释:<br>
最长的斐波那契式子序列为：[1,2,3,5,8] 。<br>
示例 2：<br>
输入: [1,3,7,11,12,14,18]<br>
输出: 3<br>
解释:<br>
最长的斐波那契式子序列有：<br>
[1,11,12]，[3,11,14] 以及 [7,11,18] 。<br>

思路：
-----
只要确定子序列的前两个值，则下一个必定按照前两个的和来进行，因此可先确定前两个数，再查找后面的数组中是否含有值为数之和的数。

解决：
-----
class Solution {<br>
public:<br>
    int lenLongestFibSubseq(vector<int>& A) {<br>
        int max=0,num=0,count=0;<br>
    int len=A.size();<br>
    //利用under_set查找<br>
    unordered_set<int> S(A.begin(),A.end());<br>
    for(int i=0;i<len-2;i++)<br>
       for(int j=i+1;j<len-1;j++){<br>
       //本来想直接三次循环，但超时了，所以找了一下，发现可以用under_set实现在数组中查找特定值<br>
           /*m=i;n=j;<br>
             for(int k=n+1;k<ASize;k++){<br>
               if(A[m]+A[n]==A[k]){<br>
                   num++;<br>
                  m=n;n=k;<br>
                }<br>
           }*/<br>
           int x=A[j],y=A[i]+A[j];<br>
           while(S.find(y)!=S.end()){<br>
               int z=x+y;<br>
               x=y;<br>
               y=z;<br>
               num++;<br>
           }<br>
           if(num!=0){<br>
               count++;<br>
               if(max<num)<br>
                 max=num;<br>
           }<br>
           num=0;<br>
       }<br>
    if(max==0)<br>
         return 0;<br>
    else<br>
         return (max+2);<br>   

    }<br>
};<br>
