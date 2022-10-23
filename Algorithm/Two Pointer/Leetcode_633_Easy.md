```java

import java.lang.Math.*;

class Solution {
    public boolean judgeSquareSum(int c) {
        if (c < 0) return false;
        
        long start = 0, end = (int) Math.sqrt(c);
        
        while(start <= end) {
            long sum = start * start + end * end;
            
            if (sum == c) {
                return true;
            } else if (sum > c) {
                end--;
                
            } else {
                start++;
            }
        }
        
        return false;
    }
}

```