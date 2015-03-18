When we program we write code that deals with data in memory. So there must be basic data types, that compiler can recognize.

`@todo` Reserve this in special `azoth.core` package of lang.

These are basic primitive types:
* `int8  | uint8`
* `int16 | uint16`
* `int32 | uint32`
* `int64 | uint64`
* `fp32`
* `fp64`

For conveniense and readability there are basic alias-types:
* `int = int32`
* `float = fp32`
* `double = fp64`
* `char = uint8`
* `char16 = uint16`
* `char32 = uint32`

As we target system programming there are platform specific basic alias-types:
* `wchar` = system char type (e.g. on Windows = `char16`, on linux = `char32`)
* `word` = CPU word
* `dword` = CPU double word

There is also boolean type that can be packed in one underlying basic type if multiple boolean vars are declared near each other:
* `bool = uint8` (can store up to 8 booleans in same `uint8`)
* `wbool = word` (more performance variant, can store up to `bitsizeof(word)` booleans)