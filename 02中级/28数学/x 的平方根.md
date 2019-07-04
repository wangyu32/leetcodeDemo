# x 的平方根	
	
实现 `int sqrt(int x)` 函数。	
	
计算并返回 *x* 的平方根，其中 *x* 是非负整数。	
	
由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。	
	
**示例 1:**	
	
```	
输入: 4	
输出: 2	
```	
	
**示例 2:**	
	
```	
输入: 8	
输出: 2	
说明: 8 的平方根是 2.82842..., 	
     由于返回类型是整数，小数部分将被舍去。	
```	
	
```java	
	public int mySqrt(int x) {	
        //牛顿迭代法	
        if (x == 0) return 0;	
        double res = 1, pre = 0;	
        while ((res - pre) > 0 ? (res - pre) > 1e-6 : (pre - res) > 1e-6) { //手动指定一个精度	
            pre = res;	
            res = (res + x / res) / 2;	
        }	
        return (int)res;	
    }	
	
    //最快的	
    public int mySqrtNewton2(int x) {	
        //牛顿迭代法	
        long res = x;	
        while (res * res > x) {	
            res = (res + x / res) / 2;	
        }	
        return (int)res;	
    }	
	
    public int mySqrtNewton1(int x) {	
        //牛顿迭代法	
        if (x == 0) return 0;	
        double last = 0;	
        double res = 1;	
        while (res != last) { //使用double的精度	
            last = res;	
            res = (res + x / res) / 2;	
        }	
        return (int)res;	
    }	
	
    public int mySqrt1(int x) {	
        //参考https://www.cnblogs.com/grandyang/p/4346413.html	
        if (x <= 1)	
            return x;	
        int left = 0, right = x;	
        while (left < right) {	
            int mid = left + (right - left) / 2;	
            if (x / mid >= mid)	
                left = mid + 1;	
            else	
                right = mid;	
        }	
        return right - 1;	
    }	
	
    //Line 16: java.lang.StackOverflowError	
    public int mySqrtWy(int x) {	
        if(x == 0 || x == 1)	
            return x;	
	
        return mySqrt(1, x/2, x/2, x);	
    }	
	
    private int mySqrt(int start, int mid, int end, int x) {	
        if(mid * mid <= x && (mid + 1) * (mid + 1) > x)	
            return mid;	
	
        if(mid * mid > x){	
            return mySqrt(start, (start + mid) / 2, mid, x);	
        } else {	
            return mySqrt(mid, end, end, x);	
        }	
    }	
```	
	
