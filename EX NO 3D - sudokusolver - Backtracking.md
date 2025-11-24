# **EX 3D – Sudoku Solver Using Backtracking**

## **DATE: 19-10-2025**

## **AIM:**

To write a Java program to solve a **9×9 Sudoku puzzle** using the **Backtracking algorithm**, by filling all empty cells (represented by `0`) such that the final board satisfies all Sudoku rules.

For example:
<img width="357" height="322" alt="image" src="https://github.com/user-attachments/assets/334b8c39-d547-4743-aca0-de92e38bdd1c" />

---

## **Algorithm**

1. Read the 9×9 Sudoku grid with `0` representing empty cells.
2. Start from the first cell and move left to right, top to bottom.
3. If the current cell is already filled, move to the next cell.
4. If the cell is empty, try placing numbers `1` to `9` one by one.
5. For each number, check if it is **safe** to place using:

   * Row validation
   * Column validation
   * 3×3 subgrid validation
6. If a number is valid, place it and recursively solve the rest of the board.
7. If recursion fails, remove the number (backtrack) and try the next number.
8. If all cells are successfully filled, the Sudoku is solved.
9. If no number fits in a cell, return failure — Sudoku has no solution.

---

## **Program**

```JAVA
/*
Program to implement Sudoku Solver using Backtracking
Developed by: MASINA SREE KARSH
Register Number: 212223100033
*/

import java.util.Scanner;

public class SudokuSolver {

    static boolean isSafe(int[][] board, int row, int col, int num) {
        for (int i = 0; i < 9; i++) {
            if (board[row][i] == num || board[i][col] == num)
                return false;
        }

        int startRow = row - row % 3;
        int startCol = col - col % 3;

        for (int i = 0; i < 3; i++)
            for (int j = 0; j < 3; j++)
                if (board[startRow + i][startCol + j] == num)
                    return false;

        return true;
    }

    static boolean solveSudoku(int[][] board, int row, int col) {

        if (row == 8 && col == 9) {
            return true;
        }

        if (col == 9) {
            row++;
            col = 0;
        }

        if (board[row][col] != 0) {
            return solveSudoku(board, row, col + 1);
        }

        for (int num = 1; num <= 9; num++) {
            if (isSafe(board, row, col, num)) {
                board[row][col] = num;

                if (solveSudoku(board, row, col + 1)) {
                    return true;
                }

                board[row][col] = 0;
            }
        }
        return false;
    }

    static void printBoard(int[][] board) {
        for (int[] row : board) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[][] board = new int[9][9];

        for (int i = 0; i < 9; i++) {
            for (int j = 0; j < 9; j++) {
                board[i][j] = sc.nextInt();
            }
        }

        if (solveSudoku(board, 0, 0)) {
            System.out.println("Solved Sudoku:");
            printBoard(board);
        } else {
            System.out.println("No solution exists.");
        }

        sc.close();
    }
}
```

---

## **Output:**

<img width="1080" height="645" alt="image" src="https://github.com/user-attachments/assets/749c7c86-5d6d-4ea3-b30a-9db35ddbeaad" />


---

## **Result:**

The Sudoku Solver program using Backtracking was successfully implemented, and the expected output was verified.

