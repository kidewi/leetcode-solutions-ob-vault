```c++
void bucketSort(vector<int>& nums) {
	if (nums.empty()) return;

	// Find min/max in nums
	// used to determine how to distribute nums across buckets
	int minValue = *min_element(nums.begin(), nums.end());
	int maxValue = *max_element(nums.begin(), nums.end());

	// Number of buckets is based on input vector size
	// Simple heuristic and can be adjusted
	int bucketCount = nums.size();

	// Vector of vectors to hold the buckets
	vector<vector<int>> buckets(bucketCount);

	// Calculate the interval for each bucket
	// Add 1 to ensure that the interval covers the entire range
	// Avoids placing all elements in first bucket when min~max
	int interval = max(1, (maxValue - minValue) / bucketCount + 1);

	// Iterate over each element in nums
	// place each element into appropriate bucket based on value
	for (int num : nums) {
		int index = (num - minValue) / interval; // calculate bucket index for num
		buckets[index].push_back(num); // add num to corresponding bucket
	}
	// Iterate over each bucket
	int currentIndex = 0;
	for (int i = 0; i < bucketCount; i++) {
		// Sort current bucket
		sort(buckets[i].begin(), buckets[i].end());

		// Merge sorted bucket back into nums
		// iterates over each element in sorted bucket
		// places it back into nums, starting from currentIndex
		for (int num : buckets[i]) {
			nums[currentIndex++] = num;
		}
	}
}
```