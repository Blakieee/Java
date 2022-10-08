## Bubble Sort

### Complexity

​	n^2

### Code

```java
class Solution {
    public int[] sortArray(int[] nums) {
        // 10.7 bubble sort 
        // complexity: N^2
        // time exceed
        int pos = nums.length-1;
        
        for (int i = pos; i>0; i--) {
            for (int j = 0; j<i; j++) {
                swap(nums, j, i);
            }
        }
        
        return nums;
    }
    
    public void swap(int[] nums, int a, int b) {
        if (nums[a] > nums[b]) {
            int tmp = nums[b];
            nums[b] = nums[a];
            nums[a] = tmp;
        } 
    }
}
```



## Selection Sort
### Complexity

​	n^2

### Code

```java
// Java program for implementation of
// selection sort
import java.util.*;
class GFG
{

// Function to implement the selection
// sort
static void selectionSort(int arr[], int n)
{
	int i, j, min_idx;

	// One by one move boundary of
	// unsorted subarray
	for (i = 0; i < n - 1; i++)
	{

		// Find the minimum element
		// in unsorted array
		min_idx = i;
		for (j = i + 1; j < n; j++)
			if (arr[j] < arr[min_idx])
				min_idx = j;

		// Swap the found minimum element
		// with the first element
		int temp = arr[min_idx];
		arr[min_idx]= arr[i];
		arr[i] = temp;
	}
}

// Function to print an array
static void printArray(int arr[], int size)
{
	int i;

	for (i = 0; i < size; i++) {
		System.out.print(arr[i]+ " ");
	}
	System.out.println();
}

// Driver Code
public static void main(String[] args)
{
	int arr[] = { 64, 25, 12, 22, 11 };
	int n = arr.length;

	// Function Call
	selectionSort(arr, n);
	System.out.print("Sorted array: \n");

	// Print the array
	printArray(arr, n);
}
}

// This code is contributed by aashish1995

```



### Example

```java
arr[] = 64 25 12 22 11

// Find the minimum element in arr[0...4]
// and place it at beginning
11 25 12 22 64

// Find the minimum element in arr[1...4]
// and place it at beginning of arr[1...4]
11 12 25 22 64

// Find the minimum element in arr[2...4]
// and place it at beginning of arr[2...4]
11 12 22 25 64

// Find the minimum element in arr[3...4]
// and place it at beginning of arr[3...4]
11 12 22 25 64
```



## Insertion Sort

​	like playing poke:
### Complexity

​	n^2

### Code

```java
// Java program for the above approach
import java.util.*;
class GFG
{
	
// Function to sort an array using
// insertion sort
static void insertionSort(int arr[], int n)
{
	int i, key, j;
	for (i = 1; i < n; i++)
	{
		key = arr[i];
		j = i - 1;

		// Move elements of arr[0..i-1],
		// that are greater than key to
		// one position ahead of their
		// current position
		while (j >= 0 && arr[j] > key)
		{
			arr[j + 1] = arr[j];
			j = j - 1;
		}
		arr[j + 1] = key;
	}
}

// Function to print an array of size N
static void printArray(int arr[], int n)
{
	int i;

	// Print the array
	for (i = 0; i < n; i++) {
		System.out.print(arr[i] + " ");
	}
	System.out.println();
}

// Driver code
public static void main(String[] args)
{
	int arr[] = { 12, 11, 13, 5, 6 };
	int N = arr.length;

	// Function Call
	insertionSort(arr, N);
	printArray(arr, N);
}
}

// This code is contributed by code_hunt.

```



### Example

![insertion sort](/Users/blake/Desktop/JavaNotes/Java/pictures/insertionsort.png)


## Merge Sort

​	sort two sides, and combine
### Complexity

​	nLog(n)

### Code

```java
/* Java program for Merge Sort */
class MergeSort {
	// Merges two subarrays of arr[].
	// First subarray is arr[l..m]
	// Second subarray is arr[m+1..r]
	void merge(int arr[], int l, int m, int r)
	{
		// Find sizes of two subarrays to be merged
		int n1 = m - l + 1;
		int n2 = r - m;

		/* Create temp arrays */
		int L[] = new int[n1];
		int R[] = new int[n2];

		/*Copy data to temp arrays*/
		for (int i = 0; i < n1; ++i)
			L[i] = arr[l + i];
		for (int j = 0; j < n2; ++j)
			R[j] = arr[m + 1 + j];

		/* Merge the temp arrays */

		// Initial indexes of first and second subarrays
		int i = 0, j = 0;

		// Initial index of merged subarray array
		int k = l;
		while (i < n1 && j < n2) {
			if (L[i] <= R[j]) {
				arr[k] = L[i];
				i++;
			}
			else {
				arr[k] = R[j];
				j++;
			}
			k++;
		}

		/* Copy remaining elements of L[] if any */
		while (i < n1) {
			arr[k] = L[i];
			i++;
			k++;
		}

		/* Copy remaining elements of R[] if any */
		while (j < n2) {
			arr[k] = R[j];
			j++;
			k++;
		}
	}

	// Main function that sorts arr[l..r] using
	// merge()
	void sort(int arr[], int l, int r)
	{
		if (l < r) {
			// Find the middle point
			int m = l + (r - l) / 2;

			// Sort first and second halves
			sort(arr, l, m);
			sort(arr, m + 1, r);

			// Merge the sorted halves
			merge(arr, l, m, r);
		}
	}

	/* A utility function to print array of size n */
	static void printArray(int arr[])
	{
		int n = arr.length;
		for (int i = 0; i < n; ++i)
			System.out.print(arr[i] + " ");
		System.out.println();
	}

	// Driver code
	public static void main(String args[])
	{
		int arr[] = { 12, 11, 13, 5, 6, 7 };

		System.out.println("Given Array");
		printArray(arr);

		MergeSort ob = new MergeSort();
		ob.sort(arr, 0, arr.length - 1);

		System.out.println("\nSorted array");
		printArray(arr);
	}
}
/* This code is contributed by Rajat Mishra */

```



