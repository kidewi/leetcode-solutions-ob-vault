
Plain
```c++
class Solution {

public:

    vector<int> sortArray(vector<int>& nums) {
        quickSort(nums, 0, nums.size() - 1);
        return nums;
    }
private:
    void quickSort(vector<int>& nums, int low, int high) {
        if (low < high) {
            int pivot_location = Partition(nums, low, high);
            quickSort(nums, low, pivot_location - 1);
            quickSort(nums, pivot_location + 1, high);
        }
    }

    int Partition(vector<int>& nums, int low, int high) {
        int pivot = nums[high];
        int leftwall = low - 1;
        
        for (int i = low; i < high; i++) {
            if (nums[i] < pivot) {
                leftwall++;
                swap(nums[i], nums[leftwall]);
            }
        }
        swap(nums[high], (nums[leftwall + 1]));
        return (leftwall + 1);
    }
};
;```

Random Pivot
```c++
#include <vector>
#include <cstdlib> // for rand() and srand()
#include <ctime>   // for time()

class Solution {
public:
    vector<int> sortArray(vector<int>& nums) {
        srand(time(NULL)); // Initialize random seed
        quickSort(nums, 0, nums.size() - 1);
        return nums;
    }

private:
    void quickSort(vector<int>& nums, int low, int high) {
        if (low < high) {
            int pivot_location = randomizedPartition(nums, low, high);
            quickSort(nums, low, pivot_location - 1);
            quickSort(nums, pivot_location + 1, high);
        }
    }

    int randomizedPartition(vector<int>& nums, int low, int high) {
        int randomPivotIdx = low + rand() % (high - low + 1);
        swap(nums[randomPivotIdx], nums[high]); // Move the pivot to the end for partitioning
        return Partition(nums, low, high);
    }

    int Partition(vector<int>& nums, int low, int high) {
        int pivot = nums[high];
        int leftwall = low - 1;

        for (int i = low; i < high; i++) {
            if (nums[i] < pivot) {
                leftwall++;
                swap(nums[i], nums[leftwall]);
            }
        }

        swap(nums[high], nums[leftwall + 1]);
        return leftwall + 1;
    }
};

```