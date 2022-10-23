```java
import java.util.Scanner;
import java.lang.Math.*;
// 注意类名必须为 Main, 不要有任何 package xxx 信息
public class Main {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        // 注意 hasNext 和 hasNextLine 的区别
        while (in.hasNextLine()) { // 注意 while 处理多个 case
            String str = in.nextLine();
            str = str.substring(2);
            int index = str.length() - 1;
            int result = 0;

            for (int i = 0; i <=index; i++) {
                char ch = str.charAt(i);
                if (ch > '0' && ch <= '9') {
                    result += (ch - '0') * Math.pow(16, (index - i));
                }
                if (ch >= 'A') {
                    result += (ch - 'A' + 10) * Math.pow(16, (index - i));
                }
            }
            System.out.println(result);

        }
    }
}
```