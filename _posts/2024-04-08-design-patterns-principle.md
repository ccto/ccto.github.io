---
layout: post
title: "设计模式的分类及原则"
category: 设计模式
---

# 一、软件设计模式的产生背景

“设计模式”这个术语最初并不是出现在软件设计中，而是被用于建筑领域的设计中。

1977 年，美国著名建筑大师、加利福尼亚大学伯克利分校环境结构中心主任克里斯托夫·亚历山大（Christopher Alexander）在他的著作《建筑模式语言：城镇、建筑、构造（A Pattern Language: Towns Building Construction）中描述了一些常见的建筑设计问题，并提出了 253 种关于对城镇、邻里、住宅、花园和房间等进行设计的基本模式。

1979 年他的另一部经典著作《建筑的永恒之道》（The Timeless Way of Building）进一步强化了设计模式的思想，为后来的建筑设计指明了方向。

1987 年，肯特·贝克（Kent Beck）和沃德·坎宁安（Ward Cunningham）首先将克里斯托夫·亚历山大的模式思想应用在 Smalltalk 中的图形用户接口的生成中，但没有引起软件界的关注。

直到 1990 年，软件工程界才开始研讨设计模式的话题，后来召开了多次关于设计模式的研讨会。

1995 年，艾瑞克·伽马（ErichGamma）、理査德·海尔姆（Richard Helm）、拉尔夫·约翰森（Ralph Johnson）、约翰·威利斯迪斯（John Vlissides）等 4 位作者合作出版了《设计模式：可复用面向对象软件的基础》（Design Patterns: Elements of Reusable Object-Oriented Software）一书，在本教程中收录了 23 个设计模式，这是设计模式领域里程碑的事件，导致了软件设计模式的突破。这 4 位作者在软件开发领域里也以他们的“四人组”（Gang of Four，GoF）匿名著称。

直到今天，狭义的设计模式还是本教程中所介绍的 23 种经典设计模式。

#  二、软件设计模式的概念与意义

有关软件设计模式的定义很多，有些从模式的特点来说明，有些从模式的作用来说明。本教程给出的定义是大多数学者公认的，从以下两个方面来说明。

1. 软件设计模式的概念
软件设计模式（Software Design Pattern），又称设计模式，是一套被反复使用、多数人知晓的、经过分类编目的、代码设计经验的总结。它描述了在软件设计过程中的一些不断重复发生的问题，以及该问题的解决方案。也就是说，它是解决特定问题的一系列套路，是前辈们的代码设计经验的总结，具有一定的普遍性，可以反复使用。其目的是为了提高代码的可重用性、代码的可读性和代码的可靠性。

2. 学习设计模式的意义
设计模式的本质是面向对象设计原则的实际运用，是对类的封装性、继承性和多态性以及类的关联关系和组合关系的充分理解。正确使用设计模式具有以下优点。

可以提高程序员的思维能力、编程能力和设计能力。
使程序设计更加标准化、代码编制更加工程化，使软件开发效率大大提高，从而缩短软件的开发周期。
使设计的代码可重用性高、可读性强、可靠性高、灵活性好、可维护性强。

当然，软件设计模式只是一个引导。在具体的软件幵发中，必须根据设计的应用系统的特点和要求来恰当选择。对于简单的程序开发，苛能写一个简单的算法要比引入某种设计模式更加容易。但对大项目的开发或者框架设计，用设计模式来组织代码显然更好。

#  三、23 种设计模式的分类和功能

## 1.根据目的来分

根据模式是用来完成什么工作来划分，这种方式可分为创建型模式、结构型模式和行为型模式 3 种。

创建型模式：用于描述“怎样创建对象”，它的主要特点是“将对象的创建与使用分离”。GoF 中提供了单例、原型、工厂方法、抽象工厂、建造者等 5 种创建型模式。
结构型模式：用于描述如何将类或对象按某种布局组成更大的结构，GoF 中提供了代理、适配器、桥接、装饰、外观、享元、组合等 7 种结构型模式。
行为型模式：用于描述类或对象之间怎样相互协作共同完成单个对象都无法单独完成的任务，以及怎样分配职责。GoF 中提供了模板方法、策略、命令、职责链、状态、观察者、中介者、迭代器、访问者、备忘录、解释器等 11 种行为型模式。

