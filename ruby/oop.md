# Object Oriented Design Tips

## Class and Method Arguments

Classes and method arguments add dependancies to your object. Not only are
dependancies added via the arguments themselves, an ordered list passed through
adds dependancy on the order the objects take in and make it unclear in the code
what the values passed through represent. Also, this makes the class difficult
to change because order must be preserved to ensure code does not break. An
example or the order args is below.

```
class Bicycle
  def initialize(size, gender, color)
  @size = size
  @gender = gender
  @color = color
  end
end
```

To help solve this problem, you can pass hash argument, and use key / value
pairs to declare your instance variables. That way, you can easily add to the
class without fear of maintaining the order dependancy, was well as, provide
clarity on instantiation of the class to what the values actually represent.

```
class Bicycle
  def initialize(args)
  @size = args[:size]
  @gender = args[:gender]
  @color = args[:color]
  end
end
```
