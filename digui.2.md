第N个泰波那契数
===
问题
--
泰波那契序列 Tn 定义如下： <br>
T0 = 0, T1 = 1, T2 = 1, 且在 n >= 0 的条件下 Tn+3 = Tn + Tn+1 + Tn+2<br>
给你整数 n，请返回第 n 个泰波那契数 Tn 的值。<br>
示例 1：<br>
输入：n = 4<br>
输出：4<br>
解释：<br>
T_3 = 0 + 1 + 1 = 2<br>
T_4 = 1 + 1 + 2 = 4<br>
示例 2：<br>
输入：n = 25<br>
输出：1389537<br>
 提示：<br>
0 <= n <= 37<br>
答案保证是一个 32 位整数，即 answer <= 2^31 - 1。<br>

解决
--
int tribonacci(int n){<br>
int a = 0;<br>
int b = 1;<br>
int c = 1;<br>
if(n == 0)<br>
{<br>
    return a;<br>
}else if(n == 1)<br>
{<br>
    return b;<br>
}else if(n == 2)<br>
{<br>
    return c;<br>
}<br>
for(int i = 3; i <= n; i++)<br>
{<br>
    int tmp = a+b+c;<br>
    a = b;<br>
    b = c;<br>
    c = tmp;<br>
}<br>
return c;   <br>
}<br>

