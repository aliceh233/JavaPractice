```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Solution {

 public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        int t = s.nextInt();
        String [] pair_left = new String[t];
        String [] pair_right = new String[t];
        
        for (int i = 0; i < t; i++) {
            pair_left[i] = s.next();
            pair_right[i] = s.next();
        }

    //create a set
    Set<String> set = new LinkedHashSet<>();
        for (int i = 0; i < t; i++) {
            //add the pair into the set, if the pair is dublicated, it won't be added successfully
            set.add(String.format("%s %s", pair_left[i], pair_right[i]));
            //print out the current size
            System.out.println(set.size());
        }
   }
}

```