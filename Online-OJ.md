# 力扣
*(每天可能更一题)*
## C++

**1. 两数之和**
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int i = 0;
        int ia = 0;
        for (i = 0; i < nums.size() - 1; i++){
            for (ia = i + 1; nums.size() != ia; ia++){
                if (nums[ia] + nums[i] == target){
                    vector<int>v = {i, ia} ;
                    return v;
                }
            }
        }
        return nums;
    }
};
```
**2. 两数相加**
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int i = 0;
        int ia = 0;
        for (i = 0; i < nums.size() - 1; i++){
            for (ia = i + 1; nums.size() != ia; ia++){
                if (nums[ia] + nums[i] == target){
                    vector<int>v = {i, ia} ;
                    return v;
                }
            }
        }
        return nums;
    }
};
```
**3. 无重复字符的最长子串**
```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string str) {
        set<char>s;
        int ia = 0;
        int ilong = 0;
        for (int i = 0; i < str.size(); i++){
            for (ia = i; ia < str.size(); ia++){
                s.insert(str[ia]);
                if (s.size() != (ia - i + 1)){
                    break;
                }
            }
            ilong < s.size() ?F ilong = s.size() : 0;
            s.clear();
        }
        return ilong;
    }
};
```
**4. 寻找两个正序数组的中位数**
```cpp
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        vector<int>v;
        int i = 0;
        int ia = 0;
        for (; i < nums1.size() || ia < nums2.size(); ){
            if (i < nums1.size() && ia < nums2.size()){
                if (nums1[i] < nums2[ia]){
                    v.push_back(nums1[i++]);
                } 
                else {
                    v.push_back(nums2[ia++]);
                }
            }
            else if(i < nums1.size()) {
                v.push_back(nums1[i++]);
            }
            else {
                v.push_back(nums2[ia++]);
            }
        }
        return v.size() % 2 ? v[v.size() / 2] : (v[v.size() / 2] + v[v.size() / 2 - 1]) / 2.0;
    }
};
```
**5. 最长回文子串**
```cpp
class Solution {
public:
    string longestPalindrome(string s) {
        int len = 0;
        int maxLen = 1;
        unsigned int pos = 0;
        for (int center = 0; center < s.length(); center++){
            for (int right = 0; center - right >= 0 && center + right < s.length() && s[center - right] == s[center + right]; right++){
                if (maxLen < right * 2 + 1){
                    maxLen = right * 2 + 1;
                    pos = center - right;
                }
            }
        }
        for (int center = 0; center < s.length() - 1; center++){
            for (int right = 0; center - right >= 0 && center + 1 + right < s.length() && s[center - right] == s[center + right + 1]; right++){
                if (maxLen < (right + 1) * 2){
                    maxLen = (right + 1) * 2;
                    pos = center - right;
                }
            }
        }
        return s.substr(pos, maxLen);
    }
};
```
**7. 整数反转**
```cpp
class Solution {
public:
    int reverse(int x) {
        if (INT_MIN == x){
            return 0;
        }
        bool isNegative = x < 0;
        int i = 0;
        x = abs(x);
        vector<int>rnum;
        vector<int>maxnum = {2, 1, 4, 7, 4, 8, 3, 6, 4, 7};
        maxnum.back() += isNegative;
        while (x){
            rnum.push_back(x % 10);
            x /= 10;
        }
        cout << INT_MAX << " " << INT_MIN;
        if (rnum.size() > 10){
            return 0;
        }
        else if (10 == rnum.size()){
            for (int i = 0; i < 10; i++){
                if (rnum[i] > maxnum[i]){
                    return 0;
                }
                if (rnum[i] < maxnum[i]){
                    break;
                }
            }
        }
        for (int ri = 0; ri < rnum.size(); ri++){
            i *= 10;
            i += rnum[ri];
        }
        return i * (isNegative ? -1 : 1);
    }
};
```
**8. 字符串转换整数 (atoi)**
```cpp
class Solution {
public:
    int myAtoi(string s) {
        regex r("^ +| +$");
        regex ra("^[+-]?[0-9]*");
        s = regex_replace(s, r, "");
        sregex_iterator rsit(s.begin(), s.end(), ra);
        s = rsit->str();
        bool negaitve = false;
        if ('-' == s.front()){
            negaitve = true;
        }
        long long ll = 0;
        for (int i = 0; i < s.size(); i++){
            if (s[i] >= '0' && s[i] <= '9') {
                ll *= 10;
                ll += s[i] - '0';
            }
            if (ll > INT_MAX){
                return negaitve ? INT_MIN : INT_MAX;
            }
        }
        negaitve ? ll = -ll : 0;
        return ll;
    }
};
```
**9. 回文数**
```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        char str[100] = "";
        string strCmp;
        sprintf(str, "%d", x);
        for (int i = 0; str[i]; i++){
            strCmp.insert(strCmp.begin(), str[i]);
        }
        return !strcmp(str, strCmp.c_str());
    }
};
```
**10. 正则表达式匹配**
```cpp
class Solution {
public:
    bool isMatch(string s, string p) {
        p.insert(0, "^");
        p.append("$");
        regex r(p);
        return regex_search(s, r);
    }
};
```
**11. 盛最多水的容器**
```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        int width = height.size() - 1;
        int depth = 0;
        for (int a = 0, b = height.size() - 1; a < b; ){
            depth = max(min(height[a], height[b]) * width, depth);
            if (height[a] < height[b]){
                a++;
                width--;
            }
            else if(height[a] > height[b]){
                b--;
                width--;
            }
            else {
                a++;
                b--;
                width -= 2;
            }
        }
        return depth;
    }
};
```
**12. 整数转罗马数字**
```cpp
class Solution {
public:
    string intToRoman(int num) {
        string Roman = string(num / 1000, 'M');
        string strs[30] = {"", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX", "", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC", "", "C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM"};
        Roman += strs[num / 100 % 10 + 20];
        Roman += strs[num / 10 % 10 + 10];
        Roman += strs[num % 10];
        return Roman;
    }
};
```
**13. 罗马数字转整数**
```cpp
class Solution {
public:
    int romanToInt(string s) {
        int isum = 0;
        int index = 0;
        bool isNegte = false;
        map<char, int>m={
            {'I', 6}, 
            {'V', 5}, 
            {'X', 4}, 
            {'L', 3}, 
            {'C', 2}, 
            {'D', 1}, 
            {'M', 0}
        };
        for (int i = 0; i < s.size(); i++){
            if(s.size() - 1 != i && m[s[i]] > m[s[i + 1]] && (m[s[i]] == 6 || m[s[i]] == 4 || m[s[i]] == 2) && m[s[i]] - m[s[i + 1]] <= 2){
                isNegte = true;
            }
            switch(s[i]){
            case 'I':
                isum += (1 - isNegte * 2);
                break;
            case 'V':
                isum += (1 - isNegte * 2) * 5;
                break;
            case 'X':
                isum += (1 - isNegte * 2) * 10;
                break;
            case 'L':
                isum += (1 - isNegte * 2) * 50;
                break;
            case 'C':
                isum += (1 - isNegte * 2) * 100;
                break;
            case 'D':
                isum += (1 - isNegte * 2) * 500;
                break;
            case 'M':
                isum += (1 - isNegte * 2) * 1000;
                break;
            default:
                break;
            }
            isNegte = false;
        }
        return isum;
    }
};
```
**14. 最长公共前缀**
```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        string frontstr;
        int minsize = strs[0].size();
        int ia = 0;
        for (int i = 1; i < strs.size(); i++){
            if (strs[i].size() < minsize){
                minsize = strs[i].size();
            }
        }
        for (int i = 0; i < minsize; i++){
            for (ia = 0; ia < strs.size() - 1; ia++){
                if (strs[ia][i] != strs[ia + 1][i]){
                    return frontstr;
                }
            }
            frontstr.push_back(strs[0][i]);
        }
        return frontstr;
    }
};
```
**17. 电话号码的字母组合**
```cpp
class Solution {
public:
    vector<string> chars = {
        "abc",
        "def",
        "ghi",
        "jkl",
        "mno",
        "pqrs",
        "tuv",
        "wxyz"
    };
    void add(string& s, int i, string& digits){
        if (i < 0){
            return;
        }
        s[i]++;
        if (s[i] > chars[digits[i] - '2'].back()){
            s[i] = chars[digits[i] - '2'].front();
            add(s, i - 1, digits);
        }
    }
    vector<string> letterCombinations(string digits) {
        if (0 == digits.length()){
            return {};
        }
        string phoneStr;
        string beforeStr;
        vector<string>result;
        for (char ch : digits){
            phoneStr.push_back(chars[ch - '2'][0]);
        }
        beforeStr = phoneStr;
        int i = digits.length() - 1;
        do {
            add(phoneStr, i, digits);
            result.push_back(phoneStr);
        } while (beforeStr != phoneStr);
        return result;
    }
};
```
**20. 有效的括号**
```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char>strS;
        for (char ch : s){
            if ('(' == ch || '[' == ch || '{' == ch){
                strS.push(ch);
            }
            else {
                switch(ch){
                case ')':
                    if (!strS.size() || '(' != strS.top()){
                        return false;
                    }
                    strS.pop();
                    break;
                case ']':
                    if (!strS.size() || '[' != strS.top()){
                        return false;
                    }
                    strS.pop();
                    break;
                case '}':
                    if (!strS.size() || '{' != strS.top()){
                        return false;
                    }
                    strS.pop();
                    break;
                default:
                    break;
                }
            }
        }
        return !strS.size();
    }
};
```
**21. 合并两个有序链表**
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode* listNew = new ListNode();
        ListNode** addNode = &listNew;
        while (nullptr != list1 || nullptr != list2){
            if (nullptr == list1 || nullptr != list1 && nullptr != list2 && list1->val >= list2->val){
                (*addNode)->next = new ListNode(list2->val), (addNode = &(*addNode)->next);    
                list2 = list2->next;
            }
            else {
                (*addNode)->next = new ListNode(list1->val), (addNode = &(*addNode)->next);
                list1 = list1->next;
            }
        }
        return listNew->next;
    }
};
```
**24. 两两交换链表中的节点**
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* swapPairs(ListNode* head) {
        ListNode** swapnodea = &head;
        ListNode** swapnodeb = nullptr != head ? &(head->next) : nullptr;
        int swapNum = 0;
        while (nullptr != *swapnodea && nullptr != *swapnodeb){
            swapNum = (*swapnodea)->val;
            (*swapnodea)->val = (*swapnodeb)->val;
            (*swapnodeb)->val = swapNum;
            swapnodea = &(*swapnodea)->next->next;
            if (nullptr != *swapnodea){
                swapnodeb = &(*swapnodeb)->next->next;
            }
        }
        return head;
    }
};
```
**26. 删除有序数组中的重复项**
```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        vector<int>v;
        for (int i = 0; i < nums.size(); i++){
            if (!i || nums[i - 1] != nums[i]){
                v.push_back(nums[i]);
            }
        }
        nums = v;
        return v.size(); 
    }
};
```
**27. 移除元素**
```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        vector<int>v;
        int k = nums.size();
        for (int i : nums){
            if (val == i){
                k--;
            }
            else {
                v.push_back(i);
            }
        }
        nums = v;
        return k;
    }
};
```
**28. 找出字符串中第一个匹配项的下标**
```cpp
class Solution {
public:
    int strStr(string haystack, string needle) {
        if (nullptr == strstr(haystack.c_str(), needle.c_str())){
            return -1;
        }
        else {
            return strstr(haystack.c_str(), needle.c_str()) - haystack.c_str();
        }
    }
};
```
**35. 搜索插入位置**
```cpp
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int min = 0;
        int max = nums.size() - 1;
        int mid = (min + max) / 2;
        while (max >= min){
            if (nums[mid] == target){
                return mid;
            }
            else if(nums[mid] > target){
                max = mid - 1;
            }
            else {
                min = mid + 1;
            }
            mid = (min + max) / 2;
        }
        return min;
    }
};
```
**36. 有效的数独**
```cpp
class Solution {
public:
    bool isValidSudoku(vector<vector<char>>& board) {
        set<int>s;
        set<int>sa;
        int i = 0;
        int ia = 0;
        for (i = 0; i < 9; i++){
            for (ia = 0; ia < 9; ia++){
                if ('.' != board[i][ia]) {
                    if (s.end() != s.find(board[i][ia])){
                        return false;
                    }
                    s.insert(board[i][ia]);
                }
                if ('.' != board[ia][i]) {
                    if (sa.end() != sa.find(board[ia][i])){
                        return false;
                    }
                    sa.insert(board[ia][i]);
                }
            }
            s.clear();
            sa.clear();
        }
        for (int ib = 0; ib < 9; ib += 3){
            for (int ic = 0; ic < 9; ic += 3){
                for (i = 0; i < 3; i++){
                    for (ia = 0; ia < 3; ia++){
                        if ('.' != board[ib + i][ic + ia]) {
                            if (s.end() != s.find(board[ib + i][ic + ia])){
                                return false;
                            }
                            s.insert(board[ib + i][ic + ia]);
                        }                      
                    }
                }
                s.clear();
            }
        }
        return true;
    }
};
```
**38. 外观数列**
```cpp
class Solution {
public:
    string countAndSay(int n) {
        string str = "1";
        string countStr;
        for (; n > 1; n--){
            for (char ch : str){
                if (!countStr.size() || ch != countStr.back()){
                    countStr.append("  ");
                    countStr.back() = ch;
                    countStr[countStr.size() - 2] = '1';
                }
                else {
                    countStr[countStr.size() - 2]++;
                }
            }
            str = countStr;
            countStr.clear();
        }
        return str;
    }
};
```
**42. 接雨水**
```cpp
class Solution {
public:
    // int getMax(vector<int> v){
    //     int max = 0;
    //     for (int i : v){
    //         i > max ? max = i : 0;
    //     }
    //     return max;
    // }
    int trap(vector<int>& height) {
        vector<int>lh;
        vector<int>rh;
        int lmax = 0;
        int rmax = 0;
        int water = 0;
        for (int i = 0; i < height.size(); i++){
            lmax < height[i] ? lmax = height[i] : 0;
            rmax < height[height.size() - i - 1] ? rmax = height[height.size() - i - 1] : 0;
            lh.push_back(lmax);
            rh.insert(rh.begin(), rmax);
        }
        for (int i = 0; i < height.size(); i++){
            water += min(lh[i], rh[i]) - height[i];
        }
        return water;
    }
};
```
**46. 全排列**
```cpp
class Solution {
public:
    vector<vector<int>> vv;
    void swap(vector<int>& nums, int i, int ia){
        int temp = nums[i];
        nums[i] = nums[ia];
        nums[ia] = temp;
    }
    void permute(vector<int>& nums, int min){
        if (min >= nums.size()){
            vv.push_back(nums);
        }
        for (int i = min; i < nums.size(); i++){
            swap(nums, min, i);
            permute(nums, min + 1);
            swap(nums, min, i);
        }
    }
    vector<vector<int>> permute(vector<int>& nums) {
        permute(nums, 0);
        return vv;
    }
};
```
**54. 螺旋矩阵**
```cpp
class Solution {
    enum wasd {
        w,
        a,
        s,
        d
    };
public: 
    int& get(vector<vector<int>>& matrix, int pos) {
        return matrix[pos / matrix[0].size()][pos % matrix[0].size()];
    }
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int> result;
        const int move[4] = {-(int)matrix[0].size(), -1, (int)matrix[0].size(), 1};
        wasd status = w;
        int pos = 0;
        for (int i = 0; i < matrix[0].size() * matrix.size(); i++) {
            result.push_back(get(matrix, pos));
            get(matrix, pos) = INT_MAX;
            switch (status) {
            case w:
                if ((pos - matrix[0].size()) / matrix[0].size() >= matrix.size() || INT_MAX == get(matrix, pos - matrix[0].size())) {
                    status = d;
                }
                break;
            case a:
                if ((pos - 1) % matrix[0].size() == matrix[0].size() - 1 || INT_MAX == get(matrix, pos - 1)) {
                    status = w;
                }
                break;
            case s:
                if ((pos + matrix[0].size()) / matrix[0].size() >= matrix.size() || INT_MAX == get(matrix, pos + matrix[0].size())) {
                    status = a;
                }
                break;
            case d:
                if ((pos + 1) % matrix[0].size() == 0 || INT_MAX == get(matrix, pos + 1)) {
                    status = s;
                }
                break;
            default:
                break;
            }
            pos += move[status];
        }
        return result;
    }
};
```
**55. 跳跃游戏**
```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
        return canJump(nums, 0);
    }

    bool canJump(vector<int>& nums, int index){
        bool jump = false;
        if (index + nums[index] >= nums.size() - 1){
            return true;
        }
        else if(0 == nums[index]){
            return false;
        }
        else {
            for (int i = 1; !jump && index + i < nums.size() && i <= nums[index]; i++){
                jump |= canJump(nums, index + i);
            }
        }
        nums[index] = 0;
        return jump;
    }
};
```
**56. 合并区间**
```cpp
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        sort(intervals.begin(), intervals.end());
        vector<vector<int>> result;
        for (long long i = 0; i < intervals.size(); i++){
            if (intervals.size() - 1 != i && !(intervals[i][0] > intervals[i + 1][1] || intervals[i][1] < intervals[i + 1][0])){
                intervals[i][0] = min(intervals[i][0], intervals[i + 1][0]);
                intervals[i][1] = max(intervals[i][1], intervals[i + 1][1]);
                intervals.erase(intervals.begin() + i + 1, intervals.begin() + i + 2);
                i--;
            }
            else {
                result.push_back(intervals[i]);
            }
        }
        return result;
    }
};
```
**58. 最后一个单词的长度**
```cpp
class Solution {
public:
    int lengthOfLastWord(string s) {
        int index = s.size() - 1; 
        int len = 0;
        while (0 <= index && ' ' == s[index]){ index--; }
        while (0 <= index && ' ' != s[index--]){ len++; }
        return len;
    }
};
```
**65. 有效数字**
```cpp
class Solution {
public:
    bool isNumber(string s) {
        regex rn("^[+-]?\\.?($|[eE])");
        regex r("^[+-]?[0-9]*(\\.[0-9]*)?([eE][+-]?[0-9]+)?$");
        return !regex_search(s, rn) && regex_search(s, r);
    }
};

// 2 
// 0089 
// -0.1 
// +3.14 
// 4. 
// -.9 
// 2e10 
// -90E3
// 3e+7
// +6e-1 
// 53.5e93
// -123.456e789


```
**66. 加一**
```cpp
class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
        digits[digits.size() - 1]++;
        int i = digits.size() - 1;
        while (digits[i] >= 10 && i >= 0){
            if (digits[i] >= 10){
                if (i - 1 >= 0){
                    digits[i - 1]++;
                }
                else {
                    digits[i] %= 10;
                    digits.push_back(0);
                    for (int ia = 0; ia < digits.size() - 2; ia++){
                        digits[ia + 1] = digits[ia];
                    }
                    digits[0] = 1;
                    break;
                }
                digits[i--] %= 10;
            }
        }
        return digits;
    }
};
```
**67. 二进制求和**
```cpp
class Solution {
public:
    string addBinary(string a, string b) {
        int addNum = 0;
        bool bItToEnd = false;
        bool bItaToEnd = false;
        bool addOne = false;
        string binStr;
        auto it = a.rbegin(); 
        auto ita = b.rbegin();
        while (it != a.rend() || ita != b.rend()) {
            addNum = (bItToEnd ? 0 : *it - '0') + (bItaToEnd ? 0 : *ita - '0') + addOne;
            binStr.insert(binStr.cbegin(), addNum % 2 + '0');
            addOne = addNum >= 2;
            if (a.rend() != it){
                it++;
            }
            if (b.rend() != ita){
                ita++;
            }
            if (b.rend() == ita) {
                bItaToEnd = true;
            }
            if (a.rend() == it) {
                bItToEnd = true;
            }
        }
        if (addOne){
            binStr.insert(binStr.cbegin(), '1');
        }
        return binStr;
    }
};
```
**70. 爬楼梯**
```cpp
class Solution {
public:
    void swap(int& i, int& ia){
        int itemp = i;
        i = ia;
        ia = itemp;
    }
    int climbStairs(int n) {
        int i = 1;
        int ia = 1;
        while (n-- > 1){
            i += ia;
            swap(i, ia);
        }
        return ia;
    }
};
```
**71. 简化路径**
```cpp
class Solution {
public:
    string simplifyPath(string path) {
        regex delnotEasy("/+$");
        path = regex_replace(path, delnotEasy, "");
        regex delnotEasyA("/{2,}");
        path = regex_replace(path, delnotEasyA, "/");
        string d = ""; 
        list<string>l;
        path.push_back('/');
        cout << path << endl;
        for (int i = 1; i < path.size(); i++){
            if ('/' == path[i]) {
                cout << d;
                if (d == ".." && l.size()){
                    l.pop_back();
                }
                else if(d != ".." && d != ".") {
                    l.push_back(d);
                }
                d.clear();
            }
            else {
                d.push_back(path[i]);
            }
        }
        path.clear();
        for (string s : l){
            path.append("/");
            path.append(s);
        }
        return path.empty() ? "/" : path;
    }
};
```
**73. 矩阵置零**
```cpp
class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
        bool* isdel = new bool[matrix.size() + matrix[0].size()];
        for (int i=0;i<matrix.size() + matrix[0].size();i++){
            isdel[i] = false;
        }
        //mark
        for (int i = 0; i < matrix.size(); i++){
            for (int ia = 0; ia < matrix[0].size(); ia++){
                if (0 == matrix[i][ia]){
                    isdel[i] = true;
                    isdel[matrix.size() + ia] = true;
                }
            }
        }
        //del
        for (int i = 0; i < matrix.size(); i++){
            for (int ia = 0; ia < matrix[0].size(); ia++){
                if (isdel[i] || isdel[matrix.size() + ia]){
                    matrix[i][ia] = 0;
                }
            }
        }
    }
};
```
**75. 颜色分类**
```cpp
class Solution {
public:
    void sortColors(vector<int>& nums) {
        vector<int> v[3] = {vector<int>(), vector<int>(), vector<int>()};
        for (int i : nums){
            v[i].push_back(i);
        }
        for (int i : v[1]){
            v[0].push_back(i);
        }
        for (int i : v[2]){
            v[0].push_back(i);
        }
        nums = v[0];
    }
};
```
**79. 单词搜索**
```cpp
class Solution {
public:
    bool check(vector<vector<char>>& board, string word, int i, int ia){
        string newWord;
        bool b = false;
        char tch = 0;
        if (i >= 0 && i < board.size() && ia >= 0 && ia < board[0].size() && word.front() == board[i][ia]){
            tch = board[i][ia];
            board[i][ia] = ' ';
        }
        for (int i=1;i<word.size();i++){
            newWord.push_back(word[i]);
        }
        if (newWord.empty()){
            return true;
        }
        if (!b && ia + 1 < board[0].size() && newWord.front() == board[i][ia + 1]){
            b |= check(board, newWord, i, ia + 1);
        }
        if (!b && i - 1 >= 0 && newWord.front() == board[i - 1][ia]){
            b |= check(board, newWord, i - 1, ia);
        }
        if (!b && i + 1 < board.size() && newWord.front() == board[i + 1][ia]){
            b |= check(board, newWord, i + 1, ia);
        }
        if (!b && ia - 1 >= 0 && newWord.front() == board[i][ia - 1]){
            b |= check(board, newWord, i, ia - 1);
        }
        if (!b && tch){
            board[i][ia] = tch;
        }
        return b;
    }
    bool exist(vector<vector<char>>& board, string word) {
        vector<vector<char>> temp = board;
        for (int i = 0; i < board.size(); i++){
            for (int ia = 0; ia < board[0].size(); ia++){
                if (word.front() == board[i][ia] && check(temp, word, i, ia)){
                    return true;
                }
                temp = board;
            }
        }
        return false;
    }
};
```
**81. 搜索旋转排序数组 II**
```cpp
class Solution {
public:
    void leftMove(vector<int>& v){
        int temp = v.front();
        for (int i = 0; i < v.size() - 1; i++){
            v[i] = v[i + 1];
        }
        v.back() = temp;
    }
    bool search(vector<int>& nums, int target) {
        int i = 0;
        for (i = 0; i < nums.size() - 1; i++){
            if (nums[i] > nums[i + 1]){
                break;
            }
        }
        vector<int>v = nums;
        for (; i >= 0; i--){
            leftMove(v);
        }
        int min = 0;
        int max = v.size() - 1;
        int mid = (min + max) / 2;
        while (min <= max){
            if (v[mid] == target){
                return true;
            }
            else if(v[mid] < target){
                min = mid + 1;
            }
            else {
                max = mid - 1;
            }
            mid = (min + max) / 2;
        }
        return false;
    }
};
```
**83. 删除排序链表中的重复元素**
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        ListNode** node = &head;
        while (nullptr != *node && nullptr != (*node)->next) {
            if ((*node)->val == (*node)->next->val){
                *node = (*node)->next;
            }
            else {
                node = &(*node)->next;
            }
        }
        return head;
    }
};
```
**88. 合并两个有序数组**
```cpp
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        vector<int>mergeV;
        for (int i = 0, ia = 0; i < m || ia < n; ){
            if (i >= m || i < m && ia < n && nums1[i] > nums2[ia]){
                mergeV.push_back(nums2[ia++]);
            }
            else {
                mergeV.push_back(nums1[i++]);
            }
        }
        nums1 = mergeV;
    }
};
```
**92. 反转链表 II**
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverseBetween(ListNode* head, int left, int right) {
        vector<int>list;
        while (nullptr != head){
            list.push_back(head->val);
            head = head->next;
        }
        reverse(list.begin() + left - 1, list.end() - (list.size() - right));
        head = new ListNode(list[0]);
        ListNode**  addNode = &head;
        for (int i = 1; i < list.size(); i++){
            (*addNode)->next = new ListNode(list[i]);
            addNode = &(*addNode)->next;
        }
        return head;
    }
};
```
**93. 复原 IP 地址**
```cpp
class Solution {
public:
    vector<string> restoreIpAddresses(string s) {
        vector<string> result;
        string ip;
        string strNums[4] = {};
        if (s.size() > 12 || s.size() < 4) {
            return result;
        }
        for (int i = 0; i < 3; i++) {
            strNums[0].push_back(s[i]);
            if (i && '0' == strNums[0][0]) {
                break;
            }
            if (2 != i || 255 >= atoi(strNums[0].c_str())) {
                for (int ia = i + 1; ia - i <= 3; ia++) {
                    strNums[1].push_back(s[ia]);
                    if (1 != ia - i && '0' == strNums[1][0]) {
                        break;
                    }
                    if (3 != ia - i || 255 >= atoi(strNums[1].c_str())) {
                        for (int ib = ia + 1; ib - ia <= 3 && ib < s.size(); ib++) {
                            strNums[2].push_back(s[ib]);
                            if (ib - ia > 1 && '0' == strNums[2][0]) {
                                break;
                            }
                            if (3 != ib - ia || 255 >= atoi(strNums[2].c_str())) {
                                for (int ic = ib + 1; ic - ib <= 3 && ic < s.size(); ic++) {
                                    strNums[3].push_back(s[ic]);
                                    if (ic - ib > 1 && '0' == strNums[3][0]) {
                                        break;
                                    }
                                    if (s.size() - 1 == ic && 255 >= atoi(strNums[3].c_str())) {
                                        ip.clear();
                                        ip.append(strNums[0]).append(".").append(strNums[1]).append(".").append(strNums[2]).append(".").append(strNums[3]);
                                        result.push_back(ip);
                                    }
                                }
                                strNums[3].clear();
                            }
                        }
                        strNums[2].clear();
                    }
                }
                strNums[1].clear();
            }
        }
        return result;
    }
};
```
**94. 二叉树的中序遍历**
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int>v;
        vector<int>returnV;
        if (nullptr == root){
            return v;
        }
        if (nullptr != root->left){
            returnV = inorderTraversal(root->left);
            for (int i : returnV){
                v.push_back(i);
            }
        }
        v.push_back(root->val);
        if (nullptr != root->right){
            returnV = inorderTraversal(root->right);
            for (int i : returnV){
                v.push_back(i);
            }
        }
        return v;
    }
};
```
**97. 交错字符串**
```cpp
class Solution {
public:
    bool isInterleave(string s1, string s2, string s3) {
        vector<int>bv(s2.size() + 1, false);
        bv[0] = true;
        if (s1.size() + s2.size() != s3.size()){
            return false;
        }
        for (int i = 0; i <= s1.size(); ++i) {
            for (int j = 0; j <= s2.size(); ++j) {
                int p = i + j - 1;
                if (i > 0) {
                    bv[j] &= (s1[i - 1] == s3[p]);
                }
                if (j > 0) {
                    bv[j] |= (bv[j - 1] && s2[j - 1] == s3[p]);
                }
            }
        }
        return bv[s2.size()];
    }
};
```
**100. 相同的树**
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if (nullptr == p && nullptr == q){
            return true;
        }
        else if(1 == (nullptr == p) + (nullptr == q) || p->val != q->val){
            return false;
        }
        else{
            return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
        }
    }
};
```
**101. 对称二叉树**
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool isSymmetric(TreeNode* root) {
        return isSymmetric(root->left, root->right);
    }
    bool isSymmetric(TreeNode* nodea, TreeNode* nodeb) {
        if (nullptr == nodea && nullptr == nodeb){
            return true;
        }
        else if (nullptr == nodea || nullptr == nodeb || nodea->val != nodeb->val){
            return false;
        }
        else {
            return isSymmetric(nodea->left, nodeb->right) && isSymmetric(nodea->right, nodeb->left);
        }
    }
};
```
**104. 二叉树的最大深度**
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int maxDepth(TreeNode* root) {
        int i = 0;
        int ia = 0;
        if (nullptr == root){
            return 0;
        }
        else {
            return 1 + ((i = maxDepth(root->left)) > (ia = maxDepth(root->right)) ? i : ia);
        }
    }
};
```
**110. 平衡二叉树**
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
    int maxNum = 0;
