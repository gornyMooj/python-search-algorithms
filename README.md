# python-search-algorithms
The very basic search algorithm that is using 'for loop' to find an element. It is more efficient because it stops iterating when finds the element. <br/>
The requirement is to use it with sorted lists.


```python
import random

n, x, y = 11, 1, 11


def create_random_list(n,x,y):

    my_list = [random.randint(x,y) for i in range(n)]
    return my_list


my_list = create_random_list(n,x,y)
print("Random list\n", my_list)


random_number = random.randint(x,y )

def insertion_sorrt(my_list, random_number):
    lst = list(my_list)
    for i in range(1, len(lst)):
        for j in range(i, 0, -1):
            if lst[j] < lst[j - 1]:
                lst[j], lst[j - 1] = lst[j - 1], lst[j]
            else:
                break

    print("Sorted list\n",lst)

    num_checked = []
    for e in lst:
        num_checked.append(str(e))
        if e == random_number:
            print("Numbers checked: ",",".join(num_checked))
            return True
        elif e > random_number:
            print(",".join(num_checked))
            return False

    print(",".join(num_checked))
    return False

print(f"List contains {random_number} => {insertion_sorrt(my_list, random_number)}")

```

<br/>
**Binary Search Algorithm**
<br/>
It is also to be used with sorted lists. 

```python
import random

n,x,y = 15,1,15

def create_random_list(n,x,y):

    my_list = [random.randint(x,y) for i in range(n)]
    return my_list


my_list = create_random_list(n,x,y)
random_number = random.randint(x, y)
print("Random list\n", my_list)
print("random_number: ",random_number)

def insterion_sort(my_list):

    for i in range(1, len(my_list)):
        for j in range(i, 0, -1):
            if my_list[j] < my_list[j - 1]:
                my_list[j], my_list[j - 1] = my_list[j - 1], my_list[j]
            else:
                break

    return my_list


my_list = insterion_sort(my_list)
print("Sorted list\n",my_list)


def binary_search(my_list,random_number):
    low = counter = 0
    high = len(my_list) - 1

    while low <= high:
        counter += 1
        mid = (low + high)//2
        if my_list[mid] == random_number:
            return True, counter
        else:
            if random_number > my_list[mid]:
                low = mid + 1
            elif random_number < my_list[mid]:
                high = mid - 1

    return False, counter


print(binary_search(my_list,random_number))

```

<br/>
**Binary Search Algorithm - recursive implementation**


```python
import random

n,x,y = 15,1,15

def create_random_list(n,x,y):

    my_list = [random.randint(x,y) for i in range(n)]
    return my_list


my_list = create_random_list(n,x,y)
random_number = random.randint(x, y)
print("Random list\n", my_list)
print("random_number: ",random_number)

def insterion_sort(my_list):

    for i in range(1, len(my_list)):
        for j in range(i, 0, -1):
            if my_list[j] < my_list[j - 1]:
                my_list[j], my_list[j - 1] = my_list[j - 1], my_list[j]
            else:
                break

    return my_list



def recursive_binary_search_internal(my_list, random_number, low, high):
    if low <= high:
        mid = (low + high) // 2
        if my_list[mid] == random_number:
            return True
        else:
            if random_number > my_list[mid]:
                return recursive_binary_search_internal(my_list, random_number, mid + 1, high)
            elif random_number < my_list[mid]:
                return recursive_binary_search_internal(my_list, random_number, low, mid - 1)
    else:
        return False


def recursive_binary_search(my_list, random_number):
    return recursive_binary_search_internal(my_list, random_number, 0, len(my_list) -1)


my_list = insterion_sort(my_list)
print("Sorted list\n",my_list)

print(f"Sorted list contains {random_number}:  {recursive_binary_search(my_list, random_number)}" )
```
