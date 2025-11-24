# **EX 3A – N Queens Problem (Backtracking Approach)**

## **DATE: 01-10-2025**

## **AIM:**

To write a Java program to solve the **N Queens Problem** using the **Backtracking approach**.

You are given an integer **N**. For an **N × N chessboard**, place **N queens** such that **no two queens attack each other**.

A queen can attack another queen if it lies in the **same row**, **same column**, or **same diagonal**.

<img width="241" height="209" alt="image" src="https://github.com/user-attachments/assets/96aacb61-4f34-423f-b324-5e34454e42b8" />

### **Conditions:**

* Input **N** must be between **1 to 4**
* If a solution exists → print a **binary matrix** with **1** where queens are placed
* If no solution exists → print **"Solution does not exist"**

---

## **Algorithm**

1. Read the value of **N** from the user.
2. Create an **N × N board**, initially filled with zeros.
3. Use a recursive function to try placing a queen column by column.
4. For every cell, check if placing a queen is **safe** using row and diagonal checks.
5. If placing the queen leads to a solution, return true; otherwise, backtrack by removing the queen and continue.
6. If all queens are placed, print the board; if not, print that no solution exists.

---

## **Program**

```JAVA
/*
Program to implement N Queens using Backtracking
Developed by: MASINA SREE KARSH
Register Number: 212223100033
*/

import java.util.Scanner;

public class NQueens {
    static int N;

    static void printSolution(int[][] board) {
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                System.out.print(board[i][j] + " ");
            }
            System.out.println();
        }
    }

    static boolean isSafe(int[][] board, int row, int col) {
        for (int i = 0; i < col; i++)
            if (board[row][i] == 1)
                return false;

        for (int i = row, j = col; i >= 0 && j >= 0; i--, j--)
            if (board[i][j] == 1)
                return false;

        for (int i = row, j = col; i < N && j >= 0; i++, j--)
            if (board[i][j] == 1)
                return false;

        return true;
    }

    static boolean solveNQUtil(int[][] board, int col) {
        if (col >= N)
            return true;

        for (int i = 0; i < N; i++) {
            if (isSafe(board, i, col)) {
                board[i][col] = 1;

                if (solveNQUtil(board, col + 1))
                    return true;

                board[i][col] = 0;
            }
        }

        return false;
    }

    static boolean solveNQ() {
        int[][] board = new int[N][N];

        if (!solveNQUtil(board, 0)) {
            System.out.println("Solution does not exist");
            return false;
        }

        printSolution(board);
        return true;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        N = scanner.nextInt();
        solveNQ();
    }
}
```

---

## **Output:**

<img width="1074" height="323" alt="image" src="https://github.com/user-attachments/assets/e625e1a4-7acc-436d-b79d-7ae6689cb940" />

---

## **Result:**

The program for solving the **N Queens Problem using Backtracking** was successfully implemented, and the output was verified.