| 序号 | 模式 & 描述| 包括                                                         |
| -------- | ------ | ------------------------------------------------------------ |
| 1    | 创建型模式<br />这些设计模式提供了一种在创建对象的同时隐藏创建逻辑的方式<br />，而不是使用 new 运算符直接实例化对象。<br />这使得程序在判断针对某个给定实例需要创建哪些对象时更加灵活。 | 工厂模式（Factory Pattern）<br/>抽象工厂模式（Abstract Factory Pattern）<br/>单例模式（Singleton Pattern）<br/>建造者模式（Builder Pattern）<br/>原型模式（Prototype Pattern） |
| 2    | 结构型模式<br/>这些设计模式关注类和对象的组合。<br />继承的概念被用来组合接口和定义组合对象获得新功能的方式。 | 适配器模式（Adapter Pattern）<br/>桥接模式（Bridge Pattern）<br/>过滤器模式（Filter、Criteria Pattern）<br/>组合模式（Composite Pattern）<br/>装饰器模式（Decorator Pattern）<br/>外观模式（Facade Pattern）<br/>享元模式（Flyweight Pattern）<br/>代理模式（Proxy Pattern） |
| 3    | 行为型模式<br/>这些设计模式特别关注对象之间的通信。          | 责任链模式（Chain of Responsibility Pattern）<br/>命令模式（Command Pattern）<br/>解释器模式（Interpreter Pattern）<br/>迭代器模式（Iterator Pattern）<br/>中介者模式（Mediator Pattern）<br/>备忘录模式（Memento Pattern）<br/>观察者模式（Observer Pattern）<br/>状态模式（State Pattern）<br/>空对象模式（Null Object Pattern）<br/>策略模式（Strategy Pattern）<br/>模板模式（Template Pattern）<br/>访问者模式（Visitor Pattern） |
| 4    | J2EE 模式<br/>这些设计模式特别关注表示层。这些模式是由 Sun Java Center 鉴定的。 | MVC 模式（MVC Pattern）<br/>业务代表模式（Business Delegate Pattern）<br/>组合实体模式（Composite Entity Pattern）<br/>数据访问对象模式（Data Access Object Pattern）<br/>前端控制器模式（Front Controller Pattern）<br/>拦截过滤器模式（Intercepting Filter Pattern）<br/>服务定位器模式（Service Locator Pattern）<br/>传输对象模式（Transfer Object Pattern） |

## 2.根据作用范围来分

根据模式是主要用于类上还是主要用于对象上来分，这种方式可分为类模式和对象模式两种。

### 1.类模式：

用于处理类与子类之间的关系，这些关系通过继承来建立，是静态的，在编译时刻便确定下来了。GoF中的工厂方法、（类）适配器、模板方法、解释器属于该模式。

### 2.对象模式：

用于处理对象之间的关系，这些关系可以通过组合或聚合来实现，在运行时刻是可以变化的，更具动态性。GoF 中除了以上 4 种，其他的都是对象模式。

