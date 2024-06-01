在 Java 中，抽象类和接口是两种用于定义类行为的不同概念。它们有各自的用途和特点。以下是抽象类和接口的主要区别：

### 抽象类

1. **定义**：
   - 抽象类是用 `abstract` 关键字修饰的类，不能实例化。
   - 可以包含抽象方法（没有方法体）和具体方法（有方法体）。

2. **继承**：
   - 一个类只能继承一个抽象类（Java 单继承）。
   - 使用 `extends` 关键字继承抽象类。

3. **构造函数**：
   - 抽象类可以有构造函数，用于子类实例化时初始化。

4. **成员变量**：
   - 抽象类可以包含成员变量（字段）。
   - 可以有各种访问修饰符（`public`, `protected`, `private`）。

5. **方法实现**：
   - 可以包含已经实现的方法，也可以包含未实现的抽象方法。

6. **应用场景**：
   - 适用于表示具有共同特征的类的抽象概念，但本身不具体化。

### 接口

1. **定义**：
   - 接口是用 `interface` 关键字定义的，不能包含任何实例字段。
   - 从 Java 8 开始，接口可以包含默认方法（`default` 关键字修饰，有方法体）和静态方法（`static` 关键字修饰，有方法体）。

2. **实现**：
   - 一个类可以实现多个接口（多继承）。
   - 使用 `implements` 关键字实现接口。

3. **构造函数**：
   - 接口不能有构造函数。

4. **成员变量**：
   - 接口只能包含常量（使用 `public static final` 修饰的变量）。

5. **方法实现**：
   - 默认情况下，接口中的方法没有方法体（抽象方法）。
   - 从 Java 8 开始，接口可以包含默认方法和静态方法，这些方法可以有方法体。
   - 从 Java 9 开始，接口可以包含私有方法。

6. **应用场景**：
   - 适用于定义类必须遵循的契约或行为，强调实现类应该具有哪些能力。

### 示例代码

#### 抽象类

```java
abstract class Animal {
    String name;

    Animal(String name) {
        this.name = name;
    }

    // 抽象方法
    abstract void makeSound();

    // 具体方法
    void sleep() {
        System.out.println(name + " is sleeping");
    }
}

class Dog extends Animal {
    Dog(String name) {
        super(name);
    }

    @Override
    void makeSound() {
        System.out.println(name + " says: Woof Woof");
    }
}
```

#### 接口

```java
interface Drivable {
    // 抽象方法
    void drive();

    // 默认方法
    default void park() {
        System.out.println("Parking the vehicle");
    }

    // 静态方法
    static void honk() {
        System.out.println("Honking the horn");
    }
}

class Car implements Drivable {
    @Override
    public void drive() {
        System.out.println("Driving the car");
    }
}
```

在实际应用中，选择使用抽象类还是接口取决于你的设计需求。如果你需要定义一个类的基本行为，并允许部分实现，可以使用抽象类。如果你需要定义一些不相关的功能，并允许多重实现，可以使用接口。