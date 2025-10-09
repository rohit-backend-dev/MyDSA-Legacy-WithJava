```
import java.util.*;

class Solution {
    // Function to find common elements in three arrays.
    public List<Integer> commonElements(List<Integer> arr1, List<Integer> arr2, List<Integer> arr3) {
        List<Integer> result = new ArrayList<>();

        for (int i = 0; i < arr1.size(); i++) {
            for (int j = 0; j < arr2.size(); j++) {
                for (int k = 0; k < arr3.size(); k++) {
                    if (arr1.get(i).equals(arr2.get(j)) && arr2.get(j).equals(arr3.get(k))) {
                        // Avoid duplicates in the result
                        if (!result.contains(arr1.get(i))) {
                            result.add(arr1.get(i));
                        }
                    }
                }
            }
        }

        return result;
    }
}

```



```
import java.util.*;

class Solution {
    // Function to find common elements in three arrays.
    public List<Integer> commonElements(List<Integer> arr1, List<Integer> arr2, List<Integer> arr3) {
        List<Integer> result = new ArrayList<>();
        int i = 0, j = 0, k = 0;

        while (i < arr1.size() && j < arr2.size() && k < arr3.size()) {
            int a = arr1.get(i);
            int b = arr2.get(j);
            int c = arr3.get(k);

            if (a == b && b == c) {
                // Avoid duplicates
                if (result.isEmpty() || result.get(result.size() - 1) != a) {
                    result.add(a);
                }
                i++;
                j++;
                k++;
            } else {
                // Increment pointer of smallest element
                if (a < b) {
                    i++;
                } else if (b < c) {
                    j++;
                } else {
                    k++;
                }
            }
        }

        return result;
    }
}

```
