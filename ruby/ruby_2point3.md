# Ruby 2.3 Features

Courtesy of many reference articles:
- Nithin Bekal's article at
  http://nithinbekal.com/posts/ruby-2-3-features/
- Alexis Mas's article on immutable strings at
  https://wyeworks.com/blog/2015/12/1/immutable-strings-in-ruby-2-dot-3

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

### Inline Comments:

```ruby
# frozen_string_literal: true

str = 'cat'
str[0] = 'b'

# frozen.rb:5:in `[]=': can't modify frozen String (RuntimeError)
#   from frozen.rb:5:in `<main>''
```

### Global Flags when running your app:

```ruby
--enable-frozen-string-literal

--disable-frozen-string-literal
```

### Debugging Flag

```ruby
--debug-frozen-string-literal
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
2.3.0-preview1 :001 > "foo bar".uppcase
NoMethodError: undefined method `uppcase' for "foo bar":String
Did you mean?  upcase
               upcase!`
```

## Hash “comparison”

```ruby
{ x: 1, y: 2 } >= { x: 1 } #=> true
{ x: 1, y: 2 } >= { x: 2 } #=> false
{ x: 1 } >= { x: 1, y: 2 } #=> false
```

## Hash#to_proc

```ruby
h = { foo: 1, bar: 2, baz: 3}
p = h.to_proc

p.call(:foo)  #=> 1
p.call(:bar)  #=> 2
p.call(:quux) #=> nil
```

```ruby
h = { foo: 1, bar: 2, baz: 3}

# instead of this:
[:foo, :bar].map { |key| h[key] } #=> [1, 2]

# we can use this syntax:
[:foo, :bar].map(&h) #=> [1, 2]
```

## Hash#fetch_values

```ruby
h = { foo: 1, bar: 2, baz: 3}
h.fetch_values(:foo, :bar) #=> [1, 2]

h.values_at(:foo, :quux)    #=> [1, nil]
h.fetch_values(:foo, :quux) #=> raise KeyError
```

## Enumerable#grep_v

```ruby
list = %w(foo bar baz)

list.grep_v(/ba/)
#=> ['foo']

list.grep(/ba/)
#=> ['bar', 'baz']
```

## Numeric#positive? and #negative?

```ruby
1.positive? #=> true
1.negative? #=> false

-1.positive? #=> false
-1.negative? #=> true
```