| 范围\目的 | 创建型模式                            | 结构型模式                                                   | 行为型模式                                                   |
| --------- | ------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 类模式    | 工厂方法                              | (类）适配器                                                  | 模板方法、解释器                                             |
| 对象模式  | 单例<br/>原型<br/>抽象工厂<br/>建造者 | 代理<br/>(对象）适配器<br/>桥接<br/>装饰<br/>外观<br/>享元<br/>组合 | 策略<br/>命令<br/>职责链<br/>状态<br/>观察者<br/>中介者<br/>迭代器<br/>访问者<br/>备忘录 |

### 3.23种设计模式的功能

1. 单例（Singleton）模式：某个类只能生成一个实例，该类提供了一个全局访问点供外部获取该实例，其拓展是有限多例模式。
2. 原型（Prototype）模式：将一个对象作为原型，通过对其进行复制而克隆出多个和原型类似的新实例。
3. 工厂方法（Factory Method）模式：定义一个用于创建产品的接口，由子类决定生产什么产品。
4. 抽象工厂（AbstractFactory）模式：提供一个创建产品族的接口，其每个子类可以生产一系列相关的产品。
5. 建造者（Builder）模式：将一个复杂对象分解成多个相对简单的部分，然后根据不同需要分别创建它们，最后构建成该复杂对象。
6. 代理（Proxy）模式：为某对象提供一种代理以控制对该对象的访问。即客户端通过代理间接地访问该对象，从而限制、增强或修改该对象的一些特性。
7. 适配器（Adapter）模式：将一个类的接口转换成客户希望的另外一个接口，使得原本由于接口不兼容而不能一起工作的那些类能一起工作。
8. 桥接（Bridge）模式：将抽象与实现分离，使它们可以独立变化。它是用组合关系代替继承关系来实现，从而降低了抽象和实现这两个可变维度的耦合度。
9. 装饰（Decorator）模式：动态的给对象增加一些职责，即增加其额外的功能。
10. 外观（Facade）模式：为多个复杂的子系统提供一个一致的接口，使这些子系统更加容易被访问。
11. 享元（Flyweight）模式：运用共享技术来有效地支持大量细粒度对象的复用。
12. 组合（Composite）模式：将对象组合成树状层次结构，使用户对单个对象和组合对象具有一致的访问性。
13. 模板方法（TemplateMethod）模式：定义一个操作中的算法骨架，而将算法的一些步骤延迟到子类中，使得子类可以不改变该算法结构的情况下重定义该算法的某些特定步骤。
14. 策略（Strategy）模式：定义了一系列算法，并将每个算法封装起来，使它们可以相互替换，且算法的改变不会影响使用算法的客户。
15. 命令（Command）模式：将一个请求封装为一个对象，使发出请求的责任和执行请求的责任分割开。
16. 职责链（Chain of Responsibility）模式：把请求从链中的一个对象传到下一个对象，直到请求被响应为止。通过这种方式去除对象之间的耦合。
17. 状态（State）模式：允许一个对象在其内部状态发生改变时改变其行为能力。
18. 观察者（Observer）模式：多个对象间存在一对多关系，当一个对象发生改变时，把这种改变通知给其他多个对象，从而影响其他对象的行为。
19. 中介者（Mediator）模式：定义一个中介对象来简化原有对象之间的交互关系，降低系统中对象间的耦合度，使原有对象之间不必相互了解。
20. 迭代器（Iterator）模式：提供一种方法来顺序访问聚合对象中的一系列数据，而不暴露聚合对象的内部表示。
21. 访问者（Visitor）模式：在不改变集合元素的前提下，为一个集合中的每个元素提供多种访问方式，即每个元素有多个访问者对象访问。
22. 备忘录（Memento）模式：在不破坏封装性的前提下，获取并保存一个对象的内部状态，以便以后恢复它。
23. 解释器（Interpreter）模式：提供如何定义语言的文法，以及对语言句子的解释方法，即解释器。

### 四、 设计模式的七大原则

1. 开闭原则
2. 里氏替换原则
3. 依赖倒置原则
4. 接口隔离原则
5. 迪米特法则
6. 合成服用原则
7. 单一职责原则

## 1.开闭原则

**1.定义：**

开闭原则（Open Closed Principle，OCP）由勃兰特·梅耶（Bertrand Meyer）提出，他在 1988 年的著作《面向对象软件构造》（Object Oriented Software Construction）中提出：软件实体应当对扩展开放，对修改关闭（Software entities should be open for extension，but closed for modification），这就是开闭原则的经典定义。

这里的软件实体包括以下几个部分：

项目中划分出的模块
类与接口
方法
开闭原则的含义是：当应用的需求改变时，在不修改软件实体的源代码或者二进制代码的前提下，可以扩展模块的功能，使其满足新的需求。

**2.作用：**

开闭原则是面向对象程序设计的终极目标，它使软件实体拥有一定的适应性和灵活性的同时具备稳定性和延续性。具体来说，其作用如下。

1. 对软件测试的影响

软件遵守开闭原则的话，软件测试时只需要对扩展的代码进行测试就可以了，因为原有的测试代码仍然能够正常运行。

2. 可以提高代码的可复用性

粒度越小，被复用的可能性就越大；在面向对象的程序设计中，根据原子和抽象编程可以提高代码的可复用性。

3. 可以提高软件的可维护性

遵守开闭原则的软件，其稳定性高和延续性强，从而易于扩展和维护。

**3.实现方法：**

可以通过“抽象约束、封装变化”来实现开闭原则，即通过接口或者抽象类为软件实体定义一个相对稳定的抽象层，而将相同的可变因素封装在相同的具体实现类中。

因为抽象灵活性好，适应性广，只要抽象的合理，可以基本保持软件架构的稳定。而软件中易变的细节可以从抽象派生来的实现类来进行扩展，当软件需要发生变化时，只需要根据需求重新派生一个实现类来扩展就可以了。

下面以 Windows 的桌面主题为例介绍开闭原则的应用。

【例1】Windows 的桌面主题设计。

分析：Windows 的主题是桌面背景图片、窗口颜色和声音等元素的组合。用户可以根据自己的喜爱更换自己的桌面主题，也可以从网上下载新的主题。这些主题有共同的特点，可以为其定义一个抽象类（Abstract Subject），而每个具体的主题（Specific Subject）是其子类。用户窗体可以根据需要选择或者增加新的主题，而不需要修改原代码，所以它是满足开闭原则的，其类图如图 1 所示。

## 2.里氏替换原则

1.定义

里氏替换原则（Liskov Substitution Principle，LSP）由麻省理工学院计算机科学实验室的里斯科夫（Liskov）女士在 1987 年的“面向对象技术的高峰会议”（OOPSLA）上发表的一篇文章《数据抽象和层次》（Data Abstraction and Hierarchy）里提出来的，她提出：继承必须确保超类所拥有的性质在子类中仍然成立（Inheritance should ensure that any property proved about supertype objects also holds for subtype objects）。

里氏替换原则主要阐述了有关继承的一些原则，也就是什么时候应该使用继承，什么时候不应该使用继承，以及其中蕴含的原理。里氏替换原是继承复用的基础，它反映了基类与子类之间的关系，是对开闭原则的补充，是对实现抽象化的具体步骤的规范。

2.作用

里氏替换原则的主要作用如下。

里氏替换原则是实现开闭原则的重要方式之一。
它克服了继承中重写父类造成的可复用性变差的缺点。
它是动作正确性的保证。即类的扩展不会给已有的系统引入新的错误，降低了代码出错的可能性。
加强程序的健壮性，同时变更时可以做到非常好的兼容性，提高程序的维护性、可扩展性，降低需求变更时引入的风险。
3.实现

里氏替换原则通俗来讲就是：子类可以扩展父类的功能，但不能改变父类原有的功能

也就是说：子类继承父类时，除添加新的方法完成新增功能外，尽量不要重写父类的方法。

根据上述理解，对里氏替换原则的定义可以总结如下：

子类可以实现父类的抽象方法，但不能覆盖父类的非抽象方法
子类中可以增加自己特有的方法
当子类的方法重载父类的方法时，方法的前置条件（即方法的输入参数）要比父类的方法更宽松
当子类的方法实现父类的方法时（重写/重载或实现抽象方法），方法的后置条件（即方法的的输出/返回值）要比父类的方法更严格或相等
通过重写父类的方法来完成新的功能写起来虽然简单，但是整个继承体系的可复用性会比较差，特别是运用多态比较频繁时，程序运行出错的概率会非常大。

如果程序违背了里氏替换原则，则继承类的对象在基类出现的地方会出现运行错误。这时其修正方法是：取消原来的继承关系，重新设计它们之间的关系。

关于里氏替换原则的例子，最有名的是“正方形不是长方形”。当然，生活中也有很多类似的例子，例如，企鹅、鸵鸟和几维鸟从生物学的角度来划分，它们属于鸟类；但从类的继承关系来看，由于它们不能继承“鸟”会飞的功能，所以它们不能定义成“鸟”的子类。同样，由于“气球鱼”不会游泳，所以不能定义成“鱼”的子类；“玩具炮”炸不了敌人，所以不能定义成“炮”的子类等。

下面以“几维鸟不是鸟”为例来说明里氏替换原则。

【例1】里氏替换原则在“几维鸟不是鸟”实例中的应用。

分析：鸟一般都会飞行，如燕子的飞行速度大概是每小时 120 千米。但是新西兰的几维鸟由于翅膀退化无法飞行。假如要设计一个实例，计算这两种鸟飞行 300 千米要花费的时间。显然，拿燕子来测试这段代码，结果正确，能计算出所需要的时间；但拿几维鸟来测试，结果会发生“除零异常”或是“无穷大”，明显不符合预期，其类图如图 1 所示。



程序代码如下

package principle;
public class LSPtest
{
    public static void main(String[] args)
    {
        Bird bird1=new Swallow();
        Bird bird2=new BrownKiwi();
        bird1.setSpeed(120);
        bird2.setSpeed(120);
        System.out.println("如果飞行300公里：");
        try
        {
            System.out.println("燕子将飞行"+bird1.getFlyTime(300)+"小时.");
            System.out.println("几维鸟将飞行"+bird2.getFlyTime(300)+"小时。");
        }
        catch(Exception err)
        {
            System.out.println("发生错误了!");
        }
    }
}
//鸟类
class Bird
{
    double flySpeed;
    public void setSpeed(double speed)
    {
        flySpeed=speed;
    }
    public double getFlyTime(double distance)
    {
        return(distance/flySpeed);
    }
}
//燕子类
class Swallow extends Bird{}
//几维鸟类
class BrownKiwi extends Bird
{
    public void setSpeed(double speed)
    {
           flySpeed=0;
    }
}

程序的运行结果如下：

如果飞行300公里：
燕子将飞行2.5小时.
几维鸟将飞行Infinity小时。
程序运行错误的原因是：几维鸟类重写了鸟类的 setSpeed(double speed) 方法，这违背了里氏替换原则。正确的做法是：取消几维鸟原来的继承关系，定义鸟和几维鸟的更一般的父类，如动物类，它们都有奔跑的能力。几维鸟的飞行速度虽然为 0，但奔跑速度不为 0，可以计算出其奔跑 300 千米所要花费的时间。其类图如图 2 所示。



## 3.依赖倒置原则

**1.定义**

依赖倒置原则（Dependence Inversion Principle，DIP）是 Object Mentor 公司总裁罗伯特·马丁（Robert C.Martin）于 1996 年在 C++ Report 上发表的文章。

依赖倒置原则的原始定义为：高层模块不应该依赖低层模块，两者都应该依赖其抽象；抽象不应该依赖细节，细节应该依赖抽象（High level modules shouldnot depend upon low level modules.Both should depend upon abstractions.Abstractions should not depend upon details. Details should depend upon abstractions）。其核心思想是：要面向接口编程，不要面向实现编程。

依赖倒置原则是实现开闭原则的重要途径之一，它降低了客户与实现模块之间的耦合。

由于在软件设计中，细节具有多变性，而抽象层则相对稳定，因此以抽象为基础搭建起来的架构要比以细节为基础搭建起来的架构要稳定得多。这里的抽象指的是接口或者抽象类，而细节是指具体的实现类。

使用接口或者抽象类的目的是制定好规范和契约，而不去涉及任何具体的操作，把展现细节的任务交给它们的实现类去完成。

**2.作用**

依赖倒置原则可以降低类间的耦合性。
依赖倒置原则可以提高系统的稳定性。
依赖倒置原则可以减少并行开发引起的风险。
依赖倒置原则可以提高代码的可读性和可维护性。
**3.实现**

依赖倒置原则的目的是通过要面向接口的编程来降低类间的耦合性，所以我们在实际编程中只要遵循以下4点，就能在项目中满足这个规则。

每个类尽量提供接口或抽象类，或者两者都具备。
变量的声明类型尽量是接口或者是抽象类。
任何类都不应该从具体类派生。
使用继承时尽量遵循里氏替换原则。

下面以“顾客购物程序”为例来说明依赖倒置原则的应用。


分析：本程序反映了 “顾客类”与“商店类”的关系。商店类中有 sell() 方法，顾客类通过该方法购物以下代码定义了顾客类通过韶关网店 ShaoguanShop 购物：

class Customer
{
    public void shopping(ShaoguanShop shop)
    {
        //购物
        System.out.println（shop.sell());
    }
}
但是，这种设计存在缺点，如果该顾客想从另外一家商店（如婺源网店 WuyuanShop）购物，就要将该顾客的代码修改如下：

class Customer
{
    public void shopping(WuyuanShop shop)
    {
        //购物
        System.out.println(shop.sell());
    }
}
顾客每更换一家商店，都要修改一次代码，这明显违背了开闭原则。存在以上缺点的原因是：顾客类设计时同具体的商店类绑定了，这违背了依赖倒置原则。解决方法是：定义“婺源网店”和“韶关网店”的共同接口 Shop，顾客类面向该接口编程，其代码修改如下：

class Customer
{
    public void shopping(Shop shop)
    {
        //购物
        System.out.println(shop.sell());
    }
}

这样，不管顾客类 Customer 访问什么商店，或者增加新的商店，都不需要修改原有代码了，其类图如图 1 所示。



程序代码如下

package principle;
public class DIPtest
{
    public static void main(String[] args)
    {
        Customer wang=new Customer();
        System.out.println("顾客购买以下商品："); 
        wang.shopping(new ShaoguanShop()); 
        wang.shopping(new WuyuanShop());
    }
}
//商店
interface Shop
{
    public String sell(); //卖
}
//韶关网店
class ShaoguanShop implements Shop
{
    public String sell()
    {
        return "韶关土特产：香菇、木耳……"; 
    } 
}
//婺源网店
class WuyuanShop implements Shop
{
    public String sell()
    {
        return "婺源土特产：绿茶、酒糟鱼……"; 
    }
} 
//顾客
class Customer
{
    public void shopping(Shop shop)
    {
        //购物
        System.out.println(shop.sell()); 
    }
}

程序的运行结果如下：

顾客购买以下商品：
韶关土特产：香菇、木耳……
婺源土特产：绿茶、酒糟鱼……

## 4.接口隔离原则

**1.定义**

接口隔离原则（Interface Segregation Principle，ISP）要求程序员尽量将臃肿庞大的接口拆分成更小的和更具体的接口，让接口中只包含客户感兴趣的方法。

2002 年罗伯特·C.马丁给“接口隔离原则”的定义是：客户端不应该被迫依赖于它不使用的方法（Clients should not be forced to depend on methods they do not use）。该原则还有另外一个定义：一个类对另一个类的依赖应该建立在最小的接口上（The dependency of one class to another one should depend on the smallest possible interface）。

以上两个定义的含义是：要为各个类建立它们需要的专用接口，而不要试图去建立一个很庞大的接口供所有依赖它的类去调用。

接口隔离原则和单一职责都是为了提高类的内聚性、降低它们之间的耦合性，体现了封装的思想，但两者是不同的：

单一职责原则注重的是职责，而接口隔离原则注重的是对接口依赖的隔离。
单一职责原则主要是约束类，它针对的是程序中的实现和细节；接口隔离原则主要约束接口，主要针对抽象和程序整体框架的构建。
**2.作用**

将臃肿庞大的接口分解为多个粒度小的接口，可以预防外来变更的扩散，提高系统的灵活性和可维护性。
接口隔离提高了系统的内聚性，减少了对外交互，降低了系统的耦合性。
如果接口的粒度大小定义合理，能够保证系统的稳定性；但是，如果定义过小，则会造成接口数量过多，使设计复杂化；如果定义太大，灵活性降低，无法提供定制服务，给整体项目带来无法预料的风险。
使用多个专门的接口还能够体现对象的层次，因为可以通过接口的继承，实现对总接口的定义。
能减少项目工程中的代码冗余。过大的大接口里面通常放置许多不用的方法，当实现这个接口的时候，被迫设计冗余的代码。
**3.实现**

在具体应用接口隔离原则时，应该根据以下几个规则来衡量。

接口尽量小，但是要有限度。一个接口只服务于一个子模块或业务逻辑。
为依赖接口的类定制服务。只提供调用者需要的方法，屏蔽不需要的方法。
了解环境，拒绝盲从。每个项目或产品都有选定的环境因素，环境不同，接口拆分的标准就不同深入了解业务逻辑。
提高内聚，减少对外交互。使接口用最少的方法去完成最多的事情。

下面以学生成绩管理程序为例介绍接口隔离原则的应用。

【例1】学生成绩管理程序。

分析：学生成绩管理程序一般包含插入成绩、删除成绩、修改成绩、计算总分、计算均分、打印成绩信息、査询成绩信息等功能，如果将这些功能全部放到一个接口中显然不太合理，正确的做法是将它们分别放在输入模块、统计模块和打印模块等 3 个模块中，其类图如图 1 所示。



程序代码如下：

package principle;
public class ISPtest
{
    public static void main(String[] args)
    {
        InputModule input =StuScoreList.getInputModule();
        CountModule count =StuScoreList.getCountModule();
        PrintModule print =StuScoreList.getPrintModule();
        input.insert();
        count.countTotalScore();
        print.printStuInfo();
        //print.delete();
    }
}
//输入模块接口
interface InputModule
{
    void insert();
    void delete();
    void modify();
}
//统计模块接口
interface CountModule
{
    void countTotalScore();
    void countAverage();
}
//打印模块接口
interface PrintModule
{
    void printStuInfo();
    void queryStuInfo();
}
//实现类
class StuScoreList implements InputModule,CountModule,PrintModule
{
    private StuScoreList(){}
    public static InputModule getInputModule()
    {
        return (InputModule)new StuScoreList();
    }
    public static CountModule getCountModule()
    {
        return (CountModule)new StuScoreList();
    }
    public static PrintModule getPrintModule()
    {
        return (PrintModule)new StuScoreList();
    }
    public void insert()
    {
        System.out.println("输入模块的insert()方法被调用！");
    }
    public void delete()
    {
        System.out.println("输入模块的delete()方法被调用！");
    }
    public void modify()
    {
        System.out.println("输入模块的modify()方法被调用！");
    }
    public void countTotalScore()
    {
        System.out.println("统计模块的countTotalScore()方法被调用！");
    }
    public void countAverage()
    {
        System.out.println("统计模块的countAverage()方法被调用！");
    }
    public void printStuInfo()
    {
        System.out.println("打印模块的printStuInfo()方法被调用！");
    }
    public void queryStuInfo()
    {
        System.out.println("打印模块的queryStuInfo()方法被调用！");
    }
}

程序的运行结果如下：

输入模块的insert()方法被调用！
统计模块的countTotalScore()方法被调用！
打印模块的printStuInfo()方法被调用！

## 5.迪米特法则

1.定义

迪米特法则（Law of Demeter，LoD）又叫作最少知识原则（Least Knowledge Principle，LKP)，产生于 1987 年美国东北大学（Northeastern University）的一个名为迪米特（Demeter）的研究项目，由伊恩·荷兰（Ian Holland）提出，被 UML 创始者之一的布奇（Booch）普及，后来又因为在经典著作《程序员修炼之道》（The Pragmatic Programmer）提及而广为人知。

