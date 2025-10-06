```
class Solution {
    public boolean arrayStringsAreEqual(String[] word1, String[] word2) {
        StringBuilder sb1 = new StringBuilder();
        StringBuilder sb2 = new StringBuilder();

        for (String w : word1) sb1.append(w);
        for (String w : word2) sb2.append(w);

        return sb1.toString().equals(sb2.toString());
    }
}

```



# Without built-in function 

```
class Solution {
    public boolean arrayStringsAreEqual(String[] word1, String[] word2) {
        // Step 1: Concatenate all strings in word1 manually
        String str1 = "";
        for (int i = 0; i < word1.length; i++) {
            str1 = str1 + word1[i]; // add each word to str1
        }

        // Step 2: Concatenate all strings in word2 manually
        String str2 = "";
        for (int i = 0; i < word2.length; i++) {
            str2 = str2 + word2[i]; // add each word to str2
        }

        // Step 3: Compare the two concatenated strings manually
        if (str1.length() != str2.length()) {
            return false;
        }

        for (int i = 0; i < str1.length(); i++) {
            if (str1.charAt(i) != str2.charAt(i)) {
                return false;
            }
        }

        return true;
    }
}

```
