# Lab-7_202001458
### Name : Kris Patel
### ID : 202001458

# Section A

## Based on the input ranges, we can identify the following equivalence classes: <br>

1. Valid dates: The input triple (day, month, year) that represent a valid date in the Gregorian calendar, such as (3, 4, 1995).
2. Invalid dates: The input triple (day, month, year) that represent an invalid date, such as (31, 2, 2022) or (29, 2, 1900).
3. Out of range dates: The input triple (day, month, year) that are outside the allowed ranges, such as (0, 5, 2010) or (15, 13, 2005).
Based on these equivalence classes, we can design the following test cases:

**Tester Action and Input Data Expected Outcome**<br>

**Valid dates:**<br>
1) Calculate previous date for (15, 10, 2022) 14, 10, 2022
2) Calculate previous date for (1, 1, 2015) 31, 12, 2014
3) Calculate previous date for (31, 3, 2000) 30, 3, 2000

**Invalid dates:**<br>
1) Calculate previous date for (29, 2, 2022) Invalid date
2) Calculate previous date for (31, 4, 2010) Invalid date
3) Calculate previous date for (30, 2, 2000) Invalid date

**Out of range dates:**<br>
1) Calculate previous date for (0, 5, 2010) Invalid date
2) Calculate previous date for (15, 13, 2005) Invalid date
3) Calculate previous date for (31, 12, 1899) Invalid date

Test Cases
| ID | Day | Month | Year| Expected Output |
|----|-----|-------|-----|-----------------|
|  1 | 1   |  5    |2000 | 30-04-2000      |
|  2 | 2   |  2    |2005 | 01-02-2005      |
|  3 | 29  |  2    |2001 | Invalid |
|  4| 1 | 3 | 2001 | 28-2-2001|
|  5| 1 | 3 | 2000 | 29-2-2001|
| 6| 31| 4|2012| Invalid|
| 7| 1| 1| 2000| 31-12-1999|
|8| 31|12|2015| 30-12-2015|
| 9| 30| 4|2016| Invalid|
|10| 1|1|1994|Invalid|

## **Boundary Value Analysis:**<br>
Using boundary value analysis, we can identify the following boundary test cases:
1) The earliest possible date: (1, 1, 1900)
2) The latest possible date: (31, 12, 2015)
3) The earliest day of each month: (1, 1, 2000), (1, 2, 2000), (1, 3, 2000),..., (1, 12, 2000)
4) The latest day of each month: (31, 1, 2000), (28, 2, 2000), (31, 3, 2000),..., (31, 12, 2000)
5) Leap year day: (29, 2, 2000)
6) Invalid leap year day: (29, 2, 1900)
7) One day before earliest date: (31, 12, 1899)
8) One day after latest date: (1, 1, 2016)<br>

Based on these boundary test cases, we can design the following test cases:<br>
Tester Action and Input Data Expected Outcome<br>

**Boundary Test Cases:**<br>
1) Calculate previous date for (1, 1, 1900) Invalid date
2) Calculate previous date for (31, 12, 2015) 30, 12, 2015
3) Calculate previous date for (1, 1, 2000) 31, 12, 1999
4) Calculate previous date for (31, 1, 2000) 30, 1, 2000
5) Calculate previous date for (29, 2, 2000) 28, 2, 2000
6) Calculate previous date for (29, 2, 1900) Invalid date
7) Calculate previous
<br>

### Equivalence Class
Day:<br />
|ID| class | validity |
|--|-------|----------|
|El| dd<1 |Invalid |
|E2 |1<=dd<=28| Valid|
|E3 |dd=31 |Valid |
|E4| dd=29 |Valid |
|ES |dd=30| Valid |
|E6| dd > 31| Invalid |

Month: <br />

|ID| class | validity |
|--|-------|----------|
|E7| mm<1 |Invalid |
|E8 |mm = 1,3,5,7,8,10,12(months with 31 days) | Valid|
|E9 |mm = 4,6,9,11(months with 30 days) |Valid |
|E10|mm = 2(month with either 28 or 29 days) |Valid |
|E11 |mm > 12| Invalid |

Year: <br/>
|ID| class | validity |
|--|-------|----------|
|E12| yy<1900 |Invalid |
|E13 | leap year 1900<=yy<=2015 | Valid|
|E14 |non leap year 1900<=yy<=2015  |Valid |
|E15 |yy > 2015 |Invalid |

<br />