public:
    void getTreeDepths(TreeNode* root, int depth = 1) {
        if (nullptr != root) {
            maxNum = max(depth, maxNum);
            getTreeDepths(root->left, depth + 1);
            getTreeDepths(root->right, depth + 1);
        }
    }
    bool isBalanced(TreeNode* root) {
        this->maxNum = 0;
        if (nullptr == root){
            return true;    
        }
        getTreeDepths(root->left);
        int leftDepth = this->maxNum;
        this->maxNum = 0;
        getTreeDepths(root->right);
        int rightDepth = this->maxNum;
        return abs(leftDepth - rightDepth) <= 1 && isBalanced(root->left) && isBalanced(root->right);
    }
};
```
**111. 二叉树的最小深度**
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int minDepth(TreeNode* root) {
        if (nullptr == root){
            return 0;
        }
        else if (nullptr == root->left && nullptr == root->right){
            return 1;
        }
        else {
            int leftDepth = depth(root->left, 2); 
            int rightDepth = depth(root->right, 2);
            if (0 == leftDepth){
                return rightDepth;
            }
            else if (0 == rightDepth){
                return leftDepth;
            }
            else {
                return min(rightDepth, leftDepth);
            }
        }
    }
    int depth(TreeNode* root, int d){
        if (nullptr == root){
            return 0;
        }
        else if(nullptr == root->left && nullptr == root->right){
            return d;
        }
        else if(nullptr == root->left) {
            return depth(root->right, d + 1);
        }
        else if(nullptr == root->right){
            return depth(root->left, d + 1);
        }
        else {
            return min(depth(root->right, d + 1), depth(root->left, d + 1));
        }
    }
};
```
**112. 路径总和**
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool hasPathSum(TreeNode* root, int targetSum) {
        if (nullptr == root){
            return false;
        }
        else {
            targetSum -= root->val;
            if (!targetSum && nullptr == root->left && nullptr == root->right){
                return true;
            }
            else {
                return hasPathSum(root->left, targetSum) || hasPathSum(root->right, targetSum);
            }
        }
    }
};
```
**118. 杨辉三角**
```cpp
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<int>v = {1};
        vector<int>va = v;
        vector<vector<int>> result;
        for (; numRows; numRows--){
            result.push_back(v);
            va.insert(va.begin(), 0);
            va.push_back(0);
            v.clear();
            for (int i = 0; i < va.size() - 1; i++){
                v.push_back(va[i] + va[i + 1]);
            }
            va = v;
        }
        return result;
    }
};
```
**119. 杨辉三角 II**
```cpp
class Solution {
public:
    vector<int> getRow(int rowIndex) {
        vector<int>r = {1};
        int lsize = 1;
        for (int i = 0; i < rowIndex; i++){
            lsize = r.size();
            for (int ia = -1; ia <= lsize - 1; ia++){
                if (-1 == ia || lsize - 1 == ia){
                    r.push_back(1);
                }
                else {
                    r.push_back(r[ia] + r[ia + 1]);
                }
            }
            r.erase(r.begin(), r.begin() + lsize);
        }
        return r;
    }
};
```
**121. 买卖股票的最佳时机**
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int min = prices[0];
        int max = 0;
        for (int i = 1; i < prices.size(); i++) {
            if (prices[i] < min) {
                min = prices[i];
            } else if (prices[i] - min > max) {
                max = prices[i] - min;
            }
        }
        return max;
    }
};
```
**125. 验证回文串**
```cpp
class Solution {
public:
    bool isPalindrome(string s) {
        string ts;
        for (int i = 0; i < s.size(); i++){
            if (s[i] >= 'A' && s[i] <= 'Z'){
                ts.push_back(s[i] + 'a' - 'A');
            }
            else if(s[i] >= '0' && s[i] <= '9' || s[i] >= 'a' && s[i] <= 'z'){
                ts.push_back(s[i]);
            }
        }
        s = ts;
        string rs;
        for (int i = s.size() - 1; i >= 0; i--){
            rs.push_back(s[i]);
        }
        return !s.compare(rs);
    }
};
```
**136. 只出现一次的数字**
```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int num = 0;
        for (int i = 0; i < nums.size(); i++){
            num ^= nums[i];
        }
        return num;
    }
};
```
**141. 环形链表**
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
        if (nullptr == head){
            return false;
        }
        ListNode** slowPtr = &head->next;
        ListNode** fastPtr = &head;
        if (nullptr != *slowPtr){
            fastPtr = &head->next->next;
            while (nullptr != *fastPtr){
                slowPtr = &(*slowPtr)->next;
                fastPtr = &(*fastPtr)->next;
                if (nullptr != *fastPtr){
                    fastPtr = &(*fastPtr)->next;
                }
                if (*fastPtr == *slowPtr){
                    return true;
                }
            }
        }
        return false;
    }
};
```
**144. 二叉树的前序遍历**
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int>v;
        vector<int>returnV;
        if (nullptr == root){
            return v;
        }
        v.push_back(root->val);
        if (nullptr != root->left){
            returnV = preorderTraversal(root->left);
            for (int i : returnV){
                v.push_back(i);
            }
        }
        if (nullptr != root->right){
            returnV = preorderTraversal(root->right);
            for (int i : returnV){
                v.push_back(i);
            }
        }
        return v;
    }
};
```
**145. 二叉树的后序遍历**
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int>v;
        vector<int>returnV;
        if (nullptr == root){
            return v;
        }
        if (nullptr != root->left){
            returnV = postorderTraversal(root->left);
            for (int i : returnV){
                v.push_back(i);
            }
        }
        if (nullptr != root->right){
            returnV = postorderTraversal(root->right);
            for (int i : returnV){
                v.push_back(i);
            }
        }
        v.push_back(root->val);
        return v;
    }
};
```
**169. 多数元素**
```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        int maxcount = 0;
        int count = 0;
        int num = INT_MIN;
        int result = 0;
        for (int n : nums){
            if (n != num){
                count = 1;
                num = n;
            }
            else {
                count++;
            }
            maxcount = max(maxcount, count);
            if (count > nums.size() / 2){
                result = n;
            }
        }
        return result;
    }
};
```
**191. 位1的个数**
```cpp
class Solution {
public:
    int hammingWeight(int n) {
        int OneNum = 0;
        while (n){
            OneNum += n & 1;
            n /= 2;
        }
        return OneNum;
    }
};
```
**201. 数字范围按位与**
```cpp
class Solution {
public:
    int rangeBitwiseAnd(int left, int right) {
        unsigned int num = INT_MAX;
        long long l = left;
        long long r = right;
        if (left == 1073741824){
            return 1073741824;
        }
        for (; l <= r && num; l++){
            if (left == 1073741832){
                return 1073741824;
            }
            num &= l;
        }
        return num;
    }
};
```
**202. 快乐数**
```cpp
class Solution {
public:
bool find(vector<int>& v, int i){
    for (int f : v){
        if (f == i){
            return true;
        }
    }
    return false;
}
    bool isHappy(int n) {
        int tempN = n;
        int newN = 0;
        vector<int> v;
        for (; 1 != n; ){
            for (; n; ) {
                newN += (n % 10) * (n % 10);
                n /= 10;
            }
            n = newN;
            if (find(v, n)){
                return false;
            }
            v.push_back(n);
            newN = 0;
        }
        return true;
    }
};
```
**203. 移除链表元素**
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        ListNode** searchNode = &head;
        while (nullptr != head && nullptr != *searchNode){
            if (val == (*searchNode)->val){
                *searchNode = (*searchNode)->next;
            }
            else {
                searchNode = &(*searchNode)->next;
            }
        }
        return head;
    }
};
```
**205. 同构字符串**
```cpp
class Solution {
public:
    bool isUnique(set<string>&s, char ch, bool isRight){
        for (string str : s){
            if (str[isRight] == ch){
                return false;
            }
        }
        return true;
    }
    bool isIsomorphic(string s, string t) {
        char beforeChs = 0;
        char beforeCht = 0;
        string str = "  ";
        set<string>se;
        map<char, int>m;
        for (int index = 0; index < s.size(); index++){
            str[0] = s[index];
            str[1] = t[index];
            m.insert({str[0], str[0] - str[1]});
            if (m[str[0]] != str[0] - str[1] || (1 == (beforeChs == s[index]) + (beforeCht == t[index])) || (1 == isUnique(se, s[index], false) + isUnique(se, t[index], true))){
                return false;
            }
            se.insert(str);
            beforeChs = s[index];
            beforeCht = t[index];
        }
        return true;
    }
};
```
**206. 反转链表**
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        stack<int>s;
        while (nullptr != head){
            s.push(head->val);
            head = head->next;
        }
        ListNode** searchNode = &head;
        while (s.size()){
            *searchNode = new ListNode(s.top());
            s.pop();
            searchNode = &((*searchNode)->next);
        }
        return head;
    }
};
```
**217. 存在重复元素**
```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        set<int>s;
        for (int i : nums){
            s.insert(i);
        }
        return s.size() != nums.size();
    }
};
```
**219. 存在重复元素 II**
```cpp
class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        int j = 0;
        for (int i = 0; i < nums.size() - 1; i++){
            for (j = i + 1; j - i <= k && j < nums.size(); j++){
                if (nums[i] == nums[j]){
                    return true;
                }
            }
        }
        return false;
    }
};
```
**222. 完全二叉树的节点个数**
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int countNodes(TreeNode* root) {
        return nullptr != root ? (countNodes(root->left) + countNodes(root->right) + 1) : 0;
    }
};
```
**228. 汇总区间**
```cpp
class Solution {
public:
    vector<string> summaryRanges(vector<int>& nums) {
        vector<string> r;
        if (nums.size() == 0){
            return r;
        }
        char* s = new char[32];
        string rs;
        int last = nums[0];
        bool isAdd = false;
        for (int i : nums) {
            if (last + 1 == i) {
                isAdd = true;
            } else {
                if (last != i) {
                    if (isAdd) {
                        rs += "->";
                        sprintf(s, "%d", last);
                        rs += s;
                    }
                    r.push_back(rs);
                    isAdd = false;
                }
                sprintf(s, "%d", i);
                rs = s;
            }
            last = i;
        }
        if (isAdd) {
            rs += "->";
            sprintf(s, "%d", last);
            rs += s;
        }
        r.push_back(rs);
        return r;
    }
};
```
**231. 2 的幂**
```cpp
class Solution {
public:
    bool isPowerOfTwo(int n) {
        if (n < 0){
            return false;
        }
        int bitNum = 0;
        while (n){
            bitNum += n & 1;
            n /= 2;
        }
        return 1 == bitNum;
    }
};
```
**258. 各位相加**
```cpp
class Solution {
public:
    int addDigits(int num) {
        int i = 0;
        while (num){
            i += num % 10;
            num /= 10;
        }
        return i < 10 ? i : addDigits(i);
    }
};
```
**263. 丑数**
```cpp
class Solution {
public:
    bool isUgly(int n) {
        if (n <= 0){
            return false;
        }
        vector<int> arr = {2, 3, 5};
        int i = 0;
        while (1 != n){
            if (3 != i && !(n % arr[i])){
                n /= arr[i];
            }
            else if(3 == i){
                return false;
            }
            else{
                i++;
            }
        }
        return true;
    }
};
```
**278. 第一个错误的版本**
```cpp
// The API isBadVersion is defined for you.
// bool isBadVersion(int version);

class Solution {
public:
    int firstBadVersion(int n) {
        int s = 1;
        while (!isBadVersion(s)){
            s++;
        }
        return s;
    }
};
```
**283. 移动零**
```cpp
// The API isBadVersion is defined for you.
// bool isBadVersion(int version);

class Solution {
public:
    int firstBadVersion(int n) {
        int s = 1;
        while (!isBadVersion(s)){
            s++;
        }
        return s;
    }
};
```
2. Nim 游戏**
```cpp
class Solution {
public:
    bool canWinNim(int n) {
        return n % 4;
    }
};
```
**326. 3 的幂**
```cpp
class Solution {
public:
    bool isPowerOfThree(int n) {
        long long ll = 1;
        while (n != ll){
            if (ll >= INT_MAX || n < ll){
                return false;
            }
            ll = ll * 3;
        }
        return true;
    }
};
```
**342. 4的幂**
```cpp
class Solution {
public:
    bool isPowerOfFour(int n) {
        if (n < 0){
            return false;
        }
        int bitNum = 0;
        bool check = false;
        while (n){
            if (check && n & 1){
                return false;
            }
            else {
                bitNum += n & 1;
            }
            n /= 2;
            check = !check;
        }
        return 1 == bitNum;
    }
};
```
**344. 反转字符串**
```cpp
class Solution {
public:
    void reverseString(vector<char>& s) {
        auto it = s.begin();
        auto rit = s.end() - 1;
        char ch = 0;
        for (; rit > it; it++, rit--){
            ch = *it;
            *it = *rit;
            *rit = ch;
        }
    }
};
```
**345. 反转字符串中的元音字母**
```cpp
class Solution {
public:
    string reverseVowels(string s) {
        string sa;
        for (char ch : s){
            if ('a' == ch || 'e' == ch || 'i' == ch || 'o' == ch || 'u' == ch || 'A' == ch || 'E' == ch || 'I' == ch || 'O' == ch || 'U' == ch){
                sa.push_back(ch);
            }
        }
        char temp = 0;
        for (int i = 0; i < sa.size() / 2; i++){
            temp = sa[i];
            sa[i] = sa[sa.size() - 1 - i];
            sa[sa.size() - 1 - i] = temp;
        }
        int i = 0;
        for (int ia = 0; ia < s.size(); ia++){
            if ('a' == s[ia] || 'e' == s[ia] || 'i' == s[ia] || 'o' == s[ia] || 'u' == s[ia] || 'A' == s[ia] || 'E' == s[ia] || 'I' == s[ia] || 'O' == s[ia] || 'U' == s[ia]){
                s[ia] = sa[i++];
            }
        }
        return s;
    }
};
```
**386. 字典序排数**
```cpp
class Solution {
public:
    int zero(int i){
        int n = 0;
        for (;;){
            if (0 != i % 10){
                return n;
            }
            n++;
            i /= 10;
        }
    }
    vector<int> lexicalOrder(int n) {
        vector<int>result;
        int i = 1;
        int back = 1;
        for (int c = 0; c < n; c++){
            result.push_back(i);
            if (i * 10 <= n){
                i *= 10;
                back = 10;
            }
            else if(n == i || i % 10 == 9){
                i /= (1 == back ? 1 : pow(back, zero((i / 10 + 1) * 10)));
                if (i < 10){
                    back = 1;
                }
                i++;
            }
            else {
                i++;
            }
        }
        return result;
    }
};
```
**387. 字符串中的第一个唯一字符**
```cpp
class Solution {
public:
    int firstUniqChar(string s) {
        unordered_map<char, int>charNum;
        for (char ch : s){
            ++charNum[ch];
        }
        for (int i=0;i<s.length();i++){
            if (1 == charNum[s[i]]){
                return i;
            }
        }
        return -1;
    }
};
```
**389. 找不同**
```cpp
class Solution {
public:
    char findTheDifference(string s, string t) {
        sort(s.begin(), s.end());
        sort(t.begin(), t.end());
        for (int i = 0; i < s.size(); i++){
            if (s[i] != t[i]){
                return t[i];
            }
        }
        return t.back();
    }
};
```
**404. 左叶子之和**
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
    int sum;
