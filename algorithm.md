* (http://myprogrammingblog.com/2015/01/19/how-to-reverse-a-string-not-using-built-in-reverse-method-how-to-reverse-every-word-in-a-sentence-part1-is-ruby/)
* (https://www.youtube.com/watch?v=OrtQ6LdK0lk)


```ruby
array.delete_at(0)
```

```ruby
array.each_with_index do |val, i| end
```

```ruby
odd?
```

```ruby
array.select { |x| (x[key_1] + x[key_2]).even? }
```

```ruby
array.delete_if{ |x| (x[key_1] + x[key_2]).even? }
```

```ruby
(5..10).reduce(:+)
```

```ruby
numbers.delete_at(numbers.index(numbers.min))
```

```ruby
string.downcase.chars.uniq.size
```

```ruby
(2..n).each do 
	divisors = (2...n).select{|item| n % item == 0}
	divisors.empty? ? "#{n} is prime" : divisors
	(arr[0..-1]).map { |x| x }
	arr.insert(index, val)
```

  - Can you solve using a hash or array
  - Prepare binary search
  - Prepare array sort
  - What is palindrome :. EYE,or RACECAR, or MADAM I'M ADAM. 

```ruby
def reverse(str)
  sum = ''
  i = str.length - 1
  (str.length).times do
    sum += str[i]
    i -= 1
  end
  puts sum

end

reverse("star")
```

```ruby
def isAnagram(str_a, str_b)
  str_list_a = Hash.new(0)
  str_list_b = Hash.new(0)

  str_a.chars.each do |s|
    str_list_a[s] += 1
  end

  str_b.chars.each do |s|
    str_list_b[s] += 1
  end

  return str_list_a == str_list_b
end

isAnagram("star", "rats")
```

```ruby
# Search a sorted array in O(lg(n)) time
def binary_search(array, value, from=0, to=nil)
    if to == nil
        to = array.count - 1
    end

    mid = (from + to) / 2

    if value < array[mid]
        return binary_search array, value, from, mid - 1
    elsif value > array[mid]
        return binary_search array, value, mid + 1, to
    else
        return mid
    end
end
```

```ruby
def bubble_sort(array)
  n = array.length

  loop do
    swapped = false

    (n-1).times do |i|
      if array[i] > array[i+1]
        array[i], array[i+1] = array[i+1], array[i]
        swapped = true
      end
    end

    break if not swapped
  end

  array
end
```

```ruby
def sum_consecutives(e)
  arr = []
  j = 1
  e.each_with_index do |val, i|
    if val == e[i+1]
      j += 1
    else
      arr.push(val * j)
      j = 1
    end
  end
  return arr
end

sum_consecutives([1,4,4,4,0,4,3,3,1]) #,[1,12,0,4,6,1]
sum_consecutives([1,1,7,7,3]) #,[2,14,3]
sum_consecutives([-5,-5,7,7,12,0]) #,[-10,14,12,0]0]
```

```ruby
def solution(n)
  # convert integer to an array of chars
  # arr_count = 8 
  # 3 5 2 3 5 2 3 5
  # 7 6 5 4 3 2 1 0
  # 8 7 6 5 4 3 2 1
  # 8 % 3 = 2
  # i = 3
  # 2.times insert at index (8-i) ","
  # i += 3
  # end
  string_arr = n.to_s.chars
  arr_count = string_arr.count
  return string_arr.join('') if arr_count < 4
  i = 3
  mod = arr_count / i
  mod.times do
    string_arr.insert(arr_count - i, ',') unless arr_count - i == 0
    i += 3
  end
  return string_arr.join('')

end

# puts solution(1) #  ->           "1"
# puts solution(10) #  ->          "10"
# puts solution(100) #  ->         "100"
# puts solution(1000) #  ->       "1,000"
# puts solution(10000) #  ->      "10,000"
# puts solution(100000) #  ->     "100,000"
# puts solution(1000000) #  ->   "1,000,000"
# puts solution(352352353) #  ->  "35,235,235"
# puts solution(3523523588) #  ->  "35,235,235"
# puts solution(3523523577) #  ->  "35,235,235"
```

```ruby
def createPhoneNumber(numbers)
  first = (numbers[0..2]).map { |s| s }
  mid = (numbers[3..5]).map { |s| s }
  last = (numbers[6..9]).map { |s| s }
  str = ''
  str += "(" + first.join('') + ") " + mid.join('') + "-" + last.join('')
  return str
end

createPhoneNumber([1, 2, 3, 4, 5, 6, 7, 8, 9, 0])
```

```ruby
def unique_in_order(iterable)
  # assign check_item = iterable[0]
  # add it to results_array
  # iterate iterable and check if iterable[n] == check_item
  # if so skip
  # if != then add it to results_array and set check_item to new value
  #return results_array
  return [] if iterable == [] || iterable == ''
  check_item = iterable[0]
  results_array = []
  results_array << check_item
  iterable = iterable.chars if iterable.class == String
  
  iterable.each do |i|
    results_array << i if i != check_item
    check_item = i
  end

  return results_array
end

#print unique_in_order('AAAABBBCCDAABBB') # ['A', 'B', 'C', 'D', 'A', 'B']
# print unique_in_order('ABBCcAD')         # ['A', 'B', 'C', 'c', 'A', 'D']
# print unique_in_order([1,2,2,3,3])       # [1,2,3]
# print unique_in_order('')

```

```ruby
def find_missing_numbers(arr)
  # find first number
  # find last number
  # create an empty array
  # create a counter and iterate till last number
  # check each number if not exists in the array add it to array
  # return array
  return [] if arr == []
  full_array = (arr[0]..arr[-1]).map { |x| x }
  result = full_array - arr
  result
end
find_missing_numbers([-3,-2,1,4]) #, [-1,0,2,3])
#find_missing_numbers([-1,0,1,2,3,4]) #, [])
# find_missing_numbers([]) #, [])
# find_missing_numbers([0]) #, [])
# find_missing_numbers([-4,4]) #, [-3,-2,-1,0,1,2,3])
```

```ruby
def list(names)
  # check array count
  # if == 1 return the name
  # if == 2 join by '&'
  # if > 2 join get last item as a variable, pop from array, join array by ',' and concat last item by & ...
  return names[0][:name] if names.count == 1
  return names[0][:name] + ' & ' + names[1][:name] if names.count == 2
  last_name = names[-1][:name]
  names.pop
  names_array = names.map { |n| n[:name]}
  return names_array.join(', ') + ' & ' + last_name
end

# puts list([{name: 'Bart'},{name: 'Lisa'},{name: 'Maggie'},{name: 'Homer'},{name: 'Marge'}])
# puts list([{name: 'Bart'},{name: 'Lisa'}])
# puts list([{name: 'Bart'}])
```

```ruby
def divisors(n)
  divisors = []
  i = 2
  while i < n
    divisors << i if n % i == 0
    i += 1
  end
  if divisors.count == 0
    return "#{n} is prime"
  else
    return divisors
  end
end

# p divisors(15) #, [3,5])
# p divisors(253) #, [11,23])
# p divisors(24) #, [2,3,4,6,8,12])
```

```ruby
def is_isogram2(string)
  return true if string.downcase.chars.uniq.size == string.size
  return false
end


def is_isogram(string)
  s= string.downcase.chars.sort
  i = 0
  until i > s.length - 1
    return false if s[i] == s[i+1]
    i += 1
  end
  return true
  
end
```
