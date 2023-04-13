# Lab-7_202001212

## IT314 - Software Engineering<br />
## Lab 7 - Software Testing<br />
202001212<br />
Hemang Joshi<br />

### Section-A<br />

1. Test cases identified using Equivalence Partitioning Method
- Valid Dates: The input triple (day, month, year) which falls in the specified range of input and is correct. 1<=date<=31, 1<=month<=12, 1900<=year<=2015
  Example Test Case: (2, 10, 2006)

- Invalid Dates: The input triple (day, month, year) which does fall in the specified range of input but is incorrect. It also includes the input triple (day, month, year) doesn't fall in the specified range of input.
  Example Test Case: (31, 4, 2004), (34, 1, 2001)
  
  Test cases identified using Boundary Value Analysis Method
- Calculate previous date for (1, 1, 1900) Invalid date
- Calculate previous date for (31, 12, 2015) 30, 12, 2015
- Calculate previous date for (1, 1, 2000) 31, 12, 1999
- Calculate previous date for (31, 1, 2000) 30, 1, 2000
- Calculate previous date for (29, 2, 2000) 28, 2, 2000
- Calculate previous date for (29, 2, 1900) Invalid date

#### Problem 1<br />

```
int linearSearch(int v, int a[])
{
    int i = 0;
    while (i < a.length)
    {
        if (a[i] == v)
        return(i);
        i++;
    }
    return (-1);
}
```

**Equivalence Partitioning**

Tester Action and Input Data | Expected Outcome
--- | ---
v is present in array a | index of v
v is not present in array a | -1

**Boundary Value Analysis**

Tester Action and Input Data | Expected Outcome
--- | ---
array a is empty | -1
v is present at the first index of array a | 0
v is present at the last index of array a | n-1
v is not present in the array a | -1

![image](https://user-images.githubusercontent.com/75677231/231719999-8c525157-af92-4282-ac7b-aab9d74508c1.png)

#### Problem 2<br />

```
int countItem(int v, int a[])
{
    int count = 0;
    for (int i = 0; i < a.length; i++)
    {
        if (a[i] == v)
        count++;

    }
    return (count);
}
```

**Equivalence Partitioning**

Tester Action and Input Data | Expected Outcome
--- | ---
v is present in array a | frequency of v
v is not present in array a | 0

**Boundary Value Analysis**

Tester Action and Input Data | Expected Outcome
--- | ---
array a is empty | 0
v is present at the first index of array a | 1
v is present in array a | frequency of v
v is present at the last index of array a | 1
v is not present in the array a | 0

#### Problem 3<br />

```
int binarySearch(int v, int a[])
{
    int lo,mid,hi;
    lo = 0;
    hi = a.length-1;
    while (lo <= hi)
    {
        mid = (lo+hi)/2;
        if (v == a[mid])
            return (mid);
        else if (v < a[mid])
            hi = mid-1;
        else
            lo = mid+1;

    }
    return(-1);
}
```

**Equivalence Partitioning**

Tester Action and Input Data | Expected Outcome
--- | ---
v is present in array a | index of v
v is not present in array a | -1

**Boundary Value Analysis**

Tester Action and Input Data | Expected Outcome
--- | ---
array a is empty | -1
v is present at the first index of array a | 0
v is present at the last index of array a | n-1
v is not present in the array a | -1

#### Problem 4<br />

```
final int EQUILATERAL = 0;
final int ISOSCELES = 1;
final int SCALENE = 2;
final int INVALID = 3;
int triangle(int a, int b, int c)
{
    if (a >= b+c || b >= a+c || c >= a+b)
    return(INVALID);
    if (a == b && b == c)
        return(EQUILATERAL);
    if (a == b || a == c || b == c)
        return(ISOSCELES);
    return(SCALENE);
}
```

**Equivalence Partitioning**

Tester Action and Input Data | Expected Outcome
--- | ---
a+b<=c | INVALID
a=b=c | EQUILATERAL
a=b<c | ISOSCELES
a<b<c | SCALENE

**Boundary Value Analysis**

Tester Action and Input Data | Expected Outcome
--- | ---
a+b<c | INVALID
a+c<b | INVALID
b+c<a | INVALID
a=b=c | EQUILATERAL
a=b<c | ISOSCELES
a=c<b | ISOSCELES
b=c<a | ISOSCELES
a<b<c | SCALENE

#### Problem 5<br />

```
public static boolean prefix(String s1, String s2)
{
    if (s1.length() > s2.length())
    {
        return false;
    }
    for (int i = 0; i < s1.length(); i++)
    {
        if (s1.charAt(i) != s2.charAt(i))
        {
            return false;
        }
    }
    return true;
}
```

**Equivalence Partitioning**

Tester Action and Input Data | Expected Outcome
--- | ---
Non-empty string s1 is prefix of non-empty string s2 | True
Non-empty string s1 is not a prefix of non-empty string s2 | False

**Boundary Value Analysis**

Tester Action and Input Data | Expected Outcome
--- | ---
Empty strings s1 and s2 | True
Empty string s1 and non-empty string s2 | True
Non-empty string s1 and empty string s2 | False
Non-empty string s1 is longer than string s2 | False

#### Problem 6<br />

a) *Identify the equivalence classes for the system*

