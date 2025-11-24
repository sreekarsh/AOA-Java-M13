# **EX 3B – Rat in Maze (Ball in Maze) – Backtracking**

## **DATE: 10-10-2025**

## **AIM:**

To write a Java program to determine whether a ball can reach the destination point in a maze using the **Backtracking (DFS) approach**.

You are given an **m × n maze**, where:

* **0 → empty space**
* **1 → wall**
* The ball rolls **up, down, left, or right**
* The ball **does not stop** until it hits a **wall**

Given:

* **start = [row, col]**
* **destination = [row, col]**

Return **true** if the ball can stop **exactly** at the destination; otherwise, return **false**.

You may assume that the borders of the maze are all walls (see examples).
<img width="573" height="573" alt="image" src="https://github.com/user-attachments/assets/d6f1c054-cdc2-4bb3-9c55-512fb2cf0fb7" />

### **Example:**

Input:
maze = [[0,0,1,0,0],
    [0,0,0,0,0],
    [0,0,0,1,0],
    [1,1,0,1,1],
    [0,0,0,0,0]]
start = [0,4]
destination = [4,4]

Output: **true**

Explanation:
Path → left → down → left → down → right → down → right

---

## **Algorithm**

1. Read the maze dimensions and the maze matrix.
2. Read the start point and the destination point.
3. Maintain a visited matrix to avoid revisiting a stop point.
4. From the current point, roll the ball in all four directions until it hits a wall.
5. When it stops, perform DFS from the new position.
6. If the ball reaches the destination, return true.
7. If all paths fail, return false.

---

## **Program**

```java
/*
Program to implement Rat in Maze (Ball in Maze) using Backtracking
Developed by:  MASINA SREE KARSH
Register Number: 212223100033
*/

import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int m = sc.nextInt();
        int n = sc.nextInt();

        int[][] maze = new int[m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                maze[i][j] = sc.nextInt();
            }
        }

        int[] start = new int[]{sc.nextInt(), sc.nextInt()};
        int[] destination = new int[]{sc.nextInt(), sc.nextInt()};

        Solution sol = new Solution();
        boolean result = sol.hasPath(maze, start, destination);

        System.out.println(result);
    }
}

class Solution {
    public boolean hasPath(int[][] maze, int[] start, int[] destination) {
        int m = maze.length, n = maze[0].length;
        boolean[][] visit = new boolean[m][n];
        return dfs(m, n, maze, start, destination, visit);
    }

    public boolean dfs(int m, int n, int[][] maze, int[] curr, int[] destination, boolean[][] visit) {
        if (visit[curr[0]][curr[1]]) {
            return false;
        }

        if (curr[0] == destination[0] && curr[1] == destination[1]) {
            return true;
        }

        visit[curr[0]][curr[1]] = true;

        int[] dirx = {0, 1, 0, -1};
        int[] diry = {-1, 0, 1, 0};

        for (int i = 0; i < 4; i++) {
            int r = curr[0];
            int c = curr[1];

            while (r + dirx[i] >= 0 && r + dirx[i] < m &&
                   c + diry[i] >= 0 && c + diry[i] < n &&
                   maze[r + dirx[i]][c + diry[i]] == 0) {
                r += dirx[i];
                c += diry[i];
            }

            if (dfs(m, n, maze, new int[]{r, c}, destination, visit)) {
                return true;
            }
        }

        return false;
    }
}
```

---

## **Output:**

<img width="679" height="593" alt="image" src="https://github.com/user-attachments/assets/5ff185ee-b901-4d76-8268-971ba13a2910" />

---

## **Result:**

The program to solve the **Rat in Maze (Ball in Maze)** problem using Backtracking was successfully implemented, and the output was verified.
