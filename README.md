#basic mergesort

procedure MERGE(A, L1, R1, L2, R2) // Regular Merge
len = R2 − L1 + 1
Array temp[len] = A[L1 . . .L1 + len]
k = L1
while L1 ≤ R1 AND L2 ≤ R2 do
if temp[L1] ≤ temp[L2] then
A[k] = temp[L1]
L1 = L1 + 1
else
A[k] = temp[L2]
L2 = L2 + 1
end if
k = k + 1
end while
while L1 ≤ R1 do // Copy remaining elements of left side of temp[] if any
A[k] = temp[L1]
L1 = L1 + 1
k = k + 1
end while
while L2 ≤ R2 do // Copy remaining elements of right side of temp[] if any
A[k] = temp[L2]
L2 = L2 + 1
k = k + 1
end while
end procedure


#modified mergesort

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
