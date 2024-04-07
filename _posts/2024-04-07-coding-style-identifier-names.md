---
layout: post
title: "C# 标识符命名规则和约定"
category: c#
---

> 来源： https://learn.microsoft.com/zh-cn/dotnet/csharp/fundamentals/coding-style/identifier-names

#### 本文内容
- 命名规则

- 命名约定

  


标识符是分配给类型（类、接口、结构、委托或枚举）、成员、变量或命名空间的名称。

## 命名规则

有效标识符必须遵循以下规则。 C# 编译器针对不遵循以下规则的任何标识符生成错误：

- 标识符必须以字母或下划线 (`_`) 开头。
- 标识符可以包含 Unicode 字母字符、十进制数字字符、Unicode 连接字符、Unicode 组合字符或 Unicode 格式字符。 有关 Unicode 类别的详细信息，请参阅 [Unicode 类别数据库](https://www.unicode.org/reports/tr44/)。

可以在标识符上使用 `@` 前缀来声明与 C# 关键字匹配的标识符。 `@` 不是标识符名称的一部分。 例如，`@if` 声明名为 `if` 的标识符。 这些[逐字标识符](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/tokens/verbatim)主要用于与使用其他语言声明的标识符的互操作性。

有关有效标识符的完整定义，请参阅 [C# 语言规范中的标识符一文](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/language-specification/lexical-structure#643-identifiers)。

 重要

[C# 语言规范](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/language-specification/lexical-structure#643-identifiers)仅允许字母（Lu、Ll、Lt、Lm、Lo 或 Nl）、数字 (Nd)、连接 (Pc)、组合 (Mn 或 Mc) 和格式 (Cf) 类别。 除此之外的任何内容都会自动使用 `_` 替换。 这可能会影响某些 Unicode 字符。



## 命名约定

除了规则之外，标识符名称的约定也在整个 .NET API 中使用。 这些约定为名称提供一致性，但编译器不会强制执行它们。 可以在项目中使用不同的约定。

按照约定，C# 程序对类型名称、命名空间和所有公共成员使用 `PascalCase`。 此外，`dotnet/docs` 团队使用从 [.NET Runtime 团队的编码风格](https://github.com/dotnet/runtime/blob/main/docs/coding-guidelines/coding-style.md)中吸收的以下约定：

- 接口名称以大写字母 `I` 开头。
- 属性类型以单词 `Attribute` 结尾。
- 枚举类型对非标记使用单数名词，对标记使用复数名词。
- 标识符不应包含两个连续的下划线 (`_`) 字符。 这些名称保留给编译器生成的标识符。
- 对变量、方法和类使用有意义的描述性名称。
- 清晰胜于简洁。。
- 将 PascalCase 用于类名和方法名称。
- 对方法参数和局部变量使用驼峰式大小写。
- 将 PascalCase 用于常量名，包括字段和局部常量。
- 专用实例字段以下划线 (`_`) 开头，其余文本为驼峰式大小写。
- 静态字段以 `s_` 开头。 此约定不是默认的 Visual Studio 行为，也不是[框架设计准则](https://learn.microsoft.com/zh-cn/dotnet/standard/design-guidelines/names-of-type-members#names-of-fields)的一部分，但[在 editorconfig 中可配置](https://learn.microsoft.com/zh-cn/dotnet/fundamentals/code-analysis/style-rules/naming-rules)。
- 避免在名称中使用缩写或首字母缩略词，但广为人知和广泛接受的缩写除外。
- 使用遵循反向域名表示法的有意义的描述性命名空间。
- 选择表示程序集主要用途的程序集名称。
- 避免使用单字母名称，但简单循环计数器除外。 此外，描述 C# 构造的语法示例通常使用与 [C# 语言规范](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/language-specification/readme)中使用的约定相匹配的以下单字母名称。 语法示例是规则的例外。
  - 将 `S` 用于结构，将 `C` 用于类。
  - 将 `M` 用于方法。
  - 将 `v` 用于变量，将 `p` 用于参数。
  - 将 `r` 用于 `ref` 参数。

 提示

可以使用[代码样式命名规则](https://learn.microsoft.com/zh-cn/dotnet/fundamentals/code-analysis/style-rules/naming-rules)强制实施涉及大写、前缀、后缀和单词分隔符的命名约定。

在下面的示例中，与标记为 `public` 的元素相关的指导也适用于使用 `protected` 和 `protected internal` 元素的情况 - 所有这些元素旨在对外部调用方可见。



### Pascal 大小写

在命名 `class`、`interface`、`struct` 或 `delegate` 类型时，使用 Pascal 大小写（“PascalCasing”）。

C#

```csharp
public class DataService
{
}
```

C#

```csharp
public record PhysicalAddress(
    string Street,
    string City,
    string StateOrProvince,
    string ZipCode);
```

C#

```csharp
public struct ValueCoordinate
{
}
```

C#

```csharp
public delegate void DelegateType(string message);
```

命名 `interface` 时，使用 pascal 大小写并在名称前面加上前缀 `I`。 此前缀可以清楚地向使用者表明这是 `interface`。

C#

```csharp
public interface IWorkerQueue
{
}
```

在命名字段、属性和事件等类型的 `public` 成员时，使用 pascal 大小写。 此外，对所有方法和本地函数使用 pascal 大小写。

C#

```csharp
public class ExampleEvents
{
    // A public field, these should be used sparingly
    public bool IsValid;

    // An init-only property
    public IWorkerQueue WorkerQueue { get; init; }

    // An event
    public event Action EventProcessing;

    // Method
    public void StartEventProcessing()
    {
        // Local function
        static int CountQueueItems() => WorkerQueue.Count;
        // ...
    }
}
```

编写位置记录时，对参数使用 pascal 大小写，因为它们是记录的公共属性。

C#

```csharp
public record PhysicalAddress(
    string Street,
    string City,
    string StateOrProvince,
    string ZipCode);
```

有关位置记录的详细信息，请参阅[属性定义的位置语法](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/record#positional-syntax-for-property-definition)。



### 驼峰式大小写

在命名 `private` 或 `internal` 字段时，使用驼峰式大小写（“camelCasing”），并对它们添加 `_` 作为前缀。 命名局部变量（包括委托类型的实例）时，请使用驼峰式大小写。

C#

```csharp
public class DataService
{
    private IWorkerQueue _workerQueue;
}
```

 提示

在支持语句完成的 IDE 中编辑遵循这些命名约定的 C# 代码时，键入 `_` 将显示所有对象范围的成员。

使用为 `private` 或 `internal` 的`static` 字段时 请使用 `s_` 前缀，对于线程静态，请使用 `t_`。

C#

```csharp
public class DataService
{
    private static IWorkerQueue s_workerQueue;

    [ThreadStatic]
    private static TimeSpan t_timeSpan;
}
```

编写方法参数时，请使用驼峰式大小写。

C#

```csharp
public T SomeMethod<T>(int someNumber, bool isValid)
{
}
```

有关 C# 命名约定的详细信息，请参阅 [.NET Runtime 团队的编码样式](https://github.com/dotnet/runtime/blob/main/docs/coding-guidelines/coding-style.md)。



### 类型参数命名指南

以下准则适用于泛型类型参数上的类型参数。 类型参数是泛型类型或泛型方法中参数的占位符。 可以在 C# 编程指南中详细了解 [泛型类型参数](https://learn.microsoft.com/zh-cn/dotnet/csharp/programming-guide/generics/generic-type-parameters)。

- 请使用描述性名称命名泛型类型参数，除非单个字母名称完全具有自我说明性且描述性名称不会增加任何作用。

  ./snippets/coding-conventions

  ```./snippets/coding-conventions
  public interface ISessionChannel<TSession> { /*...*/ }
  public delegate TOutput Converter<TInput, TOutput>(TInput from);
  public class List<T> { /*...*/ }
  ```

- 对具有单个字母类型参数的类型，**考虑**使用 `T` 作为类型参数名称。

  ./snippets/coding-conventions

  ```./snippets/coding-conventions
  public int IComparer<T>() { return 0; }
  public delegate bool Predicate<T>(T item);
  public struct Nullable<T> where T : struct { /*...*/ }
  ```

- 在类型参数描述性名称前添加前缀 "T"。

  ./snippets/coding-conventions

  ```./snippets/coding-conventions
  public interface ISessionChannel<TSession>
  {
      TSession Session { get; }
  }
  ```

- 请考虑在参数名称中指示出类型参数的约束。 例如，约束为 `ISession` 的参数可命名为 `TSession`。

可以使用代码分析规则 [CA1715](https://learn.microsoft.com/zh-cn/visualstudio/code-quality/ca1715) 确保恰当地命名类型参数。



### 额外的命名约定

- 在不包括 [using 指令](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/using-directive)的示例中，使用命名空间限定。 如果你知道命名空间默认导入项目中，则不必完全限定来自该命名空间的名称。 如果对于单行来说过长，则可以在点 (.) 后中断限定名称，如下面的示例所示。

  C#

  ```csharp
  var currentPerformanceCounterCategory = new System.Diagnostics.
      PerformanceCounterCategory();
  ```

- 你不必更改使用 Visual Studio 设计器工具创建的对象的名称以使它们适合其他准则。
