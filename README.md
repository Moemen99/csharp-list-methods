# C# List Methods

This repository provides an overview of commonly used methods for the `List<T>` class in C#. We'll focus on methods that can be called directly on a `List<T>` object, including both instance methods and extension methods.

## Table of Contents
- [Creating a List](#creating-a-list)
- [Add](#add-)
- [AddRange](#addrange-)
- [BinarySearch](#binarysearch-)
- [Clear](#clear-)
- [Contains](#contains-)
- [CopyTo](#copyto-)
- [EnsureCapacity](#ensurecapacity)
- [TrimExcess](#trimexcess)
- [Equals](#equals)
- [Exists, Find, FindAll](#exists-find-findall-)
- [FindIndex, FindLast, FindLastIndex](#findindex-findlast-findlastindex)
- [ForEach](#foreach)
- [GetRange](#getrange)
- [IndexOf and LastIndexOf](#indexof-and-lastindexof)
- [Insert and InsertRange](#insert-and-insertrange)
- [Remove, RemoveAt, RemoveRange](#remove-removeat-removerange)
- [RemoveAll](#removeall)
- [Reverse](#reverse)
- [Sort](#sort)
- [ToArray](#toarray)
- [Object Methods](#object-methods)

## Creating a List

Let's start with a simple `List<int>` that we'll use for our examples:

```csharp
List<int> numbers = new List<int>() { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
```

## Add ⭐

The `Add` method is used to add an item to the end of the list.

```csharp
numbers.Add(11);
// numbers is now { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11 }
```

## AddRange ⭐

`AddRange` takes a collection and adds all its elements to the end of the list.

```csharp
numbers.AddRange(new int[] { 12, 13, 14 });
// numbers is now { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14 }
```

## BinarySearch

`BinarySearch` searches a sorted list for a specific element and returns the index of the element if found.

```csharp
List<int> sortedNumbers = new List<int>() { 2, 4, 6, 8, 10, 12, 14, 16, 18, 20 };
int index = sortedNumbers.BinarySearch(12);
Console.WriteLine($"Index of 12: {index}"); // Output: Index of 12: 5
```

## Clear ⭐

The `Clear` method removes all elements from the list.

```csharp
numbers.Clear();
Console.WriteLine($"Count: {numbers.Count}, Capacity: {numbers.Capacity}");
// Output: Count: 0, Capacity: 16
```

## Contains ⭐

`Contains` checks if an item is in the list and returns a boolean.

```csharp
bool hasThree = numbers.Contains(3);
Console.WriteLine($"List contains 3: {hasThree}");
```

## CopyTo

`CopyTo` copies elements from the list to an array. It has several overloads:

```csharp
int[] array = new int[numbers.Count];
numbers.CopyTo(array);
// array now contains all elements from numbers
```

## EnsureCapacity

`EnsureCapacity` ensures that the list has at least the specified capacity.

```csharp
numbers.EnsureCapacity(20);
Console.WriteLine($"Capacity after EnsureCapacity(20): {numbers.Capacity}");
// Output: Capacity after EnsureCapacity(20): 32 (doubles the previous capacity of 16)
```

## TrimExcess

`TrimExcess` trims the excess capacity to minimize the memory footprint.

```csharp
numbers.TrimExcess();
Console.WriteLine($"Capacity after TrimExcess: {numbers.Capacity}");
// Output will depend on the current count of the list
```

## Equals

`Equals` compares two list addresses unless overridden.

```csharp
List<int> numbers2 = new List<int>() { 1, 2, 3, 4, 5 };
bool areEqual = numbers.Equals(numbers2);
Console.WriteLine($"Lists are equal: {areEqual}");
// Output: Lists are equal: False (comparing references, not contents)
```

## Exists, Find, FindAll ⭐

These methods use delegates (predicates) to search the list:

```csharp
bool hasMultipleOfThree = numbers.Exists(n => n % 3 == 0);
// Returns true if any number is divisible by 3

int firstMultipleOfThree = numbers.Find(n => n % 3 == 0);
// Returns the first number divisible by 3

List<int> allMultiplesOfThree = numbers.FindAll(n => n % 3 == 0);
// Returns a new list with all numbers divisible by 3
```

## FindIndex, FindLast, FindLastIndex

These methods find the index of elements that match a predicate:

```csharp
int indexOfFirstEven = numbers.FindIndex(n => n % 2 == 0);
// Returns the index of the first even number

int lastEven = numbers.FindLast(n => n % 2 == 0);
// Returns the last even number

int indexOfLastEven = numbers.FindLastIndex(n => n % 2 == 0);
// Returns the index of the last even number
```

## ForEach

`ForEach` performs an action on each element of the list:

```csharp
numbers.ForEach(n => Console.Write(n + " "));
// Prints all numbers in the list
```

## GetRange

`GetRange` returns a new list containing a specified range of elements:

```csharp
List<int> subList = numbers.GetRange(2, 3);
// subList contains { 3, 4, 5 } (starting at index 2, taking 3 elements)
```

## IndexOf and LastIndexOf

These methods find the index of a specific item:

```csharp
int indexOfFive = numbers.IndexOf(5);
// Returns the index of the first occurrence of 5

int lastIndexOfFive = numbers.LastIndexOf(5);
// Returns the index of the last occurrence of 5
```

## Insert and InsertRange

These methods insert elements at a specific position:

```csharp
numbers.Insert(2, 100);
// Inserts 100 at index 2

numbers.InsertRange(3, new int[] { 101, 102 });
// Inserts 101 and 102 starting at index 3
```

## Remove, RemoveAt, RemoveRange

These methods remove elements from the list:

```csharp
numbers.Remove(5);
// Removes the first occurrence of 5

numbers.RemoveAt(0);
// Removes the element at index 0

numbers.RemoveRange(1, 3);
// Removes 3 elements starting at index 1
```

## RemoveAll

`RemoveAll` removes all elements that match a predicate:

```csharp
int removedCount = numbers.RemoveAll(x => x % 2 == 1);
Console.WriteLine($"Removed {removedCount} odd numbers");
// Removes all odd numbers from the list
```

## Reverse

`Reverse` reverses the order of elements in the list:

```csharp
numbers.Reverse();
// Reverses the order of all elements in the list
```

## Sort

`Sort` sorts the elements in the list:

```csharp
numbers.Sort();
// Sorts the list in ascending order
```

## ToArray

`ToArray` creates an array from the list:

```csharp
int[] arrayFromList = numbers.ToArray();
// Creates a new array containing all elements from the list
```

## Object Methods

These are inherited from the `Object` class:

```csharp
Type listType = numbers.GetType();
// Gets the Type of the list

bool isEqual = numbers.Equals(numbers2);
// Compares references (unless overridden)

string listString = numbers.ToString();
// Returns a string representation of the list

int hashCode = numbers.GetHashCode();
// Gets the hash code for the list
```

This README provides an overview of common `List<T>` methods in C#. Each method is accompanied by a brief explanation and example usage. The ⭐ symbol indicates methods that are most commonly used.

Remember to always refer to the official [Microsoft documentation](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1) for the most up-to-date and comprehensive information on `List<T>` methods.
