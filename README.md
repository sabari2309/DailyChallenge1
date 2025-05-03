# 🔥 LeetCode 100 Days Challenge – Sabareeswaran G

Welcome to my personal 100-day LeetCode challenge, where I tackle one coding problem every day and explain my thought process. My goal is not just to solve problems but to deeply understand them. 💪

---

## 📌 Day 1: Minimum Domino Rotations For Equal Row

### 🧠 Problem Statement

You’re given two arrays `tops[]` and `bottoms[]` representing the top and bottom halves of dominoes. Your task is to find the **minimum number of rotations** to make all top or all bottom values the same. If it's not possible, return `-1`.

### 💡 Intuition

- There are only **two possible values** that could fill the entire row: `tops[0]` or `bottoms[0]`.
- For each candidate number (say `x`), we:
  - Check how many rotations are needed to make **all top** values equal to `x`
  - Or to make **all bottom** values equal to `x`
- If neither is possible → return `-1`.

### 🛠️ Java Code

```java
public class Day15_MinimumDominoRotations {
    public int minDominoRotations(int[] tops, int[] bottoms) {
        int res = check(tops[0], tops, bottoms);
        if (res != -1 || tops[0] == bottoms[0]) return res;
        return check(bottoms[0], tops, bottoms);
    }

    private int check(int target, int[] tops, int[] bottoms) {
        int rotateTop = 0, rotateBottom = 0;
        for (int i = 0; i < tops.length; i++) {
            if (tops[i] != target && bottoms[i] != target)
                return -1;
            else if (tops[i] != target)
                rotateTop++;
            else if (bottoms[i] != target)
                rotateBottom++;
        }
        return Math.min(rotateTop, rotateBottom);
    }
}
