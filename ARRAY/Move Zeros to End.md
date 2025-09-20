
## 1️⃣ Brute Force (Extra Array)


```java
class Solution {
    public void moveZeroes(int[] arr) {
        int n = arr.length;
        int[] temp = new int[n];  // extra array
        int index = 0;

        // Copy non-zero elements
        for (int i = 0; i < n; i++) {
            if (arr[i] != 0) {
                temp[index++] = arr[i];
            }
        }

        // Copy back to original
        for (int i = 0; i < n; i++) {
            arr[i] = temp[i];
        }
    }
}
```


## 2️⃣ Optimal (Two-pass, Shift Method)

```java
class Solution {
    public void moveZeroes(int[] arr) {
        int n = arr.length;
        int index = 0;

        // Step 1: Move non-zero elements forward
        for (int i = 0; i < n; i++) {
            if (arr[i] != 0) {
                arr[index] = arr[i];
                index++;
            }
        }

        // Step 2: Fill remaining with 0
        while (index < n) {
            arr[index] = 0;
            index++;
        }
    }
}
```


---

## 3️⃣ Most Optimal (One-pass, Swap Method)

```java
class Solution {
    public void moveZeroes(int[] arr) {
        int n = arr.length;
        int j = 0; // points to the position where next non-zero should go

        for (int i = 0; i < n; i++) {
            if (arr[i] != 0) {
                // Swap arr[i] and arr[j]
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
                j++;
            }
        }
    }
}
```

✅ In-place
✅ Single pass (best performance)
✅ Minimum writes

**Time:** O(n)
**Space:** O(1)

