# Flattening a Nested List Using an Iterator
## DATE:20.09.2026
## AIM:
To design and implement a class NestedIterator that flattens a nested list of integers such that all integers can be accessed sequentially using an iterator interface (next() and hasNext()).
## Algorithm
1.Start the program.
2.Define an interface-like class NestedInteger that can represent either a single 3.integer or a nested list.
4.Use a stack or recursion to flatten all integers from the nested list into a single list.
5.Store the flattened list and maintain an index to track the current element.
6.Implement next() to return the next integer and hasNext() to check if more integers exist.
7.Test the iterator with a sample nested list.
8.Stop the program. 
  

## Program:
```
/*
Program to find Flattening a Nested List Using an Iterator
Developed by: Rubasri R
RegisterNumber:  212224240139
*/
```
```java
import java.util.*;
    public boolean isInteger() {
        return value != null;
    }

    public Integer getInteger() {
        return value;
    }

    public List<NestedInteger> getList() {
        return list;
    }
}

class NestedIterator implements Iterator<Integer> {
    private List<Integer> flattenedList = new ArrayList<>();
    private int index = 0;

    public NestedIterator(List<NestedInteger> nestedList) {
        flatten(nestedList);
    }

    private void flatten(List<NestedInteger> nestedList) {
        for (NestedInteger ni : nestedList) {
            if (ni.isInteger()) {
                flattenedList.add(ni.getInteger());
            } else {
                flatten(ni.getList());
            }
        }
    }

    public Integer next() {
        return flattenedList.get(index++);
    }

    public boolean hasNext() {
        return index < flattenedList.size();
    }
}

public class FlattenNestedList {
    public static void main(String[] args) {
        List<NestedInteger> nestedList = new ArrayList<>();
        nestedList.add(new NI(1));
        List<NestedInteger> innerList = new ArrayList<>();
        innerList.add(new NI(2));
        innerList.add(new NI(3));
        nestedList.add(new NI(innerList));
        nestedList.add(new NI(4));

        NestedIterator i = new NestedIterator(nestedList);
        System.out.print("Flattened list: ");
        while (i.hasNext()) {
            System.out.print(i.next() + " ");
        }
    }
}
```

## Output:

<img width="1295" height="307" alt="image" src="https://github.com/user-attachments/assets/44049f69-e317-4d77-ad83-25d581493bde" />


## Result:
The NestedIterator class successfully flattens a nested list of integers into a single list and provides sequential access using standard iterator methods.
