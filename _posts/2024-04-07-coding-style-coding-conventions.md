---
layout: post
title: "常见 C# 代码约定"
category: c#
---

> 来源:  https://learn.microsoft.com/zh-cn/dotnet/csharp/fundamentals/coding-style/coding-conventions

#### 本文内容

- 工具和分析器

- 语言准则

- 样式指南

- 安全性

  


代码标准对于在开发团队中维护代码可读性、一致性和协作至关重要。 遵循行业实践和既定准则的代码更易于理解、维护和扩展。 大多数项目通过代码约定强制要求样式一致。 [`dotnet/docs`](https://github.com/dotnet/docs) 和 [`dotnet/samples`](https://github.com/dotnet/samples) 项目并不例外。 在本系列文章中，你将了解我们的编码约定和用于强制实施这些约定的工具。 你可以按原样采用我们的约定，或修改它们以满足团队的需求。

我们对约定的选择基于以下目标：

1. *正确性*：我们的示例将会复制并粘贴到你的应用程序中。 我们希望如此，因此我们需要代码具有复原能力且正确无误，即使在多次编辑之后也是如此。
2. *教学*：示例的目的是教授 .NET 和 C# 的全部内容。 因此，我们不会对任何语言功能或 API 施加限制。 相反，这些示例会告知某个功能在何时会是良好的选择。
3. *一致性*：读者期望我们的内容提供一致的体验。 所有示例应遵循相同的样式。
4. *采用*：我们积极更新示例以使用新的语言功能。 这种做法提高了对新功能的认识，并且提高了所有 C# 开发人员对这些功能的熟悉程度。

> **重要** 
> 
> Microsoft 会使用这些准则来开发示例和文档。 它们摘自 [.NET 运行时、C# 编码样式](https://github.com/dotnet/runtime/blob/main/docs/coding-guidelines/coding-style.md)和 [C# 编译器 > (roslyn)](https://github.com/dotnet/roslyn/blob/main/CONTRIBUTING.md#csharp) 准则。 我们选择这些准则是因为它们已经经过了多年开放源代码开发的测试。 他们帮助社区成员参与运行时和编译器> 项目。 它们是常见 C# 约定的示例，而不是权威列表（有关此内容，请参阅[框架设计指南](https://learn.microsoft.com/zh-cn/dotnet/standard/design-guidelines/)）。
> 
> *教学*和*采用*目标是文档编码约定不同于运行时和编译器约定的原因。 运行时和编译器对热路径具有严格的性能指标。 许多其他应用程序则并非如此。 我们的*教学*目标要求我们不会禁止任何构造。 相反，示> 例显示了何时应使用构造。 与大多数生产应用程序相比，我们在更新示例方面更加积极。 我们的*采用*目标要求我们显示你目前应该编写的代码，即使去年编写的代码无需更改。

本文将对我们的准则进行说明。 这些准则已随时间推移发生变化，因此，你会发现并不遵循准则的示例。 我们欢迎推动这些示例合规的 PR，或促使我们关注应更新的示例的问题。 我们的准则是开放源代码的，因此我们欢迎 PR 和问题。 但如果你的提交将更改这些建议，请先提出一个问题以供讨论。 欢迎使用我们的准则，或根据你的需求对其进行调整。



## 工具和分析器

工具可帮助团队强制实施标准。 可以启用[代码分析](https://learn.microsoft.com/zh-cn/dotnet/fundamentals/code-analysis/overview)来强制实施你偏好的规则。 还可以创建 [editorconfig](https://learn.microsoft.com/zh-cn/visualstudio/ide/create-portable-custom-editor-options)，以便 Visual Studio 可自动强制实施样式准则。 作为起点，可以复制 [dotnet/docs 存储库的文件](https://github.com/dotnet/docs/blob/main/.editorconfig)以使用我们的样式。

借助这些工具，团队可以更轻松地采用首选的准则。 Visual Studio 将在范围中的所有 `.editorconfig` 文件中应用规则，以设置代码的格式。 可以使用多个配置来强制实施企业范围的标准、团队标准，甚至精细的项目标准。

启用的规则被违反时，代码分析会生成警告和诊断。 可以配置想要应用于项目的规则。 然后，每个 CI 生成会在违反任何规则时通知开发人员。



### 诊断 ID

- 生成自己的分析器时[选择适当的诊断 ID](https://learn.microsoft.com/zh-cn/dotnet/csharp/roslyn-sdk/choosing-diagnostic-ids)



## 语言准则

以下部分介绍了 .NET 文档团队在准备代码示例和示例时遵循的做法。 一般情况下，请遵循以下做法：

- 尽可能利用新式语言功能和 C# 版本。
- 避免陈旧或过时的语言构造。
- 仅捕获可以正确处理的异常；避免捕获泛型异常。
- 使用特定的异常类型提供有意义的错误消息。
- 使用 LINQ 查询和方法进行集合操作，以提高代码可读性。
- 将异步编程与异步和等待用于 I/O 绑定操作。
- 请谨慎处理死锁，并在适当时使用 [Task.ConfigureAwait](https://learn.microsoft.com/zh-cn/dotnet/api/system.threading.tasks.task.configureawait)。
- 对数据类型而不是运行时类型使用语言关键字。 例如，使用 `string` 而不是 [System.String](https://learn.microsoft.com/zh-cn/dotnet/api/system.string)，或使用 `int` 而不是 [System.Int32](https://learn.microsoft.com/zh-cn/dotnet/api/system.int32)。
- 使用 `int` 而不是无符号类型。 `int` 的使用在整个 C# 中很常见，并且当你使用 `int` 时，更易于与其他库交互。 特定于无符号数据类型的文档例外。。
- 仅当读者可以从表达式推断类型时使用 `var`。 读者可在文档平台上查看我们的示例。 它们没有悬停或显示变量类型的工具提示。
- 以简洁明晰的方式编写代码。
- 避免过于复杂和费解的代码逻辑。

遵循更具体的准则。



### 字符串数据

- 使用[字符串内插](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/tokens/interpolated)来连接短字符串，如下面的代码所示。

  C#

  ```csharp
  string displayName = $"{nameList[n].LastName}, {nameList[n].FirstName}";
  ```

- 若要在循环中追加字符串，尤其是在使用大量文本时，请使用 [System.Text.StringBuilder](https://learn.microsoft.com/zh-cn/dotnet/api/system.text.stringbuilder) 对象。

  C#

  ```csharp
  var phrase = "lalalalalalalalalalalalalalalalalalalalalalalalalalalalalala";
  var manyPhrases = new StringBuilder();
  for (var i = 0; i < 10000; i++)
  {
      manyPhrases.Append(phrase);
  }
  //Console.WriteLine("tra" + manyPhrases);
  ```



### 数组

- 当在声明行上初始化数组时，请使用简洁的语法。 在以下示例中，不能使用 `var` 替代 `string[]`。

C#

```csharp
string[] vowels1 = { "a", "e", "i", "o", "u" };
```

- 如果使用显式实例化，则可以使用 `var`。

C#

```csharp
var vowels2 = new string[] { "a", "e", "i", "o", "u" };
```



### 委托

- 使用 [`Func<>` 和 `Action<>`](https://learn.microsoft.com/zh-cn/dotnet/standard/delegates-lambdas)，而不是定义委托类型。 在类中，定义委托方法。

C#

```csharp
Action<string> actionExample1 = x => Console.WriteLine($"x is: {x}");

Action<string, string> actionExample2 = (x, y) =>
    Console.WriteLine($"x is: {x}, y is {y}");

Func<string, int> funcExample1 = x => Convert.ToInt32(x);

Func<int, int, int> funcExample2 = (x, y) => x + y;
```

- 使用 `Func<>` 或 `Action<>` 委托定义的签名来调用方法。

C#

```csharp
actionExample1("string for x");

actionExample2("string for x", "string for y");

Console.WriteLine($"The value is {funcExample1("1")}");

Console.WriteLine($"The sum is {funcExample2(1, 2)}");
```

- 如果创建委托类型的实例，请使用简洁的语法。 在类中，定义委托类型和具有匹配签名的方法。

  C#

  ```csharp
  public delegate void Del(string message);
  
  public static void DelMethod(string str)
  {
      Console.WriteLine("DelMethod argument: {0}", str);
  }
  ```

- 创建委托类型的实例，然后调用该实例。 以下声明显示了紧缩的语法。

  C#

  ```csharp
  Del exampleDel2 = DelMethod;
  exampleDel2("Hey");
  ```

- 以下声明使用了完整的语法。

  C#

  ```csharp
  Del exampleDel1 = new Del(DelMethod);
  exampleDel1("Hey");
  ```



### `try-catch` 和 `using` 语句正在异常处理中

- 对大多数异常处理使用 [try-catch](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/exception-handling-statements#the-try-catch-statement) 语句。

  C#

  ```csharp
  static double ComputeDistance(double x1, double y1, double x2, double y2)
  {
      try
      {
          return Math.Sqrt((x1 - x2) * (x1 - x2) + (y1 - y2) * (y1 - y2));
      }
      catch (System.ArithmeticException ex)
      {
          Console.WriteLine($"Arithmetic overflow or underflow: {ex}");
          throw;
      }
  }
  ```

- 通过使用 C# [using 语句](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/using)简化你的代码。 如果具有 [try-finally](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/exception-handling-statements#the-try-finally-statement) 语句（该语句中 `finally` 块的唯一代码是对 [Dispose](https://learn.microsoft.com/zh-cn/dotnet/api/system.idisposable.dispose) 方法的调用），请使用 `using` 语句代替。

  在以下示例中，`try-finally` 语句仅在 `finally` 块中调用 `Dispose`。

  C#

  ```csharp
  Font bodyStyle = new Font("Arial", 10.0f);
  try
  {
      byte charset = bodyStyle.GdiCharSet;
  }
  finally
  {
      if (bodyStyle != null)
      {
          ((IDisposable)bodyStyle).Dispose();
      }
  }
  ```

  可以使用 `using` 语句执行相同的操作。

  C#

  ```csharp
  using (Font arial = new Font("Arial", 10.0f))
  {
      byte charset2 = arial.GdiCharSet;
  }
  ```

  使用不需要大括号的新 [`using` 语法](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/using)：

  C#

  ```csharp
  using Font normalStyle = new Font("Arial", 10.0f);
  byte charset3 = normalStyle.GdiCharSet;
  ```



### `&&` 和 `||` 运算符

- 在执行比较时，使用 [`&&`](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/boolean-logical-operators#conditional-logical-and-operator-) 而不是 [`&`](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/boolean-logical-operators#logical-and-operator-)，使用 [`||`](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/boolean-logical-operators#conditional-logical-or-operator-) 而不是 [`|`](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/boolean-logical-operators#logical-or-operator-)，如以下示例所示。

  C#

  ```csharp
  Console.Write("Enter a dividend: ");
  int dividend = Convert.ToInt32(Console.ReadLine());
  
  Console.Write("Enter a divisor: ");
  int divisor = Convert.ToInt32(Console.ReadLine());
  
  if ((divisor != 0) && (dividend / divisor) is var result)
  {
      Console.WriteLine("Quotient: {0}", result);
  }
  else
  {
      Console.WriteLine("Attempted division by 0 ends up here.");
  }
  ```

如果除数为 0，则 `if` 语句中的第二个子句将导致运行时错误。 但是，当第一个表达式为 false 时，&& 运算符将发生短路。 也就是说，它并不评估第二个表达式。 如果 `divisor` 为 0，则 & 运算符将同时计算这两个表达式，从而导致运行时错误。



### `new` 运算符

- 使用对象实例化的简洁形式之一，如以下声明中所示。

  C#

  ```csharp
  var firstExample = new ExampleClass();
  ```

  C#

  ```csharp
  ExampleClass instance2 = new();
  ```

  前面的声明等效于下面的声明。

  C#

  ```csharp
  ExampleClass secondExample = new ExampleClass();
  ```

- 使用对象初始值设定项简化对象创建，如以下示例中所示。

  C#

  ```csharp
  var thirdExample = new ExampleClass { Name = "Desktop", ID = 37414,
      Location = "Redmond", Age = 2.3 };
  ```

  下面的示例设置了与前面的示例相同的属性，但未使用初始值设定项。

  C#

  ```csharp
  var fourthExample = new ExampleClass();
  fourthExample.Name = "Desktop";
  fourthExample.ID = 37414;
  fourthExample.Location = "Redmond";
  fourthExample.Age = 2.3;
  ```



### 事件处理

- 使用 lambda 表达式定义稍后无需移除的事件处理程序：

C#

```csharp
public Form2()
{
    this.Click += (s, e) =>
        {
            MessageBox.Show(
                ((MouseEventArgs)e).Location.ToString());
        };
}
```

Lambda 表达式缩短了以下传统定义。

C#

```csharp
public Form1()
{
    this.Click += new EventHandler(Form1_Click);
}

void Form1_Click(object? sender, EventArgs e)
{
    MessageBox.Show(((MouseEventArgs)e).Location.ToString());
}
```



### 静态成员

使用类名调用 [static](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/static) 成员：ClassName.StaticMember。 这种做法通过明确静态访问使代码更易于阅读。 请勿使用派生类的名称来限定基类中定义的静态成员。 编译该代码时，代码可读性具有误导性，如果向派生类添加具有相同名称的静态成员，代码可能会被破坏。



### LINQ 查询

- 对查询变量使用有意义的名称。 下面的示例为位于西雅图的客户使用 `seattleCustomers`。

  C#

  ```csharp
  var seattleCustomers = from customer in customers
                         where customer.City == "Seattle"
                         select customer.Name;
  ```

- 使用别名确保匿名类型的属性名称都使用 Pascal 大小写格式正确大写。

  C#

  ```csharp
  var localDistributors =
      from customer in customers
      join distributor in distributors on customer.City equals distributor.City
      select new { Customer = customer, Distributor = distributor };
  ```

- 如果结果中的属性名称模棱两可，请对属性重命名。 例如，如果你的查询返回客户名称和分销商 ID，而不是在结果中将它们保留为 `Name` 和 `ID`，请对它们进行重命名以明确 `Name` 是客户的名称，`ID` 是分销商的 ID。

  C#

  ```csharp
  var localDistributors2 =
      from customer in customers
      join distributor in distributors on customer.City equals distributor.City
      select new { CustomerName = customer.Name, DistributorID = distributor.ID };
  ```

- 在查询变量和范围变量的声明中使用隐式类型化。 有关 LINQ 查询中隐式类型的本指导会替代适用于[隐式类型本地变量](https://learn.microsoft.com/zh-cn/dotnet/csharp/fundamentals/coding-style/coding-conventions#implicitly-typed-local-variables)的一般规则。 LINQ 查询通常使用创建匿名类型的投影。 其他查询表达式使用嵌套泛型类型创建结果。 隐式类型变量通常更具可读性。

  C#

  ```csharp
  var seattleCustomers = from customer in customers
                         where customer.City == "Seattle"
                         select customer.Name;
  ```

- 对齐 [`from`](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/from-clause) 子句下的查询子句，如上面的示例所示。

- 在其他查询子句前面使用 [`where`](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/where-clause) 子句，确保后面的查询子句作用于经过缩减和筛选的一组数据。

  C#

  ```csharp
  var seattleCustomers2 = from customer in customers
                          where customer.City == "Seattle"
                          orderby customer.Name
                          select customer;
  ```

- 使用多行 `from` 子句代替 [`join`](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/join-clause) 子句来访问内部集合。 例如，`Student` 对象的集合可能包含测验分数的集合。 当执行以下查询时，它返回高于 90 的分数，并返回得到该分数的学生的姓氏。

  C#

  ```csharp
  var scoreQuery = from student in students
                   from score in student.Scores!
                   where score > 90
                   select new { Last = student.LastName, score };
  ```



### 隐式类型本地变量

- 当变量的类型在赋值右侧比较明显时，对局部变量使用[隐式类型](https://learn.microsoft.com/zh-cn/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)。

  C#

  ```csharp
  var message = "This is clearly a string.";
  var currentTemperature = 27;
  ```

- 当类型在赋值右侧不明显时，请勿使用 [var](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/declarations#implicitly-typed-local-variables)。 请勿假设类型明显来自方法名称。 如果变量类型是 `new` 运算符、对文本值的显式强制转换或赋值，则将其视为明确的变量类型。

  C#

  ```csharp
  int numberOfIterations = Convert.ToInt32(Console.ReadLine());
  int currentMaximum = ExampleClass.ResultSoFar();
  ```

- 不要使用变量名称指定变量的类型。 它可能不正确。 请改用类型来指定类型，并使用变量名称来指示变量的语义信息。 以下示例应对类型使用 `string`，并使用类似 `iterations` 的内容指示从控制台读取的信息的含义。

  C#

  ```csharp
  var inputInt = Console.ReadLine();
  Console.WriteLine(inputInt);
  ```

- 避免使用 `var` 来代替 [dynamic](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/reference-types)。 如果想要进行运行时类型推理，请使用 `dynamic`。 有关详细信息，请参阅[使用类型 dynamic（C# 编程指南）](https://learn.microsoft.com/zh-cn/dotnet/csharp/advanced-topics/interop/using-type-dynamic)。

- 在 [`for`](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements#the-for-statement) 循环中对循环变量使用隐式类型。

  下面的示例在 `for` 语句中使用隐式类型化。

  C#

  ```csharp
  var phrase = "lalalalalalalalalalalalalalalalalalalalalalalalalalalalalala";
  var manyPhrases = new StringBuilder();
  for (var i = 0; i < 10000; i++)
  {
      manyPhrases.Append(phrase);
  }
  //Console.WriteLine("tra" + manyPhrases);
  ```

- 不要使用隐式类型化来确定 [`foreach`](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements#the-foreach-statement) 循环中循环变量的类型。 在大多数情况下，集合中的元素类型并不明显。 不应仅依靠集合的名称来推断其元素的类型。

  下面的示例在 `foreach` 语句中使用显式类型化。

  C#

  ```csharp
  foreach (char ch in laugh)
  {
      if (ch == 'h')
          Console.Write("H");
      else
          Console.Write(ch);
  }
  Console.WriteLine();
  ```

- 对 LINQ 查询中的结果序列使用隐式类型。 关于 [LINQ](https://learn.microsoft.com/zh-cn/dotnet/csharp/fundamentals/coding-style/coding-conventions#linq-queries) 的部分说明了许多 LINQ 查询会导致必须使用隐式类型的匿名类型。 其他查询则会产生嵌套泛型类型，其中 `var` 的可读性更高。

   备注

  注意不要意外更改可迭代集合的元素类型。 例如，在 `foreach` 语句中从 [System.Linq.IQueryable](https://learn.microsoft.com/zh-cn/dotnet/api/system.linq.iqueryable) 切换到 [System.Collections.IEnumerable](https://learn.microsoft.com/zh-cn/dotnet/api/system.collections.ienumerable) 很容易，这会更改查询的执行。

我们的一些示例解释了表达式的*自然类型*。 这些示例必须使用 `var`，以便编译器选取自然类型。 即使这些示例不太明显，但示例必须使用 `var`。 文本应解释该行为。



### 将 using 指令放在命名空间声明之外

当 `using` 指令位于命名空间声明之外时，该导入的命名空间是其完全限定的名称。 完全限定的名称更加清晰。 如果 `using` 指令位于命名空间内部，则它可以是相对于该命名空间的，也可以是它的完全限定名称。

C#

```csharp
using Azure;

namespace CoolStuff.AwesomeFeature
{
    public class Awesome
    {
        public void Stuff()
        {
            WaitUntil wait = WaitUntil.Completed;
            // ...
        }
    }
}
```

假设存在对 [WaitUntil](https://learn.microsoft.com/zh-cn/dotnet/api/azure.waituntil) 类的引用（直接或间接）。

现在，让我们稍作改动：

C#

```csharp
namespace CoolStuff.AwesomeFeature
{
    using Azure;

    public class Awesome
    {
        public void Stuff()
        {
            WaitUntil wait = WaitUntil.Completed;
            // ...
        }
    }
}
```

今天的编译成功了。 明天的也没问题。 但在下周的某个时候，前面（未改动）的代码失败，并出现两个错误：

控制台

```console
- error CS0246: The type or namespace name 'WaitUntil' could not be found (are you missing a using directive or an assembly reference?)
- error CS0103: The name 'WaitUntil' does not exist in the current context
```

其中一个依赖项已在命名空间中引入了此类，然后以 `.Azure` 结尾：

C#

```csharp
namespace CoolStuff.Azure
{
    public class SecretsManagement
    {
        public string FetchFromKeyVault(string vaultId, string secretId) { return null; }
    }
}
```

放置在命名空间中的 `using` 指令与上下文相关，使名称解析复杂化。 在此示例中，它是它找到的第一个命名空间。

- `CoolStuff.AwesomeFeature.Azure`
- `CoolStuff.Azure`
- `Azure`

添加匹配 `CoolStuff.Azure` 或 `CoolStuff.AwesomeFeature.Azure` 的新命名空间将在全局 `Azure` 命名空间前匹配。 可以通过向 `using` 声明添加 `global::` 修饰符来解决此问题。 但是，改为将 `using` 声明放在命名空间之外更容易。

C#

```csharp
namespace CoolStuff.AwesomeFeature
{
    using global::Azure;

    public class Awesome
    {
        public void Stuff()
        {
            WaitUntil wait = WaitUntil.Completed;
            // ...
        }
    }
}
```



## 样式指南

一般情况下，对代码示例使用以下格式：

- 使用四个空格缩进。 不要使用选项卡。
- 一致地对齐代码以提高可读性。
- 将行限制为 65 个字符，以增强文档上的代码可读性，尤其是在移动屏幕上。
- 将长语句分解为多行以提高清晰度。
- 对大括号使用“Allman”样式：左和右大括号另起一行。 大括号与当前缩进级别对齐。
- 如有必要，应在二进制运算符之前换行。



### 注释样式

- 使用单行注释（`//`）以进行简要说明。

- 避免使用多行注释（`/* */`）来进行较长的解释。 注释不进行本地化处理。 相反，配套文章中提供了较长的解释。

- 若要描述方法、类、字段和所有公共成员，请使用 [XML 注释](https://learn.microsoft.com/zh-cn/dotnet/csharp/language-reference/xmldoc/)。

- 将注释放在单独的行上，而非代码行的末尾。

- 以大写字母开始注释文本。

- 以句点结束注释文本。

- 在注释分隔符 (`//`) 与注释文本之间插入一个空格，如下面的示例所示。

  C#

  ```csharp
  // The following declaration creates a query. It does not run
  // the query.
  ```



### 布局约定

好的布局利用格式设置来强调代码的结构并使代码更便于阅读。 Microsoft 示例和样本符合以下约定：

- 使用默认的代码编辑器设置（智能缩进、4 字符缩进、制表符保存为空格）。 有关详细信息，请参阅[选项、文本编辑器、C#、格式设置](https://learn.microsoft.com/zh-cn/visualstudio/ide/reference/options-text-editor-csharp-formatting)。

- 每行只写一条语句。

- 每行只写一个声明。

- 如果连续行未自动缩进，请将它们缩进一个制表符位（四个空格）。

- 在方法定义与属性定义之间添加至少一个空白行。

- 使用括号突出表达式中的子句，如下面的代码所示。

  C#

  ```csharp
  if ((startX > endX) && (startX > previousX))
  {
      // Take appropriate action.
  }
  ```

例外情况出现在示例解释运算符或表达式优先级时。



## 安全性

请遵循[安全编码准则](https://learn.microsoft.com/zh-cn/dotnet/standard/security/secure-coding-guidelines)中的准则。
