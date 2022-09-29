> # ArrayList vs. LinkedList
> 
> The LinkedList class is a collection which can contain many objects of the same type, just like the ArrayList.
> 
> The LinkedList class has all of the same methods as the ArrayList class because they both implement the List interface. This means that you can add items, change items, remove items and clear the list in the same way.
> 
> However, while the ArrayList class and the LinkedList class can be used in the same way, they are built very differently.
> 
> ## How the ArrayList work
> 
> The ArrayList class has a regular array inside it. When an element is added, it is placed into the array. If the array is not big enough, a new, larger array is created to replace the old one and the old one is removed.
> 
> ## How the LinkedList works
> The LinkedList stores its items in "containers." The list has a link to the first container and each container has a link to the next container in the list. To add an element to the list, the element is placed into a new container and that container is linked to one of the other containers in the list.
> 
-- referred from W3Cschool:[https://www.w3schools.com/java/java_linkedlist.asp](https://www.w3schools.com/java/java_linkedlist.asp)

```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        /* Enter your code here. Read input from STDIN. Print output to STDOUT. Your class should be named Solution. */
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        // either ArrayList or LinkedList would be fine, both have remove(index), and add(index, element).
        List<Integer> arr = new ArrayList<>();
        
        for (int i = 0; i < n; i++) {
            arr.add(scanner.nextInt());
        }
        
        int operations = scanner.nextInt();
        for (int j = 1; j <= operations; j++) {
            String s = scanner.next();
            switch(s){
                case "Insert":
                // System.out.println(s);
                int insertPosition = scanner.nextInt();
                int temp = scanner.nextInt();
                arr.add(insertPosition, temp);
                break;
                case "Delete":
                // System.out.println(s);
                int deletePosition = scanner.nextInt();
                arr.remove(deletePosition);
                break;
            }
        }
        //2 methods to print numbers:
        // 
        // for (int i : arr) {
        //     System.out.print(i + " ");
        // }
        //
        scanner.close();
        System.out.println(
            arr.toString()
                .replace("[", "")
                .replace("]", "")
                .replace(",", ""));
    }
}
```