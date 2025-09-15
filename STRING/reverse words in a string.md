class Solution {
    public String reverseWords(String s) {
        // Convert string to char array
        char[] arr = s.toCharArray();
        int n = arr.length;

        // Step 1: Reverse the entire array
        reverse(arr, 0, n - 1);

        // Step 2: Reverse each word
        int start = 0;
        for (int end = 0; end <= n; end++) {
            if (end == n || arr[end] == ' ') {
                reverse(arr, start, end - 1);
                start = end + 1;
            }
        }

        // Convert back to string and trim extra spaces
        return new String(arr).trim().replaceAll("\\s+", " ");
    }

    // Helper method to reverse a part of char array
    private void reverse(char[] arr, int left, int right) {
        while (left < right) {
            char temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;
            left++;
            right--;
        }
    }
}
