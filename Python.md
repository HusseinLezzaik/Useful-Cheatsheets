## Pip
```python
$ pip install package_name==required_version
$ pip uninstall package_name
```

## Install via Brew
```python
$ brew install python@3.10
```

## Dunder or Magic Methods
- Double underscore (__) in Python class method names indicates that the method is a `magic method` or `dunder method`
- These are special methods that have a specific meaning to the Python `interpreter`
```python
$ __init__(self) // This is the constructor method for a class.
$ __str__(self) // This method is used to define the string representation of an object.
$ __len__(self) // This method is used to define the length of an object. 
$ __add__(self, other) // This method is used to define the behavior of the + operator when it is used on objects of the class. 
$ __eq__(self, other) // This method is used to define the behavior of the == operator when it is used on objects of the class.
$ __getitem__(self, key) // This method is used to define the behavior of the square brackets [] when they are used to access elements of an object.
```

## Bit Manipulation
```python
$ bin(integer) // returns binary representation
```

## Array
- Split
```python
$ homeTeam, awayTeam = competition // split in 1/2
$ _, currentIntervalEnd = currentInterval // decompose
$ a, b, c = [1, 2, 3] // unpacking
$ array[i], array[j] = array[j], array[i] // swap values
```

- Append
```python
$ result.append(value)
$ arr.insert(index, value)
$ allPairSums[currentSum].append([array[k], array[i]]) // allPairSums is a hash table
$ [[]] // list of elements []
$ arr = [1] * n // array of 1's of size n
$ arr = [i for i in range(5)] 
```

- Pop
```python
$ list.pop(idx) // remove element from list at index idx
```

- Index
```
$ orderIdx = order.index(element) // The index() method returns the position at the first occurrence of the specified value
$ arr[-1] // last element
$ arr[-2] // second last element
```

- Reverse
```python
$ arr.reverse()
$ prime_numbers = [2, 3, 5, 7], prime_numbers.reverse() // output = [7, 5, 3, 2]  - manipulates actual array
$ seq_list = [1, 2, 4, 3, 5], print(list(reversed(seq_list))) // [5, 3, 4, 2, 1] separate object
```

- Slicing
```python
$ string[currentLongest[0]:currentLongest[1]]  // prints characters between two indices
$ array[0:0] // returns an empty list, for any index
$ string[start:stop:step]
$ string[::-1] // entire string in reverse
```

- 2D 
```python
$ arr = [[0] * 4 for i in range(4) ]
$ rowLength = len(array)
$ columnLength = len(array[0])
$ cache = [[ None for j in range(len(two) + 1)] for i in range(len(one) + 1)] // generates 2d matrix
$ sum_matrix = [[0] * n for _ in range(m)]
```

## String
```python
$ s = "abc" // strings are immutable
$ s += "def" // creates a new string
$ print(ord("a")) 
$ reversedString = "", reversedString += string[i] // keep adding strings
$ reversedChars = [], reversedChars.append(string[i]) // append into list 
$ string == "".join(reversedChars) // join array
$ document.count(character) // we can count the character in string document, takes O(n) time
$ a = 97, z = 122 // unicode values for python
$ ord(letter) // returns unicode value
$ chr(letterCode) // returns character corresponding to unicode
$ str(integer) // transforms integer into string
$ string[currentLongest[0]:currentLongest[1]] // prints characters between two indices
$ sortedWord = "".join(sorted(word))
$ txt.split() // takes string as input, returns list where each element is string to filter spaces
$ x = txt.split(", ") // splits using a comma
$ txt = "apple#banana#cherry#orange", x = txt.split("#", 1) // output = ['apple', 'banana#cherry#orange']
$ systems = ['Windows', 'macOS', 'Linux'], systems.reverse() // output = ['Linux, 'macOS', 'Windows']
$ characters = [char for char in string] // generates list of strings to be easier to manipulate
```

