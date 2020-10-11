# 替换空格
**题目：** 请实现一个函数，把字符串 s 中的每个空格替换成"%20"。

**例子：** `输入：s = "We are happy."
输出："We%20are%20happy."`

**思路：** 最简单思路直接使用string的replace（）函数，api编程法，但没啥学习意义。另一种思路是首先遍历，找出有cnt个空格，然后把字符串resize到`2*cnt+s.size()`，最后从后面开始遍历，i指向原数组最后，j指向新数组最后，i遇到空格时，j将接下来三个赋值为`%20`，知道当i==j时，表明再无空格。如果从前面开始遍历，则没替换一次，后面都需要移动，复杂度n2。

**代码：**
```cpp
    class Solution {
public:
    string replaceSpace(string s) {
        int cnt = 0, i = 0, j;
        while (s[i])
        {
            if (s[i] == ' ') cnt++;
            i++;
        }
        s.resize(s.size()+2*cnt);
        i--;
        for (i,j=s.size()-1; i!=j; i--)
        {
            if (s[i] != ' ') {
                s[j--] = s[i];
            }
            else
            {
                s[j--] = '0';
                s[j--] = '2';
                s[j--] = '%';
            }
        }
        return s;
    }
};
```