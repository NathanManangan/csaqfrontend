
<style>



</style>

# Topic 1 - Merge Sort

## Introduction

Merge sort is a sorting algorithm to sort arrays. It divides the array into two parts, repeats the same process on the two parts, then merges all of these sorted arrays by sorting them as it merges. 

## How to implement

The most efficient way to implement mergesort is as a recursive function. It takes in an array, splits in half, and calls the sort function again on each half. Then, once the sort goes all the way to the lowest division of numbers (where each number is by itself), it begins merging the numbers back together.

[**Runtime Example**](/csaqfrontend/frq/codesubmission)

### Closer Look

Take a moment to examine the main recursive function of mergesort

<table> <tr>
<td>```java
void sort(int arr[], int l, int r)
    {
        if (l < r) {
            // COMMENT A
            int m = l + (r - l) / 2;
 
            // COMMENT B
            sort(arr, l, m);
            sort(arr, m + 1, r);
 
            // COMMENT C
            merge(arr, l, m, r);
        }
    }
```</td>
<td>
<iframe src="https://docs.google.com/forms/d/e/1FAIpQLSelD5Zp5EFnR3aMQcCSMJN-OZiGGY8OkZspYY2Qm3nUOv5xyQ/viewform?embedded=true" width="640" height="645" frameborder="0" marginheight="0" marginwidth="0">Loading…</iframe>
</td>
</tr>
</table>