## Sort
```python
$ ar.sort() // works with strings
$ arr.sort(reverse=True)
$ arr.sort(key=lambda x: len(x)) // custom sort by length of string
$ array.sort() // sort array in increasing order
$ array.sort(reverse=True)
$ sortedIntervals = sorted(intervals, key=lambda x: x[0]) // sort a list of list according to first element of each pair
$ sortedTasks = sorted(tasks) // sorts tasks and returns it into a new array
```

## For Loop
- Using Index
```python
for i in range(len(nums)):
	print(nums[i])
```

- Without Index
```python
for n in nums:
	print(n)
```

- With Index and Value
```python
for i,n in enumerate(nums):
	print(i,  n)
```

- Loop thru multiple arrays simultaneously with unpacking
```python
$ nums1 = [1, 3, 5]
$ nums2 = [2, 4, 6]
$ for n1, n2 in zip(nums1, nums2):
	print(n1, n2)
```

- Enumerate
```python
$ for idx, competition in enumerate(competitions):
$ for count, value in enumerate(values):
	$  print(count, value)
$ for i, char in enumerate(string)
```

- Example
```python
$ for num in array // iterate through each element
$ for value in array
$ for i in range(len(array)) // iterate thru indexes
$ sortedSquares = [0 for _ in array] // initialize an array of 0s
$ for idx in revered(range(len(array))) // iterate from final element
$ for col in revered(range(startCol, endCol)) // starts from endCol and iterates until startCol
$ for i in range(1, min(len(string), 4))
$ for pair in allPairSums[difference] // Hash Table
```

## While Loop
```python
$ left =0, right=len(array)-1, wfhile (left<right) // two pointers to cover array
```
 
- "break" to exit for/while loops
```python
$ if (condition == True):
$ break
```

- "continue" to skip iterations in for/while loops
```python
$ if (condition == True):
$ continue
``` 
 
## If/Else
```python
$ if currentSum == targetSum
$ if all(num % i != 0 for i in range(2, num)): // checks if all statements are true
$ winningTeam = homeTeam if result == HOME_TEAM_WON else awayTeam
$ if team not in scores // checks if team is not in hash table scores
$ for element in array, if type(element) is list 
$ if idx is None
$ pass statement
```

## HashMap or HashTable or Dictionary
```python
$ nums = {}
$  if potentialMatch in nums
$ nums[num] = true // store keys, to make it easier to find them
$ characterFrequencies[character] = characterFrequencies.get(character, 0) + 1 // get() will loop over dictionary, if character exists it will return 0 otherwise it will return value associated with key character
$ anagrams[sortedWord] = [word]
$ anagrams[sortedWord].append
$ counts = {"x": 0, "y": 0}
$ myMap = {}
$ myMap["alice"] = 88
$ print(myMap)
$ print(len(myMap)) // prints number of keys
$ print(myMap["alice"])
$ myMap = { "alice": 90, "bob": 70}
$ myMap = { i: 2*i for i in range(3) } // Dict Comprehension
$ for key in myMap: // loop thru keys
	print(key, myMap[key])
$ for val in myMap.values(): // loop thru values
	print(val)
$ for key, val in myMap.items(): // loop thru key/value pairs
	print(key, val)
$ HashMap[key] = 1 + HashMap.get(key, 0) // gets value for key, if not exist set default to 0
```

## Set() or HashSet
```python
$ mySet = set() // search in constant time, no duplicates
$ mySet.add(1)
$ mySet.add(2)
$ print(mySet)
$ print(len(mySet))
$ print(1 in mySet) // True
$ print(2 in mySet) // True
$ print(3 in mySet) // False
$ mySet.remove(2)
$ print(2 in mySet)
$ print(set([1, 2, 3])) // list to set
$ mySet = { i for i in range(5) } // set comprehension
$ print(mySet)
$ alreadyCounted = set() // makes it easy to search for values
$ alreadyCounted.add(value) // add new value into set
$ if character in alreadyCounted
```

## Tuple
```python
$ tup = (1, 2, 3) // like array but immutable
$ print(tup)
$ print(tup[0])
$ myMap = { (1,2): 3 } // can be used as key for hash map/set
$ print(myMap[(1,2)])
$ mySet = set()
$ mySet.add((1, 2)) // lists can't be keys
$ print((1, 2) in mySet)
```