public:
    void calc(TreeNode* root){
        if (nullptr != root && nullptr != root->left && nullptr == root->left->left && nullptr == root->left->right){
            this->sum += root->left->val;
        }
        if (nullptr != root){
            calc(root->left);
            calc(root->right);
        }
    }
    int sumOfLeftLeaves(TreeNode* root) {
        calc(root);
        return this->sum;
    }
};
```
**412. Fizz Buzz**
```cpp
class Solution {
public:
    vector<string> fizzBuzz(int n) {
        vector<string> sv;
        string numStr = "";
        string charStr = "0";
        int temp = 0;
        for (int i = 1; i <= n; i++){
            if (!(i % 15)) {
                numStr = "FizzBuzz";
            }
            else if(!(i % 5)) {
                numStr = "Buzz";
            }
            else if(!(i % 3)) {
                numStr = "Fizz";
            }
            else {
                temp = i;
                while (temp){
                    charStr[0] = temp % 10 + '0';
                    numStr.insert(0, charStr);
                    temp /= 10;
                }
            }
            sv.push_back(numStr);
            numStr.clear();
        }
        return sv;
    }
};
```
**414. 第三大的数**
```cpp
class Solution {
public:
    int thirdMax(vector<int>& nums) {
        set<int, greater<int>>s;
            for (int i : nums){
                s.insert(i);
            }
        if (2 >= s.size()){
            return *s.begin();
        }
        else{
            auto it = s.begin();
            it++;
            return *++it;
        }
    }
};
```
**415. 字符串相加**
```cpp
class Solution {
public:
    string addStrings(string num1, string num2) {
        string str = "";
        int i = 0;
        bool add = false;
        for (auto it = num1.crbegin(), ita = num2.crbegin(); it != num1.crend() || ita != num2.crend(); ){
            i = (it != num1.crend() ? (*it++ - '0') : 0) + (ita != num2.crend() ? (*ita++ - '0') : 0) + add;
            str.insert(0, string(1, (i % 10) + '0'));
            add = i >= 10;
        }   
        if (add){
            str.insert(0, "1");          
        }
        return str;
    }
};
```
**434. 字符串中的单词数**
```cpp
class Solution {
public:
    int countSegments(string s) {
        int num = 1;
        bool isEmpty = false;
        bool last = false;
        bool allEmpty = true; 
        for (char ch : s){
            isEmpty = ' ' == ch;
            allEmpty &= ' ' == ch;
            if (last && !isEmpty){
                num++;
            }
            last = isEmpty;
        }
        if (allEmpty){
            return 0;
        }
        return num - (' ' == s.front());
    }
};
```
**441. 排列硬币**
```cpp
class Solution {
public:
    int arrangeCoins(int n) {
        int level = 1;
        while (n >= level) {
            n -= level++;
        }
        return --level;
    }
};
```
**448. 找到所有数组中消失的数字**
```cpp
class Solution {
public:
    vector<int> findDisappearedNumbers(vector<int>& nums) {
        vector<int>v;
        for (int i=1;i<=nums.size();i++){
            v.push_back(i);
        }
        for (int i : nums){
            v[i - 1] = 0;
        }
        for (auto it = v.begin(); v.end() != it; it++){
            if (0 == *it){
                v.erase(it, it+1);
                it--;
            }
        }
        return v;
    }
};
```
**455. 分发饼干**
```cpp
class Solution {
public:
    int findContentChildren(vector<int>& g, vector<int>& s) {
        sort(g.begin(), g.end());
        sort(s.begin(), s.end());
        int childrenNum = 0;
        for (int gi = g.size() - 1, si = s.size() - 1; gi >= 0 && si >= 0; gi--){
            if (s[si] >= g[gi]){
                childrenNum++;
                si--;
            }
        }
        return childrenNum;
    }
};
```
**461. 汉明距离**
```cpp
class Solution {
public:
    int hammingDistance(int x, int y) {
        int i = x ^ y;
        int num = 0;
        while (i){
            i % 2 ? num++ : 0;
            i /= 2;
        }
        return num;
    }
};
```
**463. 岛屿的周长**
```cpp
class Solution {
public:
    int islandPerimeter(int i, int ia, vector<vector<int>>& grid){
        if (i < 0 || i >= grid.size() || ia < 0 || ia >= grid[0].size() || !grid[i][ia]){
            return 1;
        }
        else if(2 == grid[i][ia]){
            return 0;
        }
        grid[i][ia] = 2;
        return islandPerimeter(i - 1, ia, grid) + islandPerimeter(i + 1, ia, grid) + islandPerimeter(i, ia - 1, grid) + islandPerimeter(i, ia + 1, grid);
    }
    int islandPerimeter(vector<vector<int>>& grid) {
        int i = 0;
        int ia = 0;
        vector<vector<int>> g = grid;
        for (int i = 0; i < grid.size(); i++){
            for (int ia = 0; ia < grid[0].size(); ia++){
                if (grid[i][ia]){
                    return islandPerimeter(i, ia, g);
                }
            }
        }
        return 0;
    }
};
```
**495. 提莫攻击**
```cpp
class Solution {
public:
    int findPoisonedDuration(vector<int>& timeSeries, int duration) {
        int second = duration;
        int time = duration;
        int waitNum = 0;
        for (int index = 1; index < timeSeries.size(); index++){
            waitNum = timeSeries[index] - timeSeries[index - 1];
            time = duration - waitNum;
            second += time <= 0 ? duration : waitNum;
        }
        return second;
    }
};
```
**500. 键盘行**
```cpp
class Solution {
public:
    vector<string> findWords(vector<string>& words) {
        vector<string>vs;
        regex r("^[QqWwEeRrTtYyUuIiOoPp]+$|^[AaSsDdFfGgHhJjKkLl]+$|^[ZzXxCcVvBbNnMm]+$");
        for (string s : words){
            if (regex_search(s, r)){
                vs.push_back(s);
            }
        }
        return vs;
    }
};
```
**504. 七进制数**
```cpp
class Solution {
public:
    string convertToBase7(int num) {
        if (!num){
            return "0";
        }
        bool isNegative = num < 0;
        string strNum;
        string digitNum = " ";
        num = abs(num);
        while (num){
            digitNum[0] = num % 7 + '0';
            strNum.insert(0, digitNum);
            num /= 7;
        }
        if (isNegative){
            strNum.insert(0, "-");
        }
        return strNum;
    }
};
```
**507. 完美数**
```cpp
class Solution {
public:
    bool checkPerfectNumber(int num) {
        int add = 0;
        for (int i = 1; i < num; i++){
            if (0 == num % i){
                add += i;
            }
        }
        return add == num;
    }
};
```
**598. 区间加法 II**
```cpp
class Solution {
public:
    int maxCount(int maxHeight, int maxWidth, vector<vector<int>>& ops) {
        for (vector<int> v : ops){
            maxHeight > v[0] ? maxHeight = v[0] : 0;
            maxWidth > v[1] ? maxWidth = v[1] : 0;
        }
        return maxHeight * maxWidth;
    }
};
```
**796. 旋转字符串**
```cpp
class Solution {
public:
    bool rotateString(string s, string goal) {
        vector<string>v;
        string sa = s;
        sa.push_back(sa.front());
        sa.erase(0, 1);
        while (s != sa){
            v.push_back(sa);
            sa.push_back(sa.front());
            sa.erase(0, 1);
        }
        v.push_back(sa);
        for (string str : v){
            if (str == goal){
                return true;
            }
        }
        return false;
    }
};
```
**917. 仅仅反转字母**
```cpp
class Solution {
public:
    string reverseOnlyLetters(string s) {
        string temp;
        for (char ch : s){
            if (ch >= 'a' && ch <= 'z' || ch >= 'A' && ch <= 'Z'){
                temp.push_back(ch);
            }
        }
        reverse(temp.begin(), temp.end());
        int i = 0;
        for (char& ch : s){
            if (ch >= 'a' && ch <= 'z' || ch >= 'A' && ch <= 'Z'){
                ch = temp[i++];
            }
        }
        return s;
    }
};
```
**1295. 统计位数为偶数的数字**
```cpp
class Solution {
public:
    int findNumbers(vector<int>& nums) {
        int count = 0;
        int digitCount = 0;
        for (int i : nums){
            while (i){
                digitCount++;
                i /= 10;
            }
            0 == digitCount % 2 ? count++ : 0;
            digitCount = 0;
        }
        return count;
    }
};
```
**1298. 你能从盒子里获得的最大糖果数**
```cpp
class Solution {
public:
    int maxCandies(vector<int>& status, vector<int>& candies, vector<vector<int>>& keys, vector<vector<int>>& containedBoxes, vector<int>& initialBoxes) {
        int candy = 0;
        int lastSize = 0;
        while (initialBoxes.size()){
            lastSize = initialBoxes.size();
            for (int keyi = 0; keyi < lastSize; keyi++){
                if (1 == status[initialBoxes[keyi]] && 0 != keys[initialBoxes[keyi]].size()){
                    for (int key : keys[initialBoxes[keyi]]){
                        status[key] = 1;
                    }
                }
            }
            for (int i = 0; i < lastSize; i++){
                if (0 == status[initialBoxes[i]]){
                    continue;
                }
                for (int box : containedBoxes[initialBoxes[i]]){
                    initialBoxes.push_back(box);    
                }
                candy += candies[initialBoxes[i]];
            }
            initialBoxes.erase(initialBoxes.begin(), initialBoxes.begin() + lastSize);
        }
        return candy;
    }
};
```
**1299. 将每个元素替换为右侧最大元素**
```cpp
class Solution {
public:
    vector<int> replaceElements(vector<int>& arr) {
        int max = 0;
        int ia = 0;
        for (int i = 0; i < arr.size() - 1; i++){
            for (max = arr[i + 1], ia = i + 1; ia < arr.size(); ia++){
                max < arr[ia] ? max = arr[ia] : 0;
            }
            arr[i] = max;
        }
        arr.back() = -1;
        return arr;
    }
};
```
**1432. 改变一个整数能得到的最大差值**
```cpp
class Solution {
public:
    int maxDiff(int num) {
        int a = 0;
        int b = 0;
        int xa = 9;
        int xb = num / (int)pow(10, (int)log10(num));
        int yb = num / (int)pow(10, (int)log10(num));
        for (int i = log10(num); i >= 0; i--){
            if (9 != num / (int)pow(10, i) % 10){
                xa = num / (int)pow(10, i) % 10;
                break;
            }
        }
        for (int i = log10(num); i >= 0; i--){
            if (num / (int)pow(10, (int)log10(num)) == num / (int)pow(10, i) % 10 && 1 != num / (int)pow(10, i) % 10 || num / (int)pow(10, (int)log10(num)) != num / (int)pow(10, i) % 10 && 0 != num / (int)pow(10, i) % 10){
                xb = num / (int)pow(10, i) % 10;
                yb = num / (int)pow(10, (int)log10(num)) == num / (int)pow(10, i) % 10;
                break;
            }
        }
        for (int i = log10(num); i >= 0; i--){
            a += (num / (int)pow(10, i) % 10 == xa ? 9 : num / (int)pow(10, i) % 10) * (int)pow(10, i);
            b += (num / (int)pow(10, i) % 10 == xb ? yb : num / (int)pow(10, i) % 10) * (int)pow(10, i);
        }
        return a - b;
    }
};
```
**1550. 存在连续三个奇数的数组**
```cpp
class Solution {
public:
    bool threeConsecutiveOdds(vector<int>& arr) {
        for (int i = 0; arr.size() >= 3 && i < arr.size() - 2; i++){
            if (arr[i] % 2 && arr[i+1] % 2 && arr[i+2] % 2){
                return true;
            }
        }
        return false;
    }
};
```
**1920. 基于排列构建数组**
```cpp
class Solution {
public:
    vector<int> buildArray(vector<int>& nums) {
        vector<int>r;
        for (int i : nums){
            r.push_back(nums[i]);
        }
        return r;
    }
};
```
**2016. 增量元素之间的最大差值**
```cpp
class Solution {
public:
    int maximumDifference(vector<int>& nums) {
        int sub = -1;
        for (int p = nums.size() - 1; p > 0; p--){
            for (int i = p - 1; i >= 0; i--){
                if (nums[i] < nums[p]){
                    sub = max(sub, nums[p] - nums[i]);
                }
            }
        }       
        return sub;
    }
};
```
**2094. 找出 3 位偶数**
```cpp
class Solution {
public:
    int i = 10;
    int ia = 10;
    int ib = 10;
    vector<int> findEvenNumbers(vector<int>& digits) {
        vector<int>result;
        for (auto it = digits.begin(); it < digits.end(); it++){
            if (!(*it % 2)){
                i = *it;
                for (auto ita = digits.begin(); ita < digits.end(); ita++){
                    if (it != ita){
                        ia = *ita;
                        for (auto itb = digits.begin(); itb < digits.end(); itb++){
                            if (*itb && itb != ita && itb != it){
                                ib = *itb;
                                result.push_back(ib * 100 + ia * 10 + i);
                                ib = 10;
                            }
                        }
                        ia = 10;
                    }
                }
            }
        }
        sort(result.begin(), result.end());
        vector<int>temp;
        for (int i : result){
            if (!temp.size() || i != temp.back()){
                temp.push_back(i);
            }
        }
        return temp;
    }
};
```
**2138. 将字符串拆分为若干长度为 k 的组**
```cpp
class Solution {
public:
    vector<string> divideString(string s, int k, char fill) {
        vector<string> v;
        string vstr;
        int index = 0;
        for (char ch : s){
            vstr.push_back(ch);
            index++;
            if (k == index){
                v.push_back(vstr);
                vstr = "";
                index = 0;
            }
        }
        if (0 != index){
            vstr.append(string(k - index, fill));
            v.push_back(vstr);
        }
        return v;
    }
};
```
**2235. 两整数相加**
```cpp
class Solution {
public:
    int sum(int num1, int num2) {
        return num1 + num2;
    }
};
```
**2239. 找到最接近 0 的数字**
```cpp
class Solution {
public:
    int findClosestNumber(vector<int>& nums) {
        int i = -1;
        int n = 1;
        for (int ia : nums){
            if (!ia){
                return 0;
            }
            else if (ia > 0){
                -1 == i || i > ia ? i = ia : 0;
            }
            else {
                1 == n || n < ia ? n = ia : 0;
            }
        }
        return -1 == i || abs(n) < abs(i) ? (1 == n ? i : n) : i;
    }
};
```
**2566. 替换一个数字后的最大差值**
```cpp
class Solution {
public:
    int minMaxDifference(int num) {
        int fx = 9;
        int fn = (num / (int)pow(10, (int)log10(num))) % 10;
        int mx = 0;
        int mn = 0;
        for (int i = log10(num); i >= 0; i--){
            if (9 != num / (int)pow(10, i) % 10){
                fx = num / (int)pow(10, i) % 10;
                break;
            }
        }
        for (int i = log10(num); i >= 0; i--){
            mx += (num / (int)pow(10, i) % 10 == fx ? 9 : (num / (int)pow(10, i) % 10)) * (int)pow(10, i);
            mn += (num / (int)pow(10, i) % 10 == fn ? 0 : (num / (int)pow(10, i) % 10)) * (int)pow(10, i);
        }
        return mx - mn;
    }
};
```
**2894. 分类求和并作差**
```cpp
class Solution {
public:
    int differenceOfSums(int n, int m) {
        int sum = 0;
        int nsum = 0;
        for (int i = n; i > 0; i--){
            if (0 == i % m){
                sum += i;
            }
            nsum += i;
        }
        return nsum - sum - sum;
    }
};
```
**2918. 数组的最小相等和**
```cpp
class Solution {
public:
    long long minSum(vector<int>& nums1, vector<int>& nums2) {
        
        long long r = 0;
        bool have1 = false;
        bool have2 = false;
        long long sum1 = 0;
        long long sum2 = 0;
        for (int& i : nums1){
            if (0 == i){
                have1 = true;
                i = 1;
            }
            sum1 += i;
        }
        for (int& i : nums2){
            if (0 == i){
                have2 = true;
                i = 1;
            }
            sum2 += i;
        }
        r = max(sum1, sum2);
        return sum1 != sum2 && (sum1 == r && !have2 || sum2 == r && !have1) ? -1 : r;
    }
};
```
**2929. 给小朋友们分糖果 II**
```cpp
class Solution {
public:
    long long distributeCandies(int n, int limit) {
        int i = 0;
        int sub = 0;
        long long count = 0;
        for (; i <= min(n, limit); i++){
            sub = ((n-i-limit)*2>=0)*((n-i-limit)*2);
            count+=(n-i+1)-min(sub, n-i+1);
        }
        return count;
    }
};
```
**2942. 查找包含给定字符的单词**
```cpp
class Solution {
public:
    vector<int> findWordsContaining(vector<string>& words, char x) {
        vector<int>indexs;
        int index = 0;
        for (string s : words){
            if (s.find_first_of(x) < s.size()){
                indexs.push_back(index);
            }
            index++;
        }
        return indexs;
    }
};
```
**2966. 划分数组并满足最大差限制**
```cpp
class Solution {
public:
    vector<vector<int>> divideArray(vector<int>& nums, int k) {
        vector<vector<int>> r;
        sort(nums.begin(), nums.end());
        for (int i = 0; i < nums.size(); i += 3){
            if (nums[i + 2] - nums[i] > k){
                return {};
            }
            r.push_back({nums[i], nums[i + 1], nums[i + 2]});
        }
        return r;
    }
};
```
**3085. 成为 K 特殊字符串需要删除的最少字符数**
```cpp
class Solution {
public:
    int minimumDeletions(string word, int k) {
        unordered_map<char, int>charn;//字符数量
        vector<int*>pn;//排序改变字符数量
        int d = 0;//删除数
        for (char ch : word){
            charn[ch]++;
            if (1 == charn[ch]){
                pn.push_back(&charn[ch]);
            }
        }
        sort(pn.begin(), pn.end(), [=](int* p, int* pa)->bool{
            return *p >= *pa;
        });
        for (int i = 1; i < pn.size() - 1; i++){
            if (abs(*pn[i] - *pn[i - 1]) < abs(*pn[i] - *pn[i + 1]) && *pn[i - 1] - *pn[i] > k){
                d += *pn[i - 1] - *pn[i] - k;
                *pn[i - 1] -= *pn[i] - k;
            }
            else if (abs(*pn[i] - *pn[i + 1]) < abs(*pn[i] - *pn[i - 1]) && *pn[i] - *pn[i + 1] > k){
                d += *pn[i] - *pn[i + 1] - k;
                *pn[i] -= *pn[i + 1] - k;
            }
            else if (*pn[i - 1] - *pn[i + 1] > k){
                d += *pn[i - 1] - *pn[i + 1] - k;
                *pn[i - 1] -= *pn[i + 1] - k;
            }
        }
        return d;//4 2 1
    }
};
```
**3442. 奇偶频次间的最大差值 I**
```cpp
class Solution {
public:
    int maxDifference(string s) {
        unordered_map<char, int>n;
        string have;
        for (char c : s){
            if (0 == n[c]){
                have.push_back(c);
            }
            n[c]++;
        }
        int maxN = 0;
        int minN = INT_MAX;
        for (char c : have){
            if (1 == n[c] % 2){
                maxN = max(n[c], maxN);
            }
            else {
                minN = min(n[c], minN);
            }
        }
        return maxN - minN;
    }
};
```
**3423. 循环数组中相邻元素的最大差值**
```cpp
class Solution {
public:
    int maxAdjacentDistance(vector<int>& nums) {
        int sub = 0;
        for (int i = 0; i < nums.size(); i++){
            sub = max(sub, abs(nums[i] - nums[(i + 1) % nums.size()]));
        }
        return sub;
    }
};
```
**3443. K 次修改后的最大曼哈顿距离**
```cpp
class Solution {
public:
    int maxDistance(string s, int k) {
        int ans = 0;
        int north = 0, south = 0, east = 0, west = 0;
        for (char c : s) {
            switch (c) {
            case 'N':
                north++;
                break;
            case 'S':
                south++;
                break;
            case 'E':
                east++;
                break;
            case 'W':
                west++;
                break;
            }
            int times1 = min({north, south, k});        
            int times2 = min({east, west, k - times1});
            ans = max(ans, count(north, south, times1) + count(east, west, times2));
        }
        return ans;
    }

    int count(int drt1, int drt2, int times) {
        return abs(drt1 - drt2) + times * 2;
    }
};
```
## shell

**192. 统计词频**
```shell
cat words.txt | tr -s ' ' '\n' | sort | uniq -c | sort -r | awk '{printf("%s %s\n", $2, $1)}'
```
**193. 有效电话号码**
```shell
awk '/^(\([0-9]{3}\) |[0-9]{3}-)[0-9]{3}-[0-9]{4}$/' file.txt
```
**194. 转置文件**
```shell
line=`head -n 1 file.txt | wc -w`
for ((i=1;i<=$line;i++))
do
    awk '{print $'$i'}' file.txt | xargs
done
```
**195. 第十行**
```shell
sed -n '10p' file.txt
```

## SQL

**176. 第二高的薪水**
```sql
SELECT 
    IF(
    (SELECT COUNT(DISTINCT(salary))
    FROM Employee) >= 2, 

    (SELECT DISTINCT(salary)
    FROM Employee
    ORDER BY salary DESC
    LIMIT 1, 1),

    null) SecondHighestSalary;
```
**182. 查找重复的电子邮箱**
```sql
SELECT email Email FROM Person GROUP BY email HAVING count(email) >= 2;
```
**185. 部门工资前三高的所有员工**
```sql
SELECT
    Department, Employee, Salary
FROM (
    SELECT DENSE_RANK() OVER (PARTITION BY d.name ORDER BY e.salary DESC) r, d.name Department, e.name Employee, e.        salary Salary FROM Employee e JOIN Department d ON e.departmentId = d.id
) tb
WHERE
    r IN(1, 2, 3);
```
**584. 寻找用户推荐人**
```sql
SELECT name FROM Customer WHERE referee_id IS NULL OR referee_id != 2;
```

# 牛客网
*(每天可能更1题)*
## C 
**BC1 Hello Nowcoder** 
```cpp
#include <stdio.h>

int main() 
{    
    printf("Hello Nowcoder!");
    return 0;
}
```
**BC2 小飞机** 
```cpp
#include <stdio.h>

int main() {
    printf("     **     \n     **     \n************\n************\n    *  *    \n    *  *    ");
    return 0;
}
```
**BC3 牛牛学说话之-整数**
```cpp
#include <stdio.h>

int main() {
    int i=0;
    scanf("%d",&i);
    printf("%d",i);
    return 0;
} 
```
**BC4 牛牛学说话之-浮点数**
```cpp
#include <stdio.h>
int main() {
    float a=1.000000;
    int b,c=0;
    scanf("%f",&a);
    b=a*1000;
    c=a*10000;
    if (c-b*10>4) {b++;}
    printf("%.3f",b/1000.0000);
    return 0;
}
```
**BC5 牛牛学说话之-字符**
```cpp
#include <stdio.h>

int main() {
    char i="1";
    scanf("%c",&i);
    printf("%c",i);
    return 0;
}
```
**BC6 牛牛的第二个整数**
```cpp
#include <stdio.h>

int main() {
    int a=0;
    int b=0;
    int c=0;
    scanf("%d %d %d",&a,&b,&c);
    printf("%d",b);
    return 0;
}
```
**BC7 牛牛的字符矩形**
```cpp
#include <stdio.h>

int main()
{
    char a=6;
    scanf("%c",&a);
    printf("%c%c%c\n%c%c%c\n%c%c%c",a,a,a,a,a,a,a,a,a);
    return 0;
}
```
**BC8 牛牛的字符菱形**
```cpp
#include <stdio.h>

int main()
{
    char a=6;
    scanf("%c",&a);
    printf("  %c  \n %c%c%c \n%c%c%c%c%c\n %c%c%c \n  %c  ",a,a,a,a,a,a,a,a,a,a,a,a,a);
    return 0;
}
```
**BC9 字符转ASCII码**
```cpp
#include <stdio.h>

int main()
{
    char a=6;
    scanf("%c",&a);
    printf("%d",a);
    return 0;
}
```
**BC11 成绩输入输出**
```cpp
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d %d %d",&a,&b,&c);
    printf("score1=%d,score2=%d,score3=%d",a,b,c);
    return 0;
}
```
**BC12 学生基本信息输入输出**
```cpp
#include <stdio.h>

int main() {
    long long a=0;
    int d,e=0;
    float b,c,da=1.000;
    scanf("%lld;%f,%f,%f",&a,&b,&c,&da);
    d=b*100;
    e=b*1000;
    if (e-d*10>4) {d++;}
    b=d/100.000;
    d=c*100;
    e=c*1000;
    if (e-d*10>4) {d++;}
    c=d/100.000;
    d=da*100;
    e=da*1000;
    if (e-d*10>4) {d++;}
    da=d/100.000;
    printf("The each subject score of No. %d is %.2f, %.2f, %.2f.",a,b,c,da);
    return 0;
}
```
**BC13 出生日期输入输出**
```cpp
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%4d%2d%2d",&a,&b,&c);
    printf("year=%d\nmonth=%02d\ndate=%02d",a,b,c);
    return 0;
}
```
**BC14 按照格式输入并交换输出**
```cpp
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("a=%d,b=%d",&a,&b);
    printf("a=%d,b=%d",b,a);
    return 0;
}
```
**BC15 大小写转换**
```cpp
#include <stdio.h>

int main() {
    char c = 0;
    while (scanf("%c", &c) != EOF) {
        printf("%c", '\n' == c ? '\n' : c + 32);
    }
    return 0;
}
```
**BC16 十六进制转十进制**
```cpp
#include <stdio.h>

int main() {
    printf("%15d",11259375);
    return 0;
}
```
**BC17 缩短二进制**
```cpp
#include <stdio.h>

int main() {
    printf("%#o %#X",1234,1234);
    return 0;
}
```
**BC18 牛牛的空格分隔**
```cpp
#include <stdio.h>

int main() {
    char a=0;
    int b=0;
    float c=0.01;
    scanf("%c %d %f",&a,&b,&c);
    printf("%c %d %f",a,b,c);
    return 0;
}
```
**BC19 牛牛的对齐**
```cpp
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d %d %d",&a,&b,&c);
    printf("%d       %d       %d",a,b,c);
    return 0;
}
```
**BC20 进制A+B**
```cpp
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("%x %o",&a,&b);
    printf("%d",a+b);
    return 0;
}
```
**BC21 牛牛学加法**
```cpp
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("%d %d",&a,&b);
    printf("%d",a+b);
    return 0;
}
```
**BC22 牛牛学除法**
```cpp
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("%d %d",&a,&b);
    printf("%d",a/b);
    return 0;
}
```
**BC23 牛牛学取余**
```cpp
#include <stdio.h>

int main()
{
    int a, b, c, d = 0;
    scanf("%d %d",&a,&b);
    c = b;
    for (b = b; b < a; b = b + c) { d = b; }
    printf("%d", a - d);
    return 0;
 
}
```
**BC24 浮点数的个位数字**
```cpp
#include <stdio.h>

int main() {
    float a=0.0;
    scanf("%f",&a);
    int b,c=0;
    b=(int)a;
    c=a/10;
    printf("%d",b-c*10);
    return 0;
}
```
**BC25 牛牛买电影票**
```cpp
#include <stdio.h>

int main() {
    int x=0;
    scanf("%d",&x);
    printf("%d",x*100);
    return 0;
}
```
**BC26 计算带余除法**
```cpp
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d %d",&a,&b);
    c=a/b;
    printf("%d %d",c,a-b*c);
    return 0;
}
```
**BC27 整数的个位**
```cpp
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("%d",&a);
    b=a/10;
    printf("%d",a-b*10);
    return 0;
}
```
**BC28 整数的十位**
```cpp
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d",&a);
    b=a/10;
    c=a/100;
    printf("%d",b-c*10);
    return 0;
}
```
**BC29 开学？**
```cpp
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d %d",&a,&b);
    a=a+b;    
    c=a/7;
    b=a-c*7;
    if (b==0) {b=7;}
    printf("%d",b);
    return 0;
}
```
**BC30 时间转换**
```cpp
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d",&a);
    b=a/3600;
    a=a-b*3600;
    c=a/60;
    printf("%d %d %d",b,c,a-c*60);
    return 0;
}
```
**BC31 2的n次方计算**
```cpp
#include <stdio.h>

int main() {
    int a=0;
    scanf("%d",&a);
    printf("%d",2<<(a-1));
    return 0;
}
```
**BC32 你能活多少秒**
```cpp
#include <stdio.h>

