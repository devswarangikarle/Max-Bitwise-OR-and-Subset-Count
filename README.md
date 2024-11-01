# Max-Bitwise-OR-and-Subset-Count

In a distant land, a young adventurer named Arjun bought a magical array called "nums" from a mystical bazaar. Upon returning home, his father gave him two challenging tasks involving this array:
First, Arjun must find the maximum bitwise OR of a subset of integers from the array.
Next, his father asked him to count how many non-empty subsets in the array achieve this maximum bitwise OR.
The second task builds upon the first, and Arjun needs your help to complete both challenges and return the final answer. Can you guide Arjun to solve these tasks and fulfill his father’s challenge?
Note: The bitwise OR of an array is calculated as a[0] OR a[1] OR ... OR a[a.length - 1].

def count_max_or_subsets(nums):
    max_or = 0
    for num in nums:
        max_or |= num  
    
    n = len(nums)
    count = 0

    for mask in range(1, 1 << n):
        current_or = 0
        for i in range(n):
            if mask & (1 << i): 
                current_or |= nums[i]
        
        if current_or == max_or:
            count += 1
    
    return count

n = int(input())             
nums = list(map(int, input().split())) 
print(count_max_or_subsets(nums))        
