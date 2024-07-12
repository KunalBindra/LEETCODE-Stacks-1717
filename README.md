# LEETCODE-Stacks-1717
To do a dry run of the given `Solution` class and its `maximumGain` method, we need to trace the logic with a sample input to understand how the code works step by step. 

Let's use the following example:

- `s = "cdbcbbaaabab"`
- `x = 4`
- `y = 5`

### Code Explanation and Dry Run:

1. **Initial Call:**
   ```java
   int result = new Solution().maximumGain("cdbcbbaaabab", 4, 5);
   ```
   Since `x < y`, the method `gain(s, "ba", 5, "ab", 4)` is called.

2. **Inside the `gain` method:**

   **Initialization:**
   ```java
   int points = 0;
   Stack<Character> stack1 = new Stack<>();
   Stack<Character> stack2 = new Stack<>();
   ```

   **First Removal Phase (removing "ba" with point 5):**

   Loop through characters of `s`:
   ```java
   for (final char c : s.toCharArray())
   ```
   - `c = 'c'`: `stack1 = ['c']`
   - `c = 'd'`: `stack1 = ['c', 'd']`
   - `c = 'b'`: `stack1 = ['c', 'd', 'b']`
   - `c = 'c'`: `stack1 = ['c', 'd', 'b', 'c']`
   - `c = 'b'`: `stack1 = ['c', 'd', 'b', 'c', 'b']`
   - `c = 'b'`: `stack1 = ['c', 'd', 'b', 'c', 'b', 'b']`
   - `c = 'a'`: `stack1 = ['c', 'd', 'b', 'c', 'b']` and `points += 5` (removal of "ba")
   - `c = 'a'`: `stack1 = ['c', 'd', 'b', 'c']` and `points += 5` (removal of "ba")
   - `c = 'b'`: `stack1 = ['c', 'd', 'b', 'c', 'b']`
   - `c = 'a'`: `stack1 = ['c', 'd', 'b', 'c']` and `points += 5` (removal of "ba")
   - `c = 'b'`: `stack1 = ['c', 'd', 'b', 'c', 'b']`

   At the end of the first removal phase, `points = 15`.

   **Second Removal Phase (removing "ab" with point 4):**

   Loop through characters of `stack1`:
   ```java
   for (final char c : stack1)
   ```
   - `c = 'c'`: `stack2 = ['c']`
   - `c = 'd'`: `stack2 = ['c', 'd']`
   - `c = 'b'`: `stack2 = ['c', 'd', 'b']`
   - `c = 'c'`: `stack2 = ['c', 'd', 'b', 'c']`
   - `c = 'b'`: `stack2 = ['c', 'd', 'b', 'c', 'b']`

   In this phase, no "ab" pairs are found, so `points` remain `15`.

### Final Result:

The final result returned by the method is `15`.

### Dry Run Summary:
The method correctly calculates the maximum gain by strategically removing pairs of "ba" first, then "ab". The detailed step-by-step process confirms that the implementation is correct.

Would you like me to run any additional test cases or explain further?