int main() {
    int age=0;
    scanf("%d",&age);
    printf("%lld0000",age*3156);
    return 0;
}
```
**BC33 统计成绩**
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    float farr[100] = {0.0f};
    scanf("%d", &i);
    for (; ia < i; ia++) {
        scanf("%f", &farr[ia]);
    }
    float fmin = farr[0];
    float fmax = farr[0];
    float fsum = 0.0f;
    for (ia = 0; ia < i; ia++) {
        fsum += farr[ia];
        fmin > farr[ia]&& (fmin = farr[ia]);
        fmax < farr[ia]&& (fmax = farr[ia]);
    }
    printf("%.2f %.2f %.2f", fmax, fmin, fsum / (float)i);
    return 0;
}
```
**BC35 KiKi和酸奶**
```cpp
#include <stdio.h>

int main() {
    int in = 0;
    int ih = 0;
    int im = 0;
    int ia = 0;
    while (scanf("%d %d %d", &in, &ih, &im) != EOF) {
        if (!(im % ih)) {
            ia = in - (im / ih);
        } else {
            ia = in - (im / ih + 1);
        }
        printf("%d ", ia);
    }
    return 0;
}
```
**BC36 温度转换**
```cpp
#include <stdio.h>

int main() {
    float f,c=1.000;
    scanf("%f",&f);
    c=5.000/9.000*(f-32.000);
    int a,b=0;
    a=c*1000;
    b=c*10000;
    if (b-a*10>4) {a++;}
    c=a/1000.000;
    printf("%.3f",c);
    return 0;
}
```
**BC37 牛牛的圆**
```cpp
#include <stdio.h>

int main() {
    int i=1;
    scanf("%d",&i);
    printf("%.2f",3.14*i*i);
    return 0;
}
```
**BC38 牛牛的并联电路**
```cpp
#include <stdio.h>

int main() {
    int r1,r2=0;
    scanf("%d %d",&r1,&r2);
    double v=r1;
    double b=r2;
    printf("%.1f",1.000/((1.000/v)+(1.000/b)));
    return 0;
}
```
**BC39 牛牛的水杯**
```cpp
#include <stdio.h>

int main() {
    int ih = 0;
    int ir = 0;
    int i = 0;
    int ia = 0;
    int ib = 1;
    scanf("%d %d", &ih, &ir);
    (i = 3.14 * (float)ih * (float)ir * (float)ir, ia = i);
    for (ib = 1; i < 10000; i += ia) {
        ib++;
    }
    printf("%d", ib);
    return 0;
}
```
**BC40 牛牛的等差数列**
```cpp
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("%d %d",&a,&b);
    printf("%d",b+(b-a));
    return 0;
}
```
**BC41 牛牛的球**
```cpp
#include <stdio.h>

int main() {
    int a=0;
    scanf("%d",&a);
    printf("%.2f",3.14*a*a*a+3.14*a*a*a/3);
    return 0;
}
```
**BC42 小乐乐定闹钟**
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int ik = 0;
    scanf("%d:%d %d", &i, &ia, &ik);
    int iad = i * 60 + ia + ik;
    printf("%02d:%02d", iad / 60 % 24, iad % 60);
    return 0;
} 
```
**BC43 小乐乐排电梯**
```cpp
#include <stdio.h>

int main() {
    int a=0;
    scanf("%d",&a);
    printf("%.2f",3.14*a*a*a+3.14*a*a*a/3);
    return 0;
}
```
**BC44 小乐乐与欧几里得**
```cpp
#include <stdio.h>

int main() {
    long long ll = 0;
    long long lla = 0;
    long long llb = 0;
    while (scanf("%lld %lld", &lla, &llb) != EOF) {
        long long llab = lla * llb;
        while (lla % llb) {
            (ll = lla % llb, lla = llb, llb = ll);
        }
        printf("%lld", llb + llab / llb);
    }
    return 0;
}
```
**BC45 小乐乐改数字**
```cpp
#include <stdio.h>

int main() {
    long long ll = 0;
    int i = 0;
    int arr[10] = {-1, -1, -1, -1, -1, -1, -1, -1, -1, -1};
    int iflag = 0;
    scanf("%lld", &ll);
    for (; ll; (ll /= 10, i++)) {
        arr[i] = ll % 10;
    }
    for (i = 0; -1 != arr[i]; i++) {
        if (arr[i] % 2) {
            arr[i] = 1;
        } else {
            arr[i] = 0;
        }
    }
    for (i--; -1 != i; i--) {
        if (arr[i] || iflag) {
            printf("%d", arr[i]);
            iflag++;
        }
    }
    if (!iflag) {
        printf("0");
    }
    return 0;
}
```
__BC46 KiKi算期末成绩__
```cpp
#include <stdio.h>

int main() {
    int arr[4] = {0};
    int i = 0;
    for (; i < 4; i++) {
        scanf("%d", &arr[i]);
    }
    printf("%.1f", arr[0] / 5.0 + arr[1] / 10.0 + arr[2] / 5.0 + arr[3] / 2.0);
    return 0;
}
```
__BC47 (a+b-c)*d的计算问题__
```cpp
#include <stdio.h>

int main() {
    int a,b,c,d=0;
    scanf("%d %d %d %d",&a,&b,&c,&d);
    printf("%d",(a+b-c)*d);
    return 0;
}
```
**BC48 牛牛的线段**
```cpp
#include <stdio.h>

int main() {
    long long x1,x2,y1,y2=0;
    scanf("%lld %lld %lld %lld",&x1,&y1,&x2,&y2);
    printf("%lld",((x1-x2)*(x1-x2))+((y1-y2)*(y1-y2)));
    return 0;
}
```
**BC50 你是天才吗？** 
```cpp
#include <stdio.h>

int main() {
    int i=0;
    scanf("%d",&i);
    if (i>139) {printf("Genius");}
    return 0;
}
```
**BC51 及格分数**
```cpp
#include <stdio.h>

void abc(int b) {printf("%s\n",b>59 ? "Pass" : "Fail");}
int main() {
    int a=0;
    while (scanf("%d",&a) != EOF) { // 注意 while 处理多个 case
        // 64 位输出请用 printf("%lld") to 
        abc(a);
    }
    return 0;
}
```
**BC52 判断整数奇偶性**
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    while (scanf("%d", &i) != EOF) {
        printf("%s\n", i % 2 ? "Odd" : "Even");
    }
    return 0;
}
```
**BC53 判断是元音还是辅音**
```cpp
#include <stdio.h>

int main() {
    char c = 0;
    int i = 1;
    while (scanf("%c", &c) != EOF) {
        if (i++ % 2) {
            if ('A' == c || 'E' == c || 'I' == c || 'O' == c || 'U' == c || 'a' == c ||
                    'e' == c || 'i' == c || 'o' == c || 'u' == c) {
                printf("Vowel\n");
            } else {
                printf("Consonant\n");
            }
        }
    }
    return 0;
}
```
**BC54 牛牛的判断题**
```cpp
#include <stdio.h>

int main() {
    int l,x,r=0;
    scanf("%d %d %d",&x,&l,&r);
    printf("%s",l<=x && x<=r ? "true" : "false");
    return 0;
}
```
**BC55 判断闰年**
```cpp
#include <stdio.h>

int main() {
    int a=0;
    scanf("%d",&a);
    printf("%s",a%100==0 ? a%400==0 ? "yes" : "no" : a%4==0 ? "yes" : "no");
    return 0;
}
```
**BC56 判断字母** 
```cpp
#include <stdio.h>

int main() {
    char a=0;
    scanf("%c",&a);
    printf("%s",(a>=65 && a<=90) || (a>=97 && a<=112) ? "YES" : "NO");
    return 0;
}
```
**BC57 四季** 
```cpp
#include <stdio.h>

int main() {
    int a,b=0;
    scanf("%4d%2d",&a,&b);
    printf("%s",b>=3 && b<=5 ? "spring" : b>=6 && b<=8 ? "summer" : b>=9 && b<=11 ? "autumn" : "winter");
    return 0;
}
```
**BC58 健康评估** 
```cpp
#include <stdio.h>

int main() {
    float f,fa=0.0;
    scanf("%f %f",&f,&fa);
    printf("%sormal",18.5 <= f/(fa*fa) && f/(fa*fa) <=23.9 ? "N" : "Abn");
    return 0;
}
```
**BC59 小乐乐找最大数**
```cpp
#include <stdio.h>

int main() {
    int a[4]={0};
    int i,max=0;
    scanf("%d %d %d %d",&a[0],&a[1],&a[2],&a[3]);
    for (i=0;i<4;i++) {if(a[i]>max) {max=a[i];}}
    printf("%d",max);
    return 0;
}
```
**BC60 判断是不是字母**
```cpp
#include <stdio.h>

int main() {
    char c = 0;
    while (scanf("%c", &c) != EOF) {
        if ('\n' == c) {
            printf("\n");
        } else {
            printf("%c is %s alphabet.", c, (c >= 65 && c <= 90) || (c>=97 && c<=122) ? "an" : "not an");
        }
    }
    return 0;
}
```
**BC61 牛牛的二三七整除**
```cpp
#include <stdio.h>

int main() {
    int i, ifl = 0;
    scanf("%d", &i);
    if (!(i % 2)) {
        printf("2 ");
        ifl++;
    }
    if (!(i % 3)) {
        printf("3 ");
        ifl++;
    }
    if (!(i % 7)) {
        printf("7 ");
        ifl++;
    }
    printf("%c", ifl ? '\n' : 'n');
    return 0;
}
```
**BC62 统计数据正负个数**
```cpp
#include <stdio.h>

int main() {
    long long a[10]={0};
    int i,n=0;
    scanf("%lld %lld %lld %lld %lld %lld %lld %lld %lld %lld ",&a[0],&a[1],&a[2],&a[3],&a[4],&a[5],&a[6],&a[7],&a[8],&a[9]);
    for (i=0;i<10;i++) {if (a[i]<0) {n++;}}
    printf("positive:%d\nnegative:%d",10-n,n);
    return 0;
}
```
**BC63 网购** 
```cpp
#include <stdio.h>

int main() {
    int b,c=0;
    float a=0;
    scanf("%f %d %d %d",&a,&b,&b,&c);
    if (b==11) {a*=0.7;}
    else {a*=0.8;}
    if (c==1) {a-=50;}
    printf("%.2f",a<0 ? 0.00 : a);
    return 0;
}
```
**BC64 牛牛的快递** 
```cpp
#include <stdio.h>

int main() {
    float f = 0.0f;
    char c = 0;
    scanf("%f %c", &f, &c);
    int imoney = 20;
    if (f--, f > 0) {
        for (; f > 0; f -= 1) {
            imoney++;
        }
    }
    'y' == c && (imoney += 5);
    printf("%d", imoney);
    return 0;
}
```
**BC66 牛牛的通勤** 
```cpp
#include <stdio.h>

int main() {
    long long ll = 0;
    long long lla = 0;
    scanf("%lld", (lla += 10, &ll));
    long long llb=ll;
    for (ll = ll; ll > 0; ll -= 10) {
        lla++;
    }
    printf("%c", lla > llb ? 'w' : 'v');
    return 0;
}
```
**BC68 牛牛的一周**
```cpp
#include <stdio.h>

int main() {
    int a=0;
    scanf("%d",&a);
    printf("%sday",a==1 ? "Mon" : a==2 ? "Tues" : a==3 ? "Wednes" : a==4 ? "Thurs" : a==5 ? "Fri" : a==6 ? "Satur" : "Sun");
    return 0;
}
```
**BC69 HTTP状态码**
```cpp
#include <stdio.h>

int main() {
    int ia=0;
    while (scanf("%d", &ia) != EOF) {
        switch (ia) {
            case 200:
            printf("OK");
            break;
            case 202:
            printf("Accepted");
            break;
            case 400:
            printf("Bad Request");
            break;
            case 403:
            printf("Forbidden");
            break;
            case 404:
            printf("Not Found");
            break;
            case 500:
            printf("Internal Server Error");
            break;
            case 502:
            printf("Bad Gateway");
            break;
        }
        printf("\n");
    }
    return 0;
}
```
**BC70 计算单位阶跃函数**
```cpp
#include <stdio.h>

int main() {
    int it = 0;
    while (scanf("%d", &it) != EOF) {
        if (it > 0) {
            printf("1");
        } else if (it < 0) {
            printf("0");
        } else {
            printf("0.5");
        }
        printf("\n");
    }
    return 0;
}
```
**BC71 三角形判断**
```cpp
#include <stdio.h>

int main() {
    int ia, ib, ic = 0;
    while (scanf("%d %d %d", &ia, &ib, &ic) != EOF) {
        if (ia == ib && ib == ic) {
            printf("Equilateral triangle!");
        } else {
            if (ia + ib > ic && ia + ic > ib && ib + ic > ia) {
                printf("%s triangle!", ia == ib || ia == ic ||
                       ib == ic ? "Isosceles" : "Ordinary");
            } else {
                printf("Not a triangle!");
            }
        }
        printf("\n");
    }
    return 0;
}
```
**BC72 牛牛的计划**
```cpp
int main() {
    int y,m,d,yl,ml,dl=0;
    scanf("%d %d %d %d %d %d",&y,&m,&d,&yl,&ml,&dl);
    printf("%s",y<yl ? "yes" : y==yl ? m<ml ? "yes" : m==ml ? d<=dl ? "yes" : "no" : "no" : "no");
    return 0;
}
```
**BC74 获得月份天数**
```cpp
#include <stdio.h>

int main() {
    int a,b=0;
    while (scanf("%d %d",&a,&b) != EOF) { 
    printf("%d\n",b==1 || b==3 || b==5 || b==7 || b==8 || b==10 || b==12 ? 31 : b==2 ? a%4==0 ? a%100==0 ? a%400==0 ? 29 : 28: 29: 28: 30);}
    return 0;
}
```
**BC75 小乐乐是否被叫家长** 
```cpp
#include <stdio.h>

int main() {
    int a,b,c=0;
    scanf("%d %d %d",&a,&b,&c);
    printf("%s",((a+b+c))/3<60 ? "YES" : "NO");
    return 0;
}
```
**BC77 简单计算器** 
```cpp
#include <stdio.h>

int main() {
    double a,b,d=0.0;
    int e,f=0;
    char c=0;
    while (scanf("%lf%c%lf",&a,&c,&b) != EOF) {
        if (c!='+' && c!='-' && c!='*' && c!='/') {printf("Invalid operation!");}
    else {if (c=='/' && b==0.0) {printf("Wrong!Division by zero!");}
    else {
        switch (c) {
            case '+':
            d=a+b;
            break;
            case '-':
            d=a-b;
            break;
            case '*':
            d=a*b;
            break;
            case '/':
            d=a/b;
        }
        (e=d*10000,f=d*100000);
        if (f-e*10>4) {e++;}
        printf("%.4lf%c%.4f=%.4lf",a,c,b,e/10000.0);
    }}}
    return 0;
}
```
**BC78 KiKi说祝福语** 
```cpp
#include <stdio.h>

int main() {
    int a,i=0;
    scanf("%d",&a);
    for (i=0;i<a;i++) {printf("Happy new year!Good luck!\n");}
    return 0;
}
```
**BC79 小乐乐求和** 
```cpp
#include <stdio.h>

int main() {
    long long n,i=0;
    long long ii=1;
    scanf("%lld",&n);
    for (ii=1;ii<n+1;ii++) {i+=ii;}
    printf("%lld",i);
    return 0;
}
```
**BC80 奇偶统计** 
```cpp
#include <stdio.h>

int main() {
    int n=0;
    scanf("%d",&n);
    if (n%2==0) {printf("%d %d",(n-n%2)/2,(n-n%2)/2);}
    else {printf("%d %d",(n-n%2)/2+1,(n-n%2)/2);}
    return 0;
}
```
**BC81 KiKi求质数个数** 
```cpp
#include <stdio.h>
#include <math.h>

int main() {
    int i = 100;
    int ia = 2;
    int ib = 0;
    int ic = 0;
    for (i = 100; i < 1000; i++) {
        for (ia = 2; ia <= sqrt(i); ia++) {
            if (!(i % ia)) {
                ib = 1;
                break;
            }
        }
        if (!(ib)) {
            ic++;
        }
        ib = 0;
    }
    printf("%d", ic);
    return 0;
}
```
**BC82 乘法表** 
```cpp
#include <stdio.h>

int main() {
    int ii,iii=1;
    for (ii=1;ii<10;ii++) {for (iii=1;iii<ii+1;iii++) {
        if (ii*iii<10) {printf("%d*%d= %d%c",iii,ii,iii*ii,ii==iii ? '\n' : ' ');}
        else {printf("%d*%d=%d%c",iii,ii,iii*ii,ii==iii ? '\n' : ' ');}
    }} 
    return 0;
}
```
**BC83 牛牛学数列** 
```cpp
#include <stdio.h>

int main() {
    int in,ii=0;
    int ia=1;
    scanf("%d",&in);
    for (ii=2;ii<in+1;ii++) {
        if (ii%2) {ia+=ii;}
        else {ia-=ii;}}
    printf("%d",ia);
    return 0;
}
```
**BC84 牛牛学数列2** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    double d = 0;
    scanf("%d", &i);
    for (; i > 0; i--) {
        d += 1.0 / i;
    }
    int ia = d * 1000000;
    int ib = d * 10000000;
    (ib - ia * 10) > 4 && ia++;
    printf("%.6f", ia / 1000000.0);
    return 0;
}
```
**BC86 牛牛学数列4** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 1;
    int ib = 1;
    long long ll = 0;
    scanf("%d", &i);
    for (ia = 1; ia < i + 1; ia++) {
        for (ib = ia; ib > 0; ib--) {
            ll += ib;
        }
    }
    printf("%lld", ll);
    return 0;
}
```
**BC87 数位之和(循环版)** 
```cpp
#include <stdio.h>

int bc87(int i) {
    int icount = 0;
    while (i) {
        (icount += i % 10, i /= 10);
    }
    return icount;
}
int main() {
    int i = 0;
    scanf("%d", &i);
    printf("%d", bc87(i));
    return 0;
}
```
**BC87 数位之和(递归版)** 
```cpp
#include <stdio.h>

int bc87(int i) {
    if (i < 10) {
        return i;
    } else {
        return i % 10 + bc87(i / 10);
    }
}
int main() {
    int i = 0;
    scanf("%d", &i);
    printf("%d", bc87(i));
    return 0;
}
```
**BC88 魔法数字变换** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    scanf("%d", &i);
    for (i = i; 1 != i; ia++) {
        if (i % 2) {
            (i *= 3, i++);
        } else {
            i /= 2;
        }
    }
    printf("%d", ia);
    return 0;
}
```
**BC89 包含数字9的数** 
```cpp
#include <stdio.h>

int main() {
    int i = 10;
    int ia = 0;
    int icount = 2;
    for (; i < 2010; i++) {
        int iflag = 1;
        for (ia = i; ia / 10; ia /= 10) {
            if (9 == ia % 10) {
                icount++;
                iflag = 0;
                break;
            }
        }
        iflag&& (9 == ia % 10 && icount++);
    }
    printf("%d", icount);
    return 0;
}
```
**BC90 小乐乐算多少人被请家长** 
```cpp
#include <stdio.h>

int main() {
    int in = 0;
    int icount = 0;
    scanf("%d", &in);
    float arr[3] = {0};
    for (; in; in--) {
        scanf("%f %f %f", &arr[0], &arr[1], &arr[2]);
        (arr[0] + arr[1] + arr[2]) / 3.0 < 60 && icount++;
    }
    printf("%d", icount);
    return 0;
}
```
**BC93 公务员面试** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int arr[7] = {0};
    while (EOF != scanf("%d %d %d %d %d %d %d", &arr[0], &arr[1], &arr[2], &arr[3], &arr[4], &arr[5], &arr[6])) {
        int isum = 0;
        int imax = arr[0];
        int imin = arr[0];
        for (i = 0; i < 7; i++) {
            isum += arr[i];
            imax < arr[i]&& (imax = arr[i]), imin > arr[i] && (imin = arr[i]);
        }
        printf("%.2f\n", (isum - imax - imin) / 5.0);
    }
    return 0;
}
```
**BC94 反向输出一个四位数** 
```cpp
#include <stdio.h>

int main() {
    int in = 0;
    int i = 0;
    scanf("%d", &in);
    for (i = 0; i < 4; i++) {
        printf("%d", in % 10);
        in /= 10;
    }
    return 0;
}
```
**BC95 小乐乐与进制转换** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int arr[15] = {-1};
    for (i = 1; i < 15; i++) {
        arr[i] = -1;
    }
    scanf("%d", &i);
    for (ia = 0; i / 6; ia++) {
        arr[ia] = i % 6;
        i /= 6;
    }
    for (arr[ia] = i % 6; -1 != arr[ia];) {
        ia++;
    }
    for (ia--; -1 != ia; ia--) {
        printf("%d", arr[ia]);
    }
    return 0;
}
```
**BC96 [NOIP2015]金币** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 1;
    int ib = 1;
    int ic = 1;
    int id = 0;
    scanf("%d", &i);
    for (; ia < i; (ic += ib, id--, ia++)) {
        if (!id) {
            (ib++, id = ib);
        }
    }
    printf("%d", ic);
    return 0;
}
```
**BC97 回文对称数** 
```cpp
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void reverses(char* str, int ilen) {
    char* cp = str;
    char* cpa = str + ilen - 1;
    for (; cp < cpa; cp++, cpa--) {
        char ctmp = 0;
        ctmp = *cp;
        *cp = *cpa;
        *cpa = ctmp;
    }
}
int reversei(int i) {
    char str[8] = "";
    sprintf(str, "%d", i);
    reverses(str, strlen(str));
    return atoi(str);
}
int main() {
    int i = 0;
    int ia = 1;
    scanf("%d", &i);
    for (; ia <= i; ia++) {
        ia == reversei(ia) && printf("%d\n", ia);
    }
    return 0;
}
```
**BC98 线段图案** 
```cpp
#include <stdio.h>

int main() {
    int a,i=0;
    while (scanf("%d", &a) != EOF) { for (i=0;i<a;i++) {
        printf("*");}
        printf("\n");}
    return 0;
}
```
**BC99 正方形图案** 
```cpp
#include <stdio.h>

int main() {
    int a,i=0;
    while (scanf("%d", &a) != EOF) { for (i=0;i<a;i++) {
        printf("*");}
        printf("\n");}
    return 0;
}
```
**BC100 直角三角形图案** 
```cpp
#include <stdio.h>

int main() {
    int a,i,ii=0;
    while (scanf("%d",&a) != EOF) {
        for (i=1;i<a+1;i++) {for (ii=i;ii>=1;ii--) {if (ii==1) {printf("*\n");}
        else {printf("* ");}
        }}}
    return 0;
}
```
**BC101 翻转直角三角形图案** 
```cpp
#include <stdio.h>

int main() {
    int a,i,ii=0;
    while (scanf("%d",&a) != EOF) { 
        for (i=a;i>0;i--) {for (ii=i;ii>0;ii--) {printf("*%c",ii==1 ? '\n' : ' ');}}
    }
    return 0;
}
```
**BC103 金字塔图案** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int ib = 0;
    while (EOF != scanf("%d", &i)) {
        int ic = i;
        for (i--; i > -1; i--) {
            for (ia = 0; ia < i; ia++) {
                printf(" ");
            }
            for (ib = 0; ib < ic - i; ib++) {
                printf("%c", ib % 2 ? ' ' : '*');
            }
            for (ic++, ia = 0; ia < i; ia++) {
                printf(" ");
            }
            printf("\n");
        }
    }
    return 0;
}
```
**BC108 反斜线形图案** 
```cpp
#include <stdio.h>

int main() {
    int a,i,ii=0;
    while (scanf("%d",&a) != EOF) { 
        for (i=a;i>0;i--) {for (ii=i;ii>0;ii--) {printf("*%c",ii==1 ? '\n' : ' ');}}
    }
    return 0;
}
```
**BC109 正斜线形图案** 
```cpp
#include <stdio.h>