迪米特法则的定义是：只与你的直接朋友交谈，不跟“陌生人”说话（Talk only to your immediate friends and not to strangers）。其含义是：如果两个软件实体无须直接通信，那么就不应当发生直接的相互调用，可以通过第三方转发该调用。其目的是降低类之间的耦合度，提高模块的相对独立性。

迪米特法则中的“朋友”是指：当前对象本身、当前对象的成员对象、当前对象所创建的对象、当前对象的方法参数等，这些对象同当前对象存在关联、聚合或组合关系，可以直接访问这些对象的方法。

2.作用

迪米特法则要求限制软件实体之间通信的宽度和深度

降低了类之间的耦合度，提高了模块的相对独立性。
由于亲合度降低，从而提高了类的可复用率和系统的扩展性。

但是，过度使用迪米特法则会使系统产生大量的中介类，从而增加系统的复杂性，使模块之间的通信效率降低。所以，在釆用迪米特法则时需要反复权衡，确保高内聚和低耦合的同时，保证系统的结构清晰。

3.实现

从迪米特法则的定义和特点可知，它强调以下两点：

从依赖者的角度来说，只依赖应该依赖的对象。
从被依赖者的角度说，只暴露应该暴露的方法。

所以，在运用迪米特法则时要注意以下 6 点。
在类的划分上，应该创建弱耦合的类。类与类之间的耦合越弱，就越有利于实现可复用的目标。
在类的结构设计上，尽量降低类成员的访问权限。
在类的设计上，优先考虑将一个类设置成不变类。
在对其他类的引用上，将引用其他对象的次数降到最低。
不暴露类的属性成员，而应该提供相应的访问器（set 和 get 方法）。
谨慎使用序列化（Serializable）功能。

