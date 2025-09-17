```
class Solution {
    public int maxFreqSum(String s) {
        int[] freq = new int[26];
        // count all characters
        for (char c : s.toCharArray()) {
            freq[c - 'a']++;
        }
        int maxVowel = 0;
        int maxConsonant = 0;
        for (int i = 0; i < 26; i++) {
            char c = (char) (i + 'a');
            if (isVowel(c)) {
                maxVowel = Math.max(maxVowel, freq[i]);
            } else {
                maxConsonant = Math.max(maxConsonant, freq[i]);
            }
        }
        return maxVowel + maxConsonant;
    }
    
    private boolean isVowel(char c) {
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
    }
}

```