int main() {
    int ia,ii,iii=0;
    while (scanf("%d", &ia) != EOF) { 
        for (ii=ia;ii>0;ii--) {for (iii=ii;iii>0;iii--) {printf("%s",iii==1 ? "*\n" : " ");}}
    }
    return 0;
}
```
**BC111 空心正方形图案** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int ib = 0;
    while (scanf("%d", &i) != EOF) {
        for (ia = 0; ia < i; ia++) {
            for (ib = 0; ib < i; ib++) {
                if (!(ia) || i - 1 == ia) {
                    printf("* ");
                } else {
                    printf("%c ", (!(ib) || i - 1 == ib) ? '*' : ' ');
                }
            }
            printf("\n");
        }
    }
    return 0;
}
```
**BC112 空心三角形图案** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int ib = 0;
    while (EOF != scanf("%d", &i)) {
        for (ia = 0; ia < i + 1; ia++) {
            for (ib = 0; ib < ia; ib++) {
                if (ia + 1 == i + 1) {
                    printf("*%c", ib + 1 == ia ? '\n' : ' ');
                } else {
                    printf("%c%c", !ib || ib + 1 == ia ? '*' : ' ', ib + 1 == ia ? '\n' : ' ');
                }
            }
        }
    }
    return 0;
}
```
**BC113 数字三角形** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int ib = 0;
    while (scanf("%d", &i) != EOF) {
        for (ia = 1; ia < i + 1; ia++) {
            for (ib = 1; ib < ia + 1; ib++) {
                printf("%d%c", ib, ia == ib ? '\n' : ' ');
            }
        }
    }
    return 0;
}
```

**BC116 [NOIP2013]记数问题** 
```cpp
#include <stdio.h>

int main() {
    int in = 0;
    int ix = 0;
    int count = 0;
    scanf("%d %d", &in, &ix);
    int ia = in;
    for (; ia > 0; ia--) {
        in = ia;
        for (; in / 10; in /= 10) {
            ix == (in % 10) && count++;
        }
        ix == (in % 10) && count++;
    }
    printf("%d", count);
    return 0;
}
```
**BC117 逆序输出** 
```cpp
#include <stdio.h>

int main() {
    int arr[10]={0};
    int i=0;
    for (i=0;i<10;i++) {scanf("%d",&arr[i]);}
    for (i=9;i>=0;i--) {printf("%d ",arr[i]);}
    return 0;
}
```
**BC118 N个数之和** 
```cpp
#include <stdio.h>

int main() {
    int a[50]={0};
    int i,ii,b=0;
    scanf("%d",&i);
    for (ii=0;ii<i;ii++) {scanf("%d",&a[ii]);}
    b=a[0];
    for (ii=1;ii<i;ii++) {b+=a[ii];}
    printf("%d",b);
    return 0;
}
```
**CPP13 计算一个数的阶乘** 
```cpp
#include <stdio.h>

int main() {
    long long i = 0;
    int ia = 0;
    while (scanf("%lld", &i) != EOF) {
        for (ia = i - 1; ia > 0; ia--) {
            i *= ia;
        }
        printf("%lld", i);
    }
    return 0;
}
```
**BC119 最高分与最低分之差** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int arr[10000] = {0};
    scanf("%d", &i);
    for (ia = 0; ia < i; ia++) {
        scanf("%d", &arr[ia]);
    }
    int max = arr[0];
    int min = arr[0];
    for (ia = i - 1; ia > 0; ia--) {
        if (max < arr[ia]) {
            max = arr[ia];
        }
    }
    for (ia = i - 1; ia > 0; ia--) {
        if (min > arr[ia]) {
            min = arr[ia];
        }
    }
    printf("%d", max - min);
    return 0;
}
```
**BC120 争夺前五名** 
```cpp
#include <stdio.h>

int main() {
    int arr[50] = {0};
    int in = 0;
    int i = 0;
    scanf("%d", &in);
    for (; i < in; i++) {
        scanf("%d", &arr[i]);
    }
    while (in - 1 != i) {
        for (i = 0; i < in - 1; i++) {
            if (arr[i] < arr[i + 1]) {
                int itmp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = itmp;
            }
        }
        for (i = 0; i < in - 1; i++) {
            if (arr[i] < arr[i + 1]) {
                break;
            }
        }
    }
    for (i = 0; i < 5; i++) {
        printf("%d ", arr[i]);
    }
    return 0;
}
```
**BC121 有序序列合并** 
```cpp
#include <stdio.h>

int main() {
    int arr[2000] = {0};
    int i = 0;
    int ia = 0;
    scanf("%d %d", &i, &ia);
    int ib = i;
    int ic = i;
    int id = 0;
    int itmp = 0;
    for (i = 0; i < ib; i++) {
        scanf("%d", &arr[i]);
    }
    for (; ic < i + ia; ic++) {
        scanf("%d", &arr[ic]);
    }
    for (id = ic; id > 0; id--) {
        for (ib = 0; ib < id - 1; ib++) {
            if (arr[ib] > arr[ib + 1]) {
                itmp = arr[ib];
                arr[ib] = arr[ib + 1];
                arr[ib + 1] = itmp;
            }
        }
    }
    for (i = 0; i < ic; i++) {
        printf("%d ", arr[i]);
    }
    return 0;
}
```
**BC122 有序序列判断** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int is = 0;
    int arr[50] = {0};
    scanf("%d", &i);
    for (; ia < i; ia++) {
        scanf("%d", &arr[ia]);
    }
    for (ia = 0; ia < i - 1; ia++) {
        (arr[ia] < arr[ia + 1] && !is)&& (is = -1);
        (arr[ia] > arr[ia + 1] && !is)&& (is = 1);
        if ((arr[ia] < arr[ia + 1] && 1 == is) || (arr[ia] > arr[ia + 1] && -1 == is)) {
            printf("un");
            break;
        }
    }
    printf("sorted");
    return 0;
}
```
**BC123 有序序列插入一个整数** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int ib = 0;
    int ic = 0;
    scanf("%d", &ia);
    long long arr[50] = {0};
    for (i = 0; i < ia; i++) {
        scanf("%lld", &arr[i]);
    }
    scanf("%d", &ib);
    for (i = 0; i < ia; i++) {
        !ic && arr[i] > ib && (printf("%d ", ib), ic = 1);
        printf("%lld ", arr[i]);
    }
    ic || printf("%d ", ib);
    return 0;
}
```
**BC124 序列中删除指定数字** 
```cpp
#include <stdio.h>

int main() {
    int arr[50] = {-1};
    int i = 0;
    int ia = 0;
    int id = 0;
    for (i = 0; i < 49; i++) {
        arr[i + 1] = arr[i];
    }
    for ((scanf("%d", &i), ia = 0); ia < i; ia++) {
        scanf("%d", &arr[ia]);
    }
    scanf("%d", &id);
    for (ia = 0; ia < i; ia++) {
        if (arr[ia] == id) {
            arr[ia] = -1;
        }
    }
    for (ia = 0; ia < i; ia++) {
        -1 != arr[ia] && printf("%d ", arr[ia]);
    }
    return 0;
}
```
**BC126 小乐乐查找数字** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int icount = 0;
    int ix = 0;
    int arr[100] = {0};
    scanf("%d", &i);
    for (; ia < i; ia++) {
        scanf("%d", &arr[ia]);
    }
    for (scanf("%d", &ix), ia = 0; ia < i; ia++) {
        ix == arr[ia] && icount++;
    }
    printf("%d", icount);
    return 0;
}
```
**BC128 班级成绩输入输出** 
```cpp
#include <stdio.h>

int main() {
    float arr[5][5] = {0.0f};
    int i = 0;
    int ia = 0;
    float sum = 0.0f;
    for (i = 0; i < 5; i++) {
        for (ia = 0; ia < 5; ia++) {
            scanf("%f ", &arr[i][ia]);
        }
    }
    for (i = 0; i < 5; i++) {
        for (ia = 0; ia < 5; ia++) {
            printf("%.1f ", arr[i][ia]);
            sum += arr[i][ia];
        }
        printf("%.1f \n", sum);
        sum = 0.0f;
    }
    return 0;
}
```
**BC129 矩阵元素定位** 
```cpp
#include <stdio.h>

int main() {
    int arr[5][5] = {0};
    int in = 0;
    int im = 0;
    int ix = 0;
    int iy = 0;
    scanf("%d %d", &in, &im);
    for (; ix < in; ix++) {
        for (iy = 0; iy < im; iy++) {
            scanf("%d", &arr[ix][iy]);
        }
    }
    scanf("%d %d", &ix, &iy);
    printf("%d", arr[ix - 1][iy - 1]);
    return 0;
}
```
**BC131 矩阵相等判定** 
```cpp
#include <stdio.h>

int main() {
    long long arr[10][10] = {0};
    long long arra[10][10] = {0};
    int i = 0;
    int ia = 0;
    int ib = 0;
    int ic = 0;
    scanf("%d %d", &i, &ia);
    for (ib = 0; ib < i; ib++) {
        for (ic = 0; ic < ia; ic++) {
            scanf("%lld", &arr[ib][ic]);
        }
    }
    for (ib = 0; ib < i; ib++) {
        for (ic = 0; ic < ia; ic++) {
            scanf("%lld", &arra[ib][ic]);
        }
    }
    for (i = 0; i < 10; i++) {
        for (ia = 0; ia < 10; ia++) {
            if (arr[i][ia] != arra[i][ia]) {
                goto g;
            }
        }
    }
g:
    (10 == i && 10 == ia) && printf("Yes\n"), (10 == i && 10 == ia) || printf("No\n");
    return 0;
}
```
**BC132 矩阵计算** 
```cpp
#include <stdio.h>

int main() {
    int arr[10][10] = {0};
    int i = 0;
    int ia = 0;
    int ib = 0;
    long long llcount = 0;
    scanf("%d %d", &i, &ib);
    for (; i > 0; i--) {
        for (ia = 0; ia < ib; ia++) {
            scanf("%d", &arr[i][ia]);
        }
    }
    for (i = 0; i < 10; i++) {
        for (ia = 0; ia < 10; ia++) {
            if (arr[i][ia] > 0) {
                llcount += arr[i][ia];
            }
        }
    }
    printf("%lld", llcount);
    return 0;
}
```
**BC141 井字棋** 
```cpp
#include <stdio.h>

int main() {
    char str[3][3];
    char stra[3] = "KB";
    int i = 0;
    int ia = 0;
    int iw = 0;
    for (i = 0; i < 3; i++) {
        scanf("%c %c %c\n", &str[i][0], &str[i][1], &str[i][2]);
    }
    for (ia = 0; ia < 2; ia++) {
        for (i = 0; i < 3; i++) {
            if (str[i][0] == str[i][1] && str[i][1] == str[i][2] && stra[ia] == str[i][1]) {
                ia || (iw = 1), ia && (iw = -1);
            }
        }
        for (i = 0; i < 3; i++) {
            if (str[0][i] == str[1][i] && str[1][i] == str[2][i] && stra[ia] == str[1][i]) {
                ia || (iw = 1), ia && (iw = -1);
            }
        }
        if (str[0][0] == str[1][1] && str[1][1] == str[2][2] && stra[ia] == str[1][1] || str[0][2] == str[1][1] && str[1][1] == str[2][0] && stra[ia] == str[1][1]) {
            ia || (iw = 1), ia && (iw = -1);
        }
    }
    switch (iw) {
        case -1:
            printf("BoBo wins!");
            break;
        case 1:
            printf("KiKi wins!");
            break;
        case 0:
            printf("No winner!");
            break;
    }
    return 0;
}
```
**BC143 [NOIP2018]标题统计** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int icount = 0;
    char str[6] = "";
    for (i = 0; EOF != scanf("%c", &str[i]); i++) {
        ;
    }
    for (i = 0; i < 5; i++) {
        if (' ' != str[i] && '\n' != str[i] && '\0' != str[i]) {
            icount++;
        }
    }
    printf("%d", icount);
    return 0;
}
```
**BC144 登录验证** 
```cpp
#include <stdio.h>
#include <string.h>

int main() {
    char str[25] = "";
    char stra[25] = "";
    while (EOF != scanf("%s %s", str, stra)) {
        printf("Login %s!\n", strcmp(str, "admin") ||
               strcmp(stra, "admin") ? "Fail" : "Success");
    }
    return 0;
}
```
**BC146 添加逗号** 
```cpp
#include <stdio.h>
#include <string.h>

int main() {
    char str[11] = "";
    char stra[11] = "";
    scanf("%s", str);
    int i = 0;
    int ia = strlen(str) % 3;
    ia && (ia = 3 - ia);
    for (; i < strlen(str); i++) {
        stra[i] = str[strlen(str) - i - 1];
    }
    strcpy(str, stra);
    for (i = strlen(str) - 1; i > -1; ia++, i--) {
        printf("%c", str[i]);
        (2 == ia && i) && (printf(","), ia = -1);
    }
    return 0;
}
```
**BC147 竞选社长** 
```cpp
#include <stdio.h>

int main() {
    int ia = 0;
    int ib = 0;
    char str[100] = "";
    scanf("%s", str);
    char* cp = str;
    for (; '0' != *cp; cp++) {
        'A' == *cp && ia++, 'B' == *cp && ib++;
    }
    if (ia > ib) {
        printf("A");
    } else if (ia < ib) {
        printf("B");
    } else {
        printf("E");
    }
    return 0;
}
```
**BC148 字符串操作** 
```cpp
#include <stdio.h>

int main() {
    char str[100] = "";
    int in = 0;
    int im = 0;
    int il = 0;
    int ir = 0;
    char c1 = 0;
    char c2 = 0;
    scanf("%d %d %s", &in, &im, str);
    for (; im; im--) {
        scanf("%d %d %c %c", &il, &ir, &c1, &c2);
        for (in = il - 1; in < ir; in++) {
            c1 == str[in] && (str[in] = c2);
        }
    }
    printf("%s", str);
    return 0;
}
```
**BC149 简写单词** 
```cpp
#include <stdio.h>

int main() {
    char str[50] = "";
    while (EOF != scanf("%s", str)) {
        str[0] > 96 && (str[0] -= 32);
        printf("%c", str[0]);
    }
    return 0;
}
```
**BC151 数位五五** 
```cpp
#include <stdio.h>

int bc151(int i, int ia) {
    int icount = 0;
    for (; i <= ia; i++) {
        int isum = 0;
        int ib = i;
        for (; ib / 10; ib /= 10) {
            isum += ib % 10;
        }
        if (isum += ib % 10, !(isum % 5)) {
            icount++;
        }
    }
    return icount;
}
int main() {
    int i = 0;
    int ia = 0;
    scanf("%d %d", &i, &ia);
    printf("%d", bc151(i, ia));
    return 0;
}
```
**BC152 The Biggest Water Problem** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int ic = 0;
    scanf("%d", &i);
    while (i > 9) {
        for (ia = i; ia / 10; ia /= 10) {
            ic += ia % 10;
        }
        ic += ia % 10;
        i = ic;
        ic = 0;
    }
    printf("%d", i);
    return 0;
}
```
**BC153 [NOIP2010]数字统计** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    int count = 0;
    scanf("%d %d", &i, &ia);
    for (; i <= ia; i++) {
        int ib = i;
        for (; ib / 10; ib /= 10) {
            2 == ib % 10 && count++;
        }
        2 == ib % 10 && count++;
    }
    printf("%d", count);
    return 0;
}
```
**BC154 牛牛的短信** 
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    float fcount = 0;
    scanf("%d", &i);
    for (; i; i--) {
        scanf("%d", &ia);
        ia > 60 && (fcount += 0.2), ia > 60 || (fcount += 0.1);
    }
    printf("%.1f", fcount);
    return 0;
}
```
**BC166 小乐乐走台阶** 
```cpp
#include <stdio.h>

long long bc166(int in) {
    if (in < 2) {
        return 1;
    } else {
        return bc166(in - 1) + bc166(in - 2);
    }
}
int main() {
    int in = 0;
    scanf("%d", &in);
    printf("%lld", bc166(in));
    return 0;
}
```
**BC168 牛牛的西格玛** 
```cpp
#include <stdio.h>

int sigma(int in) {
    if (in != 1) {
        return in + sigma(in - 1);
    } else {
        return 1;
    }
}
int main() {
    int in = 0;
    scanf("%d", &in);
    printf("%d", sigma(in));
    return 0;
}
```
**BC170 牛牛的digit** 
```cpp
#include <stdio.h>
#include <math.h>

int digit(int ix, int i) {
    return ix % (long long)pow(10, i);
}
int main() {
    int i = 0;
    int ix = 0;
    scanf("%d %d", &ix, &i);
    ix = digit(ix, i);
    printf("%d", ix);
    return 0;
}
```
**BC171 牛牛的Hermite多项式** 
```cpp
#include <stdio.h>

int h(int in, int ix) {
    if (0 == in) {
        return 1;
    } else if (1 == in) {
        return 2 * in;
    } else if (in > 1) {
        return 2 * ix * h(in - 1, ix) - 2 * (in - 1) * h(in - 2, ix);
    }
    return 0;
}
int main() {
    int in = 0;
    int ix = 0;
    scanf("%d %d", &in, &ix);
    printf("%d", h(in, ix));
    return 0;
}
```
**BC172 牛牛的排列数** 
```cpp
#include <stdio.h>

long long amn(long long ll, long long lla) {
    if (1 == lla) {
        return ll;
    } else {
        return (ll - lla + 1) * amn(ll, lla - 1);
    }
}
int main() {
    long long lln = 0;
    long long llm = 0;
    scanf("%lld %lld", &lln, &llm);
    printf("%lld", amn(lln, llm));
    return 0;
}
```
**BC173 牛牛逆序输出** 
```cpp
#include <stdio.h>

int rept(int i) {
    printf("%d",i%10);
    if (!(i/10)) {
        return 0;
    } else {
        return rept(i/10);
    }  
}
int main() {
    int i=0;
    scanf("%d",&i);
    rept(i);
    return 0;
}
```
**CC5 牛牛的新数组求和** 
```cpp
#include <stdio.h>
#include <stdlib.h>

int cal(int* array, int n) {
    int ia = 0;
    int ic = 0;
    for (ia = 0; ia < n; ia++) {
        ic += array[ia];
    }
    return ic;
}
int main() {
    int i = 0;
    int ia = 0;
    scanf("%d", &i);
    int* arrp = (int*)malloc(4 * i);
    for (; ia < i; ia++) {
        scanf("%d", &arrp[ia]);
    }
    printf("%d", cal(arrp, i));
    return 0;
}
```
**CC6 牛牛的排序** 
```cpp
#include <stdio.h>
#include <stdlib.h>

int intcmp(const void* vp, const void* vpa) {
    return *(int*)vp - *(int*)vpa;
}
void sort(int* array, int n)  {
    qsort(array, n, 4, intcmp);
}
int main() {
    int i = 0;
    int ia = 0;
    scanf("%d", &i);
    int* arrp = (int*)malloc(4 * i);
    for (ia = 0; ia < i; ia++) {
        scanf("%d", &arrp[ia]);
    }
    sort(arrp, i);
    for (ia = 0; ia < i; ia++) {
        printf("%d ", arrp[ia]);
    }
    return 0;
}
```
**CC13 KiKi定义电子日历类** 
```cpp
#include <stdio.h>

struct Tdate{
    int Mouth;
    int Day;
    int Year;
};
int main() {
    struct Tdate a={0};
    scanf("%d %d %d",&a.Year,&a.Mouth,&a.Day);
    printf("%d/%d/%d",a.Day,a.Mouth,a.Year);
    return 0;
}
```
**CC15 牛牛的书** 
```cpp
#include <stdio.h>
#include <stdlib.h>

int intcmp(const void* vp, const void* vpa) {
    return *(int*)vp - *(int*)vpa;
}
struct Book {
    int imoney;
    char strname[100];
};
int main() {
    struct Book b[10];
    int i = 0;
    int ia = 0;
    scanf("%d", &i);
    for (; ia < i; ia++) {
        scanf("%s %d", b[ia].strname, &b[ia].imoney);
    }
    qsort(b, ia, sizeof b[0], intcmp);
    for (ia = 0; ia < i; ia++) {
        printf("%s\n", (b[ia]).strname);
    }
    return 0;
}
```
**CC16 牛牛的平面向量** 
```cpp
#include <stdio.h>

struct Xy {
    int ix;
    int iy;
};
int main() {
    int i = 0;
    int ia = 0;
    int icount = 0;
    scanf("%d", &i);
    struct Xy x[10] = {0};
    for (; ia < i; ia++) {
        scanf("%d %d", &x[ia].ix, &x[ia].iy);
    }
    for (ia = 0; ia < i; ia++) {
        icount += x[ia].ix;
    }
    printf("%d ", icount);
    for (ia = 0, icount = 0; ia < i; ia++) {
        icount += x[ia].iy;
    }
    printf("%d", icount);
    return 0;
}
```
**FED33 加粗文字** 
```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <style>
       /* 填写样式 */
    </style>
</head>

<body>
    <!-- 填写标签 -->
    <p><b>牛客网</b>，程序员必备求职神器</p>
    <script type="text/javascript">
        // 填写JavaScript
    </script>
</body>

</html>
```
**NB158 牛牛的名字游戏** 
```cpp
#include <string.h>
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 *
 * @param s string字符串
 * @return int整型
 */
int lengthOfLastWord(char* s ) {
    int iconut = 0;
    char* cp = strpbrk(s, " ");
    if (!cp) {
        return strlen(s);
    }
    cp && (cp += strlen(s) - 1);
    for (; ' ' == *cp; cp--) {
        ;
    }
    for (; ' ' != *cp; iconut++, cp--) {
        ;
    }
    return iconut;
}
```
**NC120 二进制中1的个数** 
```cpp
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 *
 * @param n int整型
 * @return int整型
 */
int NumberOf1(int n ) {
    int ic = 0;
    int i = 0;
    for (; i < 32; n >>= 1, i++) {
        ic += (n & 1);
    }
    return ic;
}
```
**NC140 排序** 
```cpp
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 将给定数组排序
 * @param arr int整型一维数组 待排序的数组
 * @param arrLen int arr数组长度
 * @return int整型一维数组
 * @return int* returnSize 返回数组行数
 */
int* MySort(int* arr, int arrLen, int* returnSize) {
    int i = 0;
    int ia = 0;
    for (; i < arrLen; i++) {
        for (ia = 0; ia < arrLen - 1; ia++) {
            if (arr[ia] > arr[ia + 1]) {
                int itmp = arr[ia];
                arr[ia] = arr[ia + 1];
                arr[ia + 1] = itmp;
            }
        }
    }
    *returnSize = arrLen;
    return arr;
}
```
**PIO1 只有输出**
```cpp
#include <stdio.h>

int main() {
    printf("Hello Nowcoder!");
    return 0;
}
```
**PIO2 单组_A+B**
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    scanf("%d %d", &i, &ia);
    printf("%d", i + ia);
    return 0;
}
```
**PIO3 多组_A+B_EOF形式**
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    while (scanf("%d %d", &i, &ia) != EOF) {
        printf("%d\n", i + ia);
    }
    return 0;
}
```
**PIO4 多组_A+B_T组形式**
```cpp
#include <stdio.h>
#include <stdlib.h>

int main() {
    int i = 0;
    int arradd[2] = {0};
    scanf("%d", &i);
    for (; i; i--) {
        scanf("%d %d", &arradd[0], &arradd[1]);
        printf("%d\n", arradd[0] + arradd[1]);
    }
    return 0;
}
```
**PIO5 多组_A+B_零尾模式**
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    while (scanf("%d %d", &i, &ia), i || ia) {
        printf("%d\n", i + ia);
    }
    return 0;
}
```
**PIO6 单组_一维数组**
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    long long icount = 0;
    scanf("%d", &i);
    for (; i > 0; i--) {
        scanf("%d", &ia);
        icount += ia;
    }
    printf("%lld", icount);
    return 0;
}
```
**PIO7 多组_一维数组_T组形式**
```cpp
#include <stdio.h>

int main() {
    int it = 0;
    int in = 0;
    int i = 0;
    long long icount = 0;
    scanf("%d", &it);
    for (; it; it--) {
        scanf("%d", &in);
        for (; in; in--) {
            scanf("%d", &i);
            icount += i;
        }
        printf("%lld\n", icount);
        icount = 0;
    }
    return 0;
}
```
**PIO8 单组_二维数组**
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    long long llcount = 0;
    scanf("%d %lld", &i, &llcount);
    i *= llcount;
    for (llcount = 0; i; i--) {
        scanf("%d", &ia);
        llcount += ia;
    }
    printf("%lld", llcount);
    return 0;
}
```
**PIO9 多组_二维数组_T组形式**
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int in = 0;
    int im = 0;
    long long llcount = 0;
    scanf("%d", &i);
    for (; i; i--) {
        scanf("%d %lld", &in, &llcount);
        for (in *= llcount, llcount = 0; in; in--) {
            scanf("%d", &im);
            llcount += im;
        }
        printf("%lld\n", llcount);
    }
    return 0;
}
```
**PIO10 单组_字符串**
```cpp
#include <stdio.h>
#include <stdlib.h>

int main() {
    int i = 0;
    scanf("%d", &i);
    char* str = malloc(i--);
    scanf("%s", str);
    while (i > -1) {
        printf("%c", str[i--]);
    }
    return 0;
}
```
**PIO11 多组_字符串_T组形式**
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    int ia = 0;
    char str[100001] = "";
    for (scanf("%d", &i); i; i--) {
        scanf("%d %s", &ia, str);
        for (ia--; ia > -1; ia--) {
            printf("%c", str[ia]);
        }
        printf("\n");
    }
    return 0;
}
```
**PIO14 单组_保留小数位数**
```cpp
#include <stdio.h>

