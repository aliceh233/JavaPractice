```java

import java.util.Scanner;
import java.util.*;
import java.util.Collections;
// 注意类名必须为 Main, 不要有任何 package xxx 信息
public class Main {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        Set<Integer> l = new HashSet<Integer>();
        // 注意 hasNext 和 hasNextLine 的区别
        int size = in.nextInt();
        while (in.hasNextInt()) { // 注意 while 处理多个 case

            int n = in.nextInt();
            l.add(n);
        }

        List<Integer> li = new ArrayList<Integer>(l);
        Collections.sort(li);

        for (Integer i : li) {
            System.out.println(i);
        }
    }
}
```