- EC1: One or more side lengths is negative or zero. (Invalid)
- EC2: All side lengths are positive and the sum of the lengths of any two sides is less than or equal to the length of the remaining side (Invalid).
- EC3: All side lengths are positive and the sum of the lengths of any two sides is greater than the length of the remaining side (Valid).


b) *Identify test cases to cover the identified equivalence classes. Also, explicitly mention which test case would cover which equivalence class.*

Test cases:
- TC1 (EC1): A=0, B=4, C=5 (invalid input)
- TC2 (EC1): A=-5, B=-5, C=5 (invalid input)
- TC3 (EC2): A=3, B=4, C=8 (invalid input)
- TC4 (EC3): A=3, B=4, C=5 (scalene triangle)
- TC5 (EC3): A=5, B=5, C=5 (equilateral triangle)
- TC6 (EC3): A=5, B=5, C=7 (isosceles triangle)


c) *For the boundary condition A + B > C case (scalene triangle), identify test cases to verify the boundary.*

- TC: A=2, B=3, C=6 (sum of A and B is greater than C)


d) *For the boundary condition A = C case (isosceles triangle), identify test cases to verify the boundary.*

- TC: A=2, B=1, C=2 (A and C take the smallest input possible)
- TC: A=20, B=40, C=20 (valid isosceles triangle)
- TC: A=20, B=41, C=20 (invalid input)


e) *For the boundary condition A = B = C case (equilateral triangle), identify test cases to verify the boundary.*

- TC: A=1, B=1, C=1 (A, B, C take the smallest possible integer input)


f) *For the boundary condition A^2 + B^2 = C^2 case (right-angle triangle), identify test cases to verify the boundary.*

- TC: A=3, B=4, C=5 (right-angled triangle)


g) *For the non-triangle case, identify test cases to explore the boundary.*

- TC: A=2, B=2, C=4 (sum of A and B is equal to C, hence invalid input)
- TC: A=2, B=2, C=3 (sum of A and B is greater than C, hence valid input)


h) *For non-positive input, identify test points.*

Test points for non-positive input:
- TC: A=0, B=4, C=5 (invalid input)
- TC: A=-2, B=4, C=5 (invalid input)


