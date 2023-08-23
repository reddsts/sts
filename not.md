



















# LONGEST SEQUENCE OF ONES AFTER A FLIP

import java.util.Scanner;

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter an integer value: ");
        int n = scanner.nextInt();
        scanner.close();

        fmax(n);
    }

    static void fmax(int n) {
        int c = 0, p = 0, m = 0;
        String s = Integer.toBinaryString(n);
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '1') {
                c++;
            } else {
                m = Math.max(m, c + p + 1);
                p = c;
                c = 0;
            }
        }
        m = Math.max(m, c + p + 1);
        System.out.println("Maximum consecutive ones: " + m);
    }
}


# SWAP TWO NIBBLES IN A BYTE

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a byte value (in hexadecimal): ");
        byte inputByte = (byte) scanner.nextInt();
        scanner.close();

        byte b = (byte) (inputByte & 0xFF);
        byte sb = swap(b);

        System.out.println("Original byte: " + Integer.toBinaryString(b));
        System.out.println("Swapped byte: " + Integer.toBinaryString(sb));
    }

    static byte swap(byte b) {
        byte nb;
        nb = (byte) ((b & 0x0F) << 4 | (b & 0xF0) >> 4);
        return nb;
    }
}


# MAX SUM OF HOUR GLASS

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the number of rows: ");
        int r = scanner.nextInt();

        System.out.print("Enter the number of columns: ");
        int c = scanner.nextInt();

        int a[][] = new int[r][c];

        System.out.println("Enter the matrix elements:");
        for (int i = 0; i < r; i++) {
            for (int j = 0; j < c; j++) {
                a[i][j] = scanner.nextInt();
            }
        }

        scanner.close();

        hglass(a, r, c);
    }

    static void hglass(int a[][], int r, int c) {
        int max = Integer.MIN_VALUE;
        int sum = 0;
        
        for (int i = 0; i < r - 2; i++) {
            for (int j = 0; j < c - 2; j++) {
                sum = a[i][j] + a[i][j + 1] + a[i][j + 2] + a[i + 1][j + 1] + a[i + 2][j] + a[i + 2][j + 1] + a[i + 2][j + 2];
                max = Math.max(sum, max);
            }
        }
        
        System.out.println("Maximum hourglass sum: " + max);
    }
}

# MOVING SPECIAL CHARACTERS TO THE BEGINNING

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String inputString = scanner.nextLine();

        scanner.close();

        method(inputString);
    }

    static void method(String s) {
        int n = s.length();
        String sp = "";
        String al = "";
        
        for (int i = 0; i < n; i++) {
            if ((s.charAt(i) >= 65 && s.charAt(i) <= 90) || 
                (s.charAt(i) >= 97 && s.charAt(i) <= 120) || 
                (s.charAt(i) >= 48 && s.charAt(i) <= 57)) {
                al += s.charAt(i);
            } else {
                sp += s.charAt(i);
            }
        }
        
        System.out.println(sp + al);
    }
}


# anagram

import java.util.Arrays;
import java.util.Scanner;

class Main {
  public static void main(String[] args) {
    Scanner scanner = new Scanner(System.in);

    System.out.print("Enter the first string: ");
    String str1 = scanner.nextLine();

    System.out.print("Enter the second string: ");
    String str2 = scanner.nextLine();

    scanner.close();

    str1 = str1.toLowerCase();
    str2 = str2.toLowerCase();

    // check if length is the same
    if (str1.length() == str2.length()) {

      // convert strings to char arrays
      char[] charArray1 = str1.toCharArray();
      char[] charArray2 = str2.toCharArray();

      // sort the char arrays
      Arrays.sort(charArray1);
      Arrays.sort(charArray2);

      // if sorted char arrays are the same
      // then the strings are anagrams
      boolean result = Arrays.equals(charArray1, charArray2);

      if (result) {
        System.out.println(str1 + " and " + str2 + " are anagrams.");
      } else {
        System.out.println(str1 + " and " + str2 + " are not anagrams.");
      }
    } else {
      System.out.println(str1 + " and " + str2 + " are not anagrams.");
    }
  }
}

# rotateright

import java.util.Scanner;

public class RotateRight {    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Initialize array     
        int[] arr = new int[] {1, 2, 3, 4, 5};     

        // Prompt the user to enter the rotation count    
        System.out.print("Enter the number of rotations: ");    
        int n = scanner.nextInt();

        scanner.close();
           
        // Displays the original array    
        System.out.println("Original array: ");    
        for (int i = 0; i < arr.length; i++) {     
            System.out.print(arr[i] + " ");     
        }      
            
        // Rotate the given array by n times toward the right    
        for(int i = 0; i < n; i++){    
            int j, last;    
            // Stores the last element of the array    
            last = arr[arr.length-1];    
            
            for(j = arr.length-1; j > 0; j--){    
                // Shift element of array by one    
                arr[j] = arr[j-1];    
            }    
            // Last element of array will be added to the start of the array    
            arr[0] = last;    
        }    
        
        System.out.println();    
            
        // Displays the resulting array after rotation    
        System.out.println("Array after right rotation: ");    
        for(int i = 0; i < arr.length; i++){    
            System.out.print(arr[i] + " ");    
        }    
    }    
}


