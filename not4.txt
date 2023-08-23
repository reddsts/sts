//Segmented Sieve Algorithm

import java.util.*;

public class test {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.println("Enter the lower Bound");
        int l = sc.nextInt();
        
        System.out.println("Enter the Upper Bound");
        int n = sc.nextInt();
        
        boolean[] array = new boolean[n + 1];
        
        for (int i = 2; i <= n; i++) {
            array[i] = true;
        }
        
        for (int i = 2; i * i <= n; i++) {
            if (array[i]) {
                for (int j = i * i; j <= n; j += i) {
                    array[j] = false;
                }
            }
        }
        
        System.out.println("Prime numbers from " + l + " to " + n + ":");
        
        for (int i = l; i <= n; i++) {
            if (array[i]) {
                System.out.print(i + " ");
            }
        }
    }
}

//Binary Palindrome

import java.util.*;

public class tcs {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter the number");
        int n = sc.nextInt();
        String s1 = "";
        String s2 = "";

        while (n > 0) {
            s1 = n % 2 + s1;
            s2 = s2 + n % 2;
            n = n / 2;
        }

        if (s1.equals(s2)) {
            System.out.println("Binary Palindrome");
        } else {
            System.out.println("Not Binary Palindrome");
        }
    }
}


//Booth’s Algorithm

import java.util.*;

public class tcs {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter the Multiplier");
        int a = sc.nextInt();
        System.out.println("Enter the Multiplicand");
        int b = sc.nextInt();
        int p = 0;
        int c = 0;
        
        if (a < 0) {
            a = -1 * (a);
            c++;
        }
        
        if (b < 0) {
            b = -1 * (b);
            c++;
        }
        
        while (a > 0) {
            if (a % 2 == 1) {
                p = p + b;
            }
            a = a >> 1;
            b = b << 1;
        }
        
        if (c == 1) {
            System.out.println("Result " + (-1 * p));
        } else {
            System.out.print("Result " + p);
        }
    }
}


//Euclidean Algorithm

import java.util.*;

public class test {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter the Number 1");
        int number1 = sc.nextInt();
        System.out.println("Enter the Number 2");
        int number2 = sc.nextInt();
        System.out.println(gcd(number1, number2));
    }
    
    static int gcd(int a, int b) {
        if (a == 0) {
            return b;
        }
        return gcd(b % a, a);
    }
}


//Karatsuba Algorithm

import java.util.*;

public class tcs {
    public static void main(String s[]) {
        Scanner sw = new Scanner(System.in);
        long x = sw.nextLong();
        long y = sw.nextLong();
        System.out.println(k(x, y));
    }

    static long k(long x, long y) {
        if (x < 10 && y < 10) {
            return x * y;
        }

        long n = Math.max(String.valueOf(x).length(), String.valueOf(y).length());
        long n1 = n / 2;
        long a = x / (long) Math.pow(10, n1);
        long b = x % (long) Math.pow(10, n1);
        long c = y / (long) Math.pow(10, n1);
        long d = y % (long) Math.pow(10, n1);

        long s1 = k(a, c);
        long s2 = k(b, d);
        long s3 = k(a + b, c + d);
        long s4 = s3 - s2 - s1;
        long res = s1 * (long) Math.pow(10, 2 * n1) + s4 * (long) Math.pow(10, n1) + s2;
        
        return res;
    }
}
