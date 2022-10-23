```java

class Solution {
    public int lengthOfLongestSubstring(String s) {
        int temp = 0;
        int result = 0;
        //creat a map
        Map<Character, Integer> seen = new HashMap<Character, Integer>();
        
        for (int i = 0; i < s.length(); i++) {
            Character c = s.charAt(i);
            //check every character inside the string, if it has been seen before:
            if (seen.containsKey(c)) {
                temp = (seen.get(c) + 1) > temp?  (seen.get(c) + 1) : temp;
            }
            //if not we will put (Character, position) inside map
            seen.put(c, i);
            //alwayse check the maximum value
            result = (i + 1 - temp) > result? (i + 1 - temp) : result;
        }
        
        return result;
    }
}

```