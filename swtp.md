# Sliding Window & Two Pointer :

### [Maximum Points You Can Obtain from Cards](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/description/)

There are several cards arranged in a row, and each card has an associated number of points. The points are given in the integer array cardPoints.

In one step, you can take one card from the beginning or from the end of the row. You have to take exactly k cards.

Your score is the sum of the points of the cards you have taken.

Given the integer array cardPoints and the integer k, return the maximum score you can obtain

```java
class Solution {
    // TC : O(k + k)
    // SC : O(1)
    public int maxScore(int[] cardPoints, int k) {
        int ls = 0;
        int rs = 0;
        int maxSum = 0;
        int n = cardPoints.length;

        for(int i=0; i < k; i++){
            ls = ls + cardPoints[i];
        }
        maxSum = ls;
        int rIndex = n-1;

        for(int i = k-1; i>=0; i--){
            ls = ls - cardPoints[i];
            rs = rs + cardPoints[rIndex];
            rIndex--;

            maxSum = Math.max(maxSum, ls+rs);
        }

        return maxSum;

    }
}
```
