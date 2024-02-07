



















# COMBINATIONS:



import java.util.Scanner;

public class EthCode {

    static void combinationUtil(int arr[], int n, int r, int index, int data[], int i) {
        if (index == r) {
            for (int j = 0; j < r; j++)
                System.out.print(data[j] + " ");
            System.out.println();
            return;
        }
        if (i >= n)
            return;
        data[index] = arr[i];
        combinationUtil(arr, n, r, index + 1, data, i + 1);
        combinationUtil(arr, n, r, index, data, i + 1);
    }

    static void printCombination(int arr[], int n, int r) {
        int data[] = new int[r];
        int i = 0;
        while (i < n && arr[i] == arr[i + 1])
            i++;
        combinationUtil(arr, n, r, 0, data, 0);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter the size of array:");
        int n = scanner.nextInt();
        int arr[] = new int[n];
        System.out.println("Enter the elements of the array:");

        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }
        System.out.println("Enter the value of r:");
        int r = scanner.nextInt();
        printCombination(arr, n, r);
    }
}



# HAMILTON

import java.util.Scanner;
import java.util.Arrays;

public class EthCode {
    private int V, pathCount;
    private int[] path;
    private int[][] graph;

    public void findHamiltonianCycle(int[][] g) {
        V = g.length;
        path = new int[V];
        Arrays.fill(path, -1);
        graph = g;
        try {
            path[0] = 0;
            pathCount = 1;
            solve(0);
            System.out.println("No solution");
        } catch (Exception e) {
            System.out.println(e.getMessage());
            display();
        }
    }

    public void solve(int vertex) throws Exception {
        if (graph[vertex][0] == 1 && pathCount == V)
            throw new Exception("Solution found");
        if (pathCount == V)
            return;
        for (int v = 0; v < V; v++) {
            if (graph[vertex][v] == 1) {
                path[pathCount++] = v;
                graph[vertex][v] = 0;
                graph[v][vertex] = 0;
                if (!isPresent(v))
                    solve(v);
                graph[vertex][v] = 1;
                graph[v][vertex] = 1;
                path[--pathCount] = -1;
            }
        }
    }

    public boolean isPresent(int v) {
        for (int i = 0; i < pathCount - 1; i++)
            if (path[i] == v)
                return true;
        return false;
    }

    public void display() {
        System.out.print("\nPath: ");
        for (int i = 0; i < V; i++)
            System.out.print(path[i % V] + " ");
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        EthCode hc = new EthCode();
        int V = scan.nextInt();
        int[][] graph = new int[V][V];
        for (int i = 0; i < V; i++)
            for (int j = 0; j < V; j++)
                graph[i][j] = scan.nextInt();
        hc.findHamiltonianCycle(graph);
    }
}


# JOSEPHUS:

import java.util.Scanner;

class EthCode {
    static int josephus(int n, int k) {
        if (n == 1)
            return 1;
        else
            return (josephus(n - 1, k) + k - 1) % n + 1;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the number of people in the circle: ");
        int n = scanner.nextInt();

        System.out.print("Enter the count of people to be skipped before eliminating the next person: ");
        int k = scanner.nextInt();
        System.out.println("Position of the last remaining person: " + josephus(n, k));
        scanner.close();
    }
}

# LEADERS:

import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        System.out.println("Enter size of the array:");
        int n = s.nextInt();
        int[] arr = new int[n];
        System.out.println("Enter elements of the array:");
        for (int i = 0; i < n; i++) {
            arr[i] = s.nextInt();
        }
        findLeaders(arr, n);
    }

    static void findLeaders(int arr[], int size) {
        int rightMaximum = arr[arr.length - 1];
        System.out.print(rightMaximum + " ");
        for (int i = size - 2; i >= 0; i--) {
            if (arr[i] > rightMaximum) {
                rightMaximum = arr[i];
                System.out.print(rightMaximum + " ");
            }
        }
    }
}

# MAJORITY

import java.util.Scanner;

class EthCode {
    public static int findMajorityElement(int[] A) {
        int m = -1;
        int i = 0;
        for (int j = 0; j < A.length; j++) {
            if (i == 0) {
                m = A[j];
                i = 1;
            } else if (m == A[j]) {
                i++;
            } else {
                i--;
            }
        }
        return m;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter the size of the array:");
        int n = scanner.nextInt();
        int[] arr = new int[n];
        System.out.println("Enter the elements of the array:");
        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }

        System.out.println("Majority element: " + findMajorityElement(arr));
        scanner.close();
    }
}
