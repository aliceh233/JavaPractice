# Java Interface: Comparator

java.util

## Method Detail

int compare(T o1,
               T o2)

Compares its two arguments for order. Returns a negative integer, zero, or a positive integer as the first argument is less than, equal to, or greater than the second.
In the foregoing description, the notation sgn(expression) designates the mathematical signum function, which is defined to return one of -1, 0, or 1 according to whether the value of expression is negative, zero or positive.

-- referred from Oracle Java™ Platform Standard Ed. 8:[https://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html](https://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html)

Typically:

0: if (x==y)
-1: if (x < y)
1: if (x > y)

```java
import java.util.*;

// Write your Checker class here
class Checker implements Comparator <Player>{
    @Override
    public int compare(Player p1, Player p2) {
       if(p1.score==p2.score){
            return (p1.name.compareTo(p2.name));
        }
        // Since we want a reverse order(print the lowest score at last), so if the p1.score is smaller than p2.score, we make it return 1, else -1.
        return(p1.score<p2.score)?1:-1;     
    }
}
class Player{
    String name;
    int score;
    
    Player(String name, int score){
        this.name = name;
        this.score = score;
    }
}

class Solution {

    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt();

        Player[] player = new Player[n];
        Checker checker = new Checker();
        
        for(int i = 0; i < n; i++){
            player[i] = new Player(scan.next(), scan.nextInt());
        }
        scan.close();
     
        Arrays.sort(player, checker);
        for(int i = 0; i < player.length; i++){
            System.out.printf("%s %s\n", player[i].name, player[i].score);
        }
    }
}
```

There is another example for comparator but with easy level:

```java
import java.util.*;

class Student{
	private int id;
	private String fname;
	private double cgpa;
	public Student(int id, String fname, double cgpa) {
		super();
		this.id = id;
		this.fname = fname;
		this.cgpa = cgpa;
	}
	public int getId() {
		return id;
	}
	public String getFname() {
		return fname;
	}
	public double getCgpa() {
		return cgpa;
	}
}


public class Solution
{
	public static void main(String[] args){
		Scanner in = new Scanner(System.in);
		int testCases = Integer.parseInt(in.nextLine());
		
		List<Student> studentList = new ArrayList<Student>();
		while(testCases>0){
			int id = in.nextInt();
			String fname = in.next();
			double cgpa = in.nextDouble();
			
			Student st = new Student(id, fname, cgpa);
			studentList.add(st);
			
			testCases--;
		}
    // Here we create a new comparator override the compare method, make comparation between 2 objects(students).
        studentList.sort(new Comparator<Student> () {
            @Override
            public int compare(Student s1, Student s2) {
                if (s1.getCgpa() == s2.getCgpa()) {
                    return s1.getFname().compareTo(s2.getFname());
                } else {
                    return (s1.getCgpa() < s2.getCgpa()? 1: -1);
                }
            }
        });
      
      	for(Student st: studentList){
			System.out.println(st.getFname());
		}
	}
}

```