## Function
- return statements
```python
$ return isNonDecreasing or isNonIncreasing
$ return // with no statement, this is a way to break outside of a recursive function
```

## Lambda
- `lambda` is a python way to write simple functions on spot, instead of defining them elsewhere. 
- For example if you want to write a function that returns x + 1, using `lambda` in place is good
```python
$ longest = max(odd, even, key = lambda x: x[1] - x[0])
$ sortedIntervals = sorted(intervals, key = lambda x: x[0]) // sort a list of list according to first element of each pair
```
 
## Math
```python
$ import math
$ math.pow(x,y)
$ if (n%i) == 0 // modulus to test for divisibility, returns remainder
$ math.sqrt(x) // square root of number
$ longestPeakLength = max(longestPeakLength, currentPeakLength) // max number b/w pairs
$ length = right - left + 1
$ a // b // divide with integral result (discard remainder)
$ sum(array) // returns sum of each elementf
$ middle = (left + right) // 2
$ float("inf")
$ float("-inf")
$ int(sqrt(x))
```
- print
```python
$ print(5 / 2) // 2.5
$ print( 5 // 2) // 2
$ print(-3 // 2) // rounds to -2
$ print(int(-3 / 2)) // -1
$ print( 10 % 3 ) // 1
$ print(-10 % 3) // 2 
$ print(math.fmod(-10, 3)) // -1
$ print(math.floor(3 / 2 ))) / rounds down
$ print(math.ceil(3 / 2)) // rounds up
$ fave_language = "Python"
$ print("I like coding in " + fave_language + " the most")
```
 
 - set variable to infinity to find smallest variable
```python
$ smallet = float("inf")
```

## Boolean
```python
$ isPeak = array[i-1] < array[i] and array[i] > array[i+1]
$ if not isPeak
$ if not a // checks if array is empty []
```

##  Debug 
```python
$ import pdb // python debugger
$ pdb.set_trace()
$ import code // python library for debugging
$ code.interact(local=locals()) 
```

## Class
```python
$ class MyClass:
$ p1 = Person("John", 36), del p1.age // deletes the property age of object p1
$ del p1 // delete the object
```

## Queue
```python
$ from collections import deque // double sided by default, deque = double ended queue
$ queue = deque()
$ queue.append(1) // appends 1 to queue
$ queue.popleft()
$ queue.appendleft(1)
$ queue.pop() // pops rightmost element
$ q = collections.deque()
$ while len(queue) // while the queue is not empty
$ queue = [tree]
$ queue.pop(0)
$ queue.append(element)
```

## Binary Tree
```python
$ if tree is None // leaf node of binary tree at max n/2
```

## minHeap
```python
$ import heapq // heaps are minHeaps by default in Python
$ minHeap = [] // under the hood are arrays
$ heapq.heappush(minHeap, 3)
$ heapq.heappush(minHeap, 2)
$ heapq.heappush(minHeap, 4)
$ print(minHeap[0]) // min is always at indexx 0
$ while len(minHeap):
	print(heapq.heappop(minHeap)) // prints from smallest to greatest values
```

## maxHeap
```python
$ import heapq
$ maxHeap = [] // no max heaps by default, work around is to use min heap and multiply by -1 when push and pop
$ heapq.heappush(maxHeap, -3)
$ heapq.heappush(maxHeap, -2)
$ heapq.heappush(maxHeap, -4)
$ print( -1 * maxHeap[0] ) // max is always at index 0
$ while len(maxHeap):
	print( -1 * heapq.heappop(maxHeap))

$ arr = [2, 1, 8, 4, 5] // build heap from initial values
$ heapq.heapify(arr) // takes O(n) if all values available, else O(nlogn)
$ while arr:
	print(heapq.heappop(arr))
$ nums =[1,2,3]
$ import heapq
$ heapq.heapify(nums) // O(n) time
$ var = None // None is Null in python
```
