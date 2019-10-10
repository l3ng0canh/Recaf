# What should I know before getting started?

## JVM / Class file format

### General concepts

A basic understanding of the JVM / class file format is _highly_ reccomended before contributing. Here's a short article that should bring you up to speed:

 * [JVM Architecture 101: Get to Know Your Virtual Machine](https://blog.overops.com/jvm-architecture-101-get-to-know-your-virtual-machine/)

### Terminology

**Quantified name**: Package separators using the `.` character. These are names used by runtime functions like `Class.forName(name)`.

For example: 

 * `java.lang.String`
 * `com.example.MyClass.InnerClass`

**Internal name**: Package separators using the `/` character. Inner classes specified with the `$` character. These are names how classes are specified internally in the class file.

For example: 

 * `java/lang/String`
 * `com/example/MyClass$InnerClass`

Primitives *(Not the boxed types)* use single characters:

| Primitive | Internal |
|-----------|----------|
| `long`    | `J`      |
| `int`     | `I`      |
| `short`   | `S`      |
| `byte`    | `B`      |
| `boolean` | `Z`      |
| `float`   | `F`      |
| `double`  | `D`      |
| `void`    | `V`      |

**Descriptor**: Used to describe field and method types. These are essentially the same as internal names, but class names are wrapped in a prefix (`L`) and suffix character (`;`).

For example: 

 * `Ljava/lang/String;`
 * `I` _(primitives stay the same)_
 
Method descriptors are formatted like so:
 
 * `double method(int i, String s)` = `(ILjava/lang/String;)D`
 * `void method()` = `()V`
 
Arrays are prefixed with a `[` for each level of the array.

 * `int[]` = `[I`
 * `String[][]` = `[[Ljava/lang/String;`