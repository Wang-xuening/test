任务调度器
=========
问题：
-----
给定一个用字符数组表示的 CPU 需要执行的任务列表。其中包含使用大写的 A - Z 字母表示的26 种不同种类的任务。任务可以以任意顺序执行，并且每个任务都可以在
1 个单位时间内执行完。CPU 在任何一个单位时间内都可以执行一个任务，或者在待命状态。然而，两个相同种类的任务之间必须有长度为 n 的冷却时间，因此至少有连
续 n 个单位时间内 CPU 在执行不同的任务，或者在待命状态。你需要计算完成所有任务所需要的最短时间。<br>
示例 1：<br>
输入: tasks = ["A","A","A","B","B","B"], n = 2<br>
输出: 8<br>
执行顺序: A -> B -> (待命) -> A -> B -> (待命) -> A -> B.<br>
注：任务的总个数为 [1, 10000]。<br>
    n 的取值范围为 [0, 100]。<br>

思路：
----
1.先统计数组中各个出现的次数；<br>
2.将各个任务种类出现的次数排序；<br>
3.先安排任务最多的种类,中间相隔n，再按数量由大到小安排其他种类的任务<br>
4.若安排完后还有空余时间，则总时间=次数最多的任务数+n*（次数最多任务数-1）+次数与最多的任务数相等的任务的个数；若空余时间不够安排其余任务，则总时间=总任务数。<br>

解决：
----
int leastInterval(char* tasks, int tasksSize, int n){<br>
    int a[256]={0};<br>
    //统计各种任务数量<br>
    for(char i='A';i<='Z';i++)<br>
        for(int j=0;j<tasksSize;j++)<br>
            if(tasks[j]==i) a[i]++;<br>
    //对任务数量排序<br>
    for(char i='A';i<='Z';i++)<br>
         for(char j=i+1;j<'Z';j++)<br>
             if(a[i]<a[j]){<br>
                 int t=a[i];a[i]=a[j];a[j]=t;<br>
             }<br>
     //安排任务<br>
    int max=a['A'];<br>
    int sum_t=(max-1)*n+max;<br>
    int rest_t=(max-1)*n;<br>
    for(int i='B';i<='Z';i++){<br>
       if(a[i]==max) {sum_t=sum_t+1;rest_t=rest_t-(max-1);}<br>
       if(max-a[i]==1) rest_t=rest_t-(max-2);<br>
       if(max-a[i]>=2) rest_t=rest_t-a[i];<br>
       if(rest_t<0) break;<br>
    }<br>
    if(rest_t>=0) return sum_t;<br>
    else{<br>
        sum_t=0;<br>
        for(char i='A';i<'Z';i++) sum_t=sum_t+a[i];<br>
        return sum_t;<br>
    }<br>
    
         
