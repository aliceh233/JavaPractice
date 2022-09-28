```java

import java.util.*;

public class Solution {
    // that's a graph problem, we need to find if there is a cycle.
    public static boolean canWin(int leap, int[] game, int i) {
        //if the current location is winnable, then return true
        if(i>game.length-1){
            return true;}
        // if the current location is accessible but not reachable, return false
        if(i<0 || game[i]==1){
            return false;
        }
        //if not the case above, make this location 1 (reached)
        game[i]=1;

        //check for if current location + leap or current location + 1 is reachable, or if it is 
        return canWin(leap, game, i+leap)||canWin(leap, game, i+1)||canWin(leap, game, i-1);
        }

    /* example: 5 3             game[] size n = 5, leap = 3 (first query)
                                0 0 0 0 0
     go from index 0, 
     0>5? false, 
     game[0] = 1?, false, 
     make game[0] = 1,
    check canWin(leap,game,3) || canWin(leap, game, 1) || canWin(leap, game, -1)


    canWin(leap, game, -1): 
    -1 > 5? false,
    -1< 0 ? true,
    return false.

    canWin(leap,game,3)
    3 > 5? false,
    3 > 0 || game[3] == 1? false,
    make game[3] = 1,
    check canWin(leap,game,6) || canWin(leap, game, 4) || canWin(leap, game, 2)
    canWin(leap,game,6):
    6 > 5? true
    return true.

    canWin(leap, game, 1):
    1 > 5? false,
    1 > 0 || game[1] == 1? false;
    make game[1] = 1,
    check canWin(leap,game,4) || canWin(leap, game, 2) || canWin(leap, game, 0)
    canWin(leap, game, 0):
    game[0] == 1;
    return false.
    check canWin(leap,game,4):
    4 > 5? false,
    4 < 0 || game[4] == 1? fasle,
    check canWin(leap,game,7) || canWin(leap, game, 5) || canWin(leap, game, 3) 
    return true.

    canWin(leap, game, 2)...

    Finally we know, it's true || true || false,
    return true.


    */
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int q = scan.nextInt();
        while (q-- > 0) {
            int n = scan.nextInt();
            int leap = scan.nextInt();
            
            int[] game = new int[n];
            for (int i = 0; i < n; i++) {
                game[i] = scan.nextInt();
            }

            System.out.println( (canWin(leap, game, 0)) ? "YES" : "NO" );
        }
        scan.close();
    }
}

```