【例1】明星与经纪人的关系实例。

分析：明星由于全身心投入艺术，所以许多日常事务由经纪人负责处理，如与粉丝的见面会，与媒体公司的业务洽淡等。这里的经纪人是明星的朋友，而粉丝和媒体公司是陌生人，所以适合使用迪米特法则，其类图如图 1 所示。



程序代码如下：

package principle;
public class LoDtest
{
    public static void main(String[] args)
    {
        Agent agent=new Agent();
        agent.setStar(new Star("林心如"));
        agent.setFans(new Fans("粉丝韩丞"));
        agent.setCompany(new Company("中国传媒有限公司"));
        agent.meeting();
        agent.business();
    }
}
//经纪人
class Agent
{
    private Star myStar;
    private Fans myFans;
    private Company myCompany;
    public void setStar(Star myStar)
    {
        this.myStar=myStar;
    }
    public void setFans(Fans myFans)
    {
        this.myFans=myFans;
    }
    public void setCompany(Company myCompany)
    {
        this.myCompany=myCompany;
    }
    public void meeting()
    {
        System.out.println(myFans.getName()+"与明星"+myStar.getName()+"见面了。");
    }
    public void business()
    {
        System.out.println(myCompany.getName()+"与明星"+myStar.getName()+"洽淡业务。");
    }
}
//明星
class Star
{
    private String name;
    Star(String name)
    {
        this.name=name;
    }
    public String getName()
    {
        return name;
    }
}
//粉丝
class Fans
{
    private String name;
    Fans(String name)
    {
        this.name=name;
    }
    public String getName()
    {
        return name;
    }
}
//媒体公司
class Company
{
    private String name;
    Company(String name)
    {
        this.name=name;
    }
    public String getName()
    {
        return name;
    }
}

