# BINARY SEARCH

## QUESTIONS
| Question | Level |
|----------|-------|
| [Koko Eating Bananas (875)](https://leetcode.com/problems/koko-eating-bananas/submissions/2135278243/) | Medium |
| [Capacity to Ship Package within d days (1011)](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/description/) | Medium |
| [First & Last Position (34)](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/) | Medium |

## PATTERNS
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
        /*  Target: 4 (Element is present in the array)
            left:0 right:9 Mid:4 arr[mid]: 5
            left:0 right:3 Mid:1 arr[mid]: 2
            left:2 right:3 Mid:2 arr[mid]: 3
            left:3 right:3 Mid:3 arr[mid]: 4

            Target: 8 (Element is missing)
            left:0 right:9 Mid:4 arr[mid]: 5
            left:5 right:9 Mid:7 arr[mid]: 9
            left:5 right:6 Mid:5 arr[mid]: 6
            left:6 right:6 Mid:6 arr[mid]: 7
            left:7 right:6 (loop break: left = right+1, left (upper limit), right (lower limit))

            Target: 0 (Lower boundary)
            left:0 right:9 Mid:4 arr[mid]: 5
            left:0 right:3 Mid:1 arr[mid]: 2
            left:0 right:0 Mid:0 arr[mid]: 1
            left:0 right:-1 (loop break: left = right+1, left (upper limit), right (lower limit))

            Target: 12 (Upper boundary)
            left:0 right:9 Mid:4 arr[mid]: 5
            left:5 right:9 Mid:7 arr[mid]: 9
            left:8 right:9 Mid:8 arr[mid]: 10
            left:9 right:9 Mid:9 arr[mid]: 11
            left:10 right:9 (loop break: left = right+1, left (upper limit), right (lower limit))
        */
    }
}
```