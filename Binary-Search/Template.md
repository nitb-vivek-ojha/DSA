# BINARY SEARCH

## QUESTIONS
| Question | Level |
|----------|-------|
| [Koko Eating Bananas (875)](https://leetcode.com/problems/koko-eating-bananas/submissions/2135278243/) | Medium |
| [Capacity to Ship Package within d days (1011)](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/description/) | Medium |
| [First & Last Position (34)](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/) | Medium |
| [Search Insert Position (35)](https://leetcode.com/problems/search-insert-position/description/) | Easy |

## PATTERN 1
> Standard Binary Search
- CASE 1: Target element is present in array
- CASE 2: Target element is not present in the array 
    - a. `Target < arr[0]: ` left = 0, right = -1
    - b. `Traget > arr[arr.length-1]: ` left = arr.length, right = arr.length-1 
- CASE 3: Target element is not present in the array but `arr[0] < Target < arr[arr.length-1]` 
    - left = element higher than target
    - right = element lower than target

```Java
public class Main {
    public static void main(String[] args) {
        int[] arr = {1,2,3,4,5,6,7,9,10,11};
        int left = 0, right = arr.length-1;
        int target = 12;

        while(left <= right){
            int mid = left + (right-left)/2;
            System.out.println("left:"+left+" right:"+right+" Mid:"+mid+" arr[mid]: "+arr[mid]);

            if(arr[mid] == target){
                break;
            }else if(target > arr[mid]) left = mid+1;
            else{
                right = mid-1;
            }
        }
        /*  Target: 4 (Case 1)
            left:0 right:9 Mid:4 arr[mid]: 5
            left:0 right:3 Mid:1 arr[mid]: 2
            left:2 right:3 Mid:2 arr[mid]: 3
            left:3 right:3 Mid:3 arr[mid]: 4

            Target: 0 (Case 2 a)
            left:0 right:9 Mid:4 arr[mid]: 5
            left:0 right:3 Mid:1 arr[mid]: 2
            left:0 right:0 Mid:0 arr[mid]: 1
            left:0 right:-1 (loop break: left = right+1, left (upper limit), right (lower limit))

            Target: 12 (Case 2 b)
            left:0 right:9 Mid:4 arr[mid]: 5
            left:5 right:9 Mid:7 arr[mid]: 9
            left:8 right:9 Mid:8 arr[mid]: 10
            left:9 right:9 Mid:9 arr[mid]: 11
            left:10 right:9 (loop break: left = right+1, left (upper limit), right (lower limit))

            Target: 8 (Case 3)
            left:0 right:9 Mid:4 arr[mid]: 5
            left:5 right:9 Mid:7 arr[mid]: 9
            left:5 right:6 Mid:5 arr[mid]: 6
            left:6 right:6 Mid:6 arr[mid]: 7
            left:7 right:6 (loop break: left = right+1, left (upper limit), right (lower limit))
        */
    }
}
```

## PATTERN 2
> Lower bound and upper bound of an element

```Java
public class Example{
    public static void main(String[] args){
        int[] arr = {1,2,3,3,3,3,4,5,6};
        int target = 3, left = 0, right = arr.length-1;
        int ans = -1;
        boolean find_lower_bound = true;

        while(left <= right){
            int mid = left + (right-left)/2;
            
            if (arr[mid] == target){
                ans = mid;

                if(find_lower_bound) right=mid-1;
                else left=mid+1;
            }
            else if(target > arr[mid]) left = mid+1;
            else right = mid-1;
        }
        /*
            Target = 3 (Lower bound)
            Left:0 Right:8 Mid:4 Ans = 4
            Left:0 Right:3 Mid:1 Ans = 1
            Left:2 Right:3 Mid:2 Ans = 2
            Left:2 Right: 1 

            Target = 3 (Upper bound)
            Left:0 Right:8 Mid:4 Ans = 4
            Left:5 Right:8 Mid:6 Ans = 6
            Left:5 Right:5 Mid:5 Ans = 5
            Left:6 Right: 5
        */
    }
}
```

## PATTERN 3
> This a specialized case of pattern 2 where you have to minimize your search space based on some condition. The condition or constraint returns `True` from a particular point k in search space otherwise `False`, our goal is to find that smallest point k (similar to finding lower bound of an element).

```Java
public class Example{
    public static void main(String[] args){

        while(left <= right){
            int mid = left + (right-left)/2;
            
            if (condition()){
                ans = mid;
                right = mid-1;
            }
            else left = mid+1;
        }
    }
}
```

## PATTERN 4
> Search in rotated sorted array.
- `arr[left] <= arr[mid]`: Either search in sorted part or shift to unsorted part.
- `arr[mid] <= arr[right]`: Either search in sorted part or shift to unsorted part.
- `arr[left] = arr[mid] = arr[right]`: Trim down the search space.

```Java
public class Example{
    public static void main(String[] args){

        while(left <= right){
            int mid = left + (right-left)/2;
            
            if (left == mid or mid == target){
                // calculate ans
            }
            else if(arr[mid] <= arr[right]){
                // right part is sorted - search or shift (mid or mid-1)
            }
            else{
                // left part is sorted - search or shift (mid or mid+1)
            }
        }
    }
}
```