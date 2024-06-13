Functions can be recursive, which means that they can call itself: each such invocation creates independent frame on the stack. Of course, we have to ensure that such recursive invocations will not be executed forever — somewhere in the body of the function, usually at the beginning, some condition must be checked telling if the function should return without calling itself. A classic example is the factorial function:
factorials 0! and 1! are returned without recursive invocation, for other values recursion n! = n · (n − 1)! is used:

# Listing 24 BHL-RecFun/RecFun.java Page 49


```java
public class RecFun {

    static int fact(int n) {
        if (n < 0) throw new IllegalArgumentException();
        if (n <= 1) return 1;
        return n * fact(n - 1);
    }

    public static void main(String[] args) {
        for (int num = 0; num <= 12; ++num)
            System.out.println("Factorial of " + num +
                    " is " + fact(num));
    }
}
```

Output:
```
Factorial of 0 is 1
Factorial of 1 is 1
Factorial of 2 is 2
Factorial of 3 is 6
Factorial of 4 is 24
Factorial of 5 is 120
Factorial of 6 is 720
Factorial of 7 is 5040
Factorial of 8 is 40320
Factorial of 9 is 362880
Factorial of 10 is 3628800
Factorial of 11 is 39916800
Factorial of 12 is 479001600
(note that 13! is already too big to fit in an int!)
```
