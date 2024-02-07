



















# NATURAL

import java.util.Arrays;
import java.util.Comparator;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the number of file names: ");
        int n = scanner.nextInt();
        scanner.nextLine();
        String[] strings = new String[n];
        System.out.println("Enter the file names:");
        for (int i = 0; i < n; i++) {
            strings[i] = scanner.nextLine();
        }
        Arrays.sort(strings, new NaturalSortComparator());
        System.out.println("Sorted file names:");
        for (String s : strings) {
            System.out.println(s);
        }
        
        scanner.close();
    }

    static class NaturalSortComparator implements Comparator<String> {
        public int compare(String s1, String s2) {

            String[] split1 = s1.split("(?<=\\D)(?=\\d)|(?<=\\d)(?=\\D)");
            String[] split2 = s2.split("(?<=\\D)(?=\\d)|(?<=\\d)(?=\\D)");
            int length = Math.min(split1.length, split2.length);
            for (int i = 0; i < length; i++) {
                if (split1[i].matches("\\d+") && split2[i].matches("\\d+")) {
                    int number1 = Integer.parseInt(split1[i]);
                    int number2 = Integer.parseInt(split2[i]);
                    int result = Integer.compare(number1, number2);
                    if (result != 0) {
                        return result;
                    }
                } else {
                    int result = split1[i].compareTo(split2[i]);
                    if (result != 0) {
                        return result;
                    }
                }
            }
            return Integer.compare(split1.length, split2.length);
        }
    }
}

# n-queen :

import java.util.Scanner;

class EthCode {
    static int N;
    static int[] ld;
    static int[] rd;
    static int[] cl;

    static void printSolution(int board[][]) {
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++)
                System.out.printf(" %d ", board[i][j]);
            System.out.printf("\n");
        }
    }

    static boolean solveNQUtil(int board[][], int col) {
        if (col >= N)
            return true;
        for (int i = 0; i < N; i++) {
            if ((ld[i - col + N - 1] != 1 &&
                    rd[i + col] != 1) && cl[i] != 1) {
                board[i][col] = 1;
                ld[i - col + N - 1] = rd[i + col] = cl[i] = 1;
                if (solveNQUtil(board, col + 1))
                    return true;
                board[i][col] = 0; // BACKTRACK
                ld[i - col + N - 1] = rd[i + col] = cl[i] = 0;
            }
        }
        return false;
    }

    static boolean solveNQ() {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter the size of the chessboard (N):");
        N = scanner.nextInt();
        scanner.close();

        ld = new int[2 * N];
        rd = new int[2 * N];
        cl = new int[N];

        int board[][] = new int[N][N];

        if (solveNQUtil(board, 0) == false) {
            System.out.println("Solution does not exist");
            return false;
        }

        printSolution(board);
        return true;
    }

    public static void main(String[] args) {
        solveNQ();
    }
}


# SELECTION SORT :

import java.util.Scanner;

public class EthCode {

    void sort(int arr[]) {

        int n = arr.length;
        for (int i = 0; i < n - 1; i++) {
            int min_idx = i;
            for (int j = i + 1; j < n; j++)
                if (arr[j] < arr[min_idx])
                    min_idx = j;
            int temp = arr[min_idx];
            arr[min_idx] = arr[i];
            arr[i] = temp;
        }
    }

    void printArray(int arr[]) {
        int n = arr.length;
        for (int i = 0; i < n; ++i)
            System.out.print(arr[i] + " ");
        System.out.println();
    }

    public static void main(String args[]) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the number of elements: ");
        int numElements = scanner.nextInt();
        int arr[] = new int[numElements];
        System.out.println("Enter the elements:");
        for (int i = 0; i < numElements; i++) {
            arr[i] = scanner.nextInt();
        }
        scanner.close();

        EthCode ob = new EthCode();

        ob.sort(arr);
        System.out.println("Sorted array:");
        ob.printArray(arr);
    }
}