## Program 1:
The function linearSearch searches for a value v in an array of integers a. <br>
If v appears in the array a, then the function returns the first index i, such that a[i] == v; otherwise, -1 is returned.<br>
```
int linearSearch(int v, int a[]){
    int i = 0;
    while (i < a.length){
      if (a[i] == v)
        return(i);
      i++;
    }
    return (-1);
  }
```

| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| [2, 4, 6, 8, 10],v = 2 | 0 |
| [1, 3, 5, 7, 9],v = 2 | -1 |
| [2, 4, 6, 8, 10],v = 11 | -1 |
| [-100, 100] | 0 |
| [1,2,3,4,5,6],v = 6 | 5 |
| [],v = 10 | -1 |
| NULL,v = 111 | -1 |

**Boundary value analysis**
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| NULL | -1 |
| [],v = 5 | -1 |
| [5],v = 5 | 0 |
| [5],v = 60 | -1 |
| [3,5],v = 3 | 0 |
| [3,5],v = 5 | 1 |
| [3,5],v = 14 | -1 |
| [1,3,5],v = 1 | 0 |
| [1,3,5],v = 5 | 2 |
| [1,3,5],v = 10 | -1 |
|[1,2,3,4,5,6,7,8,9,1,0,11,111],v = 1| 0 |
|[1,2,3,4,5,6,7,8,9,1,0,11,111],v = 111| 12 |
|[1,2,3,4,5,6,7,8,9,1,0,11,111],v = 1111| -1 |

<br>

## Program 2:
The function countItem returns the number of times a value v appears in an array of integers a.<br>
```
int countItem(int v, int a[]){
  int count = 0;
  for (int i = 0; i < a.length; i++){
    if (a[i] == v)
    count++;
  }
  return (count);
}
```
**Equivalence Partitioning:**

| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| [265, 41, 60, 80, 100],v = 100 | 1 |
| [2655, 451, 6560, 1050, 1050],v = 1050 | 2 |
| [[265545, 451, 65460, 1050, 105024]],v = 1 | 0 |
| [[10,10,10,10]],v = 11 | 0 |
| [],v = 100 | 0 |
| NULL,v = 51 | 0 |
| [0],v = 0 | 1 |
| [-89,-89],v = -89 | 2 |

**Boundary value analysis**
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| [1, 2, 3, 4],v = 2 | 2 |
| 15, 10, 15, 15],v = 15 | 3 |
| [],v = 100 | 0 |
| NULL,v = 51 | 0 |
|[-100,100,100,100],v = 10000| 0 |
| [-89,89],v = -89 | 1 |
| [-890,890],v = 890 | 1 |

<br>

