



















//SORTED UNIQUE PERMUTATION:
import java.util.*;

public class EthCOde {

    static int factorial(int n) {
        int f = 1;
        for (int i = 1; i <= n; i++)
            f = f * i;
        return f;
    }

    static void print(char[] temp) {
        for (int i = 0; i < temp.length; i++)
            System.out.print(temp[i]);
        System.out.println();
    }

    static int calculateTotal(char[] temp, int n) {
        int f = factorial(n);
        HashMap<Character, Integer> hm = new HashMap<Character, Integer>();
        for (int i = 0; i < temp.length; i++) {
            if (hm.containsKey(temp[i]))
                hm.put(temp[i], hm.get(temp[i]) + 1);
            else
                hm.put(temp[i], 1);
        }
        for (Map.Entry<Character, Integer> e : hm.entrySet()) {
            Integer x = e.getValue();
            if (x > 1) {
                int temp5 = factorial(x);
                f = f / temp5;
            }
        }
        return f;
    }

    static void nextPermutation(char[] temp) {
        int i;
        for (i = temp.length - 1; i > 0; i--)
            if (temp[i] > temp[i - 1])
                break;
        int min = i;
        int j, x = temp[i - 1];
        for (j = i + 1; j < temp.length; j++)
            if ((temp[j] < temp[min]) && (temp[j] > x))
                min = j;
        char temp_to_swap;
        temp_to_swap = temp[i - 1];
        temp[i - 1] = temp[min];
        temp[min] = temp_to_swap;
        Arrays.sort(temp, i, temp.length);
        print(temp);
    }

    static void printAllPermutations(String s) {
        char temp[] = s.toCharArray();
        Arrays.sort(temp);
        print(temp);
        int total = calculateTotal(temp, temp.length);
        for (int i = 1; i < total; i++)
            nextPermutation(temp);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a string: ");
        String s = scanner.nextLine();
        scanner.close();
        printAllPermutations(s);
    }
}

//WARNSDROFF:
import java.util.*;

class EthCode {

    public static final int N = 5;
    public static final int[] row = {2, 1, -1, -2, -2, -1, 1, 2, 2};
    public static final int[] col = {1, 2, 2, 1, -1, -2, -2, -1, 1};

    private static boolean isValid(int x, int y) {
        return x >= 0 && y >= 0 && x < N && y < N;
    }

    private static void print(int[][] visited) {
        for (var r : visited) {
            System.out.println(Arrays.toString(r));
        }
        System.out.println();
    }

    public static void knightTour(int[][] visited, int x, int y, int pos) {
        visited[x][y] = pos;
        if (pos >= N * N) {
            print(visited);
            visited[x][y] = 0;
            return;
        }
        for (int k = 0; k < 8; k++) {
            int newX = x + row[k];
            int newY = y + col[k];
            if (isValid(newX, newY) && visited[newX][newY] == 0) {
                knightTour(visited, newX, newY, pos + 1);
            }
        }
        visited[x][y] = 0;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter the starting row (0-4):");
        int startX = scanner.nextInt();
        System.out.println("Enter the starting column (0-4):");
        int startY = scanner.nextInt();
        int[][] visited = new int[N][N];
        int pos = 1;
        knightTour(visited, startX, startY, pos);
        scanner.close();
    }
}

//Quicksort :

import java.util.Scanner;

class GFG {
 
    // A utility function to swap two elements
    static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
 
    // This function takes last element as pivot,
    // places the pivot element at its correct position
    // in sorted array, and places all smaller to left
    // of pivot and all greater elements to right of pivot
    static int partition(int[] arr, int low, int high) {
        // Choosing the pivot
        int pivot = arr[high];
 
        // Index of smaller element and indicates
        // the right position of pivot found so far
        int i = (low - 1);
 
        for (int j = low; j <= high - 1; j++) {
            // If current element is smaller than the pivot
            if (arr[j] < pivot) {
                // Increment index of smaller element
                i++;
                swap(arr, i, j);
            }
        }
        swap(arr, i + 1, high);
        return (i + 1);
    }
 
    // The main function that implements QuickSort
    // arr[] --> Array to be sorted,
    // low --> Starting index,
    // high --> Ending index
    static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            // pi is partitioning index, arr[p]
            // is now at right place
            int pi = partition(arr, low, high);
 
            // Separately sort elements before
            // partition and after partition
            quickSort(arr, low, pi - 1);
            quickSort(arr, pi + 1, high);
        }
    }
    
    // To print sorted array
    public static void printArr(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
    }
 
    // Driver Code
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter the number of elements in the array: ");
        int N = scanner.nextInt();
        int[] arr = new int[N];
        
        System.out.println("Enter the elements of the array:");
        for (int i = 0; i < N; i++) {
            arr[i] = scanner.nextInt();
        }
        
        // Function call
        quickSort(arr, 0, N - 1);
        System.out.println("Sorted array:");
        printArr(arr);
        
        scanner.close();
    }
}




