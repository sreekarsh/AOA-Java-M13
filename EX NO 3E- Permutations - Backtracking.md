# **EX 3E – Generate Permutations using Backtracking Approach**

## **DATE: 22-10-2025**

## **AIM:**

To write a Java program to generate all possible **permutations** of a given array of **distinct integers** using the **Backtracking** technique.

### **Example:**

Input:
nums = [1, 2, 3]

Output:
[[1,2,3], [1,3,2], [2,1,3], [2,3,1], [3,1,2], [3,2,1]]

---

## **Algorithm**

1. Read the input array containing distinct integers.
2. Create a list to store all permutations.
3. Use a **backtracking** function that builds permutations by choosing one unused number at a time.
4. If the current list size equals the array size, add a copy of the list to the answer.
5. Otherwise, continue selecting unused numbers, adding them, recursing, and removing them (backtracking).
6. Print all generated permutations.

---

## **Program**

```java
/*
Program to implement Permutation Generation using Backtracking
Developed by: MASINA SREE KARSH
Register Number: 212223100033
*/

import java.util.*;

public class Solution {

    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        backtrack(new ArrayList<>(), ans, nums);
        return ans;
    }

    public void backtrack(List<Integer> curr, List<List<Integer>> ans, int[] nums) {
        if (curr.size() == nums.length) {
            ans.add(new ArrayList<>(curr));
            return;
        }

        for (int num : nums) {
            if (!curr.contains(num)) {
                curr.add(num);
                backtrack(curr, ans, nums);
                curr.remove(curr.size() - 1);
            }
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String inputLine = scanner.nextLine().trim();
        inputLine = inputLine.replaceAll(".*\\[|\\].*", "");
        String[] parts = inputLine.split(",");

        int[] nums = new int[parts.length];
        for (int i = 0; i < parts.length; i++) {
            nums[i] = Integer.parseInt(parts[i].trim());
        }

        Solution solution = new Solution();
        List<List<Integer>> permutations = solution.permute(nums);
        System.out.println(permutations);

        scanner.close();
    }
}
```

---

## **Output:**

<img width="1340" height="260" alt="image" src="https://github.com/user-attachments/assets/6de86446-0de6-4ae2-8a41-1905d1d0b325" />


---

## **Result:**

The program to generate **all permutations using Backtracking** was successfully implemented, and the expected output was verified.

