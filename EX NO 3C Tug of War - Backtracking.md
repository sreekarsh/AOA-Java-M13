# **EX 3C – Tug of War Problem (Partition Equal Subset Sum)**

## **DATE: 17-10-2025**

## **AIM:**

To write a Java program to determine whether a given integer array can be partitioned into **two subsets with equal sum**, using a **Backtracking / Dynamic Programming approach**.

### **Problem:**

Given an array `nums`, return **true** if the array can be split into two subsets such that both subsets have **equal sum**.

### **Example:**

Input:
4
1 5 11 5

Output:
true

Explanation:
The array can be divided as:
Subset 1 → [1, 5, 5]
Subset 2 → [11]

### **Constraints:**

* 1 ≤ nums.length ≤ 200
* 1 ≤ nums[i] ≤ 100

---

## **Algorithm**

1. Read the number of elements and the array values.
2. Find the total sum of all elements in the array.
3. If the sum is odd → equal partition is not possible → return false.
4. Compute the target sum = totalSum / 2.
5. Use a DP array to determine whether a subset exists with the target sum.
6. If dp[targetSum] = true → equal partition is possible.
7. Print the result.

---

## **Program**

```java
/*
Program to implement Tug of War Problem (Partition Equal Subset Sum)
Developed by:  MASINA SREE KARSH
Register Number: 212223100033
*/

import java.util.Scanner;
public class Solution {

    public boolean canPartition(int[] nums) {
        if(nums.length == 0){
            return false; 
        }

        int totalSum = 0;
        for(int num : nums){
            totalSum += num;
        }

        if(totalSum % 2 != 0){
            return false;
        }

        int subSetSum = totalSum / 2;
        boolean[] dp = new boolean[subSetSum + 1];
        dp[0] = true;

        for(int curr : nums){
            for(int j = subSetSum; j >= curr; j--){
                dp[j] |= dp[j - curr];
            }
        }

        return dp[subSetSum];
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        Solution sol = new Solution();
        int n = scanner.nextInt();

        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }

        boolean canBePartitioned = sol.canPartition(nums);
        System.out.println(canBePartitioned);
    }
}
```

---

## **Output:**

<img width="903" height="288" alt="image" src="https://github.com/user-attachments/assets/ee8b04d5-ca92-4293-800f-0cf4680f74c2" />

---

## **Result:**

The program for the **Tug of War problem using Backtracking / DP** was successfully implemented, and the expected output was verified.
