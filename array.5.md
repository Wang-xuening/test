搜索旋转排序数组
===========
问题:
--
假设按照升序排序的数组在预先未知的某个点
上进行了旋转。( 例如，数组 [0,1,2,4,5
,6,7] 可能变为 [4,5,6,7,0,1,2] )。搜
索一个给定的目标值，如果数组中存在这个目
标值，则返回它的索引，否则返回 -1 。你可
以假设数组中不存在重复的元素。你的算法时
间复杂度必须是 O(log n) 级别。<br>
示例 1:<br>
输入: nums = [4,5,6,7,0,1,2], target = 0<br>
输出: 4<br>
示例 2:<br>
输入: nums = [4,5,6,7,0,1,2], target = 3<br>
输出: -1<br>

思路:
--
假设“nums”是这样的：[12，13，14，15，16，17，18，19，0，1，2，3，4，5，6，7，8，9，10，11]
因为它没有完全排序，所以我们不能进行普通的二进制搜索。但诀窍来了：
-如果target是14，那么我们将'nums'调整为这个值，其中“inf”表示无穷大：
[12、13、14、15、16、17、18、19、inf、inf、inf、inf、inf、inf、inf、inf、inf、inf、inf、inf、inf]
-如果目标是7，那么我们将“nums”调整为：
[-inf，-inf，-inf，-inf，-inf，-inf，-inf，0，1，2，3，4，5，6，7，8，9，10，11]
然后我们就可以做普通的二进制搜索。

解决:
--

    class Solution {
    public:
        int search(vector<int>& nums, int target) {
            if(nums.size() == 0)
                return -1;
            int left = 0;
            int right = nums.size()-1;
            while(left <= right){
                int mid = (left right)/2;
                if(target == nums[mid])
                    return mid;
                if((nums[mid]>=nums[left] && (target>nums[mid] || (target<nums[left]))) || (nums[mid]<nums[left] && target>nums[mid] && target<=nums[right]))
                    left = mid   1;
                else
                    right = mid -1;
            }
            return -1;
        }
    };
