# デフォルト引数と名前付き引数

メソッドの引数にはデフォルト値を設定することができます。デフォルト値のある引数を複数指定することもできますが、「1. デフォルト値のない引数」そして「2. デフォルト値のある引数」の順序でのみ指定可能です。

```crystal
class Person
  def become_older(by = 1)
    @age += by
  end
end

john = Person.new "John"
john.age #=> 0

john.become_older
john.age #=> 1

john.become_older 2
john.age #=> 3
```

デフォルト値を設定した引数に対して、メソッドの実行時にその名前を指定することができます。

```crystal
john.become_older by: 5
```

メソッドがデフォルト引数を複数持つときには、メソッド実行時の引数の順序に関係なく、指定した名前の引数として渡されます。また、引数を省略することも可能です。

```crystal
def some_method(x, y = 1, z = 2, w = 3)
  # do something...
end

some_method 10 # x = 10, y = 1, z = 2, w = 3
some_method 10, z: 10 # x = 10, y = 1, z = 10, w = 3
some_method 10, w: 1, y: 2, z: 3 # x = 10, y = 2, z = 3, w = 1
```

上記において、`x` はデフォルト値を持たないため、その名前を指定することができないことに注意してください。

このように、デフォルト引数と名前付き引数には密接な関係があります。つまり、デフォルト引数を指定した場合、同事に呼び出し側がその名前で引数を指定できるようになるということです。引数には良い名前をつけるよう心がけましょう。