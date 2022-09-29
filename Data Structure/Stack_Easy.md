```java
import java.util.*;
class Solution{
	
	public static void main(String []argh)
	{
		Scanner sc = new Scanner(System.in);
        // Use map to pair up the parentheses 
		Map pairs = new HashMap<String, String>();
        
        pairs.put(")", "(");
        pairs.put("}", "{");
        pairs.put("]", "[");
        
		while (sc.hasNext()) {
			String input=sc.next();

            // check the size of the input, if the size is odd, this is definitly unbalanced.
            if (input.length() % 2 > 0) {
                System.out.println("false");
            } else {
                //create a stack
                Stack stack = new Stack<String>();
                
                //split the input string
                for (String s: input.split("")) {
                //if we've got a string here, if the input string is valid , and if the input string match the the string.
                    if (stack.size() > 0 && pairs.keySet().contains(s) && (pairs.get(s).equals(stack.peek()))) {
                //the stack would pop out and the stack would be empty
                        stack.pop();
                    } else {
                //if not we push the string in
                        stack.push(s);
                    }
                }
                System.out.println(stack.size() == 0);
            }

		}
		
	}
}

```