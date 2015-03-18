## Literals
Specification defines this literals:
* `42` = `int` family
* `42.2` = `fp64`
* `42.2f` = `fp32`
* `0xFFAA` = `int` family
* `0b110011` = `int` family
* `0o7234` = `int` family
* `"text"` = `char[]`
* `u16"text"` = `char16[]`
* `u32"text"` = `char32[]`
* `w"text"` = `wchar[]`

## Declaring types
`azoth.core` spec package defines such syntax to define user data types:

```
type my_struct:  
    int32 a  
    word b  
    bool c  
    bool d  
    float e
```

When generating equivalent C code this text will be generated for 64bit system:

```
struct my_struct {
    int32_t a;
    int64_t b;
    uint8_t c:1;
    uint8_t d:1;
    float e;
};
```

Looks very simple. It is! The aim of language is to be beautiful and same time efficient and compact in memory. Code must be transparent for programmer so he can control memory consumption as embedded and system programming requies.
