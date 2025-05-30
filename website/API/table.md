These are Lua functions defined in the `table` namespace:

## table.concat(table, sep?, i?, j?)
Concatenates the elements of a table into a string using a separator.

Example:
```lua
local fruits = {"apple", "banana", "orange"}
print(table.concat(fruits, ", "))  -- prints: apple, banana, orange
print(table.concat(fruits, "", 1, 2))  -- prints: applebanana
```

## table.insert(table, pos, value)
## table.insert(table, value)
Inserts a value into a table at the specified position, shifting elements up. If position is not provided, appends the value at the end of the table.

Example:
```lua
local fruits = {"apple", "orange"}
table.insert(fruits, "banana")  -- appends at end
print(table.concat(fruits, ", "))  -- prints: apple, orange, banana

table.insert(fruits, 2, "grape")  -- inserts at position 2
print(table.concat(fruits, ", "))  -- prints: apple, grape, orange, banana
```

## table.remove(table, pos?)
Removes an element from a table at the specified position, shifting elements down. If position is not provided, removes the last element.

Example:
```lua
local fruits = {"apple", "grape", "orange", "banana"}
table.remove(fruits, 2)  -- removes "grape"
print(table.concat(fruits, ", "))  -- prints: apple, orange, banana

table.remove(fruits)  -- removes last element
print(table.concat(fruits, ", "))  -- prints: apple, orange
```

## table.sort(table, comp?)
Sorts a table in-place using the optional comparison function. Without a comparison function, sorts in ascending order.

Example:
```lua
local numbers = {3, 1, 4, 1, 5, 9}
table.sort(numbers)  -- ascending order
print(table.concat(numbers, ", "))  -- prints: 1, 1, 3, 4, 5, 9

-- Custom comparison (descending order)
table.sort(numbers, function(a, b) return a > b end)
print(table.concat(numbers, ", "))  -- prints: 9, 5, 4, 3, 1, 1
```

## table.keys(table)
Returns an array containing all the keys in the table.

Example:
```lua
local person = {name = "John", age = 30, city = "New York"}
local keys = table.keys(person)
print(table.concat(keys, ", "))  -- prints: name, age, city
```

## table.includes(table, value)
Checks if a list-table contains a specific value.

Example:
```lua
local fruits = {"apple", "banana", "orange"}
print(table.includes(fruits, "banana"))  -- prints: true
print(table.includes(fruits, "grape"))   -- prints: false
```

## table.pack(...)
Creates a new table with the given arguments. The resulting table has all arguments stored at integer keys starting with 1, and a field "n" with the total number of arguments.

Example:
```lua
local args = table.pack("apple", "banana", "orange")
print(args[1], args[2], args[3])  -- prints: apple banana orange
print(args.n)  -- prints: 3
```

## table.unpack(table, i?, j?)
Returns all elements from the table as separate values. The optional `i` and `j` parameters specify the range of elements to return (defaults to 1 and the table length).

Example:
```lua
local fruits = {"apple", "banana", "orange"}
local a, b, c = table.unpack(fruits)
print(a, b, c)  -- prints: apple banana orange

-- With range specification
local x, y = table.unpack(fruits, 2, 3)
print(x, y)  -- prints: banana orange
```

# Non-standard functions
## table.find(table, criteriaFn, fromIndex?)
Finds an element in a table that matches a criteria function. Returns a Lua multi value of index and first element or nil if no element is found.

Example:
```lua
local numbers = {1, 2, 3, 4, 5}
local _, firstEven = table.find(numbers, function(n) return n % 2 == 0 end)
print(firstEven)  -- prints: 2

-- With fromIndex parameter
local _, firstEvenAfter3 = table.find(numbers, function(n) return n % 2 == 0 end, 3)
print(firstEvenAfter3)  -- prints: 4

-- No match case
local result = table.find(numbers, function(n) return n > 10 end)
print(result)  -- prints: nil
```
