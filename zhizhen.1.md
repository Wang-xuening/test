划分字母区间
===
问题：
--
字符串 S 由小写字母组成。我们要把这个字符串划分为尽可能多的片段，同一个字母只会出现在其中的一个片段。返回一个表示每个字符串片段的长度的列表。<br>
示例 1:<br>
输入: S = "ababcbacadefegdehijhklij"<br>
输出: [9,7,8]<br>
解释:<br>
划分结果为 "ababcbaca", "defegde", "hijhklij"。<br>
每个字母最多出现在一个片段中。<br>
像 "ababcbacadefegde", "hijhklij" 的划分是错误的，因为划分的片段数较少。<br>
注意:<br>
    S的长度在[1, 500]之间。<br>
    S只包含小写字母'a'到'z'。<br>
    
解决：
--
class Solution {<br>
public:<br>
    vector<int> partitionLabels(string S) {<br>
         int N = S.size();<br>
        vector<int> ends(26, -1);<br>
        for (int i = 0; i < N; ++i) {<br>
            ends[S[i] - 'a'] = i;<br>
        }<br>
        vector<int> res;<br>
        int i = 0;<br>
        while (i < N) {<br>
            int r = ends[S[i] - 'a'];<br>
            for (int j = i + 1; j <= r; ++j) {<br>
                r = max(r, ends[S[j] - 'a']);<br>
            }<br>
            res.push_back(r - i + 1);<br>
            i = r + 1;<br>
        }<br>
        return res;<br>

    }<br>
};<br>
