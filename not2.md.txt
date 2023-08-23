#Chainese reminder theorm

#with scanner class

import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in); // Create a Scanner object
        
        System.out.print("Enter the number of modular equations: ");
        int k = scanner.nextInt(); // Read the number of modular equations
        
        int num[] = new int[k];
        int rem[] = new int[k];
        
        System.out.println("Enter the values for num array:");
        for (int i = 0; i < k; i++) {
            num[i] = scanner.nextInt(); // Read values for num array
        }
        
        System.out.println("Enter the values for rem array:");
        for (int i = 0; i < k; i++) {
            rem[i] = scanner.nextInt(); // Read values for rem array
        }
        
        System.out.println("x = " + crt(num, rem, k));
        
        scanner.close(); // Close the Scanner object
    }

    static int crt(int num[], int rem[], int k) {
        int x = 1;
        int i;
        while (true) {
            for (i = 0; i < k; i++) {
                if (x % num[i] != rem[i]) {
                    break;
                }
            }
            if (i == k) {
                return x;
            }
            x++;
        }
    }
}


#without scanner class


public class Main{
    public static void main(String[] args){
        int num[] = {17,7,11};
        int rem[] = {7,4,5};
        int k = num.length;
        System.out.println("x = " + crt(num,rem,k));
    }
    static int crt(int num[],int rem[],int k){
        int x = 1;
        int i;
        while(true){
            for(i=0;i<k;i++){
                if(x%num[i]!=rem[i]){
                    break;
                }
            }
            if(i==k){
                return x;
            }
            x++;
        }
    }
}

#ALICE APPLE TREE :

import java.util.*;
public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int apple = sc.nextInt();
        int count=0,sum=0;
        while(sum<apple){
            count++;
            sum += 12*count*count;
        }
        System.out.println(8*count);
    }
}

#TOGGLE THE SWITCH :

import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] counts = toggle(n);
        System.out.println("Closed : " + counts[0]);
        System.out.println("Opened : " + counts[1]);
    }
    static int[] toggle(int n) {
        boolean a[] = new boolean[n + 1];
        for(int i=1;i<=n;i++){
            a[i] = true;
        }
        for (int j = 1; j <= n; j++) {
            for (int k = j;k<= n; k+=j) {
                a[k] = !a[k];
            }
        }
        int c = 0, o = 0;
        for (int p = 1; p <= n; p++) {
            if (a[p] == true) {
                c++;
            } 
            else {
                o++;
            }
        }
        int counts[] = { c, o };
        return counts;
    }
}


#STROBOGRAMMATIC NUMBER :

import java.util.*;
public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        String str = sc.nextLine();
        if(strobo(str)){
            System.out.println("YES");
        }
        else{
            System.out.println("NO");
        }
    }
    static boolean strobo(String str){
        Map<Character,Character> map = new HashMap<>();
        map.put('0','0');
        map.put('1','1');
        map.put('8','8');
        map.put('6','9');
        map.put('9','6');
        int left = 0;
        int right = str.length()-1;
        while(left<=right){
            char l = str.charAt(left);
            char r = str.charAt(right);
            if((!map.containsKey(l)) || (map.get(l) != r)){
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
}


#EULERS PHI ALGORITHM :

import java.util.*;
public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        System.out.println("phi("+n+") = "+phi(n));
    }
    static int phi(int n){
        int c=1;
        for(int i=2;i<n;i++){
            if(gcd(i,n)==1){
                c++;
            }
        }
        return c;
    }
    static int gcd(int a,int b){
        if(a==0){
          return b;
        }
        else{
            return gcd(b%a,a);
        }
    }
}


#SIMPLE SIEVE :

import java.util.*;
public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        sieve(n);
    }
    public static void sieve(int n){
        boolean a[] = new boolean[n+1];
        for(int i=0;i<=n;i++){
            a[i]  = true;
        }
        for(int j=2;j*j<=n;j++){
            if(a[j]==true){
                for(int k=j*j;k<=n;k+=j){
                    a[k] = false;
                }
            }
        }
        int c=0;
        for(int m=2;m<=n;m++){
            if(a[m]==true){
                System.out.print(m+" ");
            }
        }
        
    }
}
