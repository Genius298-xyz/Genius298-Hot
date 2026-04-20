
Author- Genius 299
<br
Just learning Github

#include <bits/stdc++.h>
using namespace std;

// Function to merge two sorted halves
void merge(vector<int> &arr, int left, int mid, int right) {
    vector<int> temp;
    
    int i = left;      // starting index of left half
    int j = mid + 1;   // starting index of right half

    // Merge the two halves
    while (i <= mid && j <= right) {
        if (arr[i] <= arr[j]) {
            temp.push_back(arr[i]);
            i++;
        } else {
            temp.push_back(arr[j]);
            j++;
        }
    }

    // Remaining elements
    while (i <= mid) {
        temp.push_back(arr[i]);
        i++;
    }

    while (j <= right) {
        temp.push_back(arr[j]);
        j++;
    }

    // Copy back to original array
    for (int k = 0; k < temp.size(); k++) {
        arr[left + k] = temp[k];
    }
}

// Recursive merge sort function
void mergeSort(vector<int> &arr, int left, int right) {
    if (left >= right) return;

    int mid = (left + right) / 2;

    mergeSort(arr, left, mid);       // left half
    mergeSort(arr, mid + 1, right);  // right half

    merge(arr, left, mid, right);    // merge both halves
}

int main() {
    vector<int> arr = {5, 2, 4, 6, 1, 3};

    mergeSort(arr, 0, arr.size() - 1);

    for (int x : arr) {
        cout << x << " ";
    }
}