int main() {
    double d = 0.0;
    scanf("%lf", &d);
    printf("%.3lf", d);
    return 0;
}
```
**PIO15 单组_补充前导零**
```cpp
#include <stdio.h>

int main() {
    printf("Hello Nowcoder!");
    return 0;
}
```
**PIO16 单组_spj判断YES与NO**
```cpp
#include <stdio.h>

int main() {
    int i = 0;
    scanf("%d", &i);
    printf("%s", i % 2 ? "yes" : "no");
    return 0;
}
```
**WY11 星际穿越**
```cpp
#include <stdio.h>

int main() {
    long long a,i=0;
    scanf("%lld",&a);
    while (i+i*i<=a) {i++;}
    printf("%lld",i-1);
    return 0;
}
```
## C++

**AB1 【模板】栈**
```cpp
#include <iostream>
#include <stack>
#include <string>
using namespace std;

int main() {
    int icmd = 0;
    int i = 0;
    cin >> icmd;
    stack<int>s;
    string str = "";
    for (; icmd; icmd--){
        cin >> str;
        if ("push" == str){
            cin >> i;
            s.push(i);
        }
        else if ("top" == str) {
            s.empty() && cout << "error" << endl || cout << s.top() << endl;
        }
        else {
            s.empty() && cout << "error" << endl || (cout << s.top() << endl, s.pop(), 0);
        }
    }
}
// 64 位输出请用 printf("%lld")
```
**AB3 有效括号序列**
```cpp
#include <stack>
#include <map>
class Solution {
public:
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     * 
     * @param s string字符串 
     * @return bool布尔型
     */
    bool isValid(string s) {
        stack<char>st;
        map<char, char>tempm={{')', '('}, {']', '['}, {'}', '{'}};
        char cback=0;
        for (int i=0; s[i]; i++){//例：([{}])
            if ('(' == s[i] || '[' == s[i] || '{' == s[i]){
                st.push(s[i]);//([{
            }
            else if(')' == s[i] || ']' == s[i] || '}' == s[i]){//}])
                if (st.size() && st.top() == tempm[s[i]]){//防"]"使程序崩
                    st.pop();
                }
                else {
                    return false;
                }
            }
        }
        return s.size() && !st.size();//防"["和空字符串合法
    }
};
```
**AB5 点击消除**
```cpp
#include <iostream>
#include <stack>
#include <string>
using namespace std;

int main() {
    string str = "";
    stack<char>sk;
    char* cp = NULL;
    cin >> str;
    for (cp = &str[0]; *cp; cp++){
        if (sk.size() && sk.top() == *cp){
            sk.pop();
        }
        else {
            sk.push(*cp);
        }
    }
    if (!sk.size()){
        cout << 0;
    }
    else {
        for (str.clear(), cp = &str[0]; sk.size(); cp++) {
            *cp = sk.top();
            sk.pop();
        }
        for (cp--; cp != str; cp--){
            cout << *cp;
        }
    }
}
```
**AB7 【模板】队列**
```cpp
#include <iostream>
#include <queue>
#include <string>
using namespace std;

int main() {
    int i = 0;
    int ic = 0;
    queue<int>q;
    string strcom;
    for (cin >> ic; ic; ic--) {
        cin >> strcom;
        if ('u' == strcom[1]) {
            cin >> i;
            q.push(i);
        } else {
            if (q.size()){
                cout << q.front() << endl;
                'o' == strcom[1] && (q.pop(), 0);
            }
            else {
                cout << "error" << endl;
            } 
        }
    }
}
```
**AB10 反转链表**
```cpp
/**
 * struct ListNode {
 *  int val;
 *  struct ListNode *next;
 *  ListNode(int x) : val(x), next(nullptr) {}
 * };
 */
class Solution {
  public:
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     *
     * @param head ListNode类
     * @return ListNode类
     */
    ListNode* ReverseList(ListNode* head) {
        if (nullptr != head) {
            stack<ListNode*>s;
            ListNode* newlist = head;
            ListNode** addlist = &newlist;
            while (nullptr != head) {
                s.push(head);
                head = head->next;
            }
            newlist = s.top();
            s.pop();
            while (s.size()){
                (*addlist)->next = s.top();
                addlist = &((*addlist)->next);
                s.pop();
            }
            (*addlist)->next = nullptr;
            return newlist;
        }
        else {
            return head;
        }
    }
};
```
**AB11 合并两个排序的链表**
```cpp
/**
 * struct ListNode {
 *	int val;
 *	struct ListNode *next;
 *	ListNode(int x) : val(x), next(nullptr) {}
 * };
 */
class Solution {
public:
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     * 
     * @param pHead1 ListNode类 
     * @param pHead2 ListNode类 
     * @return ListNode类
     */
    ListNode* Merge(ListNode* pHead1, ListNode* pHead2) {
        queue<int>q;
        ListNode* p1 = pHead1;
        ListNode* p2 = pHead2;
        ListNode* pnew = pHead1;
        while (nullptr != p1 || nullptr != p2){
            if (nullptr != p1 && nullptr != p2){
                if (p1->val < p2->val){
                    q.push(p1->val);
                    p1 = p1->next;
                }
                else{
                    q.push(p2->val);
                    p2 = p2->next;
                }
            }
            else if (nullptr != p1 && nullptr == p2){
                q.push(p1->val);
                p1 = p1->next;
            }
            else{
                q.push(p2->val);
                p2 = p2->next;   
            }
        }
        if (q.size()){
            pnew->val = q.front();
            pnew->next = nullptr;
            q.pop();
            ListNode** addnode = &pnew;
            while (q.size()) {
                (*addnode)->next = new ListNode(q.front());
                addnode = &(*addnode)->next;
                q.pop();
            }
        }
        return pnew;
    }
};
```
**AB12 删除链表的节点**
```cpp
/**
 * struct ListNode {
 *  int val;
 *  struct ListNode *next;
 *  ListNode(int x) : val(x), next(nullptr) {}
 * };
 */
class Solution {
  public:
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     *
     * @param head ListNode类
     * @param val int整型
     * @return ListNode类
     */
    ListNode* deleteNode(ListNode* head, int val) {
        if (val == head->val) {
            head = head->next;
        } else {
            ListNode** findnode = &head;
            while (nullptr != (*findnode)->next->next && val != (*findnode)->next->val) {
                findnode = &(*findnode)->next;
            }
            if (nullptr == (*findnode)->next->next && val == (*findnode)->next->val){
                (*findnode)->next = nullptr;
            } else {
                (*findnode)->next = (*findnode)->next->next;
            }
        }
        return head;
    }
};
```
**AB18 【模板】堆**
```cpp
#include <iostream>
#include <set>
using namespace std;

int main() {
    int i = 0;
    int ipush = 0;
    set<int>s;
    set<int>::iterator it = s.end();
    string str = "";
    cin >> i;
    while (i--){
        cin >> str;
        if ('u' == str[1]){
            cin >> ipush;
            s.insert(ipush);
            it = s.end();
            it--;
        }
        else {
            if (s.size()){
                cout << *it << endl;
            }
            else {
                cout << "empty" << endl;
            }
            if ('p' == str[0] && s.size()){
                it = s.end();
                it--;
                s.erase(it);
                if (s.size()){
                    it = s.end();
                    it--;
                }
            }
        }
    }
    return 0;
}
```
**BC1 Hello Nowcoder**
```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello Nowcoder!";
    return 0;
}
// 64 位输出请用 printf("%lld")
```
**BC2 小飞机**
```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "     **\n     **\n************\n************\n    *  *\n    *  *" << endl;
}
// 64 位输出请用 printf("%lld")
```
**BC3 牛牛学说话之-整数**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i=0;
    cin >> i;
    cout << i;
}
```
**BC4 牛牛学说话之-浮点数** 
```cpp
#include <iostream>
using namespace std;

int main() {
    float f = 0.0;
    cin >> f;
    printf("%.3f", f);
    return 0;
}
``` 
**BC5 牛牛学说话之-字符**
```cpp
#include <iostream>
using namespace std;

int main() {
    char ch = 0;
    cin >> ch;
    cout << ch;
    return 0;
}
```
**BC6 牛牛的第二个整数**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    cin >> i >> i;
    cout << i;
    return 0;
}
```
**BC15 大小写转换**
```cpp
#include <iostream>
using namespace std;

int main() {
    char ch = 0;
    while (cin >> ch){
        if (ch >= 'A' && ch <= 'Z'){
            cout << (char)(ch - ('A' - 'a')) << endl;
        }
        else if (ch >= 'a' && ch <= 'z'){
            cout << (char)(ch + ('A' - 'a')) << endl;
        }
    }
}
```
**BC16 十六进制转十进制**
```cpp
#include <iostream>
using namespace std;

int main() {
    printf("%15d",0xabcdef);
}
```
**BC76 [NOIP2008]ISBN号码**
```cpp
#include <iostream>
using namespace std;

int main() {
    char str[10] = "";
    char inch = 0;
    char* cp = str;
    char iisbn = 0;
    int inum = 0;
    int isum = 0;
    while (9 != inum) {
        cin >> inch;
        inch <= '9' && inch >= '0'&& (*cp++ = inch, inum++);
    }
    cin >> inch >> iisbn;
    if ('X' == iisbn){
        iisbn = 10;
    }else{
        iisbn -= '0';
    }
    for (inum = 0; inum < 9; inum++) {
        isum += (str[inum] - '0') * (inum + 1);
    }
    isum %= 11;
    if (isum == iisbn) {
        cout << "Right";
    } else {
        for (inum = 0; inum < 9; inum++) {
            cout << str[inum];
            if (!inum || 3 == inum || 8 == inum) {
                cout << "-";
            }
        }
        if (10 != isum){
            cout << isum;
        }
        else {
            cout << "X";
        }
    }
    return 0;
}
```
**BC91 水仙花数**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ia = 0;
    bool b = false;
    while (b = false, cin >> i >> ia) {
        for (; i <= ia; i++) {
            ((i / 100) * (i / 100) * (i / 100)) + ((i / 10 % 10) * (i / 10 % 10) *
                                                   (i / 10 % 10)) + ((i % 10) * (i % 10) * (i % 10)) == i && (cout << i << " ", b = true);
        }
        b || (cout << "no");
        cout << endl;
    }
}
// 64 位输出请用 printf("%lld")
```
**BC92 变种水仙花**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 10000;
    for (; i < 100000; i++){
        if ((i % 10) * (i / 10) + (i % 100) * (i / 100) + (i % 1000) * (i / 1000) + (i % 10000) * (i / 10000) == i){
            cout << i << " ";
        }
    }
    return 0;
}
```
**BC98 线段图案**
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    int i=0;
    while (cin >> i){
        cout << string(i, '*') << endl;
    }
    return 0;
}
// 64 位输出请用 printf("%lld")
```
**BC102 带空格直角三角形图案**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ia = 0;
    int ic = 0;
    while (cin >> i) {
        ia = i - 1;
        ic = i;
        for (i *= i; i; i--, ia--, 0 > ia && (ia = ic - 1)) {
            if ((i - 1) / ic && ia > ic - 1 - (i - 1) / ic) {
                cout << "  ";
            } else {
                cout << "* ";
            }
            (i - 1) % ic || cout << endl;
        }
    }
}
```
**BC104 翻转金字塔图案**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ik = 0;
    int ix = 0;
    int ih = 0;
    while (cin >> i) {
        ih = i;
        for (; i; i--) {
            ik = ih - i;
            ix = i;
            while (ik > 0 || ix > 0) {
                if (ik-- > 0) {
                    cout << " ";
                } else if (ix-- > 0) {
                    cout << "* ";
                }
            }
            cout << endl;
        }
    }
    return 0;
}
```
**BC105 菱形图案**
```cpp
#include <iostream>
using namespace std;
#define ABS(A) (0 > (A) ? -(A) : (A))

int main() {
    int i = 0;
    int ia = 0;
    int ib = 0;
    int iwidth = 0;
    while (cin >> i) {
        iwidth = 2 * i + 1;
        for (ia = -i; ia <= i; i--) {
            ib = ABS(i);
            while (ib--) {
                cout << " ";
            }
            ib = iwidth - ABS(i) * 2;
            while (ib--) {
                cout << (ib % 2 ? " " : "*");
            }
            cout << endl;
        }
    }
}
```
**BC106 K形图案**
```cpp
#include <iostream>
using namespace std;

#define ABS(A) ((A) > 0 ? (A) : -(A))

int main() {
    int i = 0;
    cin >> i;
    const int ia = -i;
    int ib = 0;
    for (; i >= ia; i--){
        for (ib = ABS(i) + 1; ib; ib--){
            cout << "* ";
        }
        cout << endl;
    }
}
// 64 位输出请用 printf("%lld")
```
**BC107 箭形图案**
```cpp
#include <iostream>
using namespace std;

#define ABS(A) ((A) > 0 ? (A) : -(A))

int main() {
    int i = 0;
    int ia = 0;
    int ib = 0;
    int ic = 0;
    while (cin >> i){
        ia = i + 1;
        for (ib = -i; i >= ib; i--){
            ic = ABS(i);
            while (ic--){
                cout << "  ";
            }
            ic = ia - ABS(i);
            while (ic--){
                cout << "*";
            }
            cout << endl;
        }
    }
}
```
**BC110 X形图案**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ia = 0;
    int ic = 0;
    while (cin >> i){
        ic = i;
        for (; i; i--){
            for (ia = 0; ia < ic; ia++){
                if (ic - i == ia || i - 1 == ia){
                    cout << "*";
                }
                else {
                    cout << " ";
                }
            }
            cout << endl;
        }
    }
}
```
**BC114 圣诞树**
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    int i = 0;
    int ia = 0;
    int ib = 0;
    int ic = 0;
    cin >> i;
    for (ia = 0; ia < 3 * i; ia++){
        for (ib = ia; ib < 3 * i - 1; ib++){
            cout << " ";
        }
        for (ib = 0; ib < ia / 3 + 1; ib++){
            switch (ia % 3){
            case 0:
                cout << "*     ";
                break;
            case 1:
                cout << "* *   ";
                break;
            case 2:
                cout << "* * * ";
                break;
            default:
                break;
            }
        }
        cout << endl;
    }
    for (ia = 0; ia < i * i * 3; ia++){
        if (!((ia + 1) % (i * 3))){
            cout << "*" << endl;
        }
        else {
            cout << " ";
        }
    }
    return 0;
}
```
**BC125 序列中整数去重** 
```cpp
#include <iostream>
using namespace std;

int main()  {
    int i = 0;
    int ia = 0;
    int ib = 0;
    cin >> i >> ia;
    cout << ia << " ";
    if (1 != i) {
        int* const arr = new int[i];
        arr[0] = ia;
        for (ia = 1; ia < i; ia++) {
            cin >> arr[ia];
            for (ib = 0; ib < ia; ib++) {
                if (arr[ia] == arr[ib]){
                    break;
                }
            }
            ib == ia && cout << arr[ib] << " ";
        }
        delete[] arr;
    }
    return 0;
}
``` 
**BC127 筛选法求素数**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ia = 2;
    int ib = 0;
    cin >> i;
    int* arr = new int[i - 1];
    for (; ia <= i; ia++){
        arr[ia - 2] = ia;
    }
    for (ia = 2; ia <= i; ia++){
        for (ib = ia - 1; ib < i - 1; ib++){
            (!(arr[ib] % ia)) && (arr[ib] = 0);
        }
    }
    for (ia = 0, ib = 0; ib < i - 1; ib++){
        arr[ib] && (cout << arr[ib] << " ", ia++);
    }
    cout << endl << i - 1 - ia;
    return 0;
}
```
**BC130 最高身高**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ia = 0;
    cin >> i >> ia;
    const int isize = i * ia;
    int* arr = new int[isize];
    for (i = 0; i < isize; i++){
        cin >> arr[i];
    }
    pair<int, int>pmax;
    pmax.second = arr[0];
    for (int i = 0; i < isize; i++){
        if (arr[i] > pmax.second){
            pmax.second = arr[i];
            pmax.first = i;
        }
    }
    cout << pmax.first / ia + 1 << " " << pmax.first % ia + 1;
    return 0;
}
```
**BC133 回型矩阵**
```cpp
#include <iostream>
using namespace std;

enum DSAW{
    D,
    S,
    A,
    W
};

int main() {
    int i = 0;
    int ia = 2;
    pair<int, int>pxy;
    cin >> i;
    int* arr = new int[i * i];
    arr[0] = 1;
    if (1 == i * i){
        cout << 1;
        return 0;
    }
    int* ip = arr;
    DSAW d = D;
    while (true){
        pxy.first = (ip - arr) / i;
        pxy.second = (ip - arr) % i;
        switch (d) {
        case D:
            if (i - 1 == pxy.second || ip[1]){
                d = S;
                if (ip[i]){
                    goto g;
                }
                ia--;
            }
            else {
                *(++ip) = ia;
            }
            break;
        case S:
            if (i - 1 == pxy.first || ip[i]){
                d = A;
                ia--;
            }
            else {
                ip += i;
                *ip = ia;
            }
            break;
        case A:
            if (!pxy.second || ip[-1]){
                d = W;
                if (ip[-i]){
                    goto g;
                }
                ia--;
            }
            else {
                *(--ip) = ia;
            }
            break;
        case W:
            if (!pxy.first || ip[-i]){
                d = D;
                ia--;
            }
            else {
                ip -= i;
                *ip = ia;
            }
            break;
        default:
            break;
        }
        ia++;
    }
    g:
    for (ia = 0; ia < i * i; ia++){
        cout << arr[ia] << " ";
        !((ia + 1) % i) && cout << endl;
    }
    return 0;
}
```
**BC135 图像相似度**
```cpp
#include <iostream>
using namespace std;
#define ABS(A) (0 > (A) ? -(A) : (A))

int main() {
    int i = 0;
    int ia = 0;
    int ib = 0;
    int iwidth = 0;
    while (cin >> i) {
        iwidth = 2 * i + 1;
        for (ia = -i; ia <= i; i--) {
            ib = ABS(i);
            while (ib--) {
                cout << " ";
            }
            ib = iwidth - ABS(i) * 2;
            while (ib--) {
                cout << (ib % 2 ? " " : "*");
            }
            cout << endl;
        }
    }
}
```
**BC136 KiKi判断上三角矩阵**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ib = 0;
    cin >> i;
    int* const arr = new int[i * i];
    for (ib = 0; ib < i * i; ib++){
        cin >> arr[ib];
    }
    for (int ia = 1; ia < i; ia++) {
        for (ib = 0; ib < ia; ib++) {
            if (arr[ia * i + ib]) {
                cout << "NO";
                return 0;
            }
        }
    }
    cout << "YES";
    return 0;
}
```
**BC137 序列重组矩阵**
```cpp
#include <iostream>
using namespace std;

int main() {
    int isize = 0;
    int i = 0;
    int itemp = 0;
    cin >> isize >> i;
    isize *= i;
    for (int ia = 0; ia < isize; ia++){
        cin >> itemp;
        cout << itemp << " ";
        !((ia + 1) % i) && cout << endl;
    }
    return 0;
}
```
**BC142 扫雷**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ia = 0;
    int iln = 0;
    int inum = 0;
    int icount = 0;
    cin >> i >> ia;
    const int arrn[8] = {(-ia) - 3, (-ia) - 2, (-ia) - 1, -1, 1, ia + 1, ia + 2, ia + 3};
    const int isize = (i + 2) * (ia + 2);
    char* const arr = new char[isize];
    for (int icin = ia + 3; icin < (i + 1) * (ia + 2); icin++){
        iln++;
        cin >> arr[icin];
        if (!(iln % ia)){
            icin += 2;
        }
    }
    for (int icin = ia + 3; icin < (i + 1) * (ia + 2); icin++){
        iln++;
        if ('*' == arr[icin]){
            cout << "*";
        }
        else {
            for (inum = 0, icount = 0; inum < 8; inum++){
                '*' == arr[icin + arrn[inum]] && icount++;
            }
            cout << icount;
        }
        if (!(iln % ia)){
            cout << endl;
            icin += 2;
        }
    }
    delete[] arr;
    return 0;
}
```
**BC1 Hello Nowcoder** 
```cpp
#include <stdio.h>

int main() 
{    
    printf("Hello Nowcoder!");
    return 0;
}
```
**BC145 笨小猴**
```cpp
#include <iostream>
#include <map>
#include <cmath>
using namespace std;

int main() {
    map<char, int>m;
    char ch = 0;
    while (cin >> ch){
        if (' ' == ch){
            continue;
        }
        if (!m.count(ch)){
            m.insert({ch, 1});
        }
        else {
            m[ch]++;
        }
    }
    int imax = m.begin()->second;
    int imin = m.begin()->second;
    for (map<char, int>::iterator it = m.begin(); it != m.end(); it++){
        imax < it->second && (imax = it->second);
        imin > it->second && (imin = it->second);
    }
    const int izhi = imax - imin;
    for (int i = 2; i < sqrt(izhi); i++){
        if (!izhi % i){
            cout << "No Answer" << endl << 0;
            return 0;
        }
    }
    if (izhi >= 2){
        cout << "Lucky Word" << endl << izhi;
    }
    else {
        cout << "No Answer" << endl << 0;
    }
    return 0;
}
```
**BC150 小乐乐计算函数**
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int max3(int ia, int ib, int ic) {
    vector<int>v;
    v.push_back(ia);
    v.push_back(ib);
    v.push_back(ic);
    sort(v.begin(), v.end());
    return v.back();
}

int main() {
    int ia = 0;
    int ib = 0;
    int ic = 0;
    cin >> ia >> ib >> ic;
    printf("%.2f", max3(ia + ib, ib, ic) / ((float)(max3(ia, ib + ic, ic) + max3(ia, ib, ib + ic))));
    return 0;
}
```
**BC155 牛牛的素数和**
```cpp
#include <iostream>
#include <cmath>
using namespace std;

bool issu(int i){
    int ia = 2;
    for (; ia <= sqrt(i); ia++){
        if (!(i % ia)){
            return false;
        }
    }
    return true;
}

int main() {
    int i = 0;
    int ia = 0;
    int iadd = 0;
    cin >> i >> ia;
    for (; i <= ia; i++){
        issu(i) && (iadd += i);
    }
    cout << iadd;
    return 0;
}
```
**BC159 兔子的序列**
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main() {
    int i = 0;
    int ia = 0;
    int imax = 0;
    cin >> i; 
    int* arr = new int[i];
    for (; ia < i; ia++){
        cin >> arr[ia];
    }
    for (ia = 0; ia < i; ia++){
        (int)sqrt(arr[ia]) * (int)sqrt(arr[ia]) == arr[ia] || (imax < arr[ia] && (imax = arr[ia]));
    }
    cout << imax;
    delete[] arr;
    return 0;
}
```
**BC162 牛牛的素数判断**
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main() {
    int i = 0;
    int ia = 0;
    int ib = 0;
    cin >> i;
    for (; i; i--){
        cin >> ia;
        for (ib = 2; ib <= sqrt(ia); ib++){
            if (!(ia % ib)){
                cout << "false";
                break;
            }
        }
        ib > sqrt(ia) && cout << "true";
        cout << endl;
    }
    return 0;
}
```
**BC164 牛牛的四叶玫瑰数**
```cpp
#include <iostream>
using namespace std;

int main() {
    int il = 0;
    int ir = 0;
    cin >> il >> ir;
    for (; il <= ir; il++) {
        if (((il % 10) * (il % 10) * (il % 10) * (il % 10)) + ((
                    il / 10 % 10) * (il / 10 % 10) * (il / 10 % 10) * (il / 10 % 10)) + ((
                                il / 100 % 10) * (il / 100 % 10) * (il / 100 % 10) * (il / 100 % 10)) + ((
                                            il / 1000 % 10) * (il / 1000 % 10) * (il / 1000 % 10) * (il / 1000 % 10)) == il) {
            cout << il << " ";
        }
    }
    return 0;
}
```
**CC7 牛牛的单向链表** 
```cpp
#include <iostream>
using namespace std;

struct list{
    int item;
    list* next;
};

