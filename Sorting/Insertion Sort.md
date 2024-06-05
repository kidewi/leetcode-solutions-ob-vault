```c++
class Solution {
public:
    vector<int> sortArray(vector<int>& nums) {
        if (nums.size() == 1) {
            return nums;
        }
        for (int i = 1; i < nums.size(); i++) {
            int key = nums.at(i);
            int j = i - 1;
            while (j >= 0 && nums.at(j) > key) {
                nums.at(j + 1) = nums.at(j);
                j--;
            }
            nums.at(j + 1) = key;
        }
        return nums;
    }
};