# TWO POINTERS & SLIDING WINDOW

## QUESTIONS
| Question | Level |
|----------|-------|
| [Container With Most Water (11)](https://leetcode.com/problems/container-with-most-water/description/) | Medium |
| [3 Sum (15)](https://leetcode.com/problems/3sum/) | Medium |
| [3 Sum Closest (16))](https://leetcode.com/problems/3sum-closest/submissions/2109621502/) | Medium |
| [4 Sum (18)](https://leetcode.com/problems/4sum/submissions/2110865086/) | Medium |
| [Longest Substring Without Repeating Characters (3)](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/) | Medium |
| [Minimum Window Substring (76)](https://leetcode.com/problems/minimum-window-substring/submissions/2113807427/) | Hard |
| [Minimum Size Subarray Sum (209)](https://leetcode.com/problems/minimum-size-subarray-sum/description/) | Medium |

## SLIDING WINDOW PATTERNS

### CONSTANT SIZE WINDOW
```Java
// form k size window
while(end < k) {
	sum += arr[end];
	ans = end;
	++end;
}

// slide the window
while(end < arr.length){
	sum += arr[end] - arr[end-k];
	ans = Math.max(sum, ans);
}
```

### DYNAMIC SIZE WINDOW (TYPE A)
```Java
int start=0,end=0, maxLength = -1;

while(end < arr.length){
	sum = sum + arr[end];
	
	while(sum > k){ // TC = O(2N) worst case
		sum -= arr[start];
		++start;
	}
	
	maxLength = Math.max(end-start+1, maxLength);
	++end;
}
```

### DYNAMIC SIZE WINDOW (TYPE B)
```Java
while(end < arr.length){
	sum = sum + arr[end];
	
	if(sum > k){
		sum -= arr[start];
		++start;
	}
	
	if(sum <= k){
		maxLength = Math.max(maxLength, end-start+1);
	}
	
	++end;
}
```

### NO. OF SUBSTRINGS
```Java
// VARIATION 1 (NO. OF SUBSTRING WITH A GIVEN CONDITION)

// NO OF SUBARRAYS WITH SUM = K
// No of subarrays with sum <= k => X
// No of subarrays with sum <= k-1 => Y
// Ans = X-Y

// VARIATION 2 (NO. OF SUBSTRING CONTAINING  ALL THREE CHARACTERS)
// 1. a= -1, b= -1, c= -1
// 2. Once all indexes are not -1 then
// 3. No of subarrays += MinIndex + 1
```