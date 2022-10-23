```java
class Solution {
    public boolean backspaceCompare(String s, String t) {
        Stack<Character> A = new Stack<Character>();
        Stack<Character> B = new Stack<Character>();
        
        int i = 0, j = 0;
        
        while (i < s.length()) {
            if (s.charAt(i) == '#' && !A.empty())
                A.pop();
            else if (s.charAt(i) != '#') A.push(s.charAt(i));
            i++;
        }
        
        while (j < t.length()) {
            if (t.charAt(j) == '#' && !B.empty())
                B.pop();
            else if (t.charAt(j) != '#') B.push(t.charAt(j));
            j++;
        }
        
        return (A.equals(B));
    }
    
}
```