## Program 3:
The function binarySearch searches for a value v in an ordered array of integers a. <br>
If v appears in the array a, then the function returns an index i, such that a[i] == v; otherwise, -1 is returned.<br>
Assumption: the elements in the array a are sorted in non-decreasing order.<br>
```
int binarySearch(int v, int a[]){
  int lo,mid,hi;
  lo = 0;
  hi = a.length-1;
  while (lo <= hi){
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

**Equivalence Partitioning:**
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| [1, 21, 30, 40, 50],v = 21 | 1 |
| [10, 20, 30, 40, 50, 60],v = 30 | 2 |
| [10,100,1000,10000],v = 100000 | -1 |
| [,11,22,33,44],v = 444 | -1 |
| [11,20,200,300],v=11 | 0 |
| [-100,-90,-80,100,1000],v = 10000 | 4 |
| [],v = 12 | -1 |
| NULL,v = 168 | -1 |
| [1,2],v = 3 | -1 |
| [1,3],v=3 | 1 |

**Boundary value analysis**
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| [1, 2, 3, 4, 5],v = 2 | 1 |
| [1, 2, 2, 351, 551],v = 2 | 2 |
| [1,22,33,44,55],v = 66 | -1 |
| [2, 4, 6, 8, 10],v = 51 | -1 |
| [-100, 0, 1000],v = -100 | 0 |
| [-100, 0, 1000],v = 1000 | 2 |
| [],v=0 | -1 |
| NULL,v = 4 | -1 |
<br>

## Program 4:
P4. The following problem has been adapted from The Art of Software Testing, by G. Myers (1979). <br>
The function triangle takes three integer parameters that are interpreted as the lengths of the sides of a triangle. <br>
It returns whether the triangle is equilateral (three lengths equal), isosceles (two lengths equal), scalene (no lengths equal), or invalid (impossible lengths).<br>
```
final int EQUILATERAL = 0;
final int ISOSCELES = 1;
final int SCALENE = 2;
final int INVALID = 3;
int triangle(int a, int b, int c){
  if (a >= b+c || b >= a+c || c >= a+b)
    return(INVALID);
  if (a == b && b == c)
    return(EQUILATERAL);
  if (a == b || a == c || b == c)
    return(ISOSCELES);
  return(SCALENE);
}
```

**Equivalence Partitioning:**

| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| a=2,b=2,c=2 | EQUILATERAL |
| a=1,b=1,c=1 | EQUILATERAL |
| a=0,b=0,c=0 | INVALID |
| a=-1,b=-1,c=-1 | INVALID |
| a=10,b=10,c=0 | INVALID |
| a=17,b=17,c=5 | ISOCELES |
| a=15,b=2,c=15 | ISOCELES |
| a=6,b=11,c=5 | SCALENE |
| a=16,b=21,c=25 | SCALENE |
| a=-1,b=21,c=25 | INVALID |
| a=2,b=3,c=4 | SCALENE |

**Boundary value analysis**
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| a=2,b=2,c=2 | EQUILATERAL |
| a=0,b=0,c=0 | INVALID |
| a=INT_MAX,b = INT_MAX,c = INT_MAX | EQUILATERAL |
| a=INT_MIN,b=INT_MIN,c=INT_MIN | INVALID |
| a=1,b=1,c=2 | ISOCELES |
| a=15,b=12,c=15 | ISOCELES |
| a = INT_MAX,b = 1,c = INT_MAX | ISOCELES |
| a=1,b=2,c=3 | SCALENE |
| a = INT_MAX,b = 1,c = INT_MAX - 1 | SCALENE |

<br>

## Program 5:
The function prefix (String s1, String s2) returns whether or not the string s1 is a prefix of string s2 (you may assume that neither s1 nor s2 is null).<br>
```
public static boolean prefix(String s1, String s2){
  if (s1.length() > s2.length()){
    return false;
  }
  for (int i = 0; i < s1.length(); i++){
    if (s1.charAt(i) != s2.charAt(i)){
      return false;
    }
  }
  return true;
}
```
**Equivalence Partitioning:**

| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| s1= "abcd",s2 = "abcd" | true |
| s1 = "",s2 = "" | true |
| s1 = "po",s2 = "poojan" | true |
| s1 = "poo",s2 = "po" | false |
| s1 = "abc",s2 = "" | false |
| s1 = "",s2 = "abc" | true |
| s1 = "o",s2 = "ott" | true |
| s1 = "abc",s2 = "def" | false |
| s1 = "deg",s2 = "def" | false |

**Boundary value analysis**
| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| s1= "abcd",s2 = "abcd" | true |
| s1= "",s2 = "" | true |
| s1= "abcd",s2 = "" | false |
| s1= "",s2 = "abcd" | true |
| s1 = "aef",s2 = "def" | false |
| s1 = "def",s2 = "deg" | false |
| s1 = "a",s2 = "att" | true |
| s1 = "poojan",s2 = "patel" | false |

<br>

## Program 6:
Consider again the triangle classification program (P4) with a slightly different specification: <br>
The program reads floating values from the standard input. The three values A, B, and C are interpreted as representing the lengths of the sides of a triangle. <br>
The program then prints a message to the standard output that states whether the triangle, if it can be formed, is scalene, isosceles, equilateral, or right angled.<br>
Determine the following for the above program:<br>
<br>

**a) Identify the equivalence classes for the system<br>**

Equivalence Classes:<br>
| Class ID | Class |
|----------|-------|
| E1 | All sides are positive |
| E2 | two of its sides are zero |
| E3 | One of its sides are negative |
| E4 | Sum of two sides is less than third side |
| E5 | Any of the side/sides is negative |
<br>


**b) Identify test cases to cover the identified equivalence classes. Also, explicitly mention which test case would cover which equivalence class.<br>**
(Hint: you must need to be ensure that the identified set of test cases cover all identified equivalence classes)<br>

Test cases:<br>
| Test Case ID | Class ID | Test Case |
|--------------|----------|-----------|
| T1 | E1 | A = 1,B = 1,C = 1 |
| T2 | E1 | A = 3, B = 4, C= 5 |
| T3 | E2 | A = 0,B = 0,C = 1 |
| T4 | E3 | A = 0,B = 1,C = 2 |
| T5 | E4 | A = 1, B = 3, C = 8 |
| T6 | E5 | A = -1,C = 1,D = 5 |

<br>


**c) For the boundary condition A + B > C case (scalene triangle), identify test cases to verify the boundary.<br>**

Test cases for the boundary condition A + B > C:<br>
TC7 (EC4): A=2, B=3, C=6 (sum of A and B is equal to C)<br>

<br>


**d) For the boundary condition A = C case (isosceles triangle), identify test cases to verify the boundary.<br>**

Test cases for the boundary condition A = C:<br>
TC8 (EC4): A=5, B=6, C=5 (A equals to C)<br>

<br>

**e) For the boundary condition A = B = C case (equilateral triangle), identify test cases to verify the boundary.<br>**

Test cases for the boundary condition A = B = C:<br>
TC9 (EC4): A=1, B=1, C=1 (all sides are equal)<br>

<br>

**f) For the boundary condition A2 + B2 = C2 case (right-angle triangle), identify test cases to verify the boundary.<br>**

Test cases for the boundary condition A^2 + B^2 = C^2:<br>
TC10 (EC4): A=3, B=4, C=5 (right-angled triangle)<br>

<br>

**g) For the non-triangle case, identify test cases to explore the boundary.<br>**

Test cases for the non-triangle case:<br>
TC11 (EC3): A=2, B=2, C=4 (sum of A and B is less than C)<br>

<br>

**h) For non-positive input, identify test points.<br>**

Test points for non-positive input:<br>
TP1 (EC2): A=0, B=4, C=5 (invalid input)<br>
TP2 (EC2): A=-2, B=4, C=5 (invalid input)<br>
Note: Test cases TC1 to TC10 covers all identified equivalence classes.<br>

<br>


![Final](https://user-images.githubusercontent.com/62084382/231538537-89c3769c-1ee2-436b-8f1e-de80bd7ed551.png)
```
package lab_7;
public class unittesting {
public int linearSearch(int v, int a[])
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
public int countItem(int v, int a[])
{
int count = 0;
for (int i = 0; i < a.length; i++)
{
if (a[i] == v)
count++;

}
return count;
}

public int binarySearch(int v, int a[])
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

public static String triangle(int a, int b, int c)
{
if (a >= b+c || b >= a+c || c >= a+b)
return ("Incorrect input");
if (a == b && b == c)
return ("Equal");
if (a == b || a == c || b == c)
return ("Isosceles");
return ("Scalene");
}

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
}
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

