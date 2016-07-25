# Ruby 2.3 Features

Courtesy of Nithin Bekal's article at http://nithinbekal.com/posts/ruby-2-3-features/

## Safe Navigation Operator

```ruby
if user && user.admin?
  puts 'This sucks!'
end
```

```ruby
if user&.admin?
  puts 'This is awesome!'
end
```

## Frozen String Literals
```ruby
# frozen_string_literal: true

str = 'cat'
str[0] = 'b'

# frozen.rb:5:in `[]=': can't modify frozen String (RuntimeError)
#   from frozen.rb:5:in `<main>''
```

## Array#dig and Hash#dig

### For Arrays:
```ruby
list = [
  [2, 3],
  [5, 7, 9],
  [ [11, 13], [17, 19] ]
]

list.dig(1, 2)    #=> 9
list.dig(2, 1, 0) #=> 17
list.dig(0, 3)    #=> nil
list.dig(4, 0)    #=> nil
```

### For Hashes:
```ruby
dict = {
  a: { x: 23, y: 29 },
  b: { x: 31, z: 37 }
}

dict.dig(:a, :x) #=> 23
dict.dig(:b, :z) #=> 37
dict.dig(:b, :y) #=> nil
dict.dig(:c, :x) #=> nil
```

## "Did you mean?"

```ruby
```
