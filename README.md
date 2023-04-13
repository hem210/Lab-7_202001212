# Lab-7_202001212

## IT314 - Software Engineering<br />
## Lab 7 - Software Testing<br />
202001212<br />
Hemang Joshi<br />

### Section - A<br />

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

