```java

class Solution {
    public int[] twoSum(int[] numbers, int target) {
        //Base case: if no numbers, return null.
        if (numbers == null) return null;
        //initialize the counters.
        int start = 0, tail = numbers.length - 1;

        //Since the integer array is ordered, we make two pointer, one is from the start and the other is from the end.
        while (start < tail) {
            int sum = numbers[start] + numbers[tail];
            //if founded, return the indexs.
            if (sum == target) {
                return new int[]{start + 1, tail + 1};          
            } else if (sum < target) {
                //if the sum is still way smaller than the target, make the sum bigger.
                start++;
            } else {
                //else we move tail so that get smaller sum.
                tail--;
            }
        }
        return null;
    }
}

```