程序的运行结果如下：

粉丝韩丞与明星林心如见面了。
中国传媒有限公司与明星林心如洽淡业务。

## 6.合成复用原则

1.定义

合成复用原则（Composite Reuse Principle，CRP）又叫组合/聚合复用原则（Composition/Aggregate Reuse Principle，CARP）。它要求在软件复用时，要尽量先使用组合或者聚合等关联关系来实现，其次才考虑使用继承关系来实现。

如果要使用继承关系，则必须严格遵循里氏替换原则。合成复用原则同里氏替换原则相辅相成的，两者都是开闭原则的具体实现规范。

2.重要性

通常类的复用分为继承复用和合成复用两种，继承复用虽然有简单和易实现的优点，但它也存在以下缺点。

继承复用破坏了类的封装性。因为继承会将父类的实现细节暴露给子类，父类对子类是透明的，所以这种复用又称为“白箱”复用。
子类与父类的耦合度高。父类的实现的任何改变都会导致子类的实现发生变化，这不利于类的扩展与维护。
它限制了复用的灵活性。从父类继承而来的实现是静态的，在编译时已经定义，所以在运行时不可能发生变化。

采用组合或聚合复用时，可以将已有对象纳入新对象中，使之成为新对象的一部分，新对象可以调用已有对象的功能，它有以下优点。
它维持了类的封装性。因为成分对象的内部细节是新对象看不见的，所以这种复用又称为“黑箱”复用。
新旧类之间的耦合度低。这种复用所需的依赖较少，新对象存取成分对象的唯一方法是通过成分对象的接口。
复用的灵活性高。这种复用可以在运行时动
3.实现