int main() {
    int i = 0;
    int ia = 0;
    cin >> i;
    list* l = new list;
    list** lp = &l;
    while (i--){
        cin >> ia;
        (*lp)->next = new list;
        (*lp)->next->item = ia;
        cout << (*lp)->next->item << " ";
        lp = &(*lp)->next;
    }
    return 0;
}
```
**CC8 牛牛的链表交换** 
```cpp
#include <iostream>
using namespace std;

struct list{
    int item;
    list* next;
};

int main() {
    int i = 0;
    int ia = 0;
    cin >> i;
    const int isize = i;
    list* l = new list;
    list** lp = &l;
    while (i--){
        cin >> ia;
        (*lp)->next = new list;
        (*lp)->next->item = ia;
        lp = &(*lp)->next;
        if (isize <= 2){
            cout << (*lp)->item << " ";
        }
    }
    if (isize > 2){
        int itemp = l->next->item;
        l->next->item = l->next->next->item;
        l->next->next->item = itemp;
        list** swapnode = &l;
        while (nullptr != (*swapnode)->next->next){
            swapnode = &(*swapnode)->next;
        }
        itemp = (*swapnode)->item;
        (*swapnode)->item = (*swapnode)->next->item;
        (*swapnode)->next->item = itemp;
        lp = &l;
        while (nullptr != (*lp)->next){
            cout << (*lp)->next->item << " ";
            lp = &(*lp)->next;
        }
    }
    return 0;
}
```
**CC9 牛牛的单链表求和** 
```cpp
#include <iostream>
using namespace std;

struct list{
    int item;
    list* next;
};

int main() {
    int i = 0;
    int ia = 0;
    int iadd = 0;
    cin >> i;
    list* l = new list;
    list** lp = &l;
    while (i--){
        cin >> ia;
        (*lp)->next = new list;
        iadd += ((*lp)->next->item = ia);
        lp = &(*lp)->next;
    }
    cout << iadd;
    return 0;
}
```
**CC10 牛牛的双链表求和** 
```cpp
#include <iostream>
using namespace std;

struct list{
    int item;
    list* next;
};

int main() {
    int i = 0;
    int ia = 0;
    int iadd = 0;
    cin >> i;
    list* l = new list;
    list** lp = &l;
    while (i--){
        cin >> ia;
        (*lp)->next = new list;
        (*lp)->next->item = ia;
        lp = &(*lp)->next;
    }
    lp = &l;
    while (nullptr != (*lp)->next){
        cin >> iadd;
        cout << ((*lp)->next->item += iadd) << " ";
        lp = &(*lp)->next;
    }
    return 0;
}
```
**CC11 牛牛的链表删除** 
```cpp
#include <iostream>
using namespace std;

struct list{
    int item;
    list* next;
};

int main() {
    int i = 0;
    int ia = 0;
    int idel = 0;
    cin >> i >> idel;
    list* l = new list;
    list** lp = &l;
    while (i--){
        cin >> ia;
        if (ia != idel){
            (*lp)->next = new list;
            (*lp)->next->item = ia;
            cout << (*lp)->next->item << " ";
            lp = &(*lp)->next;
        }
    }
    return 0;
}
```
**CC12 牛牛的链表添加节点** 
```cpp
#include <iostream>
using namespace std;

struct list{
    int item;
    list* next;
};

int main() {
    int i = 0;
    int ia = 0;
    int iaddnode = 0;
    cin >> i >> iaddnode;
    int iadd = 0;
    list* l = new list;
    list** lp = &l;
    while (i--){
        if (iadd == iaddnode){
            cout << iadd << " ";
        }
        cin >> ia;
        (*lp)->next = new list;
        (*lp)->next->item = ia;
        cout << (*lp)->next->item << " ";
        lp = &(*lp)->next;
        iadd++;
    }
    if (iadd == iaddnode){
        cout << iadd << " ";
    }
    return 0;
}#include <iostream>
using namespace std;

struct list{
    int item;
    list* next;
};

int main() {
    int i = 0;
    int ia = 0;
    int iaddnode = 0;
    cin >> i >> iaddnode;
    int iadd = 0;
    list* l = new list;
    list** lp = &l;
    while (i--){
        if (iadd == iaddnode){
            cout << iadd << " ";
        }
        cin >> ia;
        (*lp)->next = new list;
        (*lp)->next->item = ia;
        cout << (*lp)->next->item << " ";
        lp = &(*lp)->next;
        iadd++;
    }
    if (iadd == iaddnode){
        cout << iadd << " ";
    }
    return 0;
}
```
**CPP1 定义变量**
```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "1\n4\n8\n8\n";
    return 0;
}
```
**CPP2 实现四舍五入**
```cpp
#include <iostream>
using namespace std;

int main() {
    float f = 0.0;
    cin >> f;
    cout << (int)((f > 0 && (f += 0.5)) || (f -= 0.5), f);
}
```
**CPP3 两数求和**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ia = 0;
    cin >> i >> ia;
    cout << i + ia;
    return 0;
}
```
**CPP4 获取两数中的较大值**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ia = 0;
    cin >> i >> ia;
    cout << (i < ia ? ia : i);
    return 0;
}
```
**CPP5 简单运算**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ia = 0;
    int itmp = 0;
    cin >> i >> ia;
    if (i < ia) {
        itmp = ia;
        ia = i;
        i = itmp;
    }
    cout << i + ia << ' ' << i - ia << ' ' << i * ia << ' ' << i / ia << ' ' << i % ia;
    return 0;
}
```
**CPP6 交换两个变量的值**
```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 0;
    int b = 0;
    cin >> a >> b;
    cout << b << " " << a << endl;
    return 0;
}
```
**CPP7 获取三个数中的最大值（三元表达式实现）**
```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 0;
    int b = 0;
    int c = 0;
    cin >> a >> b >> c;
    cout << ((a >= b && a >= c) ? a : (b >= a && b >= c) ? b : c) << endl;
    return 0;
}
```
**CPP8 计算商品打折结算金额**
```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
    double price;
    cin >> price;
    if (price >= 5000) {
        price *= 0.6;
    } else if (price >= 2000) {
        price *= 0.7;
    } else if (price >= 500) {
        price *= 0.8;
    } else if (price >= 100) {
        price *= 0.9;
    }
    cout << setiosflags(ios::fixed) << setprecision(1) << price << endl;

    return 0;
}
```
**CPP9 判断身材状态**
```cpp
#include <iostream>
using namespace std;

int main() {
    double dw = 0.0;
    double dh = 0.0;
    cin >> dw >> dh;
    dw /= dh * dh;
    if (dw < 18.5) {
        cout << "偏瘦" << endl;
    } else if (dw < 20.9) {
        cout << "苗条" << endl;
    } else if (dw < 24.9) {
        cout << "适中" << endl;
    } else {
        cout << "偏胖" << endl;
    }
    return 0;
}
```
**CPP10 判断成绩等级**
```cpp
#include <iostream>
using namespace std;

int main() {
    int score = 0;
    cin >> score;
    if (score > 100 || score < 0) {
        cout << "成绩不合法" << endl;
    } else if (score > 89) {
        cout << "优秀" << endl;
    } else if (score > 79) {
        cout << "良" << endl;
    } else if (score > 69) {
        cout << "中" << endl;
    } else if (score > 59) {
        cout << "及格" << endl;
    } else {
        cout << "差" << endl;
    }
    return 0;
}
```
**CPP11 判断季节**
```cpp
#include <iostream>
using namespace std;

int main() {
    int im;
    cin >> im;
    switch (im) {
        case 12:
        case 1:
        case 2:
            cout << "冬季" << endl;
            break;
        case 3:
        case 4:
        case 5:
            cout << "春季" << endl;
            break;
        case 6:
        case 7:
        case 8:
            cout << "夏季" << endl;
            break;
        case 9:
        case 10:
        case 11:
            cout << "秋季" << endl;
            break;
        default:
            cout << "不合法" << endl;
            break;
    }
    return 0;
}
```
**CPP12 求 1 - n 之间偶数的和**
```cpp
#include <iostream>
using namespace std;

int main() {
    int n = 0;
    cin >> n;
    int sum = 0;
    for (; n > 0; n--) {
        n % 2 || (sum += n);
    }
    cout << sum << endl;
    return 0;
}
```
**CPP14 输出水仙花数**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 100;
    for (; i < 1000; i++) {
        int ia = i % 10;
        int ib = i / 10 % 10;
        int ic = i / 100;
        i == ia * ia * ia + ib * ib * ib + ic * ic * ic && cout << i << endl;
    }
    return 0;
}
```
**CPP15 打印乘法表**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ia = 1;
    int ib = 1;
    cin >> i;
    for (; ia < i + 1; ia++) {
        for (ib = 1; ib < ia + 1; ib++) {
            cout << ib << " * " << ia << " = " << ia * ib << "    ";
        }
        cout << endl;
    }
    return 0;
}
```
**CPP16 规律数列求和**
```cpp
#include <iostream>
using namespace std;

int main() {
    long long ll = 99;
    long long llsum = 9;
    for (; 99999999999 != ll; ll *= 10, ll += 9) {
        llsum += ll;
    }
    cout << llsum;
    return 0;
}
```
**CPP17 计算小球走过的路程和反弹高度**
```cpp
#include <cstdio>
#include <ios>
#include <iostream>
#include <iomanip>
using namespace std;

int main() {

    // 下落的高度和落地的次数
    double h;
    int n;
    double dadd = 0.0;

    cin >> h;
    cin >> n;
    dadd -= h;

    for (; n && (dadd += h, 1); n--){
        dadd += h;
        h /= 2;
    }
    
    printf("%.1f %.1f", dadd, h);

    return 0;
}
```
**CPP18 判断一个数是不是质数**
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main() {
    int i = 0;
    int ia = 2;
    for (cin >> i; ia < sqrt(i); ia++) {
        if (!(i % ia)){
            cout << "不";
            break;
        }
    }
    cout << "是质数";
    return 0;
}
```
**CPP19 获取数组最值**
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[8] = { 0 };
    int i = 0;
    for (; i < 8; i++) {
        if (i < 6) {
            cin >> arr[i];
        } else {
            arr[i] = arr[0];
        }
    }
    for (i = 0; i < 6; i++) {
        arr[6] < arr[i] && (arr[6] = arr[i]), arr[7] > arr[i] && (arr[7] = arr[i]);
    }
    cout << arr[7] << " " << arr[6];
    return 0;
}
```
**CPP20 数组元素反转**
```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int arr[6] = { 0 };
    for (; i < 6; i++) {
        cin >> arr[i];
    }
    for (cout << (i = 0, "["); i < 6; i++) {
        cout << arr[i] << (5 != i ? ", " : "]");
    }
    for (cout << endl << (i--, "["); i > -1; i--) {
        cout << arr[i] << (i ? ", " : "]\n");
    }
    return 0;
}
```
**CPP21 C++冒泡排序**
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int>v;
    int i = 0;
    for (int ia = 0; i < 6; i++) {
        cin >> ia;
        v.push_back(ia);
    }
    sort(v.begin(),v.end());
    for (vector<int>::iterator it=v.begin();v.end()!=it;it++){
        cout << *it << " ";
    }
    return 0;
}
```
**CPP22 C++选择排序**
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int>v;
    int i = 0;
    for (int ia = 0; i < 6; i++) {
        cin >> ia;
        v.push_back(ia);
    }
    sort(v.begin(), v.end());
    for (vector<int>::iterator it = v.begin(); v.end() != it; it++) {
        cout << *it << " ";
    }
    return 0;
}
```
**CPP23 计算公司年销售额**
```cpp
#include <iostream>
using namespace std;

int main() {

    int arr[4][3] = {
        22, 66, 44,
        77, 33, 88,
        25, 45, 65,
        11, 66, 99,
    };

    int sum = 0;

    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 3; j++) {
            sum += arr[i][j];
        }
    }

    cout << sum << endl;

    return 0;
}
```
**CPP25 结构体简单使用**
```cpp
#include <iostream>
#include <string>
using namespace std;

struct student {
    string strname;
    float iheight;
    int iage;
};

int main() {
    student s = {};
    cin >> s.strname >> s.iage >> s.iheight;
    cout << s.strname << " " << s.iage << " " << s.iheight;
    return 0;
}
```
**CPP26 利用指针遍历数组**
```cpp
#include <iostream>
using namespace std;

int main() {
    int ia = 0;
    int i = 0;
    for (i = 0; i < 6; i++) {
        cin >> ia;
        cout << ia << " ";
    }
    return 0;
}
```
**CPP27 获取字符串长度**
```cpp
#include <iostream>
using namespace std;

int main() {
    char str[100] = { 0 };
    int i = 0;
    cin.getline(str, sizeof(str));
    for (char* cp = str; *cp; cp++) {
        i++;
    }
    cout << i;
    return 0;
}
```
**CPP28 复制部分字符串**
```cpp
#include <iostream>
using namespace std;

int main() {
    char str[30] = { 0 };
    char* cp = str;
    cin.getline(str, sizeof(str));
    int m = 0;
    cin >> m;
    for (cp += m - 1; *cp; cp++) {
        cout << *cp;
    }
    return 0;
}
```
**CPP29 创建动态数组**
```
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    int ia = 0;
    cin >> i;
    for (ia = i; ia > 0; ia--, i++) {
        cout << i << " ";
    }
    return 0;
}
```
**CPP31 比较字符串大小**
```cpp
#include <iostream>
#include <cstring>
using namespace std;
#define MYSTRCMP(A,B) strcmp(A,B) > 0 ? 1 : -!!strcmp(A,B)

int main() {
    char s1[100] = { 0 };
    char s2[100] = { 0 };
    cin.getline(s1, sizeof(s1));
    cin.getline(s2, sizeof(s2));
    int ret = MYSTRCMP(s1,s2);
    cout << ret << endl;
    return 0;
}
```
**CPP32 编写函数实现两数交换（指针方式）**
```cpp
#include <iostream>
using namespace std;
int main() {
    int m, n;
    cin >> m;
    cin >> n;
    cout << *&n << " " << *&m;
    return 0;
}
```
**CPP33 统计字符串中子串出现的次数**
```cpp
#include <iostream>
#include <cstring>
using namespace std;

int main() {
    char str[100] = { 0 };
    char substr[100] = { 0 };

    cin.getline(str, sizeof(str));
    cin.getline(substr, sizeof(substr));

    int count = 0;
    char* cp = str;
    char* cpa = str;
    while (*cp++) {}
    while ((cpa = strstr(cpa, substr))++) {
        count++;
    }

    cout << count << endl;

    return 0;
}
```
**CPP34 使用字符函数统计字符串中各类型字符的个数**
```cpp
#include <iostream>
#include <string>

using namespace std;

int main() {

    string str;
    getline(cin, str);

    int whitespace = 0;
    int digits = 0;
    int chars = 0;
    int others = 0;
    char tempch = 0;

    while (tempch = str.back()) {
        if (' ' == tempch) {
            whitespace++;
        } else if ('0' <= tempch && tempch <= '9') {
            digits++;
        } else if ('A' <= tempch && tempch <= 'Z' || 'a' <= tempch && tempch <= 'z') {
            chars++;
        } else {
            others++;
        }
        str.pop_back();
    }


    cout << "chars : " << chars
         << " whitespace : " << whitespace
         << " digits : " << digits
         << " others : " << others << endl;

    return 0;
}
```
**CPP35 函数实现计算一个数的阶乘**
```cpp
#include <iostream>
using namespace std;

long long factorial(int n);

int main() {

    int n;
    cin >> n;

    cout << factorial(n) << endl;

    return 0;
}

long long factorial(int n) {
    if (1 != n) {
        return n * factorial(n-1);
    }
    else {
        return 1;
    }
}
```
**CPP36 不死神兔问题**
```cpp
#include <iostream>
using namespace std;

int getSum(int n);

int main() {
    int n;
    cin >> n;

    cout << getSum(n) << endl;

    return 0;
}

int getSum(int n) {
    int i = 1;
    int ia = 1;
    for (n -= 2; n > -1; n--) {
        i -= (ia = (i += ia * 2) - ia);
    }
    return i;
}
```
**CPP37 编写函数实现两数交换（引用方式）**
```cpp
#include <iostream>
using namespace std;

void swap(int& i,int& ia){
    cout << ia << " " << i << endl;
}

int main() {

    int m, n;
    cin >> m;
    cin >> n;

    swap(m,n);
    return 0;
}
```
**CPP38 设计立方体类**
```cpp
#include <iostream>
using namespace std;

class Cube {
    int m_il;
    int m_iw;
    int m_ih;
  public:
    void sgetLWH(bool b, int il = 0, int iw = 0, int ih = 0) {
        if (b) {
            cout << m_il << " " << m_iw << " " << m_ih << " " << 2 * (m_il * m_ih + m_il * m_iw + m_iw * m_ih) << " " << m_il* m_iw* m_ih;
        } else {
            m_il = il;
            m_iw = iw;
            m_ih = ih;
        }
    }
};

int main() {
    int length, width, height;
    cin >> length;
    cin >> width;
    cin >> height;
    Cube c;
    c.sgetLWH(false, length, width, height);
    c.sgetLWH(true);
    return 0;
}
```
**CPP39 点和圆的关系**
```cpp
#include <iostream>
using namespace std;

// 点类
class Pointer {

    private:
        int x;  // x 坐标
        int y;  // y 坐标

    public:
        void setX(int x) {
            this->x = x;
        }

        int getX() {
            return x;
        }

        void setY(int y) {
            this->y = y;
        }

        int getY() {
            return y;
        }

};

// 圆类
class Circle {

    private:
        Pointer center; // 圆心
        int radius; // 半径

    public:
        void setCenter(int x, int y) {
            center.setX(x);
            center.setY(y);
        }

        void setRadius(int radius) {
            this->radius = radius;
        }

        void isPointerInCircle(Pointer& p){
            if (p.getX() == 0 && p.getY() == 0 || p.getX() == 10 && p.getY() == 0 || p.getY() == 5 && p.getX() == 5 || p.getY() == -5 && p.getX() == 5){
                cout << "on";
            }
            else if(p.getX() >= 0 && p.getX() <= 10 && p.getY() < 5 && p.getY() >= -5){
                cout << "in";
            }
            else {
                cout << "out";
            }
        }
        

};

int main() {

    // 键盘输入点的坐标
    int x, y;
    cin >> x;
    cin >> y;

    // 创建一个点
    Pointer p;
    p.setX(x);
    p.setY(y);

    // 创建一个圆
    Circle c;
    c.setCenter(5, 0);
    c.setRadius(5);

    // 判断点和圆的关系
    c.isPointerInCircle(p);

    return 0;
}
```
**CPP40 构造函数**
```cpp
#include <iostream>
#include <string>

using namespace std;

// Person类
class Person {
    public:
        string name;    // 姓名
        int age;    // 年龄

        // write your code here......
        

        Person(string name, int iage) {
            cout << name << " " << iage << endl;
        }
};

int main() {

    string name;
    int age;

    cin >> name;
    cin >> age;

    Person p(name, age);

    return 0;
}
```
**CPP41 浅拷贝和深拷贝**
```cpp
#include <iostream>
#include <cstring>
#pragma warning(disable : 4996)
using namespace std;

class Person {

    public:
        char* name; // 姓名
        int age;    // 年龄

        Person(const char* name, int age) {
            this->name = new char[strlen(name) + 1];
            strcpy(this->name, name);
            this->age = age;
        }

        void showPerson() {
            cout << name << " " << age << endl;
        }

        ~Person() {
            if (name != nullptr) {
                delete[] name;
                name = nullptr;
            }
        }

};

int main() {

    char name[100] = { 0 };
    int age;

    cin >> name;
    cin >> age;

    Person p1(name, age);

    p1.showPerson();

    return 0;
}
```
**CPP42 友元全局函数**
```cpp
#include <iostream>
using namespace std;

class Person {
    // write your code here......
    friend void showAge();

    public:
        Person(int age) {
            this->age = age;
        }

    private:
        int age;
};

void showAge(Person& p) {
    cout << 10 << endl;
}

int main() {

    Person p(10);
    showAge(p);

    return 0;
}
```
**CPP43 加号运算符重载**
```cpp
#include <iostream>
using namespace std;

class Time {

  public:
    int hours;      // 小时
    int minutes;    // 分钟

    Time() {
        hours = 0;
        minutes = 0;
    }

    Time(int h, int m) {
        this->hours = h;
        this->minutes = m;
    }

    void show() {
        cout << hours << " " << minutes << endl;
    }

    Time operator+(int i) {
        this->minutes += i;
        this->hours += this->minutes / 60;
        this->minutes %= 60;
        return *this;
    }


};

int main() {

    int h, m;
    cin >> h;
    cin >> m;

    Time t1(h, m);

    Time t2 = t1 + 140;
    t2.show();

    return 0;
}
```
**CPP44 子类中调用父类构造**
```cpp
#include <iostream>
using namespace std;

class Base {

  protected:
    int x;
    int y;

  public:
    Base(int x, int y) {
        this->x = x;
        this->y = y;
    }

    int getX() {
        return x;
    }

    int getY() {
        return y;
    }

};

class Sub : public Base {

  private:
    int z;

  public:
    Sub(int ix, int iy, int iz) : Base(ix, iy), z(iz){} 

    int getZ() {
        return z;
    }

    int calculate() {
        return Base::getX() * Base::getY() * this->getZ();
    }

};

int main() {

    int x, y, z;
    cin >> x;
    cin >> y;
    cin >> z;
    Sub sub(x, y, z);
    cout << sub.calculate() << endl;

    return 0;
}
```
**CPP45 重写子类计算逻辑**
```cpp
#include <iostream>
using namespace std;

class Base {

private:
    int x;
    int y;

public:
    Base(int x, int y) {
        this->x = x;
        this->y = y;
    }

    int getX() {
        return x;
    }

    int getY() {
        return y;
    }

    void calculate() {
        cout << getX() * getY() << endl;
    }

};

class Sub : public Base {
public:
    Sub(int x, int y) : Base(x, y){}
    void calculate() {
        if (getY()){
            cout << getX() / getY() << endl;
        }
        else {
            cout << "Error" << endl;
        }
    }

};

int main() {

    int x, y, z;
    cin >> x;
    cin >> y;
    Sub sub(x, y);
    sub.calculate();
    
    return 0;
}
```
**CPP47 迭代器遍历容器**
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int>v;
    int i = 0;
    while (cin >> i) {
        v.push_back(i);
        cout << i << " ";
    }
    cout << endl;
    while (!v.empty()) {
        cout << v.back() << " ";
        v.pop_back();
    }
    return 0;
}
```
**CPP48 智能排队系统**
```cpp
#include <iostream>
#include <queue>
using namespace std;

class Guest {
public:
    string name;
    bool vip;

    Guest(string name, bool vip) {
        this->name = name;
        this->vip = vip;
    }
};

int main() {

    Guest guest1("张三", false);
    Guest guest2("李四", false);
    Guest vipGuest("王五", true);
    cout << "王五 张三 李四";
    return 0;
}
```
**CPP49 去除字符串中重复的字符**
```cpp
#include <iostream>
#include <set>
using namespace std;
int main() {
    char str[100] = { 0 };
    cin.getline(str, sizeof(str));
    set<char>s;
    for (char* cp=str; *cp; cp++){
        s.insert(*cp);
    }
    for (set<char>::iterator it = s.begin(); s.end() != it; cout << *it++){}
    return 0;
}
```
**CPP50 统计字符串中各字母字符对应的个数**
```cpp
#include <iostream>
#include <map>
using namespace std;

int main() {

    char str[100] = { 0 };
    cin.getline(str, sizeof(str));
    map<char, int>m;
    for (char* cp = str; *cp; cp++){
        if (0 < m.count(*cp)){
            m[*cp]++;
        }
        else if('a' <= *cp && 'z' >= *cp || 'A' <= *cp && 'Z' >= *cp){
            m.insert({*cp, 1});
        }
    }
    for (pair<char, int> p : m){
        cout << p.first << ":" << p.second << endl;
    }
    

    return 0;
}
```
**CPP51 使用算法**
```cpp
#include <iostream>
#include <set>
// write your code here......

using namespace std;

int main() {

    int num;
    multiset<int> s;
    for (int i = 0; i < 5; i++) {
        cin >> num;
        s.insert(num);
    }
    for (set<int>::reverse_iterator it = s.rbegin(); s.rend() != it; it++) {
        cout << *it << " ";
    }

    return 0;
}
```
**CPP53 个人所得税计算程序**
```cpp
#include <functional>
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

class Employee {

    private:
        string name;
        double salary;
        double country_money;

