# Pow(x, n)	
	
实现 [pow(*x*, *n*)](https://www.cplusplus.com/reference/valarray/pow/) ，即计算 x 的 n 次幂函数。	
	
**示例 1:**	
	
```	
输入: 2.00000, 10	
输出: 1024.00000	
```	
	
**示例 2:**	
	
```	
输入: 2.10000, 3	
输出: 9.26100	
```	
	
**示例 3:**	
	
```	
输入: 2.00000, -2	
输出: 0.25000	
解释: 2-2 = 1/22 = 1/4 = 0.25	
```	
	
**说明:**	
	
- -100.0 < *x* < 100.0	
- *n* 是 32 位有符号整数，其数值范围是 [−231, 231 − 1] 。	
	
```java	
	public double myPow(double x, int n) {	
        if(x == 0)	
            return 0D;	
        if(n == 0)	
            return 1D;	
        if(n == 1)	
            return x;	
        if(n == -1)	
            return 1 / x;	
	
        //二分法	
        if(n > 0){	
            if(n % 2 == 1){	
                double d = myPow(x, (n-1) / 2);	
                return d * d * x;	
            } else {	
                double d = myPow(x, n / 2);	
                return d * d;	
            }	
        } else {	
            if(n % 2 == -1){	
                double d = myPow(x, (n+1) / 2);	
                return d * d / x;	
            } else {	
                double d = myPow(x, n / 2);	
                return d * d;	
            }	
        }	
    }	
	
    //超时算发	
    public double myPow1(double x, int n) {	
        if(x == 0)	
            return 0D;	
        if(n == 0)	
            return 1D;	
	
        double c = 1.0D;	
        if(n > 0){	
            while (n > 0){	
                c *= x;	
                n--;	
            }	
        } else {	
            while (n < 0){	
                c /= x;	
                n++;	
            }	
        }	
        return c;	
    }	
```	
	
