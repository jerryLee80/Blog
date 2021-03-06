# 题目
给出一个非负整数数组，你最初定位在数组的第一个位置。　　　

数组中的每个元素代表你在那个位置可以跳跃的最大长度。　　　　

判断你是否能到达数组的最后一个位置。

**样例**
A = [2,3,1,1,4]，返回 true.

A = [3,2,1,0,4]，返回 false.

# 分析
这个问题有两个方法，一个是贪心和 动态规划。

贪心方法时间复杂度为O（N）。

动态规划方法的时间复杂度为为O（n^2）。

# 代码
```
public class Solution {
    /**
     * @param A: A list of integers
     * @return: The boolean answer
     */
    public boolean canJump(int[] A) {
        boolean[] can = new boolean[A.length];
        can[0] = true;
        
        for(int i=1;i<A.length;i++) {
        	for(int j=0;j<i;j++) {
        		if(j+A[j]>=i && can[j]) {
        			can[i] = true;
        			break;
        		}
        			
        	}
        }
        
        return can[A.length-1];

    }
}

```
```
public class Solution {
    /**
     * @param A: A list of integers
     * @return: The boolean answer
     */
    public boolean canJump(int[] A) {
        if(A.length == 0 || A == null)
	    	return false;
	    
	    int farthest = A[0];
	    
	    for(int i=1;i<A.length;i++) {
	    	if(i+A[i]>farthest && farthest>=i)
	    		farthest = i+A[i];
	    }
	    
	    return farthest >= A.length-1;

    }
}

```
