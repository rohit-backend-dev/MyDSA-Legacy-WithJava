# Array Rotation by `d` Places

---

## 🔥 Concept: Rotate Array by `d` Places

### ➤ Left Rotation

Move elements to the **left**, shifting starting elements to the end.

**Example:**

```
arr = [1, 2, 3, 4, 5, 6, 7], d = 2
Result: [3, 4, 5, 6, 7, 1, 2]
```

### ➤ Right Rotation

Move elements to the **right**, shifting ending elements to the beginning.

**Example:**

```
arr = [1, 2, 3, 4, 5, 6, 7], d = 2
Result: [6, 7, 1, 2, 3, 4, 5]
```

---

## 🧠 Core Concept Behind Rotation

- **Left Rotation**: Move first `d` elements to the end.
- **Right Rotation**: Move last `d` elements to the start.

---

## ✅ Brute Force Approach

### 1. Left Rotation - Brute Force

```java
public void leftRotateBrute(int[] arr, int d) {
    int n = arr.length;
    d = d % n; // In case d > n
    int[] temp = new int[d];

    // Store first d elements
    for (int i = 0; i < d; i++) {
        temp[i] = arr[i];
    }

    // Shift the rest to the left
    for (int i = d; i < n; i++) {
        arr[i - d] = arr[i];
    }

    // Put temp elements at the end
    for (int i = 0; i < d; i++) {
        arr[n - d + i] = temp[i];
    }
}
```

**Example:**

```
Input: [1, 2, 3, 4, 5], d=2
Step1: temp = [1,2]
Step2: Shift → [3,4,5,4,5]
Step3: Fill temp → [3,4,5,1,2]
```

---

### 2. Right Rotation - Brute Force

```java
public void rightRotateBrute(int[] arr, int d) {
    int n = arr.length;
    d = d % n;
    int[] temp = new int[d];

    // Store last d elements
    for (int i = 0; i < d; i++) {
        temp[i] = arr[n - d + i];
    }

    // Shift rest to the right
    for (int i = n - d - 1; i >= 0; i--) {
        arr[i + d] = arr[i];
    }

    // Place temp at beginning
    for (int i = 0; i < d; i++) {
        arr[i] = temp[i];
    }
}
```

**Example:**

```
Input: [1, 2, 3, 4, 5], d=2
Step1: temp = [4,5]
Step2: Shift → [1,2,3,3,4]
Step3: Fill temp → [4,5,1,2,3]
```

---

## 🚀 Optimal Approach (Reversal Algorithm)

**Idea:** Reverse parts of the array in place to rotate efficiently.

---

### 1. Left Rotation - Optimal (Reversal)

```java
public class LeftRotateArray {

    // Reverse elements in the array from start to end index
    private static void reverse(int[] arr, int start, int end) {
        while (start < end) {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }

    // Perform left rotation by d places using reversal algorithm
    public static void leftRotateOptimal(int[] arr, int d) {
        int n = arr.length;
        if (n == 0 || d == 0) return;

        d = d % n;  // Handle d > n

        reverse(arr, 0, d - 1);     // Reverse first d elements
        reverse(arr, d, n - 1);     // Reverse remaining elements
        reverse(arr, 0, n - 1);     // Reverse whole array
    }

    // Print array
    public static void printArray(int[] arr) {
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5, 6, 7};
        int d = 2;

        System.out.println("Original Array:");
        printArray(arr);

        leftRotateOptimal(arr, d);

        System.out.println("Array after Left Rotation by " + d + " positions:");
        printArray(arr);
    }
}
```

**Example:** `[1, 2, 3, 4, 5]`, d = 2

```
Step1: Reverse(0,1) → [2,1,3,4,5]
Step2: Reverse(2,4) → [2,1,5,4,3]
Step3: Reverse(0,4) → [3,4,5,1,2]
```

---

### 2. Right Rotation - Optimal (Reversal)

```java
public class RightRotateArray {

    // Reverse elements in the array from start to end index
    private static void reverse(int[] arr, int start, int end) {
        while (start < end) {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }

    // Perform right rotation by d places using reversal algorithm
    public static void rightRotateOptimal(int[] arr, int d) {
        int n = arr.length;
        if (n == 0 || d == 0) return;

        d = d % n; // Handle d > n
        reverse(arr, 0, n - 1);     // Reverse whole array
        reverse(arr, 0, d - 1);     // Reverse first d elements
        reverse(arr, d, n - 1);     // Reverse the rest
    }

    // Print array
    public static void printArray(int[] arr) {
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5, 6, 7};
        int d = 2;

        System.out.println("Original Array:");
        printArray(arr);

        rightRotateOptimal(arr, d);

        System.out.println("Array after Right Rotation by " + d + " positions:");
        printArray(arr);
    }
}
```

**Example:** `[1, 2, 3, 4, 5]`, d = 2

```
Step1: Reverse whole → [5,4,3,2,1]
Step2: Reverse first d → [4,5,3,2,1]
Step3: Reverse rest → [4,5,1,2,3]
```

---

## 📌 Time and Space Complexity

| Method            | Time | Space |
| ----------------- | ---- | ----- |
| Brute Force       | O(n) | O(d)  |
| Optimal (Reverse) | O(n) | O(1)  |

---

## ✅ Summary Table

| Operation    | Brute Force                      | Optimal (Reversal Algorithm) |
| ------------ | -------------------------------- | ---------------------------- |
| Left Rotate  | Use temp for first d, shift rest | Reverse 0→d-1, d→n-1, 0→n-1  |
| Right Rotate | Use temp for last d, shift rest  | Reverse 0→n-1, 0→d-1, d→n-1  |

---
