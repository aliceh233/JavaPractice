> # Java class: PriorityQueue
> 
> java.lang.Object
>   java.util.AbstractCollection<E>
>       java.util.AbstractQueue<E>
>           java.util.PriorityQueue<E>
> 
> An unbounded priority queue based on a priority heap. The elements of the priority queue are ordered according to their natural ordering, or by a Comparator provided at queue construction time, depending on which constructor is used. A priority queue does not permit null elements. A priority queue relying on natural ordering also does not permit insertion of non-comparable objects (doing so may result in ClassCastException).
> The head of this queue is the least element with respect to the specified ordering. If multiple elements are tied for least value, the head is one of those elements -- ties are broken arbitrarily. The queue retrieval operations poll, remove, peek, and element access the element at the head of the queue.
-- referred from Oracle Java™ Platform Standard Ed. 8:[https://docs.oracle.com/javase/7/docs/api/java/util/PriorityQueue.html](https://docs.oracle.com/javase/7/docs/api/java/util/PriorityQueue.html)

## Example:
Make a priority queue to manage student system

```java
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;
import java.util.*;
import java.util.stream.Collectors;
/*
 * Create the Student and Priorities classes here.
 */
class Priorities {
    
    public List<Student> getStudents(List<String> events) {
        PriorityQueue<Student> q = new PriorityQueue<>();

        for (String event : events) {
            if (event.contains("ENTER")) {
                String[] student = event.split(" ");
                Student s = new Student(
                        student[1],
                        Double.parseDouble(student[2]),
                        Integer.parseInt(student[3]));
                q.add(s);
            }

            if (event.contains("SERVED")) {
                if (q.size() > 0) {
                    q.poll();
                }
            }
        }
        
        return q.stream().sorted().collect(Collectors.toList());
    }
}

class Student implements Comparable<Student>{
    
    private String name;
    private double cgpa;
    private int id;
    
    public Student(){}
    
    public Student(String name, double cgpa, int id) {
        this.id = id;
        this.name = name;
        this.cgpa = cgpa;
    }
    
    public int getId() {
        return this.id;
    }
    
    public String getName() {
        return this.name;
    }
    
    public double getCGPA() {
        return this.cgpa;
    }
    
    @Override
    public int compareTo(Student o) {
        if(this.cgpa == o.cgpa) {
            if(this.name.equals(o.name)) {
                return this.id - o.id;
            }else {
                return this.name.compareTo(o.name);
            }
        }else {
            return this.cgpa < o.cgpa ? 1 : -1;
        }
    }
    
}


public class Solution {
    private final static Scanner scan = new Scanner(System.in);
    private final static Priorities priorities = new Priorities();
    
    public static void main(String[] args) {
        int totalEvents = Integer.parseInt(scan.nextLine());    
        List<String> events = new ArrayList<>();
        
        while (totalEvents-- != 0) {
            String event = scan.nextLine();
            events.add(event);
        }
        
        List<Student> students = priorities.getStudents(events);
        
        if (students.isEmpty()) {
            System.out.println("EMPTY");
        } else {
            for (Student st: students) {
                System.out.println(st.getName());
            }
        }
    }
}
```