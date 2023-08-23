# leftrotate

import java.util.Scanner;

public class RotateLeft {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the number of elements in the array: ");
        int length = scanner.nextInt();
        
        int[] arr = new int[length];
        System.out.println("Enter the elements of the array:");
        for (int i = 0; i < length; i++) {
            arr[i] = scanner.nextInt();
        }

        System.out.print("Enter the number of rotations: ");
        int n = scanner.nextInt();
        scanner.close();

        System.out.println("Original array:");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }

        // Rotate the given array by n times toward the left
        for (int i = 0; i < n; i++) {
            int j, first;
            // Stores the first element of the array
            first = arr[0];
            for (j = 0; j < arr.length - 1; j++) {
                // Shift element of array by one
                arr[j] = arr[j + 1];
            }
            // First element of array will be added to the end
            arr[j] = first;
        }
        
        System.out.println();
        System.out.println("Array after left rotation:");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}

#maxsubarrayproduct

import java.util.Scanner;

public class MaxProductSubArray {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the number of elements in the array: ");
        int length = scanner.nextInt();
        
        int[] a = new int[length];
        System.out.println("Enter the elements of the array:");
        for (int i = 0; i < length; i++) {
            a[i] = scanner.nextInt();
        }
        
        scanner.close();

        method(a);
    }

    static void method(int a[]) {
        int res = a[0];
        int s = 0, e = 0;
        int n = a.length;
        for (int i = 0; i < n; i++) {
            int mul = a[i];
            for (int j = i + 1; j < n; j++) {
                if (mul > res) {
                    s = i;
                    e = j;
                    res = mul;
                }
                mul *= a[j];
            }
            if (mul > res) {
                s = i;
                e = n;
                res = mul;
            }
        }
        System.out.println("Maximum product subarray:");
        for (int i = s; i < e; i++) {
            System.out.print(a[i] + " ");
        }
    }
}

# factors for a number 

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int num = scanner.nextInt();
        scanner.close();

        System.out.println("Factors of " + num + " are:");

        // finding and printing factors between 1 to num
        for (int i = 1; i <= num; i++) {
            if (num % i == 0) {
                System.out.println(i + " ");
            }
        }
    }
}

