```java
import java.lang.Math.*;
class Solution {
    public int[][] intervalIntersection(int[][] firstList, int[][] secondList) {
        List<int[]> result = new ArrayList<int[]>();
        
        if (firstList == null || secondList == null || firstList.length == 0 || secondList.length == 0) return new int[0][];
        
        int i = 0, j = 0;
        
        while (i < firstList.length && j < secondList.length) {
            int min = Math.max(firstList[i][0], secondList[j][0]);
            int max = Math.min(firstList[i][1], secondList[j][1]);
            
            if (min <= max) {
                result.add(new int[]{min, max});
            } 
            
            if (firstList[i][1] < secondList[j][1])
                i++;
            else 
                j++;
        }
        
        
        return result.toArray(new int[result.size()][]);
    }
}
```