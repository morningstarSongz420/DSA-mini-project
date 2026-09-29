# Data Structures & Algorithms — Part B Pseudocode

---

## Task B1: Selection Sort

```text
Algorithm SelectionSort(arr)
    Input: An array 'arr' of n elements
    Output: Array 'arr' sorted in ascending order with comparison and swap metrics

    n = length(arr)
    comparisons = 0
    swaps = 0

    For i = 0 To n - 2 Do
        minIdx = i
        For j = i + 1 To n - 1 Do
            comparisons = comparisons + 1
            If arr[j] < arr[minIdx] Then
                minIdx = j
            End If
        End For

        If minIdx != i Then
            Swap arr[i] and arr[minIdx]
            swaps = swaps + 1
        End If
    End For

    Print "Comparisons:", comparisons
    Print "Swaps:", swaps
End Algorithm
```

---

## Task B2: Insertion Sort

```text
Algorithm InsertionSort(arr)
    Input: An array 'arr' of n elements
    Output: Array 'arr' sorted in ascending order with comparison and shift metrics

    n = length(arr)
    comparisons = 0
    shifts = 0

    For i = 1 To n - 1 Do
        key = arr[i]
        j = i - 1

        While j >= 0 Do
            comparisons = comparisons + 1
            If arr[j] > key Then
                arr[j + 1] = arr[j]
                shifts = shifts + 1
                j = j - 1
            Else
                Break While
            End If
        End While

        arr[j + 1] = key
    End For

    Print "Comparisons:", comparisons
    Print "Shifts:", shifts
End Algorithm
```

---

## Task B3: Merge Sort

```text
Algorithm MergeSort(arr, left, right)
    Input: An array 'arr', starting index 'left', ending index 'right'
    Output: Array 'arr' recursively sorted in ascending order

    If left < right Then
        mid = left + (right - left) / 2
        
        MergeSort(arr, left, mid)        // Sort left half
        MergeSort(arr, mid + 1, right)   // Sort right half
        Merge(arr, left, mid, right)     // Merge sorted halves
    End If
End Algorithm

Algorithm Merge(arr, left, mid, right)
    n1 = mid - left + 1
    n2 = right - mid

    Create array L[0..n1-1] and R[0..n2-1]

    For i = 0 To n1 - 1 Do: L[i] = arr[left + i]
    For j = 0 To n2 - 1 Do: R[j] = arr[mid + 1 + j]

    i = 0, j = 0, k = left

    While i < n1 AND j < n2 Do
        comparisons = comparisons + 1
        If L[i] <= R[j] Then
            arr[k] = L[i]
            i = i + 1
        Else
            arr[k] = R[j]
            j = j + 1
        End If
        k = k + 1
    End While

    While i < n1 Do
        arr[k] = L[i]
        i = i + 1
        k = k + 1
    End While

    While j < n2 Do
        arr[k] = R[j]
        j = j + 1
        k = k + 1
    End While
End Algorithm
```

---

## Task B4: Quick Sort

```text
Algorithm QuickSort(arr, low, high)
    Input: An array 'arr', starting index 'low', ending index 'high'
    Output: Array 'arr' partitioned and sorted in ascending order

    If low < high Then
        pi = Partition(arr, low, high)   // Pivot index after partitioning

        QuickSort(arr, low, pi - 1)      // Recursively sort left sub-array
        QuickSort(arr, pi + 1, high)     // Recursively sort right sub-array
    End If
End Algorithm

Algorithm Partition(arr, low, high)
    // Pivot-selection rule: Rightmost element (Lomuto scheme)
    pivot = arr[high]
    i = low - 1

    For j = low To high - 1 Do
        comparisons = comparisons + 1
        If arr[j] < pivot Then
            i = i + 1
            Swap arr[i] and arr[j]
        End If
    End For

    Swap arr[i + 1] and arr[high]
    Return i + 1
End Algorithm
```