# Section B

<h2>Control flow graph of doGraham method</h2>

<img src="https://user-images.githubusercontent.com/96994497/231539242-be401050-1cb2-4cce-93e6-e7ad69197b7b.png" width="661" height="818">

<h2>Statement coverage test cases:</h2> every statement in code is executed at least once

Test 1: p = empty vector

Test 2: p = vector with one point

Test 3: p = vector with two points with the same y component

Test 4: p = vector with two points with different y components

Test 5: p = vector with three or more points with different y components

Test 6: p = vector with three or more points with the same y component

<h2>Branch coverage test sets:</h2> every branch in code is executed at least once

Test 1: p = empty vector

Test 2: p = vector with one point

Test 3: p = vector with two points with the same y component

Test 4: p = vector with two points with different y components

Test 5: p = vector with three or more points with different y components, and none of them have the same x component

Test 6: p = vector with three or more points with the same y component, and some of them have the same x component

Test 7: p = vector with three or more points with the same y component, and all of them have the same x component


<h2>Basic condition coverage test sets:</h2> every boolean expression is executed at least once

Test 1: p = empty vector

Test 2: p = vector with one point

Test 3: p = vector with two points with the same y component, and the first point has a smaller x component

Test 4: p = vector with two points with the same y component, and the second point has a smaller x component

Test 5: p = vector with two points with different y components

Test 6: p = vector with three or more points with different y components, and none of them have the same x component

Test 7: p = vector with three or more points with the same y component, and some of them have the same x component

Test 8: p = vector with three or more points with the same y component, and all of them have the same x component.


<h2>Examples of such test cases</h2>

Test cases :
1) p=[(x=2,y=2),(x=2,y=3),(x=1,y=3),(x=1,y=4)]

2) p=[(x=2,y=3),(x=3,y=4),(x=1,y=2),(x=5,y=6)]

3) p=[(x=1,y=5),(x=2,y=7),(x=3,y=5),(x=4,y=5),(x=5,y=6)] 4) p=[(x=1,y=2)]

4) p=[]

These 5 test cases cover all the tests discussed above.
