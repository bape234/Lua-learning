# LUA Language

## Comments
```lua
-- comment
-- [[multi line comment]]
```
## Output
```lua
io.write("string", 5, 4, "string", 3 ) -->"string54string3"
print("that ".."what") --> "das was"
```
## String
```lua
name = "🅱️eter"
multiline = [[multiline string]]
longString = name .. multiline
string.format("Pi = %.10f", math.pi) --> Pi = 3.1415926535
string.len(name) --> returns length of string
#name--> returns length of string
string.gsub(name, "p", "me") --> Replaces every p with me in name
string.find(name, "p") --> 1, finds the first index of the searched term
string.upper(name) --> "PETER"
string.lower(name) --> "peter"
string.gmatch(name, "e") --> returns every match it finds in the string
```
## Number
```lua
bigNum = 9223372036854775807 --> Biggest number possible in LUA
precision of up to 13 decimals
number = number + 1 --> Increment
```
## Boolean
isAble = true

## Nil
Everything is nil if it is not defined

## Table
### Description
Tables are key value paired list, can be used to create arrays, lists, and even used to implement OOP
 
Loops in LUA always start at index 1.
So every table starts at index 1. You don’t have to follow this convention, it is possible to write onto the index 0. But it is recommended to use 1 as starting index.

### Example
```lua
myTable = {}
#myTable -->  Number of items
 
for i = 1, 10 do 
 myTable[i] = i
end
 
-- same as
myTable = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 }
 
-- same as
myTable = { [1]=1, [2]=2, [3]=3, [4]=4, [5]=5, [6]=6, [7]=7, [8]=8, [9]=9, [10]=10 }
 
print(myTable[1]) --> 1
table.insert(myTable, 1, 0)
print(myTable[1]) --> 0
 
print(table.concat(myTable, ", "))
 
table.remove(myTable, 1)
print(table.concat(myTable, ", "))
```
## Type conversion
```lua
string --> tostring(variable)
number --> tonumber(variable)
table --> table.concat(variabel, ", ")
```
## Relational Operators
### Description
greater than >  
smaller than <  
same or greater >=  
same or smaller <=  
same == br  
not same ~=  

### Example
```lua
age = 13
if age < 16 then
 print("you cant go to school")
 local localVar = 10
elseif (age <= 16) and (age < 18) then
 print("you cant drive")
else
 print("you can vote")
end
```
## Logical Operators
and, or, not
```lua
age = 13
if (age < 14) or (age > 67) then print("you shouldnt work")
print(string.format("not true = %s", tostring(not true)))
```
## Local

### Description
local Variables are only accessible where defined

### Example
```lua
function myFunc () 
 local myLocal = "local"
end
 
print(myLocal) --> nil
```
## Math

### Description
5+3 --> 8  
5-3 --> 2  
5*3 --> 15  
5/3 --> 1.66666666666667  
5%3 --> 2

### Example
floor, ceil, max, min, sin, cos, tan, asin, acos, exp, log, log10, pow, sqrt, random, randomseed

## Random numbers
```lua
math.random() -- number between 0 and 1
math.random(10) -- number between 1 and 10
math.random(5, 100) -- number between 5 and 100
math.randomseed(os.time()) -- good random value
```
## Ternary operator
```lua
person = "hans"
 
evaluation = person == "hans" and "joe" or "mike"
print(jan) --> "joe"
 
evaluation = person == "michael" and "joe" or "mike"
print(jan) --> "mike"
```
## Type checking
```lua
type(variable) --> returns type
```
## Looping
```lua
i = 1
 
-- Asks first before executing code
while (i <= 10) do 
 print(i)
 i = i + 1
 
 if i == 8 then 
  break 
 end
end
 
-- Executes the code first before it asks
repeat
 print("Enter your guess : ")
 guess = io.read() 
until tonumber(guess) == 15
 
 
 
-- for loops, start at 1 go until 10, increment each time with 1
 
for i = 1, 10, 1 do
 print(i)
end
 
-- loop over tables
months = { "Jan", "Feb", "Mar", "Apr", "Jun", "Jul", "Aug", "Sep", "Oct", "Dec"}
 
for key, month in pairs(months) do
 print(month)
end
```
## Multi table
### Description
Nested Arrays, nested tables. These can be used as a representation of objects or more complex structures and not just tables.

### Example
```lua
aMultiTable = { }
 
for i = 0, 9 do
 aMultiTable[i] = {}
 for j = 0, 9 do
  aMultiTable[i][j] = tostring(i) .. tostring(j)
 end
end
 
print("Table[1][2] : ", aMultiTable[1][2], "\n")
 
for key, value in pairs(aMultiTable) do
  print("Key " .. key)
  for scndKey, scndValue in pairs(value) do
    print("Value " .. scndValue)
  end
end 
```
## Functions
### Description
In LUA you define functions by using the keyword "function" followed by the name of the function and the parameters. Closing it with an end is necessary. Functions can return Values, more than 1 or 2. If you know the exact amount of returning values, you can prepare the variables to hold the value. But if there are dynamically values that are getting returned you will have to look into the next block -> dynamic return functions
 
In the example I used an regular expression, it makes it easier to filter for specific rules. Just like Phone numbers or other such things.

### Example
```lua
function getSum(num1, num2)
 return num1 + num2
end
 
print(string.format("5 + 2 = ".. getSum(5,2)))
 
function splitStr(theString)
 stringTable = {}
 local i = 1
 for word in string.gmatch(theString, "[^%s]+") do
  stringTable[i] = word
  i = i + 1
 end
 
 return stringTable, i 
end
 
splitStrTable, numOfStr = splitStr("The Turtle")
 
for j = 1, numOfStr - 1 do
 print(string.format("%d : %s", j, splitStrTable[j]))
end
 ```
## Input/Output
### Description
There are some crucial commands for the io library:  
io.close([file])  
io.flush()  
io.lines([filename])  
io.output([file])  
using the standard library and standard in and out, the files get closed automatically when you iterate over them with a for loop, so you don't have to manually call file.close()


### Example
```lua
result, errmsg, errcode = io.lines("code.a51")

if (result ~= nil) then
  for line in result do
    print(line)
  end
end
```