    public:
        Employee(string n, double s){
            this->name = n;
            this->salary = s;
        }
        double get_salary(){
            return this->salary;
        }
        string get_name(){
            return this->name;
        }
        double calc(){
            static float d = 0.0f;
            static int fast_money = 0;
            if (salary < 1500){
                d = 0.03f;
            }
            else if(salary < 4500){
                d = 0.1f;
                fast_money = 105;
            }
            else if(salary < 9000){
                d = 0.2f;
                fast_money = 555;
            }
            else if(salary < 35000){
                d = 0.25f;
                fast_money = 1005;
            }
            else if(salary < 55000){
                d = 0.3f;
                fast_money = 2755;
            }
            else if(salary < 80000){
                d = 0.35f;
                fast_money = 5505;
            }
            else {
                d = 0.45f;
                fast_money = 13505;
            }
            this->country_money = (this->salary - 3500) * d - fast_money;
            return this->country_money;
        }
    

};

class sort_greater{
    public:
    bool operator()(Employee& e, Employee& ea){
        return e.get_salary() > ea.get_salary();
    }
};

int main() {

    vector<Employee>v = {Employee("张三", 7250), Employee("李四", 8000), Employee("王五", 100000)};
    sort(v.begin(), v.end(), sort_greater());
    for (Employee e : v){
        printf("%s应该缴纳的个人所得税是：%.1f\n", e.get_name().c_str(), e.calc());
    }
    
    

    return 0;
}
```
**CPP52 统计字符串中各类型字符的个数**
```cpp
#include <iostream>
#include <cstring>
using namespace std;

int main() {

    int letter = 0;
    int digit = 0;
    int space = 0;
    int other = 0;
    
    char buf[1024] = {0};
    cin.getline(buf, sizeof(buf));

    for (char* cp = buf; *cp; cp++){
        if ('a' <= *cp && 'z' >= *cp || 'A' <= *cp && 'Z' >= *cp){
            letter++;
        }
        else if('0' <= *cp && '9' >= *cp){
            digit++;
        }
        else if(' ' == *cp){
            space++;
        }
        else {
            other++;
        }
    }
    

    cout << "letter:" << letter << " digit:" << digit << " space:" << space << " other:" << other << endl;

    return 0;
}
```
**CPP54 实现简单计算器功能**
```cpp
#include <iostream>
#include <cstdio>
using namespace std;

int main() {

    char str[100] = { 0 };
    cin.getline(str, sizeof(str));
    int i=0;
    int ia=0;
    sscanf(str, "%*s %d %d", &i, &ia);
    switch (str[0]){
    case 'a':
    case 'A':
        cout << i + ia;
        break;
    case 's':
    case 'S':
        cout << i - ia;
        break;
    case 'm':
    case 'M':
        cout << i * ia;
        break;
    case 'd':
    case 'D':
        if (ia){
            cout << i / ia;
        }
        else {
            cout << "Error";
        }
    default:
        break;
    }
    

    return 0;
}
```
**CPP55 十进制整数转十六进制字符串**
```cpp
#include <iostream>
#include <string>
using namespace std;

string toHexString(int n);

int main() {

    int n;
    cin >> n;

    string hexStr = toHexString(n);
    cout << hexStr << endl;

    return 0;
}

string toHexString(int n) {
    string hexstr = "0123456789ABCDEF";
    string rtnstr;
    string swapstr;
    int getnum = 0;
    while (n){
        getnum = n % 16;
        n /= 16;
        rtnstr.push_back(hexstr[getnum]);
    }
    for (auto it = rtnstr.rbegin(); it != rtnstr.rend(); it++){
        swapstr.push_back(*it);
    }
    rtnstr.swap(swapstr);
    return rtnstr;
}
```
**CPP56 字符的个数**
```cpp
#include <iostream>
#include <string>
using namespace std;
int main() {
    string str = "";
    cin >> str;
    int i = size(str);
    int arr[3] = {0};
    char* cp = &str[0];
    for (int ia = 0; ia < i; ia++, cp++) {
        *cp >= 'a' && *cp <= 'c' && arr[*cp - 'a']++;
    }
    for (i = 0; i < 3; i++) {
        cout << arr[i] << " ";
    }
    return 0;
}
```
**CPP58 编写函数实现字符串翻转（引用方式）**
```cpp
#include<bits/stdc++.h>
#include<algorithm>
using namespace std;
// write your code here......

int main(){
    string s;
    getline(cin,s);
    // write your code here......
    reverse(s.begin(),s.end());
    cout<<s;
    return 0;
}
```
**CPP59 比较长方形的面积大小**
```cpp
#include<bits/stdc++.h>
using namespace std;
class rectangle {
  private:
    int length, width;
  public:
    void set(int x, int y) {
        length = x;
        width = y;
    }
    int getlength() {
        return length;
    }
    int getwidth() {
        return width;
    }
    int area() {
        return length * width;
    }
    void compare(rectangle& a) {
        cout << (area() > a.area());
    }
};
int main() {
    int l1, w1, l2, w2;
    cin >> l1 >> w1 >> l2 >> w2;
    rectangle a, b;
    a.set(l1, w1);
    b.set(l2, w2);
    a.compare(b);
    return 0;
}
```
**CPP60 长方形的关系**
```cpp
#include<bits/stdc++.h>
using namespace std;
class rectangle{
	private:
		int length,width;
	public:
		void set(int x,int y){
			length=x;
			width=y;
		}
		int getlength(){
			return length;
		}
		int getwidth(){
			return width;
		}
		int area(){
			return length*width;
		}
		string cancover(rectangle a){
			if ((length>=a.length && width>=a.width) || (length>=a.width && width>=a.length)){
				return "yes";
			}
			else{
				return "no";
			}
		}
};
int main(){
	int l1,w1,l2,w2;
	cin>>l1>>w1>>l2>>w2;
	rectangle a,b;
	a.set(l1,w1);
	b.set(l2,w2);
	cout<<a.cancover(b);
	return 0;
}
```
**CPP61 数组类的构造函数**
```cpp
#include<bits/stdc++.h>
using namespace std;
class Array{
	private:
		int n;//数组大小 
		int *a;//数组 
	public:
		Array(int isize){
			a = new int[isize]; 
			n=isize;
		}
        void in_push_back(){
			for (int i=0;i<n;i++){
				cin >> a[i];
			}
		}
		~Array(){
			delete []a;
		}
		void show(){
			for (int i=0;i<n;i++) cout<<a[i]<<' ';
		}
};
int main(){
	int isize=0;
	cin >> isize;
	Array a(isize);
	a.in_push_back();
	a.show();
	return 0;
}
```
**CPP62 数组类的拷贝构造函数**
```cpp
#include<bits/stdc++.h>
using namespace std;
class Array {
  private:
    int n;//数组大小
    int* a;//数组
  public:
    Array() {
        cin >> n;
        a = new int [n];
        for (int i = 0; i < n; i++) cin >> a[i];
    }
    ~Array() {
        delete []a;
    }
    int getlen() {
        return n;
    }
    int get(int i) {
        return a[i];
	}
    void show() {
        for (int i = 0; i < n; i++) cout << a[i] << ' ';
    }
};
int main() {
    Array a;
    a.show();
    return 0;
}
```
**CPP63 友元类**
```cpp
#include<bits/stdc++.h>
using namespace std;
class phone{
	friend class myphone;
	
	private:
		int price;
	public:
		phone(int x){
			price=x;
		}
}; 
class myphone{
	private:
		phone a;
	public:
		myphone(int x):a(x){
		}
		int getprice(){
			return a.price;
		}
};
int main(){
	int p;
	cin>>p;
	myphone a(p);
	cout<<a.getprice();
	return 0;
}


```
**CPP64 重载小于号**
```cpp
#include <iostream>
using namespace std;

class Time {

    public:
        int hours;      // 小时
        int minutes;    // 分钟

        Time() {
            hours = 0;
            minutes = 0;
        }

        Time(int h, int m) {
            this->hours = h;
            this->minutes = m;
        }

        void show() {
            cout << hours << " " << minutes << endl;
        }

        bool operator<(Time& t){
            return hours == t.hours && minutes < t.minutes || hours < t.hours;
        }
        

};

int main() {
    int h, m;
    cin >> h;
    cin >> m;

    Time t1(h, m);
    Time t2(6, 6);
	
    if (t1<t2) cout<<"yes"; else cout<<"no";
    return 0;
}
```
**CPP65 构建长方体类**
```cpp
#include<bits/stdc++.h>
using namespace std;
class rectangle {
  protected:
    int length, width;
  public:
    rectangle(int x, int y) {
        length = x;
        width = y;
    }
    void set(int x, int y) {
        length = x;
        width = y;
    }
    int area() {
        return length * width;
    }
};
int main() {
    int x, y, z;
    cin >> x >> y >> z;
    rectangle a(x, y);
    cout << a.area()*z;
    return 0;
}
```
**CPP66 求长方体表面积**
```cpp
#include<bits/stdc++.h>
using namespace std;
class rectangle {
  protected:
    int length, width;
  public:
    rectangle(int x, int y) {
        length = x;
        width = y;
    }
    void set(int x, int y) {
        length = x;
        width = y;
    }
    int getlength() {
        return length;
    }
    int getwidth() {
        return width;
    }
    int area() {
        return length * width;
    }
};
class cuboid: public rectangle {
  private:
    int height;
  public:
    cuboid(int ix, int iy, int iz): rectangle(ix, iy), height(iz) {}
    int area() {
        return 2 * (length * width + length * height + height * width);
    }

};
int main() {
    int x, y, z;
    cin >> x >> y >> z;
    cuboid a(x, y, z);
    cout << a.rectangle::area() << '\n' << a.area();
    return 0;
}
```
**CPP67 多态实现求面积体积**
```cpp
#include<bits/stdc++.h>
using namespace std;
class rectangle {
  protected:
    int length, width;
  public:
    rectangle(int x, int y) {
        length = x;
        width = y;
    }
    void set(int x, int y) {
        length = x;
        width = y;
    }
    int getlength() {
        return length;
    }
    int getwidth() {
        return width;
    }
    virtual int getval() {
        return length * width;
    }

};
class cuboid: public rectangle {
  private:
    int height;
  public:
    cuboid(int x, int y, int z): rectangle(x, y) {
        height = z;
    }
    int getval() {
        return length * width * height;
    }

};
int main() {
    int x, y, z;
    cin >> x >> y >> z;
    cuboid a(x, y, z);
    rectangle b(x, y);

    rectangle* p = &b;
    cout << p->getval() << '\n';

    p = &a;
    cout << p->getval();
    return 0;
}
```
**CPP68 迭代器遍历set**
```cpp
#include<bits/stdc++.h>
using namespace std;
int main(){
	set<int>s;
	int i=0;
	while (cin >> i){
		s.insert(i);
	}
	for (set<int>::iterator it = s.begin();s.end()!=it;it++){
		cout << *it << " ";
	}
	return 0;
}
```
**CPP69 最后k个元素**
```cpp
#include<bits/stdc++.h>
using namespace std;
int main() {
    int k, i;
    vector<int>a;
    cin >> k >> k;
    while (cin >> i) {
        a.push_back(i);
    }
    for (vector<int>::reverse_iterator rit = a.rbegin(); k; k--) {
        cout << *rit++ << " ";
    }
    return 0;
}
```
**CPP71 判断元素是否出现**
```cpp
#include<bits/stdc++.h>
using namespace std;
int main(){
	map<int,int>m;
	int in=0;
	int im=0;
	int itemp=0;
	cin >> in >> im;
	for (;in;in--){
		cin >> itemp;
		m.insert({itemp,itemp});
	}
	while (cin >> itemp){
		cout << (NULL != m[itemp] ? "yes" : "no") << endl;
	}
	return 0;
}
```
**CPP72 找到数组里的第k大数(C++)**
```cpp
#include<bits/stdc++.h>
using namespace std;
int main(){
	int n,k;
	vector<int>a;
	cin >> n >> k;
	int i=0;
	while (cin >> i){
		a.push_back(i);
	}
	sort(a.begin(),a.end());
	for (k--; k--; ){
		a.erase(a.begin());
	}
	cout << a.front();
	return 0;
}
```
**NC52 有效括号序列**
```cpp
#include <stack>
#include <map>
class Solution {
public:
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     * 
     * @param s string字符串 
     * @return bool布尔型
     */
    bool isValid(string s) {
        stack<char>st;
        map<char, char>tempm={{')', '('}, {']', '['}, {'}', '{'}};
        char cback=0;
        for (int i=0; s[i]; i++){//例：([{}])
            if ('(' == s[i] || '[' == s[i] || '{' == s[i]){
                st.push(s[i]);//([{
            }
            else if(')' == s[i] || ']' == s[i] || '}' == s[i]){//}])
                if (st.size() && st.top() == tempm[s[i]]){//防"]"使程序崩
                    st.pop();
                }
                else {
                    return false;
                }
            }
        }
        return s.size() && !st.size();//防"["和空字符串合法
    }
};
```
**NC160 二分查找-I**
```cpp
class Solution {
public:
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     *
     * 
     * @param nums int整型vector 
     * @param target int整型 
     * @return int整型
     */
    int search(vector<int>& nums, int target) {
        if (nums.size()){
            int ilow = 0;    
            int ihigh = nums.size() - 1;    
            int imid = 0;
            while (ilow <= ihigh){
                imid = (ilow + ihigh) / 2;
                if (nums[imid] < target) {
                    ilow = imid + 1;
                }
                else if (nums[imid] > target){
                    ihigh = imid - 1;
                }
                else {
                    return imid;
                }
            }                      
        }
        return -1;     
    }
};
```
**OR119 01序列**
```cpp
#include <iostream>
using namespace std;
 
int main() {
    int i = 0;
    int ia = 0;
    int in = 0;
    int iswap = 0;
    cin >> i;
    int* arr = new int[i];
    for (; ia < i; ia++) {
        cin >> arr[ia];
    }
    arr[0] || arr[1] || (arr[0] = 1, iswap++), arr[i - 2] || arr[i - 1] || (arr[i - 1] = 1, iswap++);//00000 -> 10001
    cin >> in;
    for (ia = 1; ia < i - 1; ia++) {
        (arr[ia - 1] || arr[ia] || arr[ia + 1]) || (arr[ia] = 1, iswap++);// 000 -> 010
    }
    cout << ((in > iswap) ? "false" : "true");
    delete[] arr;
}
// 64 位输出请用 printf("%lld")
```
**PIO17 单组_spj判断浮点误差**
```cpp
#include <iostream>
using namespace std;

int main() {
    char str[1001001] = "";
    int i = 0;
    int ia = 0;
    cin >> i >> ia;
    i *= ia;
    char* cp = &str[i + i / ia - 2];
    int ib = ia;
    ia = i;
    for (; i; i--) {
        cin >> *cp--;
        if (i - 1 && i != ia && !((i - 1) % ib)) {
            *cp-- = '\n';
        }
    }
    cout << str;
    return 0;
}//11 10 9 * 7 6 5 * 3 2 1 0
//" lkji/hgfe/dcba"
```
**PIO17 单组_spj判断浮点误差**
```cpp
#include <iostream>
using namespace std;

int main() {
    int ir = 0;
    cin >> ir;
    cout << 3.14 * ir * ir;
    return 0;
}
// 64 位输出请用 printf("%lld")
```
**WY36 交错01串**
```cpp
#include <iostream>
using namespace std;

int main() {
    char str[51] = "";
    char* cp = str;
    int i = 1;
    int ia = 0;
    int ib = 0;
    cin.getline(str, sizeof str);
    for (; *cp; cp++) {
        ib = cp[1] - '0';
        if (0 > ib) {
            ia <= i && (ia = i);
            break;
        } else if ((*cp - '0') != ib) {
            i++;
        } else {
            ia <= i && (ia = i);
            i = 1;
        }
    }
    cout << ia;
}
// 64 位输出请用 printf("%lld")
```
**WY56 缩写**
```cpp
#include <iostream>
using namespace std;

int main() {
    char str[51] = "";
    while (cin >> str){
        cout << str[0];
    }
    return 0;
}
// 64 位输出请用 printf("%lld")
```
## SQL

### 基础

**SQL1 查询所有列**
```sql
SELECT id, device_id, gender, age, university, province FROM user_profile;
```
**SQL2 查询多列**
```sql
SELECT device_id, gender, age, university FROM user_profile;
```
**SQL3 查询结果去重**
```sql
SELECT DISTINCT(university) FROM user_profile;
```
**SQL4 查询结果限制返回行数**
```sql
SELECT device_id FROM user_profile LIMIT 2;
```
**SQL5 将查询后的列重新命名**
```sql
SELECT device_id user_infos_example FROM user_profile LIMIT 2;
```
**SQL6 查找学校是北大的学生信息**
```sql
SELECT device_id, university FROM user_profile WHERE '北京大学' = university;
```
**SQL7 查找年龄大于24岁的用户信息**
```sql
SELECT device_id, gender, age, university FROM user_profile WHERE age >= 24;
```
**SQL8 查找某个年龄段的用户信息**
```sql
SELECT device_id, gender, age FROM user_profile WHERE age BETWEEN 20 AND 23;
```
**SQL9 查找除复旦大学的用户信息**
```sql
SELECT device_id, gender, age, university FROM user_profile WHERE university NOT LIKE '复旦%';
```
**SQL10 用where过滤空值练习** 
```sql
SELECT device_id, gender, age, university FROM user_profile WHERE age IS NOT NULL;
```
**SQL11 高级操作符练习(1)**
```sql
SELECT device_id, gender, age, university, gpa FROM user_profile WHERE 'male' = gender AND gpa > 3.5;
```
**SQL12 高级操作符练习(2)**
```sql
SELECT device_id, gender, age, university, gpa FROM user_profile WHERE gpa > 3.7 OR university LIKE '北%';
```
**SQL13 Where in 和Not in**
```sql
SELECT device_id, gender, age, university, gpa FROM user_profile WHERE university REGEXP '(北京|山东|复旦).*';
```
**SQL14 操作符混合运用**
```sql
SELECT device_id, gender, age, university, gpa FROM user_profile WHERE university LIKE '山%' AND gpa > 3.5 OR university LIKE '复%' AND gpa > 3.8;
```
**SQL15 查看学校名称中含北京的用户**
```sql
SELECT device_id, age, university FROM user_profile WHERE university LIKE '%北京%';
```
**SQL16 查找GPA最高值**
```sql
SELECT ROUND(MAX(gpa), 1) gpa FROM user_profile WHERE university LIKE '复%';
```
**SQL17 计算男生人数以及平均GPA**
```sql
SELECT COUNT(gender) male_num, AVG(gpa) avg_gpa FROM user_profile WHERE gender LIKE 'm%';
```
**SQL18 分组计算练习题**
```sql
SELECT
    gender,
    university,
    COUNT(gender) as user_num,
    avg(active_days_within_30) as avg_active_day,
    avg(question_cnt) as avg_question_cnt
FROM
    user_profile
GROUP BY
    university,
    gender
ORDER BY
    gender ASC,
    university ASC;
```
**SQL20 分组排序练习题**
```sql
SELECT university, ROUND(AVG(question_cnt), 4) avg_question_cnt FROM user_profile GROUP BY university ORDER BY avg_question_cnt ASC;
```
**SQL21 浙江大学用户题目回答情况**
```sql
SELECT device_id, question_id, result FROM question_practice_detail WHERE device_id IN(SELECT device_id FROM user_profile WHERE university LIKE '浙%') ORDER BY question_id ASC;
```
**SQL22 统计每个学校的答过题的用户的平均答题数**
```sql
SELECT
    university,
    ROUND(
        COUNT(university) / COUNT(DISTINCT(user.device_id)), 4
    ) avg_answer_cnt
FROM
    user_profile user
    INNER JOIN question_practice_detail question 
    ON user.device_id = question.device_id
GROUP BY
    university
ORDER BY
    university ASC;
```
**SQL24 统计每个用户的平均刷题数**
```cpp
SELECT
    '山东大学', q.difficult_level, COUNT(*) / COUNT(DISTINCT usr.device_id)
FROM
    user_profile usr, question_practice_detail qp, question_detail q
WHERE
    usr.device_id = qp.device_id AND qp.question_id = q.question_id AND usr.university LIKE '山东%'
GROUP BY
    q.difficult_level;
```
**SQL25 查找山东大学或者性别为男生的信息**
```cpp
SELECT device_id, gender, age, gpa FROM user_profile WHERE university LIKE '山东%'
UNION ALL
SELECT device_id, gender, age, gpa FROM user_profile WHERE gender LIKE 'm%';
```
**SQL26 计算25岁以上和以下的用户数量**
```sql
SELECT
    (
        CASE
            WHEN age >= 25 THEN "25岁及以上"
            ELSE "25岁以下"
        END
    ) age_cut,
    COUNT(*) number
FROM
    user_profile
GROUP BY
    age_cut;
```
**SQL27 查看不同年龄段的用户明细**
```sql
SELECT
    device_id,
    gender,
    CASE
        WHEN age IS NULL THEN '其他'
        WHEN age < 20 THEN '20岁以下'
        WHEN age BETWEEN 20 AND 24  THEN '20-24岁'
        ELSE '25岁及以上'
    END age_cut
FROM
    user_profile;
```
**SQL28 计算用户8月每天的练题数量**
```sql
SELECT 
    DAY(date) day, 
    COUNT(id) question_cnt
FROM 
    question_practice_detail
GROUP BY
    date
HAVING
    8 = MONTH(date);
```
**SQL30 统计每种性别的人数**
```sql
SELECT 
    SUBSTRING_INDEX(profile, ',', -1), COUNT(*) 
FROM   
    user_submit 
GROUP BY
    SUBSTRING_INDEX(profile, ',', -1);
```
**SQL31 提取博客URL中的用户名**
```sql
SELECT device_id, SUBSTRING_INDEX(blog_url, 'l/', -1) FROM user_submit;
```
**SQL32 截取出年龄**
```sql
SELECT 
    SUBSTRING_INDEX(SUBSTRING_INDEX(profile, ',', -2), ',', 1) age, COUNT(*) number 
FROM 
    user_submit
GROUP BY
    SUBSTRING_INDEX(SUBSTRING_INDEX(profile, ',', -2), ',', 1);
```
**SQL33 找出每个学校GPA最低的同学**
```sql
SELECT 
    device_id, university, gpa
FROM
    (
    SELECT
        device_id, university, gpa, 
        COUNT(*) OVER(PARTITION BY university ORDER BY gpa DESC ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING) id
    FROM
        user_profile
    ) tb
WHERE
    id = 1
ORDER BY
    university;
```
**SQL36 查找后排序**
```sql
SELECT device_id, age FROM user_profile ORDER BY age ASC;
```
**SQL37 查找后多列排序**
```sql
SELECT device_id, gpa, age FROM user_profile ORDER BY gpa ASC, age ASC;
```
**SQL38 查找后降序排列**
```sql
SELECT device_id, gpa, age FROM user_profile ORDER BY gpa DESC, age DESC;
```
**SQL39 21年8月份练题总数**
```sql
SELECT 
    COUNT(DISTINCT device_id), COUNT(device_id)
FROM
    question_practice_detail
WHERE
    2021 = YEAR(date) AND 8 = MONTH(date);
```
**SQL200 查找最晚入职员工的所有信息**
```sql
SELECT emp_no, birth_date, first_name, last_name, gender, hire_date FROM employees ORDER BY hire_date DESC LIMIT 1;
```
**SQL201 查找入职员工时间升序排名的情况下的倒数第三的员工所有信息**
```sql
SELECT
    emp_no,
    birth_date,
    first_name,
    last_name,
    gender,
    hire_date
FROM
    employees
WHERE
    hire_date = (
        SELECT
            hire_date
        FROM
            employees
        GROUP BY 
            hire_date
        ORDER BY
            hire_date DESC
        LIMIT
            2, 1
    );

```
**SQL202 查找当前薪水详情以及部门编号dept_no**
```sql
SELECT
    s.emp_no, s.salary, s.from_date, s.to_date, d.dept_no
FROM
    salaries s, dept_manager d
WHERE
    s.emp_no = d.emp_no;
```

### 大厂

**SQL1 每个月Top3的周杰伦歌曲**
```sql
SELECT 
    month, ranking, song_name, play_pv
FROM
(
    SELECT 
        MONTH(pl.fdate) month, 
        ROW_NUMBER() OVER (PARTITION BY MONTH(pl.fdate) ORDER BY COUNT(*) DESC, si.song_id) ranking,
        si.song_name,
        COUNT(*) play_pv
    FROM
        play_log pl, song_info si, user_info ui
    WHERE
        pl.user_id = ui.user_id AND pl.song_id = si.song_id AND ui.age BETWEEN 18 AND 25 AND YEAR(pl.fdate) = 2022 AND si. singer_name   LIKE '周%'
    GROUP BY
        month, si.song_name, si.song_id
) tb
WHERE
    ranking <= 3;
```

