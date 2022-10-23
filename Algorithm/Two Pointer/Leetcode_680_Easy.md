```java
class Solution {
    public boolean validPalindrome(String s) {
        if (s == null || s.length() == 0) return false;
        for (int i = 0, j = s.length() - 1; i < j; i++, j--) {
            if (s.charAt(i) != s.charAt(j)) {
                return isPlalindrome(s, i, j-1) || isPlalindrome(s, i + 1, j);
            }
        }
        return true;
    }
    
    private boolean isPlalindrome(String s, int i, int j) {
        while (i < j) {
            if (s.charAt(i++) != s.charAt(j--)) {
                return false;
            }
        }
        return true;
    }
}
```