##### Testing Code:
![image](https://user-images.githubusercontent.com/75677231/231823010-6747ecd1-1c84-4eed-ae86-012647248bb7.png)

```
package lab_7;
import static org.junit.Assert.*;
import org.junit.Test;
public class LinaerSearch {
	@Test
	public void test() {
		unittesting obj = new unittesting();
       int[] arr1 = {2, 4, 6, 8, 10};
       int[] arr2 = {-3, 0, 3, 7, 11};
       int[] arr3 = {1, 3, 5, 7, 9};
      
       //assertEquals(2, obj.linearSearch(6, arr1));
       assertEquals(8, obj.linearSearch(3, arr2));
       assertEquals(4, obj.linearSearch(9, arr3));
	}
	
	@Test
	public void test2() {
		unittesting counter = new unittesting();
		int[] arr1 = {1, 2, 4, 4, 5};
		int[] arr2 = {1, 2, 3, 4, 5, 6, 7, 8, 9};
		int[] arr3 = {1, 2, 3, 4, 4, 4, 5, 6, 7, 8, 9};
		int v1 = 4;
		int v2 = 10;
		assertEquals(2, counter.countItem(v1, arr1));
		assertEquals(0, counter.countItem(v2, arr1));
		
	}
	
	@Test
	public void test3() {
		unittesting bs = new unittesting();
		
		int[] arr1 = {1, 3, 5, 7, 9};
		assertEquals(0, bs.binarySearch(1, arr1)); // search for 1 in {1, 3, 5, 7, 9}
		assertEquals(2, bs.binarySearch(5, arr1)); // search for 5 in {1, 3, 5, 7, 9}
		
		int[] arr2 = {2, 4, 6, 8, 10, 12};
		assertEquals(-1, bs.binarySearch(1, arr2)); // search for 1 in {2, 4, 6, 8, 10, 12}
		assertEquals(2, bs.binarySearch(6, arr2)); // search for 6 in {2, 4, 6, 8, 10, 12}
		
	}
	
	 @Test
	  public void testEquilateral() {
	    assertEquals("Equal", unittesting.triangle(3, 3, 3));
	  }
	  @Test
	  public void testIsosceles() {
	    assertEquals("Isosceles", unittesting.triangle(5, 5, 6));
	   
	  }
	  @Test
	  public void testScalene() {
	    assertEquals("Scalene", unittesting.triangle(3, 4, 5));
	  }
	  @Test
	  public void testIncorrectInput() {
	    assertEquals("Incorrect input", unittesting.triangle(1, 2, 3));
	   
	  }
	 
	  @Test
	    public void testPrefix() {
	        String s1 = "hello";
	        String s2 = "hello world";
	        assertTrue(unittesting.prefix(s1, s2));
	       
	        s1 = "abc";
	        s2 = "abcd";
	        assertTrue(unittesting.prefix(s1, s2));
	       
	        s1 = "";
	        s2 = "hello";
	        assertTrue(unittesting.prefix(s1, s2));
	       
	        s1 = "hello";
	        s2 = "hi";
	        assertFalse(unittesting.prefix(s1, s2));
	       
	        s1 = "abc";
	        s2 = "def";
	        assertFalse(unittesting.prefix(s1, s2));
	    }
	 
}
```

### Section-B<br />

1. **Control Flow Diagram**

![image](https://user-images.githubusercontent.com/75677231/231825365-72ca406f-6abb-4a44-9675-930c7b60b30a.png)

2. **Test Sets:**

a) **Statement Coverage**: To achieve statement coverage, we need to make sure that every statement in the code is executed at least once.

* Test 1: p is an empty vector
* Test 2: p is a vector with one point
* Test 3: p is a vector with two points with the same y component
* Test 4: p is a vector with two points with different y components
* Test 5: p is a vector with three or more points with different y components
* Test 6: p is a vector with three or more points with the same y component

b) **Branch Coverage**: To achieve branch coverage, we need to make sure that every possible branch in the code is taken at least once

* Test 1: p is an empty vector
* Test 2: p is a vector with one point
* Test 3: p is a vector with two points with the same y component
* Test 4: p is a vector with two points with different y components
* Test 5: p is a vector with three or more points with different y components, and none of them have the same x component
* Test 6: p is a vector with three or more points with the same y component, and some of them have the same x component
* Test 7: p is a vector with three or more points with the same y component, and all of them have the same x component

c) **Basic condition Coverage**: To achieve basic condition coverage, we need to make sure that every basic condition in the code (i.e., every Boolean subexpression) is evaluated as both true and false at least once

* Test 1: p is an empty vector
* Test 2: p is a vector with one point
* Test 3: p is a vector with two points with the same y component, and the first point has a smaller x component
* Test 4: p is a vector with two points with the same y component, and the second point has a smaller x component
* Test 5: p is a vector with two points with different y components
* Test 6: p is a vector with three or more points with different y components, and none of them have the same x component
* Test 7: p is a vector with three or more points with the same y component, and some of them have the same x component
* Test 8: p is a vector with three or more points with the same y component, and all of them have the same x component.
