> # Java Interface: Deque
> 
> java.util
>
This interface extends the Queue interface. When a deque is used as a queue, FIFO (First-In-First-Out) behavior results. Elements are added at the end of the deque and removed from the beginning. The methods inherited from the Queue interface are precisely equivalent to Deque methods as indicated in the following table:

<table>
  <tr>
    <th>Queue Method</th>
    <th>Equivalent Deque Method</th>
  </tr>
  <tr>
    <td>add(e)</td>
    <td>addLast(e)</td>
  </tr>
  <tr>
    <td>offer(e)</td>
    <td>offerLast(e)</td>
  </tr>
    <tr>
    <td>remove()</td>
    <td>removeFirst()</td>
  </tr>
    <tr>
    <td>poll()</td>
    <td>pollFirst()</td>
  </tr>
    <tr>
    <td>element()</td>
    <td>getFirst()</td>
  </tr>
    <tr>
    <td>peek()</td>
    <td>peekFirst()</td>
  </tr>
 </table>

 Deques can also be used as LIFO (Last-In-First-Out) stacks. This interface should be used in preference to the legacy Stack class. When a deque is used as a stack, elements are pushed and popped from the beginning of the deque. Stack methods are precisely equivalent to Deque methods as indicated in the table below:
<table>
  <tr>
    <th>Stack Method</th>
    <th>Equivalent Deque Method</th>
  </tr>
  <tr>
    <td>push(e)</td>
    <td>addFirst(e)</td>
  </tr>
  <tr>
    <td>pop()</td>
    <td>removeFirst()</td>
  </tr>
    <tr>
    <td>peek()</td>
    <td>peekFirst()</td>
  </tr>
 </table>

-- referred from Oracle Java™ Platform Standard Ed. 8:[https://docs.oracle.com/javase/7/docs/api/java/util/Deque.html](https://docs.oracle.com/javase/7/docs/api/java/util/Deque.html)
 ## Example:
Find the maximum number of unique integers among all the possible contiguous subarrays of any size m.

 ```java
import java.util.*;
    public class test {
        public static void main(String[] args) {
            Scanner in = new Scanner(System.in);
            Deque deque = new ArrayDeque<>();
            int n = in.nextInt();
            int m = in.nextInt();
            Set<Integer> set = new HashSet<Integer>();
            int max = 0;
            
            for (int i = 0; i < n; i++) {
                int num = in.nextInt();
                deque.add(num);
                set.add(num);
                
                if (deque.size() == m) {
                    if (max < set.size()) {
                        max = set.size();
                    }
                    Object remove_num = deque.pollFirst();
                    if (!deque.contains(remove_num)) {
                        set.remove(remove_num);
                    }
                }
                
            }
            System.out.println(max);
        }
    }

 ```
	
	
	
	