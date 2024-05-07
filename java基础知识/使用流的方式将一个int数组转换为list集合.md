**要使用 Java Stream API 将一个 int 数组转换为 List<Integer>集合，您可以遵循以下步骤：**
```Java
Import java. Util. Arrays;
Import java. Util. List;
Import java. Util. Stream. Collectors;

Public class ArrayToListExample {

    Public static void main (String[] args) {
        Int[] numbers = {1, 2, 3, 4, 5};

        // 使用 Java Stream API 将 int 数组转换为 List<Integer>
        List<Integer> numberList = Arrays. Stream (numbers)
                                      .boxed () // 将 int 流转换为 Integer 流
                                      .collect (Collectors. ToList ());

        // 输出转换后的 List<Integer>
        System. Out. Println (numberList);
    }
}
```

**在这个示例中：**
- **使用 Arrays.Stream (numbers) 将给定的 int 数组 numbers 转换为一个 IntStream 对象。**
- **调用 boxed () 方法将 IntStream 转换为 Stream<Integer>。这是因为 IntStream 处理的是原始 int 类型，而我们要构建的是一个包含对象包装类型的 List<Integer>。boxed () 方法负责将原始类型流中的每个元素装箱为对应的包装类型对象。**
- **最后，使用 collect (Collectors.ToList ()) 作为终端操作，将 Stream<Integer>收集到一个 List<Integer>集合中。Collectors.ToList () 是一个内置的收集器，用于将流元素收集到一个 List 中。**
运行上述代码，您将看到输出：
`[1, 2, 3, 4, 5]`
**使用 Java Stream API 遍历 int 数组，您可以创建一个 IntStream 对象，然后通过各种中间操作（如 map、filter 等）和终端操作（如 forEach、collect 等）来处理数组中的元素。以下是使用 IntStream 遍历 int 数组的示例：**

```java
Import java. Util. Stream. IntStream;

Int[] numbers = {1, 2, 3, 4, 5};

// 1. 使用 forEach () 方法遍历并打印数组元素
IntStream.Of (numbers). ForEach (System. Out::println);

// 2. 使用 map () 和 collect () 方法将数组元素翻倍后收集到新的数组中
Int[] doubledNumbers = IntStream.Of (numbers)
                               .map (n -> n * 2)
                               .toArray ();

// 3. 使用 filter () 方法筛选出大于 3 的元素，再使用 sum () 方法求和
Int sumOfLargeNumbers = IntStream.Of (numbers)
                                .filter (n -> n > 3)
                                .sum ();

// 4. 使用 sorted () 方法对数组元素进行升序排序，再使用 peek () 方法遍历并打印排序后的元素
IntStream.Of (numbers)
        .sorted ()
        .peek (System. Out::println)
        .count (); // 这里使用 count () 作为终端操作，避免 Stream 未被关闭的警告
```
