>[!info] Resources
>https://www.geeksforgeeks.org/python/itertools-in-python3/
>https://www.geeksforgeeks.org/python/python-itertools-cycle/
>https://stackabuse.com/pythons-itertools-count-cycle-and-chain/

Itertools is a module in Python, it is used to iterate over data structures that can be stepped over using a for-loop. 

#### 1. combinations()
`combination(iterable,n-integer)`
It creates all possible combinations of all the values in the iterable. The output will be an itertool object (convert it into list or smthin) where there will be tuples with 'n' elements in them. Basically it creates all subsets possible of iterable and prints only where the subset has n elements in them 

#### 2. combinations_with_replacement()
does the same thing as combination, The difference is that combinations_with_replacement() allows elements to be repeated in the tuples it returns.   

#### 3. permutations() 
https://www.geeksforgeeks.org/python/python-itertools-permutations/
`itertools.permutations(iterable, r)`
Generates all possible ordered arrangements of a given iterable (like a list, string, or tuple)
- ****iterable:**** The sequence (list, string, tuple, etc.) from which permutations are generated.
- ****r (optional):**** The length of the permutation. Defaults to the length of the iterable. If specified, only permutations of this length are generated.

#### 4. chain.from_iterable() "for flattening a list"
Converting a list of lists (2D), into a list (1D) is called flattening. Flattening a list of lists merges all the sublists into one unified list.

#### 5. count() - may go to infinite 
The `count(start, step)` function creates an iterator and is used to generate evenly-spaced values, where the space between them is defined by the `step` argument. The `start` argument defines the starting value of the iterator - and these are set to `start=0` and `step=1` by default.
While zipping, we'd use `count()` to generate values for these indices
```
from itertools import count 
list = ['John', 'Marie', 'Jack', 'Anna'] 
for i in zip(count(), list): 
	print(i)

Result
(0, 'John') 
(1, 'Marie')
(2, 'Jack') 
(3, 'Anna')
```
Can use enumarate function
#### 6. cycle() - may go to infinite
The `cycle()` function accepts an _iterable_ and generates an _iterator_, which contains all of the iterable's elements.
Once we iterate through to the end of the elements, we start iterating through the copies. While iterating through the copies, new copies are made. Once the first set of copies runs out - we iterate through the new set. 
So in a way modular arithmetic (it wraps around)


##### *Difference between ITERATOR AND ITERABLE*
An **iterable** is an object which can be iterated over. When using the `iter()` function, an **iterator** is being generated. Generally speaking, most sequences are iterable, such as _lists_, _tuples_, _strings_, etc.
An **iterator** is also an object, which is used to iterate over an **iterable** and an iterator can also iterate over _itself_. This is done by using the `next()` method, passing in the **iterator** that we're trying to traverse.

The `cycle()` function accepts an _iterable_ and generates an _iterator_, which contains all of the iterable's elements. In addition to these elements, it contains a _copy_ of each element. Once we iterate through to the end of the elements, we start iterating through the copies. While iterating through the copies, new copies are made. Once the first set of copies runs out - we iterate through the new set.
