# perm_check

A non-empty array A consisting of N integers is given.

A permutation is a sequence containing each element from 1 to N once, and only once.

For example, array A such that:

    A[0] = 4
    A[1] = 1
    A[2] = 3
    A[3] = 2
is a permutation, but array A such that:

    A[0] = 4
    A[1] = 1
    A[2] = 3
is not a permutation, because value 2 is missing.

The goal is to check whether array A is a permutation.

Write a function:

```fun solution(A: IntArray): Int```

that, given an array A, returns 1 if array A is a permutation and 0 if it is not.

For example, given array A such that:

    A[0] = 4
    A[1] = 1
    A[2] = 3
    A[3] = 2
the function should return 1.

Given array A such that:

    A[0] = 4
    A[1] = 1
    A[2] = 3
the function should return 0.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [1..100,000];
each element of array A is an integer within the range [1..1,000,000,000].

Solution 1 (Kotlin):
```
fun main() {
    //val A: IntArray = intArrayOf(4,1,3,2)
    val A: IntArray = intArrayOf(4,1,3)
    A.sort()
    var r = 1
    var i = 0
    while(i < A.size-1) {
        if((A[i]+1) != A[i+1]) {
           r = 0
           break 
        }
        i++
    }
    println(r)
}
```

Solution 2 (Kotlin) 66%

```
fun solution(A: IntArray): Int {
    // write your code in Kotlin
    A.sort()
    var r = 1
    var i = 0
    while(i < A.size-1) {
        if((A[i]+1) != A[i+1]) {
           r = 0
           break 
        }
        i++
    }
    return r
}
```

Solution 3 (Java) (100%)

```
import java.util.Map;
import java.util.HashMap;

class Solution {
    public int solution(int[] A) {
        // write your code in Java SE 8
        int arrLen = A.length;
        Map<Integer,Integer> m = new HashMap<>();
        
        for(int ctr=arrLen; ctr > 0; ctr--)
            m.put(ctr,1);
        
        for(int a : A)
            if(m.containsKey(a))
                m.remove(a);
        return (m.size() == 0) ? 1 : 0;
    }
}
```

