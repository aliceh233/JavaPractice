# Java Interface: BitSet

java.util

-- referred from Oracle Java™ Platform Standard Ed. 8:[https://docs.oracle.com/javase/7/docs/api/java/util/BitSet.html](https://docs.oracle.com/javase/7/docs/api/java/util/BitSet.html)

## Example:
Make operation between two determined bitSize of bit set.

```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        /* Enter your code here. Read input from STDIN. Print output to STDOUT. Your class should be named Solution. */
        Scanner s = new Scanner(System.in);
        int bitSize = s.nextInt();
        int inputSize = s.nextInt();
        
        BitSet bitSet_1 = new BitSet(bitSize);
        BitSet bitSet_2 = new BitSet(bitSize);
        BitSet[] bitSets = {bitSet_1, bitSet_2};
        
        for (int i = 0; i < inputSize; i++) {
            String operation = s.next();
            int firstArg = s.nextInt();
            int secondArg = s.nextInt();
            
            switch (operation) {
                case "AND":
                bitSets[firstArg-1].and(bitSets[secondArg-1]);
                break;
                case "OR":
                bitSets[firstArg-1].or(bitSets[secondArg-1]);
                break;
                case "XOR":
                bitSets[firstArg-1].xor(bitSets[secondArg-1]);
                break;
                case "FLIP":
                bitSets[firstArg-1].flip(secondArg);
                break;
                case "SET":
                bitSets[firstArg-1].set(secondArg);
                break;
            }
           System.out.println(bitSet_1.cardinality() + " " + bitSet_2.cardinality());     
        }
        
    }
}
```