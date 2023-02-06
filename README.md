# Merge sort 

Merge sort is a sorting algorithm that divides an array into smaller subarrays, sorts each subarray, and then merges the sorted subarrays to form the final sorted array.

In simple terms, merge sort divides the array into two halves, sorts each half, and then merges the sorted halves back together. This is repeated until the entire array has been sorted.

## How to use merge sort?

step 1: start

step 2: declare array and left, right, mid variable

step 3: perform merge function.
    if left > right
        return
    mid= (left+right)/2
    mergesort(array, left, mid)
    mergesort(array, mid+1, right)
    merge(array, left, mid, right)

step 4: Stop

The approach described above is implemented as follows:

// C++ program for Merge Sort
#include <iostream>
using namespace std;
 
// Merges two subarrays of array[].
// First subarray is arr[begin..mid]
// Second subarray is arr[mid+1..end]
void merge(int array[], int const left, int const mid,
           int const right)
{
    auto const subArrayOne = mid - left + 1;
    auto const subArrayTwo = right - mid;
 
    // Create temp arrays
    auto *leftArray = new int[subArrayOne],
         *rightArray = new int[subArrayTwo];
 
    // Copy data to temp arrays leftArray[] and rightArray[]
    for (auto i = 0; i < subArrayOne; i++)
        leftArray[i] = array[left + i];
    for (auto j = 0; j < subArrayTwo; j++)
        rightArray[j] = array[mid + 1 + j];
 
    auto indexOfSubArrayOne
        = 0, // Initial index of first sub-array
        indexOfSubArrayTwo
        = 0; // Initial index of second sub-array
    int indexOfMergedArray
        = left; // Initial index of merged array
 
    // Merge the temp arrays back into array[left..right]
    while (indexOfSubArrayOne < subArrayOne
           && indexOfSubArrayTwo < subArrayTwo) {
        if (leftArray[indexOfSubArrayOne]
            <= rightArray[indexOfSubArrayTwo]) {
            array[indexOfMergedArray]
                = leftArray[indexOfSubArrayOne];
            indexOfSubArrayOne++;
        }
        else {
            array[indexOfMergedArray]
                = rightArray[indexOfSubArrayTwo];
            indexOfSubArrayTwo++;
        }
        indexOfMergedArray++;
    }
    // Copy the remaining elements of
    // left[], if there are any
    while (indexOfSubArrayOne < subArrayOne) {
        array[indexOfMergedArray]
            = leftArray[indexOfSubArrayOne];
        indexOfSubArrayOne++;
        indexOfMergedArray++;
    }
    // Copy the remaining elements of
    // right[], if there are any
    while (indexOfSubArrayTwo < subArrayTwo) {
        array[indexOfMergedArray]
            = rightArray[indexOfSubArrayTwo];
        indexOfSubArrayTwo++;
        indexOfMergedArray++;
    }
    delete[] leftArray;
    delete[] rightArray;
}
 
// begin is for left index and end is
// right index of the sub-array
// of arr to be sorted */
void mergeSort(int array[], int const begin, int const end)
{
    if (begin >= end)
        return; // Returns recursively
 
    auto mid = begin + (end - begin) / 2;
    mergeSort(array, begin, mid);
    mergeSort(array, mid + 1, end);
    merge(array, begin, mid, end);
}
 
// UTILITY FUNCTIONS
// Function to print an array
void printArray(int A[], int size)
{
    for (auto i = 0; i < size; i++)
        cout << A[i] << " ";
}
 
// Driver code
int main()
{
    int arr[] = { 13, 12, 14, 4, 7, 8 };
    auto arr_size = sizeof(arr) / sizeof(arr[0]);
 
    cout << "Given array is \n";
    printArray(arr, arr_size);
 
    mergeSort(arr, 0, arr_size - 1);
 
    cout << "\nSorted array is \n";
    printArray(arr, arr_size);
    return 0;
}


# Modified mergesort (based on the article attached)

procedure ENHANCED MERGESORT(A)
 for i = 0 to n − 2 do // Pairwise sort for n/2 pairs
 if A[i] > A[i + 1] then
 swap(A[i], A[i + 1])
 end if
 i = i + 2
 end for
 for round = 1 to log n − 1 do // log n − 1 rounds
 subarray size = 2
round
 subarray count = 𝑛
𝑠𝑢𝑏𝑎𝑟𝑟𝑎𝑦 𝑠𝑖𝑧𝑒
 for subarray number = 0 to 𝑠𝑢𝑏𝑎𝑟𝑟𝑎𝑦 𝑐𝑜𝑢𝑛𝑡
2 − 1 do 
 // Merge each of 𝑛 2
round+1
pairs of subarrays
 L1 = subarray number ∗ 2 ∗ subarray size
 R1 = L1 + subarray size − 1
  L2 = R1 + 1
 R2 = L2 + subarray size – 1
 if A[R1] ≤ A[L2] then // Case A
 return
 end if
 if A[R2] ≤ A[L1] then // Case B
 while L1 ≤ R1 do
 swap(A[L1], A[L2])
 L1 = L1 + 1
 L2 = L2 + 1
 end while
 return
 end if
 MERGE(A, L1, R1, L2, R2) // Case C
 end for
 end for
 end procedure
