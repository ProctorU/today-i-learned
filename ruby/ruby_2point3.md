# Ruby 2.3 Features

Courtesy of Nithin Bekal's article at http://nithinbekal.com/posts/ruby-2-3-features/

## Safe Navigation Operator
```ruby
```

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
