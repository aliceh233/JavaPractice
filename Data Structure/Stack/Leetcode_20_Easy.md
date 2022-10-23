```java
class Solution {
    public boolean isValid(String s) {
        if (s == null || s.length() == 0 || s.length() % 2 != 0) return false;
        Map pairs = new HashMap<String, String>();
        Stack<String> stack = new Stack<String>();
        
        pairs.put(")", "(");
        pairs.put("}", "{");
        pairs.put("]", "[");
        
        for (String c: s.split("")) {
            if (stack.size() > 0 && pairs.containsKey(c) && pairs.get(c).equals(stack.peek())) {
                stack.pop();
            } else {
                stack.push(c);
            }
        }
        
        return stack.size() == 0;
    }
}

```