



















# MANEUVERING(number od paths)

import java.util.Scanner;

public class EthCode {
    static int numberOfPaths(int m, int n) {
        int[] dp = new int[n];
        dp[0] = 1;
        for (int i = 0; i < m; i++) {
            for (int j = 1; j < n; j++) {
                dp[j] += dp[j - 1];
            }
        }
        return dp[n - 1];
    }

    public static void main(String args[]) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the number of rows: ");
        int rows = scanner.nextInt();
        System.out.print("Enter the number of columns: ");
        int cols = scanner.nextInt();
        System.out.println("Number of paths: " + numberOfPaths(rows, cols));
        scanner.close();
    }
}

#EQUILIBRIUM:

import java.util.Scanner;

class Main {
    static int findMaxSum(int[] arr, int n) {
        int totalSum = 0;
        for (int num : arr) {
            totalSum += num;
        }

        int leftSum = 0;
        for (int i = 0; i < n; i++) {
            if (leftSum == totalSum - leftSum - arr[i]) {
                return leftSum;
            }
            leftSum += arr[i];
        }

        return -1; // If no such split is possible
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter the number of elements in the array:");
        int n = scanner.nextInt();
        int[] arr = new int[n];
        System.out.println("Enter the elements of the array:");
        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }
        System.out.println(findMaxSum(arr, n));

        scanner.close();
    }
}

# maze
import java.util.Scanner;

public class RatMaze {
    static int N;

    void printSolution(int sol[][]) {
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++)
                System.out.print(" " + sol[i][j] + " ");
            System.out.println();
        }
    }

    boolean isSafe(int maze[][], int x, int y) {
        return (x >= 0 && x < N && y >= 0 && y < N && maze[x][y] == 1);
    }

    boolean solveMazeUtil(int maze[][], int x, int y, int sol[][]) {
        if (x == N - 1 && y == N - 1 && maze[x][y] == 1) {
            sol[x][y] = 1;
            return true;
        }

        if (isSafe(maze, x, y)) {
            sol[x][y] = 1;
            if (solveMazeUtil(maze, x + 1, y, sol))
                return true;
            if (solveMazeUtil(maze, x, y + 1, sol))
                return true;

            sol[x][y] = 0; // Backtrack
            return false;
        }

        return false;
    }

    boolean solveMaze(int maze[][]) {
        int sol[][] = new int[N][N];
        if (!solveMazeUtil(maze, 0, 0, sol)) {
            System.out.println("Solution doesn't exist");
            return false;
        }
        System.out.println("Solution:");
        printSolution(sol);
        return true;
    }

    public static void main(String args[]) {
        Scanner scanner = new Scanner(System.in);
        RatMaze m = new RatMaze();
        System.out.print("Enter the size of the maze: ");
        N = scanner.nextInt();
        int[][] maze = new int[N][N];
        System.out.println("Enter the maze (0 for blocked, 1 for path):");
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                maze[i][j] = scanner.nextInt();
            }
        }
        m.solveMaze(maze);

        scanner.close();
    }
}
