# Excel表列序号	
	
给定一个Excel表格中的列名称，返回其相应的列序号。	
	
例如，	
	
```	
    A -> 1	
    B -> 2	
    C -> 3	
    ...	
    Z -> 26	
    AA -> 27	
    AB -> 28 	
    ...	
```	
	
**示例 1:**	
	
```	
输入: "A"	
输出: 1	
```	
	
**示例 2:**	
	
```	
输入: "AB"	
输出: 28	
```	
	
**示例 3:**	
	
```	
输入: "ZY"	
输出: 701	
```	
	
**致谢：**	
特别感谢 [@ts](http://leetcode.com/discuss/user/ts) 添加此问题并创建所有测试用例。	
	
```java	
	public int titleToNumber(String s) {	
        // A - Z 对应asc码 65-90	
        char[] array = s.toCharArray();	
        int total = 0;	
        int len = array.length;	
        for (int i = 0; i < len; i++) {	
            total += ((int)array[i] - 64) * pow(26, len - i - 1);	
        }	
        return total;	
    }	
	
    //求a的b次幂	
    private int pow(int a, int b){	
        if(b == 0)	
            return 1;	
	
        int c = 1;	
        while (b > 0){	
            c *= a;	
            b--;	
        }	
        return c;	
    }	
```	
	
