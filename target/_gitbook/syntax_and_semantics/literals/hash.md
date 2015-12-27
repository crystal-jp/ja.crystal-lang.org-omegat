# ハッシュ (Hash)

ハッシュ ([Hash](http://crystal-lang.org/api/Hash.html)) は、`K` 型のキーと `V` 型の値のマッピングを表現するための型です。通常、以下のハッシュリテラルを利用して書きます。

```crystal
{1 => 2, 3 => 4}     # Hash(Int32, Int32)
{1 => 2, 'a' => 3}   # Hash(Int32 | Char, Int32)
```

ハッシュは異なる型を持つことが可能です。これは `K`/`V` それぞれが複数の型の組み合わせ (ユニオン型) となることを意味しています。ただ、それらの型はハッシュが作られたときに決定されます。つまり、ハッシュの生成時に明示的に指定された `K` と `T` か、ハッシュリテラルで生成した場合であれば、リテラルのキーと値それぞれの型の組み合わせによって型が決まります。

空のハッシュを作りたいときには、必ず `K` と `V` を指定しなければなりません。

```crystal
{} of Int32 => Int32 # Hash(Int32, Int32).new と同じ
{}                   # シンタックスエラーになる
```

## キーがシンボルのハッシュ

キーがシンボルである場合は、以下の特別な記法を使うことができます。

```crystal
{key1: 'a', key2: 'b'} # Hash(Symbol, Char)
```

## キーが文字列のハッシュ

キーが文字列である場合は、以下の特別な記法を使うことができます。

```crystal
{"key1": 'a', "key2": 'b'} # Hash(String, Char)
```

## ハッシュライクな型

ハッシュが持つ特別なシンタックスを他の型で使うこともできます。ただし、引数のない `new` と `[]=` メソッドが定義されている必要があります。

```crystal
MyType{"foo": "bar"}
```

もし `MyType` がジェネリック型でない場合は、上記は以下と同じ意味です。

```crystal
tmp = MyType.new
tmp["foo"] = "bar"
tmp
```

もし `MyType` がジェネリック型である場合は、上記は以下と同じ意味です。

```crystal
tmp = MyType(typeof("foo"), typeof("bar")).new
tmp["foo"] = "bar"
tmp
```

ジェネリック型である場合には、型引数を指定することも可能です。

```crystal
MyType(String, String) {"foo": "bar"}
```