合成复用原则是通过将已有的对象纳入新对象中，作为新对象的成员对象来实现的，新对象可以调用已有对象的功能，从而达到复用。

下面以汽车分类管理程序为例来介绍合成复用原则的应用。

【例1】汽车分类管理程序。

分析：汽车按“动力源”划分可分为汽油汽车、电动汽车等；按“颜色”划分可分为白色汽车、黑色汽车和红色汽车等。如果同时考虑这两种分类，其组合就很多。图 1 所示是用继承关系实现的汽车分类的类图。




从图 1 可以看出用继承关系实现会产生很多子类，而且增加新的“动力源”或者增加新的“颜色”都要修改源代码，这违背了开闭原则，显然不可取。但如果改用组合关系实现就能很好地解决以上问题，其类图如图 2 所示。



结合前几节的内容，我们一共介绍了 7 种设计原则，它们分别为开闭原则、里氏替换原则、依赖倒置原则、单一职责原则、接口隔离原则、迪米特法则和本节所介绍的合成复用原则。

这 7 种设计原则是软件设计模式必须尽量遵循的原则，各种原则要求的侧重点不同。其中，开闭原则是总纲，它告诉我们要对扩展开放，对修改关闭；里氏替换原则告诉我们不要破坏继承体系；依赖倒置原则告诉我们要面向接口编程；单一职责原则告诉我们实现类要职责单一；接口隔离原则告诉我们在设计接口的时候要精简单一；迪米特法则告诉我们要降低耦合度；合成复用原则告诉我们要优先使用组合或者聚合关系复用，少用继承关系复用。