### Example

![merge sort](/Users/blake/Desktop/JavaNotes/Java/pictures/MergeSort.png)

### Question:

**In an array, if we add all the numbers in the left of a number, we call it a "small sum" of a number. For example: for [1,3,4,2,5]**

**find sum of all "small sum" in this array**

leftside numbers which less than 1: null；
leftside numbers which less than 3: 1；
leftside numbers which less than 4: 1、3；
leftside numbers which less than 2: 1；
leftside numbers which less than 5: 1、3、4、2；
so "small sum" sum is 1+1+3+1+1+3+4+2=16



idea:

for 4 in [1,3,4,2,5], "small sum" is 1+3. However, we can reverse the thinking process: when we see 1, we can see 3,4,2,5 are on the right, so we add 1*4 to the total result.

By using the merge sort idea, we can divide the array in half, and then merge the results.

```java
public static int smallSum(int[] arr) {
    if (arr == null || arr.length < 2) {
        return 0;
    }
    return mergeSort(arr, 0, arr.length - 1);
}

public static int mergeSort(int[] arr, int left, int right) {
    if (left == right) {
        return 0;
    }
    int mid = left + (right - left) >> 1;
    return mergeSort(arr, left, mid) + mergeSort(arr, mid + 1, right) + merge(arr, left, mid, right);
}

public static int merge(int[] arr, int left, int mid, int right) {
    int[] help = new int[right - left + 1];
    int i = 0, p1 = left, p2 = mid + 1, result = 0;
    while (p1 <= mid && p2 <= right) {
        //并入的时候，利用有序性
        //eg.134和25,由1<2,推出2后面的数都>1,故直接(right-indexOf(2)+1)*1
        result += arr[p1] < arr[p2] ? (right - p2 + 1) * arr[p1] : 0;
        help[i++] = arr[p1] < arr[p2] ? arr[p1++] : arr[p2++];
    }
    while (p1 <= mid) {
        help[i++] = arr[p1++];
    }
    while (p2 <= right) {
        help[i++] = arr[p2++];
    }
    for (int j = 0; j < help.length; j++) {
        arr[left + j] = help[j];
    }
    return result;
}

```



## Quick Sort



### Complexity

**n**log(**n**)



### Code

```java
// Java implementation of QuickSort
import java.io.*;

class GFG {

	// A utility function to swap two elements
	static void swap(int[] arr, int i, int j)
	{
		int temp = arr[i];
		arr[i] = arr[j];
		arr[j] = temp;
	}

	/* This function takes last element as pivot, places
	the pivot element at its correct position in sorted
	array, and places all smaller (smaller than pivot)
	to left of pivot and all greater elements to right
	of pivot */
	static int partition(int[] arr, int low, int high)
	{

		// pivot
		int pivot = arr[high];

		// Index of smaller element and
		// indicates the right position
		// of pivot found so far
		int i = (low - 1);

		for (int j = low; j <= high - 1; j++) {

			// If current element is smaller
			// than the pivot
			if (arr[j] < pivot) {

				// Increment index of
				// smaller element
				i++;
				swap(arr, i, j);
			}
		}
		swap(arr, i + 1, high);
		return (i + 1);
	}

	/* The main function that implements QuickSort
			arr[] --> Array to be sorted,
			low --> Starting index,
			high --> Ending index
	*/
	static void quickSort(int[] arr, int low, int high)
	{
		if (low < high) {

			// pi is partitioning index, arr[p]
			// is now at right place
			int pi = partition(arr, low, high);

			// Separately sort elements before
			// partition and after partition
			quickSort(arr, low, pi - 1);
			quickSort(arr, pi + 1, high);
		}
	}

	// Function to print an array
	static void printArray(int[] arr, int size)
	{
		for (int i = 0; i < size; i++)
			System.out.print(arr[i] + " ");

		System.out.println();
	}

	// Driver Code
	public static void main(String[] args)
	{
		int[] arr = { 10, 7, 8, 9, 1, 5 };
		int n = arr.length;

		quickSort(arr, 0, n - 1);
		System.out.println("Sorted array: ");
		printArray(arr, n);
	}
}

==// This code is contributed by Ayush Choudhary
```



## Bitwise Operation:

xor (**^**): 

two principles:

**Commutative Law:** ab = ba

**Associative Law:** (ab)c = (a)bc

a^b^a = b

a^a = 0

a^0 = a



For a^b^c, the bit on a specific position in a result depends on number of 1s at this posititon in different numbers

even number of 1: 0

odd number of 1: 1




### Question 1: find numbers which ocurrs odd times 
there are two numbers occur odd times, other numbers occur even times.

Find these two numbers;

```java
// "static void main" must be defined in a public class.
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello World!");
        int[] nums = {1,1,2,2,3,3,5,6};
        printOddTimesNums(nums);
    }
    
    public  static void printOddTimesNums(int[] nums) {
        int aorb = 0;

        for (Integer num:nums) {
            aorb^=num;
        }

        int rightmost1 = aorb & (~aorb+1);
        int aorb1 = 0;
        for (Integer num:nums) {
            if ((rightmost1&num) == 0) {
                aorb1^=num;
            }
        }
        
        int aorb2 = aorb1^aorb;

        System.out.println("first number is :" + aorb1);
        System.out.println("second number is :" + aorb2);
    }
}



```