## 7.单一职责原则

1.定义

单一职责原则（Single Responsibility Principle，SRP）又称单一功能原则，由罗伯特·C.马丁（Robert C. Martin）于《敏捷软件开发：原则、模式和实践》一书中提出的。这里的职责是指类变化的原因，单一职责原则规定一个类应该有且仅有一个引起它变化的原因，否则类应该被拆分（There should never be more than one reason for a class to change）。

该原则提出对象不应该承担太多职责，如果一个对象承担了太多的职责，至少存在以下两个缺点：

一个职责的变化可能会削弱或者抑制这个类实现其他职责的能力；
当客户端需要该对象的某一个职责时，不得不将其他不需要的职责全都包含进来，从而造成冗余代码或代码的浪费。
2.作用

降低类的复杂度。一个类只负责一项职责，其逻辑肯定要比负责多项职责简单得多。
提高类的可读性。复杂性降低，自然其可读性会提高。
提高系统的可维护性。可读性提高，那自然更容易维护了。
变更引起的风险降低。变更是必然的，如果单一职责原则遵守得好，当修改一个功能时，可以显著降低对其他功能的影响。
3.实现

单一职责原则是最简单但又最难运用的原则，需要设计人员发现类的不同职责并将其分离，再封装到不同的类或模块中。而发现类的多重职责需要设计人员具有较强的分析设计能力和相关重构经验。下面以大学学生工作管理程序为例介绍单一职责原则的应用。

【例1】大学学生工作管理程序。

分析：大学学生工作主要包括学生生活辅导和学生学业指导两个方面的工作，其中生活辅导主要包括班委建设、出勤统计、心理辅导、费用催缴、班级管理等工作，学业指导主要包括专业引导、学习辅导、科研指导、学习总结等工作。如果将这些工作交给一位老师负责显然不合理，正确的做 法是生活辅导由辅导员负责，学业指导由学业导师负责，其类图如图 1 所示。




注意：单一职责同样也适用于方法。一个方法应该尽可能做好一件事情。如果一个方法处理的事情太多，其颗粒度会变得很粗，不利于重用。
