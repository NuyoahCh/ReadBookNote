<h1 id="nbllR">参考文献</h1>
> <font style="color:rgb(119, 119, 119);">“我的语言极限，即是我的世界的极限。” ——路德维希·维特根斯坦（</font>_<font style="color:rgb(119, 119, 119);">Wittgenstein</font>_<font style="color:rgb(119, 119, 119);">）</font>
>

[译者的话 · 《Java 编程思想》第五版 · 看云](https://www.kancloud.cn/alex_wsc/java_thinking/1921117)

[On Java 8](https://usigned.github.io/OnJava8/#/sidebar)

<h1 id="yDylu">第一章 对象的概念</h1>
<h2 id="ihFqU">抽象</h2>
<font style="color:rgb(82, 82, 82);">程序员必须要在机器模型（“解决方案空间”）和实际解决的问题模型（“问题空间”）之间建立起一种关联。这个过程既费精力，又脱离编程语言本身的范畴。这使得程序代码很难编写，维护代价高昂。同时还造就了一个副产业“编程方法”学科。</font>

1. <font style="color:rgb(119, 119, 119);">可以从要解决的问题身上抽象出概念性的组件，然后在程序中将其表示为一个对象。</font>
2. **<font style="color:rgb(119, 119, 119);">程序是一组对象，通过消息传递来告知彼此该做什么</font>**<font style="color:rgb(119, 119, 119);">。要请求调用一个对象的方法，你需要向该对象发送消息。</font>
3. **<font style="color:rgb(119, 119, 119);">每个对象都有自己的存储空间，可容纳其他对象</font>**<font style="color:rgb(119, 119, 119);">。或者说，通过封装现有对象，可制作出新型对象。所以，尽管对象的概念非常简单，但在程序中却可达到任意高的复杂程度。</font>
4. **<font style="color:rgb(119, 119, 119);">每个对象都有一种类型</font>**<font style="color:rgb(119, 119, 119);">。根据语法，每个对象都是某个“类”的一个“实例”。其中，“类”（Class）是“类型”（Type）的同义词。一个类最重要的特征就是“能将什么消息发给它？”。</font>
5. **<font style="color:rgb(119, 119, 119);">同一类所有对象都能接收相同的消息</font>**<font style="color:rgb(119, 119, 119);">。这实际是别有含义的一种说法，大家不久便能理解。由于类型为“圆”（Circle）的一个对象也属于类型为“形状”（Shape）的一个对象，所以一个圆完全能接收发送给"形状”的消息。这意味着可让程序代码统一指挥“形状”，令其自动控制所有符合“形状”描述的对象，其中自然包括“圆”。这一特性称为对象的“可替换性”，是OOP最重要的概念之一。</font>

_<font style="color:rgb(82, 82, 82);">Grady Booch</font>_<font style="color:rgb(82, 82, 82);">提供了对对象更简洁的描述：一个对象具有自己的状态，行为和标识。这意味着对象有自己的内部数据(提供状态)、方法 (产生行为)，并彼此区分（每个对象在内存中都有唯一的地址）。</font>

> <font style="color:rgb(82, 82, 82);">作为一名程序员，当我们在解决一项实际问题的时候，首先我们要去把我们实际解决问题的方法，也就是我们在和计算机聊天过程中的自然语言通过转化的方式生成机器可以识别的语言，在自然语言和机器语言转化的过程中不可避免的就是抽象的这个过程</font>
>
> <font style="color:rgb(82, 82, 82);">面向对象的程序设计在此基础上跨出了一大步，程序员可利用一些工具表达“问题空间”内的元素。由于这种表达非常具有普遍性，所以不必受限于特定类型的问题。我们将问题空间中的元素以及它们在解决方案空间的表示称作“对象”（</font>**<font style="color:rgb(82, 82, 82);">Object</font>**<font style="color:rgb(82, 82, 82);">）。当然，还有一些在问题空间没有对应的对象体。通过添加新的对象类型，程序可进行灵活的调整，以便与特定的问题配合。所以当你在阅读描述解决方案的代码时，也是在阅读问题的表述。与我们以前见过的相比，这无疑是一种更加灵活、更加强大的语言抽象方法。总之，OOP 允许我们根据问题来描述问题，而不是根据运行解决方案的计算机。然而，它仍然与计算机有联系，每个对象都类似一台小计算机：它们有自己的状态并且可以进行特定的操作。这与现实世界的“对象”或者“物体”相似：它们都有自己的特征和行为。</font>
>

<h2 id="vBuRy">接口</h2>
当我们根据现实生活的具体特征，对于每一实体进行区分时，创建的实体是存在多个属性的，<font style="color:rgb(82, 82, 82);">这个实体便是“对象”，而且每个对象都隶属一个特定的“类”，那个类具有自己的通用特征与行为。</font>

```java
Light lt = new Light();
lt.on();
```

<font style="color:rgb(82, 82, 82);">因此，在面向对象的程序设计中，尽管我们真正要做的是新建各种各样的数据“类型”（Type），但几乎所有面向对象的程序设计语言都采用了</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">class</font>`<font style="color:rgb(82, 82, 82);">关键字。当你看到 “type” 这个词的时候，请同时想到</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">class</font>`<font style="color:rgb(82, 82, 82);">；反之亦然。</font>

> <font style="color:rgb(82, 82, 82);">对于我们实现的每一个对象而产生的每一个类，包含的每一个属性之间都是存在着关系的，当然，子类和父类之间也是存在相似的关系的，也就是我们在 Java 中所提及到的继承的方式，但是我并不倾向于继承的使用，当然我不能否定这是一个伟大的语法策略，但是因为从事 Golang 后端开发也有一段时间，当我使用组合结构体+接口的实现方式的时候，更加被这种灵活的方式所吸引，但是语言、语法之间并没有所说的高低之分，也是主观性的凭借着自己的个人习惯；当然 </font>`<font style="color:rgb(82, 82, 82);">extends</font>`<font style="color:rgb(82, 82, 82);"> 关键字的清晰明了也是十分推荐的。</font>
>

<h2 id="Bm8ne"><font style="color:rgb(82, 82, 82);">服务提供</font></h2>
<font style="color:rgb(82, 82, 82);">在开发或理解程序设计时，我们可以将对象看成是“服务提供者”。你的程序本身将为用户提供服务，并且它能通过调用其他对象提供的服务来实现这一点。我们的最终目标是开发或调用工具库中已有的一些对象，提供理想的服务来解决问题。</font>

<font style="color:rgb(82, 82, 82);">那么问题来了：我们该选择哪个对象来解决问题呢？例如，你正在开发一个记事本程序。</font>_<font style="color:rgb(82, 82, 82);">你可能会想到在屏幕输入默认的记事本对象</font>_<font style="color:rgb(82, 82, 82);">，一个用于检测不同类型打印机并执行打印的对象。这些对象中的某些已经有了。那对于还没有的对象，我们该设计成啥样呢？这些对象需要提供哪些服务，以及还需要调用其他哪些对象？</font>

<font style="color:rgb(82, 82, 82);">我们可以将这些问题一一分解，抽象成一组服务。软件设计的基本原则是高内聚：每个组件的内部作用明确，功能紧密相关。然而经常有人将太多功能塞进一个对象中。例如：在支票打印模块中，你需要设计一个可以同时读取文本格式又能正确识别不同打印机型号的对象。正确的做法是提供三个或更多对象：一个对象检查所有排版布局的目录；一个或一组可以识别不同打印机型号的对象展示通用的打印界面；第三个对象组合上述两个服务来完成任务。这样，每个对象都提供了一组紧密的服务。在良好的面向对象设计中，每个对象功能单一且高效。这样的程序设计可以提高我们代码的复用性，同时也方便别人阅读和理解我们的代码。只有让人知道你提供什么服务，别人才能更好地将其应用到其他模块或程序中。</font>

> <font style="color:rgb(82, 82, 82);">这点服务提供的方式，想要向我们展示的就是，对于软件开发行业中“高内聚、低耦合”的明显特点，我们并不推荐实现一个对象后在对象的属性中过度的添加关联性较小的字段，导致其耦合严重，当代码量较大之后对象复用性很差等相关问题；所以我们可以将其分解，进行抽离，使得各司其职。</font>
>

<h2 id="MyJrQ"><font style="color:rgb(82, 82, 82);">封装</font></h2>
<font style="color:rgb(82, 82, 82);">Java 有三个显式关键字来设置类中的访问权限：</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">public</font>`<font style="color:rgb(82, 82, 82);">（公开），</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">private</font>`<font style="color:rgb(82, 82, 82);">（私有）和</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">protected</font>`<font style="color:rgb(82, 82, 82);">（受保护）。这些访问修饰符决定了谁能使用它们修饰的方法、变量或类。</font>

1. `<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">public</font>`<font style="color:rgb(82, 82, 82);">（公开）表示任何人都可以访问和使用该元素；</font>
2. `<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">private</font>`<font style="color:rgb(82, 82, 82);">（私有）除了类本身和类内部的方法，外界无法直接访问该元素。</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">private</font>`<font style="color:rgb(82, 82, 82);">是类和调用者之间的屏障。任何试图访问私有成员的行为都会报编译时错误；</font>
3. `<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">protected</font>`<font style="color:rgb(82, 82, 82);">（受保护）类似于</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">private</font>`<font style="color:rgb(82, 82, 82);">，区别是子类（下一节就会引入继承的概念）可以访问</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">protected</font>`<font style="color:rgb(82, 82, 82);">的成员，但不能访问</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">private</font>`<font style="color:rgb(82, 82, 82);">成员；</font>
4. `<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">default</font>`<font style="color:rgb(82, 82, 82);">（默认）如果你不使用前面的三者，默认就是</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">default</font>`<font style="color:rgb(82, 82, 82);">访问权限。</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">default</font>`<font style="color:rgb(82, 82, 82);">被称为包访问，因为该权限下的资源可以被同一包（库组件）中其他类的成员访问。</font>

<font style="color:rgb(82, 82, 82);">程序员开发一个工具类，该工具类仅向应用程序员公开必要的内容，并隐藏内部实现的细节。这样可以有效地避免该工具类被错误的使用和更改，从而减少程序出错的可能。彼此职责划分清晰，相互协作。当应用程序员调用研发程序员开发的工具类时，双方建立了关系。</font>

> <font style="color:rgb(82, 82, 82);">当我们在初学计算机相关的知识，使用 C 语言进行代码的实现时，对于面向过程的语言，对封装的实现并不是很明显，也没有很强烈的感知，但是当我们实现代码的能力越来越强，代码的编写也越来越规范时，不难发现，我们也更加倾向于把每一段代码段进行封装，抽象成为一个个方法进行函数内部逻辑的封装。</font>
>

<h2 id="e4lXx">复用</h2>
<font style="color:rgb(82, 82, 82);">一个类经创建和测试后，理应是可复用的。然而很多时候，由于程序员没有足够的编程经验和远见，我们的代码复用性并不强。</font>

<font style="color:rgb(82, 82, 82);">代码和设计方案的复用性是面向对象程序设计的优点之一。我们可以通过重复使用某个类的对象来达到这种复用性。同时，我们也可以将一个类的对象作为另一个类的成员变量使用。新的类可以是由任意数量和任意类型的其他对象构成。这里涉及到“组合”和“聚合”的概念：</font>

+ **<font style="color:rgb(82, 82, 82);">组合</font>**<font style="color:rgb(82, 82, 82);">（Composition）经常用来表示“拥有”关系（has-a relationship）。例如，“汽车拥有引擎”。</font>
+ **<font style="color:rgb(82, 82, 82);">聚合</font>**<font style="color:rgb(82, 82, 82);">（Aggregation）动态的</font>**<font style="color:rgb(82, 82, 82);">组合</font>**<font style="color:rgb(82, 82, 82);">。</font>

<font style="color:rgb(82, 82, 82);">在面向对象编程中经常重点强调“继承”。在新手程序员的印象里，或许先入为主地认为“继承应当随处可见”。沿着这种思路产生的程序设计通常拙劣又复杂。相反，在创建新类时首先要考虑“组合”，因为它更简单灵活，而且设计更加清晰。等我们有一些编程经验后，一旦需要用到继承，就会明显意识到这一点。</font>

> <font style="color:rgb(82, 82, 82);">最下面这段话感受真的很深，和我上述的表述进行对应，过多的继承本质上真的会让代码变得冗余不堪，所以我们也要更加倾向于这样组合的方式，当然我们也可以很轻松的联系到 Golang 这门相比较 Java 的新兴语言，结合很多程序员的思考，还是选择并非显式继承而是隐式的使用组合结构体的方式进行继承</font>
>
> <font style="color:rgb(82, 82, 82);">当然，小范围作为软件开发方向，或者宏观上说的计算机行业，我们很难去选择到一套最优的解决方案，而是不断的在每一种可行方案之中做折中方案而已，所以也没有一定要优与劣、好与坏，最适合我们当前的业务场景的方案也就是更好的、更加适合我们当前的方案。</font>
>

<h2 id="cEmot"><font style="color:rgb(82, 82, 82);">继承</font></h2>
<font style="color:rgb(82, 82, 82);">通过使用 </font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">class</font>`<font style="color:rgb(82, 82, 82);"> 关键字，这些概念形成了编程语言中的基本单元。遗憾的是，这么做还是有很多麻烦：在创建了一个类之后，即使另一个新类与其具有相似的功能，你还是得重新创建一个新类。但我们若能利用现成的数据类型，对其进行“克隆”，再根据情况进行添加和修改，情况就显得理想多了。“继承”正是针对这个目标而设计的。但继承并不完全等价于克隆。在继承过程中，若原始类（正式名称叫作基类、超类或父类）发生了变化，修改过的“克隆”类（正式名称叫作继承类或者子类）也会反映出这种变化。</font>

<font style="color:rgb(82, 82, 82);">对于继承可能会引发争论：继承应该只覆盖基类的方法(不应该添加基类中没有的方法)吗？如果这样的话，基类和派生类就是相同的类型了，因为它们具有相同的接口。这会造成，你可以用一个派生类对象完全替代基类对象，这叫作"纯粹替代"，也经常被称作"替代原则"。在某种意义上，这是一种处理继承的理想方式。我们经常把这种基类和派生类的关系称为是一个（is-a）关系，因为可以说"圆是一个形状"。判断是否继承，就看在你的类之间有无这种 is-a 关系。</font>

<font style="color:rgb(82, 82, 82);">有时你在派生类添加了新的接口元素，从而扩展接口。虽然新类型仍然可以替代基类，但是这种替代不完美，原因在于基类无法访问新添加的方法。这种关系称为像是一个(is-like-a)关系。新类型不但拥有旧类型的接口，而且包含其他方法，所以不能说新旧类型完全相同。</font>

<font style="color:rgb(82, 82, 82);">当你看到替代原则时，很容易会认为纯粹替代是唯一可行的方式，并且使用纯粹替代的设计是很好的。但有些时候，你会发现必须得在派生(扩展)类中添加新方法(提供新的接口)。只要仔细审视，你可以很明显地区分两种设计方式的使用场合。</font>

> <font style="color:rgb(82, 82, 82);">对于上述继承使用的两种方式，不管是 </font>`<font style="color:rgb(82, 82, 82);">is-a</font>`<font style="color:rgb(82, 82, 82);"> 还是 </font>`<font style="color:rgb(82, 82, 82);">is-like-a</font>`<font style="color:rgb(82, 82, 82);"> 都要根据具体的业务场景而选择使用，反而我认为 </font>`<font style="color:rgb(82, 82, 82);">is-a</font>`<font style="color:rgb(82, 82, 82);"> 的方式并不是一个好的设计，我们有的时候还是有必要在原本的对象中对于新的类进行补充和实现的。</font>
>

<h2 id="AEWdR"><font style="color:rgb(82, 82, 82);">多态</font></h2>
<font style="color:rgb(82, 82, 82);">我们在处理类的层次结构时，通常把一个对象看成是它所属的基类，而不是把它当成具体类。通过这种方式，我们可以编写出不局限于特定类型的代码。在上个“形状”的例子中，“方法”（method）操纵的是通用“形状”，而不关心它们是“圆”、“正方形”、“三角形”还是某种尚未定义的形状。所有的形状都可以被绘制、擦除和移动，因此“方法”向其中的任何代表“形状”的对象发送消息都不必担心对象如何处理信息。</font>

```java
void doSomething(Shape shape) {
    shape.erase();
    // ...
    shape.draw();
}

Circle circle = new Circle();
Triangle triangle = new Triangle();
Line line = new Line();
doSomething(circle);
doSomething(triangle);
doSomething(line);
```

<font style="color:rgb(82, 82, 82);">子类当成其基类来处理的过程叫做“向上转型”（</font>**<font style="color:rgb(82, 82, 82);">upcasting</font>**<font style="color:rgb(82, 82, 82);">）。</font>

<font style="color:rgb(82, 82, 82);">在面向对象的编程里，经常利用这种方法来给程序解耦</font>

> + 向上转型指将**子类对象**转换为**父类类型**，这是一种**自动完成**的转换，不需要显式声明。
> + 向下转型指将**父类对象**转换为**子类类型**，这是一种**必须显式声明**的转换，且可能存在风险。
>

<h2 id="ZEFWV">单继承结构</h2>
<font style="color:rgb(82, 82, 82);">自从 C++ 引入以来，一个 OOP 问题变得尤为突出：是否所有的类都应该默认从一个基类继承呢？这个答案在 Java 中是肯定的（实际上，除 C++ 以外的几乎所有OOP语言中也是这样）。在 Java 中，这个最终基类的名字就是</font><font style="color:rgb(82, 82, 82);"> </font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">Object</font>`<font style="color:rgb(82, 82, 82);">。</font>

<font style="color:rgb(82, 82, 82);">Java 的单继承结构有很多好处。由于所有对象都具有一个公共接口，因此它们最终都属于同一个基类。相反的，对于 C++ 所使用的多继承的方案则是不保证所有的对象都属于同一个基类。从向后兼容的角度看，多继承的方案更符合 C 的模型，而且受限较少。</font>

<font style="color:rgb(82, 82, 82);">对于完全面向对象编程，我们必须要构建自己的层次结构，以提供与其他 OOP 语言同样的便利。我们经常会使用到新的类库和不兼容的接口。为了整合它们而花费大气力（有可能还要用上多继承）以获得 C++ 样的“灵活性”值得吗？如果从零开始，Java 这样的替代方案会是更好的选择。</font>

<font style="color:rgb(82, 82, 82);">另外，单继承的结构使得垃圾收集器的实现更为容易。这也是 Java 在 C++ 基础上的根本改进之一。</font>

<font style="color:rgb(82, 82, 82);">由于运行期的类型信息会存在于所有对象中，所以我们永远不会遇到判断不了对象类型的情况。这对于系统级操作尤其重要，例如</font>[<font style="color:rgb(65, 131, 196);">异常处理</font>](https://www.kancloud.cn/alex_wsc/java_thinking/1921288#%E5%BC%82%E5%B8%B8%E5%A4%84%E7%90%86)<font style="color:rgb(82, 82, 82);">。同时，这也让我们的编程具有更大的灵活性。</font>

> <font style="color:rgb(82, 82, 82);">个人更加倾向于单继承的方式进行实现，因为 Java 之父也在之前说，如果可能的话更加倾向于不去使用继承的方式进行实现，更别说多继承的方式，对于代码的开发和维护实在是太难实现了，同时因为 C++使用了多继承的方式，在当今时代的软件开发行业，C++这门语言因为代码的复杂性和维护性已经逐渐的退出了这个历史的舞台；所以我个人也更加倾向于实现接口的方式，进行多实现的规范化开发的方式，这样相比较于 Java 中的继承的方式，实现接口的方式让其变得更加的灵活方便。</font>
>

<h2 id="gnoS2"><font style="color:rgb(82, 82, 82);">集合</font></h2>
<font style="color:rgb(82, 82, 82);">在面向对象的设计中，问题的解决方案有些过于轻率：创建一个新类型的对象来引用、容纳其他的对象。当然，我们也可以使用多数编程语言都支持的“数组”（array）。在 Java 中“集合”（Collection）的使用率更高。（也可称之为“容器”，但“集合”这个称呼更通用。）</font>

<font style="color:rgb(82, 82, 82);">从设计的角度来看，我们真正想要的是一个能够解决某个问题的集合。如果一种集合就满足所有需求，那么我们就不需要剩下的了。之所以选择集合有以下两个原因：</font>

1. <font style="color:rgb(82, 82, 82);">集合可以提供不同类型的接口和外部行为。堆栈、队列的应用场景和集合、列表不同，它们中的一种提供的解决方案可能比其他灵活得多。</font>
2. <font style="color:rgb(82, 82, 82);">不同的集合对某些操作有不同的效率。例如，List 的两种基本类型：ArrayList 和 LinkedList。虽然两者具有相同接口和外部行为，但是在某些操作中它们的效率差别很大。在 ArrayList 中随机查找元素是很高效的，而 LinkedList 随机查找效率低下。反之，在 LinkedList 中插入元素的效率要比在 ArrayList 中高。由于底层数据结构的不同，每种集合类型在执行相同的操作时会表现出效率上的差异。</font>

<font style="color:rgb(82, 82, 82);">我们可以一开始使用 LinkedList 构建程序，在优化系统性能时改用 ArrayList。通过对 List 接口的抽象，我们可以很容易地将 LinkedList 改为 ArrayList。</font>

<font style="color:rgb(82, 82, 82);">在 Java 5 泛型出来之前，集合中保存的是通用类型</font><font style="color:rgb(82, 82, 82);"> </font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">Object</font>`<font style="color:rgb(82, 82, 82);">。Java 单继承的结构意味着所有元素都基于</font><font style="color:rgb(82, 82, 82);"> </font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">Object</font>`<font style="color:rgb(82, 82, 82);"> </font><font style="color:rgb(82, 82, 82);">类，所以在集合中可以保存任何类型的数据，易于重用。要使用这样的集合，我们先要往集合添加元素。由于 Java 5 版本前的集合只保存</font><font style="color:rgb(82, 82, 82);"> </font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">Object</font>`<font style="color:rgb(82, 82, 82);">，当我们往集合中添加元素时，元素便向上转型成了</font><font style="color:rgb(82, 82, 82);"> </font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">Object</font>`<font style="color:rgb(82, 82, 82);">，从而丢失自己原有的类型特性。这时我们再从集合中取出该元素时，元素的类型变成了</font><font style="color:rgb(82, 82, 82);"> </font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">Object</font>`<font style="color:rgb(82, 82, 82);">。那么我们该怎么将其转回原先具体的类型呢？这里，我们使用了强制类型转换将其转为更具体的类型，这个过程称为对象的“向下转型”。通过“向上转型”，我们知道“圆形”也是一种“形状”，这个过程是安全的。可是我们不能从“Object”看出其就是“圆形”或“形状”，所以除非我们能确定元素的具体类型信息，否则“向下转型”就是不安全的。也不能说这样的错误就是完全危险的，因为一旦我们转化了错误的类型，程序就会运行出错，抛出“运行时异常”（RuntimeException）。（后面的章节会提到） 无论如何，我们要寻找一种在取出集合元素时确定其具体类型的方法。另外，每次取出元素都要做额外的“向下转型”对程序和程序员都是一种开销。以某种方式创建集合，以确认保存元素的具体类型，减少集合元素“向下转型”的开销和可能出现的错误难道不好吗？这种解决方案就是：参数化类型机制（Parameterized Type Mechanism）。</font>

<font style="color:rgb(82, 82, 82);">参数化类型机制可以使得编译器能够自动识别某个</font><font style="color:rgb(82, 82, 82);"> </font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">class</font>`<font style="color:rgb(82, 82, 82);"> </font><font style="color:rgb(82, 82, 82);">的具体类型并正确地执行。举个例子，对集合的参数化类型机制可以让集合仅接受“形状”这种类型的元素，并以“形状”类型取出元素。Java 5 版本支持了参数化类型机制，称之为“泛型”（Generic）。泛型是 Java 5 的主要特性之一。你可以按以下方式向 ArrayList 中添加 Shape（形状）：</font>

```java
ArrayList<Shape> shapes = new ArrayList<>();
```

<font style="color:rgb(82, 82, 82);">泛型的应用，让 Java 的许多标准库和组件都发生了改变。</font>

> <font style="color:rgb(82, 82, 82);">Java 中的集合不单单停留在使用的阶段，更多的是要了解其底层的数据结构，进行分析和使用，当我们在操作集合的这个过程中，本人更加倾向于联想到其底层数据结构的使用和操作。我们总不能单单学会怎么在已经打好地基的楼层上进行搬砖吧，更希望是当我们搬的每一块砖都可以放到最合适的位置，同时了解在这块砖的地基究竟是怎么样的，然后实现的，知其然、更知其所以然。</font>
>

<h2 id="RrKNW"><font style="color:rgb(82, 82, 82);">对象创建与生命周期</font></h2>
<font style="color:rgb(82, 82, 82);">我们在使用对象时要注意的一个关键问题就是对象的创建和销毁方式。每个对象的生存都需要资源，尤其是内存。为了资源的重复利用，当对象不再被使用时，我们应该及时释放资源，清理内存。</font>

<font style="color:rgb(82, 82, 82);">Java 使用动态内存分配。每次创建对象时，使用</font><font style="color:rgb(82, 82, 82);"> </font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">new</font>`<font style="color:rgb(82, 82, 82);"> </font><font style="color:rgb(82, 82, 82);">关键字构建该对象的动态实例。这又带来另一个问题：对象的生命周期。较之堆内存，在栈内存中创建对象，编译器能够确定该对象的生命周期并自动销毁它；然而如果你在堆内存创建对象的话，编译器是不知道它的生命周期的。在 C++ 中你必须以编程方式确定何时销毁对象，否则可能导致内存泄漏。Java 的内存管理是建立在垃圾收集器上的，它能自动发现对象不再被使用并释放内存。垃圾收集器的存在带来了极大的便利，它减少了我们之前必须要跟踪的问题和编写相关代码的数量。因此，垃圾收集器提供了更高级别的保险，以防止潜在的内存泄漏问题，这个问题使得许多 C++ 项目没落。</font>

<font style="color:rgb(82, 82, 82);">Java 的垃圾收集器被设计用来解决内存释放的问题（虽然这不包括对象清理的其他方面）。垃圾收集器知道对象什么时候不再被使用并且自动释放内存。结合单继承和仅可在堆中创建对象的机制，Java 的编码过程比用 C++ 要简单得多。我们所要做的决定和要克服的障碍也会少很多！</font>

> <font style="color:rgb(82, 82, 82);">C++ 和 Java 的 GC 还是存在一定的区别的，C++ 的设计理念更多的是给程序员更大的自由空间，把 GC 的压力交给程序员，而 Java 的 GC 更多的是为了程序员减少压力。</font>
>

<h2 id="AP4d4"><font style="color:rgb(82, 82, 82);">异常处理</font></h2>
<font style="color:rgb(82, 82, 82);">自编程语言被发明以来，程序的错误处理一直都是个难题。因为很难设计出一个好的错误处理方案，所以许多编程语言都忽略了这个问题，把这个问题丢给了程序类库的设计者。他们提出了在许多情况下都可以工作但很容易被规避的半途而废的措施，通常只需忽略错误。多数错误处理方案的主要问题是：它们依赖程序员之间的约定俗成而不是语言层面的限制。换句话说，如果程序员赶时间或没想起来，这些方案就很容易被忘记。</font>

<font style="color:rgb(82, 82, 82);">异常处理机制将程序错误直接交给编程语言甚至是操作系统。“异常”（Exception）是一个从出错点“抛出”（thrown）后能被特定类型的异常处理程序捕获(catch)的一个对象。它不会干扰程序的正常运行，仅当程序出错的时候才被执行。这让我们的编码更简单：不用再反复检查错误了。另外，异常不像方法返回的错误值和方法设置用来表示发生错误的标志位那样可以被忽略。异常的发生是不会被忽略的，它终究会在某一时刻被处理。</font>

<font style="color:rgb(82, 82, 82);">最后，“异常机制”提供了一种可靠地从错误状况中恢复的方法，使得我们可以编写出更健壮的程序。有时你只要处理好抛出的异常情况并恢复程序的运行即可，无需退出。</font>

<font style="color:rgb(82, 82, 82);">Java 的异常处理机制在编程语言中脱颖而出。Java 从一开始就内置了异常处理，因此你不得不使用它。这是 Java 语言唯一接受的错误报告方法。如果没有编写适当的异常处理代码，你将会收到一条编译时错误消息。这种有保障的一致性有时会让程序的错误处理变得更容易。值得注意的是，异常处理并不是面向对象的特性。尽管在面向对象的语言中异常通常由对象表示，但是在面向对象语言之前也存在异常处理。</font>

> <font style="color:rgb(82, 82, 82);">Java 的异常处理机制相比较 Golang 的异常处理机制真的标准很多，更加具备可读性和维护性</font>
>

<h2 id="wrLVQ"><font style="color:rgb(82, 82, 82);">本章小结</font></h2>
<font style="color:rgb(82, 82, 82);">面向过程程序包含数据定义和函数调用。要找到程序的意图，你必须要在脑中建立一个模型，弄清函数调用和更底层的概念。这些程序令人困扰，因为它们的表示更多地面向计算机而不是我们要解决的问题，这就是我们在设计程序时需要中间表示的原因。OOP 在面向过程编程的基础上增加了许多新的概念，所以有人会认为使用 Java 来编程会比同等的面向过程编程要更复杂。在这里，我想给大家一个惊喜：通常按照 Java 规范编写的程序会比面向过程程序更容易被理解。</font>

<font style="color:rgb(82, 82, 82);">你看到的是对象的概念，这些概念是站在“问题空间”的（而不是站在计算机角度的“解决方案空间”），以及发送消息给对象以指示该空间中的活动。面向对象编程的一个优点是：设计良好的 Java 程序代码更容易被人阅读理解。由于 Java 类库的复用性，通常程序要写的代码也会少得多。</font>

<font style="color:rgb(82, 82, 82);">OOP 和 Java 不一定适合每个人。评估自己的需求以及与现有方案作比较是很重要的。请充分考虑后再决定是不是选择 Java。如果在可预见的未来，Java 并不能很好的满足你的特定需求，那么你应该去寻找其他替代方案（特别是，我推荐看 Python）。如果你依然选择 Java 作为你的开发语言，我希望你至少应该清楚你选择的是什么，以及为什么选择这个方向。</font>

<h1 id="AOpYI">第二章 安装Java和本书用例</h1>
<h2 id="RN1FC">IDE</h2>
<font style="color:rgb(82, 82, 82);">首先你需要安装一个编辑器来创建和修改本书用例里的 Java 代码。有可能你还需要使用编辑器来更改系统配置文件。</font>

<font style="color:rgb(82, 82, 82);">相比一些重量级的 IDE（Integrated Development Environments，集成开发环境），如 Eclipse、NetBeans 和 IntelliJ IDEA (译者注：做项目强烈推荐IDEA)，编辑器是一种更纯粹的文本编辑器。如果你已经有了一个用着顺手的 IDE，那就可以直接用了。为了方便后面的学习和统一下教学环境，我推荐大家使用 Atom 这个编辑器。大家可以在</font>[<font style="color:rgb(65, 131, 196);">atom.io</font>](https://atom.io/)<font style="color:rgb(82, 82, 82);">上下载。</font>

<font style="color:rgb(82, 82, 82);">Atom 是一个免费开源、易于安装且跨平台（支持 Window、Mac和Linux）的文本编辑器。内置支持 Java 文件。相比 IDE 的厚重，它比较轻量级，是学习本书的理想工具。Atom 包含了许多方便的编辑功能，相信你一定会爱上它！更多关于 Atom 使用的细节问题可以到它的网站上寻找。</font>

<font style="color:rgb(82, 82, 82);">还有很多其他的编辑器。有一种亚文化的群体，他们热衷于争论哪个更好用！如果你找到一个你更喜欢的编辑器，换一种使用也没什么难度。重要的是，你要找一个用着舒服的。</font>

<h2 id="d6YcJ"><font style="color:rgb(82, 82, 82);">操作方法</font></h2>
<font style="color:rgb(82, 82, 82);">当 Java 安装完毕，下一步就是安装本书的代码示例了。安装步骤所有平台一致：</font>

1. <font style="color:rgb(82, 82, 82);">从</font>[<font style="color:rgb(65, 131, 196);">GitHub 仓库</font>](https://github.com/BruceEckel/OnJava8-Examples/archive/master.zip)<font style="color:rgb(82, 82, 82);">中下载本书代码示例</font>
2. <font style="color:rgb(82, 82, 82);">解压到你所选目录里。</font>
3. <font style="color:rgb(82, 82, 82);">使用 Windows 资源管理器，Mac Finder，Linux 的 Nautilus 或其他等效工具浏览，在该目录下打开 Shell。</font>
4. <font style="color:rgb(82, 82, 82);">如果你在正确的目录中，你应该看到该目录中名为 gradlew 和 gradlew.bat 的文件，以及许多其他文件和目录。目录与书中的章节相对应。</font>
5. <font style="color:rgb(82, 82, 82);">在shell中输入下面的命令运行：</font>

```java
Windows 系统：
gradlew run

Mac/Linux 系统：
./gradlew run
```

<font style="color:rgb(82, 82, 82);">第一次安装时 Gradle 需要安装自身和其他的相关的包，请稍等片刻。安装完成后，后续的安装将会快很多。</font>

**<font style="color:rgb(82, 82, 82);">注意</font>**<font style="color:rgb(82, 82, 82);">： 第一次运行 gradlew 命令时必须连接互联网。</font>

**<font style="color:rgb(82, 82, 82);">Gradle 基础任务</font>**

<font style="color:rgb(82, 82, 82);">本书构建的大量 Gradle 任务都可以自动运行。Gradle 使用约定大于配置的方式，简单设置即可具备高可用性。本书中“一起去骑行”的某些任务不适用于此或无法执行成功。以下是你通常会使用上的 Gradle 任务列表：</font>

```java
编译本书中的所有 java 文件，除了部分错误示范的
gradlew compileJava

编译并执行 java 文件（某些文件是库组件）
gradlew run

执行所有的单元测试（在本书第16章会有详细介绍）
gradlew test

编译并运行一个具体的示例程序
gradlew <本书章节>:<示例名称>
示例：gradlew objects:HelloDate
```

> Maven 在国内的使用更加广泛，Gradle 不常用，操作不熟练
>

<h1 id="dPXSg">第三章 万物皆对象</h1>
> <font style="color:rgb(119, 119, 119);">如果我们说另外一种不同的语言，我们会发觉一个不同的世界！— Ludwig Wittgenstein (1889-1951)</font>
>

<font style="color:rgb(82, 82, 82);">相比 C++ ，Java 是一种更纯粹的面向对象编程语言。虽然它们都是混合语言，但在 Java 中，设计者们认为混合的作用并非像在 C++ 中那般重要。混合语言允许多种编程风格，这也是 C++ 支持向后兼容 C 的原因。正因为 C++ 是 C 语言的超集，所以它也同时包含了许多 C 语言不具备的特性，这使得 C++ 在某些方面过于复杂。</font>

<font style="color:rgb(82, 82, 82);">Java 语言假设你只进行面向对象编程。开始学习之前，我们需要将思维置于面向对象的世界。本章你将了解到 Java 程序的基本组成，学习在 Java 中万物（几乎）皆对象的思想。</font>

> <font style="color:rgb(82, 82, 82);">就像是上述所说的这样，我们要深入的把面向对象的思想烙印在大脑中，以便在开发过程中更好的应用</font>
>

<h2 id="eBIuE"><font style="color:rgb(82, 82, 82);">对象操纵</font></h2>
<font style="color:rgb(82, 82, 82);">所有的编程语言都会操纵内存中的元素。有时程序员必须要有意识地直接或间接地操纵它们。在 C/C++ 中，对象的操纵是通过指针来完成的。</font>

<font style="color:rgb(82, 82, 82);">Java 利用万物皆对象的思想和单一一致的语法方式来简化问题。</font>

<font style="color:rgb(82, 82, 82);">下面来创建一个</font>**<font style="color:rgb(82, 82, 82);">String</font>**<font style="color:rgb(82, 82, 82);">引用，用于保存单词或语句。代码示例：</font>

```java
String s;
```

<font style="color:rgb(82, 82, 82);">这里我们只是创建了一个</font>**<font style="color:rgb(82, 82, 82);">String</font>**<font style="color:rgb(82, 82, 82);">对象的引用，而非对象。直接拿来使用会出现错误：因为此时你并没有给变量</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">s</font>`<font style="color:rgb(82, 82, 82);">赋值--指向任何对象。通常更安全的做法是：创建一个引用的同时进行初始化。代码示例：</font>

```java
String s = "asdf";
```

> 创建引用并且直接进行初始化当然是一个更好的选择
>

<h2 id="ZHar4">对象创建</h2>
<font style="color:rgb(82, 82, 82);">“引用”用来关联“对象”。在 Java 中，通常我们使用</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">new</font>`<font style="color:rgb(82, 82, 82);">操作符来创建一个新对象。</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">new</font>`<font style="color:rgb(82, 82, 82);">关键字代表：创建一个新的对象实例。所以，我们也可以这样来表示前面的代码示例：</font>

```java
String s = new String("asdf");
```

<font style="color:rgb(82, 82, 82);">以上展示了字符串对象的创建过程，以及如何初始化生成字符串。除了</font>**<font style="color:rgb(82, 82, 82);">String</font>**<font style="color:rgb(82, 82, 82);">类型以外，Java 本身自带了许多现成的数据类型。除此之外，我们还可以创建自己的数据类型。事实上，这是 Java 程序设计中的一项基本行为。在本书后面的学习中将会接触到。</font>

> <font style="color:rgb(82, 82, 82);">new 关键字对于对象的创建是不可或缺的</font>
>

<h3 id="G2uGd"><font style="color:rgb(82, 82, 82);">数据存储</font></h3>
<font style="color:rgb(82, 82, 82);">那么，程序在运行时是如何存储的呢？尤其是内存是怎么分配的。有5个不同的地方可以存储数据：</font>

1. **<font style="color:rgb(82, 82, 82);">寄存器</font>**<font style="color:rgb(82, 82, 82);">（Registers）最快的存储区域，位于 CPU 内</font>部<font style="color:rgb(82, 82, 82);">。然而，寄存器的数量十分有限，所以寄存器根据需求进行分配。我们对其没有直接的控制权，也无法在自己的程序里找到寄存器存在的踪迹（另一方面，C/C++ 允许开发者向编译器建议寄存器的分配）。</font>
2. **<font style="color:rgb(82, 82, 82);">栈内存</font>**<font style="color:rgb(82, 82, 82);">（Stack）存在于常规内存 RAM（随机访问存储器，Random Access Memory）区域中，可通过栈指针获得处理器的直接支持。栈指针下移分配内存，上移释放内存。这是一种仅次于寄存器的非常快速有效的分配存储方式。创建程序时，Java 系统必须知道栈内保存的所有项的生命周期。这种约束限制了程序的灵活性。因此，虽然在栈内存上存在一些 Java 数据（如对象引用），但 Java 对象本身的数据却是保存在堆内存的。</font>
3. **<font style="color:rgb(82, 82, 82);">堆内存</font>**<font style="color:rgb(82, 82, 82);">（Heap）这是一种通用的内存池（也在 RAM 区域），所有 Java 对象都存在于其中。与栈内存不同，编译器不需要知道对象必须在堆内存上停留多长时间。因此，用堆内存保存数据更具灵活性。创建一个对象时，只需用</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">new</font>`<font style="color:rgb(82, 82, 82);">命令实例化对象即可，当执行代码时，会自动在堆中进行内存分配。这种灵活性是有代价的：分配和清理堆内存要比栈内存需要更多的时间（如果可以用 Java 在栈内存上创建对象，就像在 C++ 中那样的话）。随着时间的推移，Java 的堆内存分配机制现在已经非常快，因此这不是一个值得关心的问题了。</font>
4. **<font style="color:rgb(82, 82, 82);">常量存储</font>**<font style="color:rgb(82, 82, 82);">（Constant storage）常量值通常直接放在程序代码中，因为它们永远不会改变。如需严格保护，可考虑将它们置于只读存储器 ROM （只读存储器，Read Only Memory）中。</font>
5. **<font style="color:rgb(82, 82, 82);">非 RAM 存储</font>**<font style="color:rgb(82, 82, 82);">（Non-RAM storage）数据完全存在于程序之外，在程序未运行以及脱离程序控制后依然存在。两个主要的例子：（1）序列化对象：对象被转换为字节流，通常被发送到另一台机器；（2）持久化对象：对象被放置在磁盘上，即使程序终止，数据依然存在。这些存储的方式都是将对象转存于另一个介质中，并在需要时恢复成常规的、基于 RAM 的对象。Java 为轻量级持久化提供了支持。而诸如 JDBC 和 Hibernate 这些类库为使用数据库存储和检索对象信息提供了更复杂的支持。</font>

> <font style="color:rgb(82, 82, 82);">栈内存和堆内存存储之间的区别还是需要去分清楚的</font>
>

<h3 id="ufM99"><font style="color:rgb(82, 82, 82);">基本类型的存储</font></h3>
<font style="color:rgb(82, 82, 82);">有一组类型在 Java 中使用频率很高，它们需要特殊对待，这就是 Java 的基本类型。之所以这么说，是因为它们的创建并不是通过</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">new</font>`<font style="color:rgb(82, 82, 82);">关键字来产生。通常</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">new</font>`<font style="color:rgb(82, 82, 82);">出来的对象都是保存在堆内存中的，以此方式创建小而简单的变量往往是不划算的。所以对于这些基本类型的创建方法，Java 使用了和 C/C++ 一样的策略。也就是说，不是使用</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">new</font>`<font style="color:rgb(82, 82, 82);">创建变量，而是使用一个“自动”变量。 这个变量直接存储"值"，并置于栈内存中，因此更加高效。</font>

<font style="color:rgb(82, 82, 82);">Java 确定了每种基本类型的内存占用大小。 这些大小不会像其他一些语言那样随着机器环境的变化而变化。这种不变性也是 Java 更具可移植性的一个原因。</font>

| <font style="color:rgb(82, 82, 82);">基本类型</font> | <font style="color:rgb(82, 82, 82);">大小</font> | <font style="color:rgb(82, 82, 82);">最小值</font> | <font style="color:rgb(82, 82, 82);">最大值</font> | <font style="color:rgb(82, 82, 82);">包装类型</font> |
| :---: | :---: | :---: | :---: | :---: |
| <font style="color:rgb(82, 82, 82);">boolean</font> | <font style="color:rgb(82, 82, 82);">—</font> | <font style="color:rgb(82, 82, 82);">—</font> | <font style="color:rgb(82, 82, 82);">—</font> | <font style="color:rgb(82, 82, 82);">Boolean</font> |
| <font style="color:rgb(82, 82, 82);">char</font> | <font style="color:rgb(82, 82, 82);">16 bits</font> | <font style="color:rgb(82, 82, 82);">Unicode 0</font> | <font style="color:rgb(82, 82, 82);">Unicode 216-1</font> | <font style="color:rgb(82, 82, 82);">Character</font> |
| <font style="color:rgb(82, 82, 82);">byte</font> | <font style="color:rgb(82, 82, 82);">8 bits</font> | <font style="color:rgb(82, 82, 82);">-128</font> | <font style="color:rgb(82, 82, 82);">+127</font> | <font style="color:rgb(82, 82, 82);">Byte</font> |
| <font style="color:rgb(82, 82, 82);">short</font> | <font style="color:rgb(82, 82, 82);">16 bits</font> | <font style="color:rgb(82, 82, 82);">- 215</font> | <font style="color:rgb(82, 82, 82);">+ 215-1</font> | <font style="color:rgb(82, 82, 82);">Short</font> |
| <font style="color:rgb(82, 82, 82);">int</font> | <font style="color:rgb(82, 82, 82);">32 bits</font> | <font style="color:rgb(82, 82, 82);">- 231</font> | <font style="color:rgb(82, 82, 82);">+ 231-1</font> | <font style="color:rgb(82, 82, 82);">Integer</font> |
| <font style="color:rgb(82, 82, 82);">long</font> | <font style="color:rgb(82, 82, 82);">64 bits</font> | <font style="color:rgb(82, 82, 82);">- 263</font> | <font style="color:rgb(82, 82, 82);">+ 263-1</font> | <font style="color:rgb(82, 82, 82);">Long</font> |
| <font style="color:rgb(82, 82, 82);">float</font> | <font style="color:rgb(82, 82, 82);">32 bits</font> | <font style="color:rgb(82, 82, 82);">IEEE754</font> | <font style="color:rgb(82, 82, 82);">IEEE754</font> | <font style="color:rgb(82, 82, 82);">Float</font> |
| <font style="color:rgb(82, 82, 82);">double</font> | <font style="color:rgb(82, 82, 82);">64 bits</font> | <font style="color:rgb(82, 82, 82);">IEEE754</font> | <font style="color:rgb(82, 82, 82);">IEEE754</font> | <font style="color:rgb(82, 82, 82);">Double</font> |
| <font style="color:rgb(82, 82, 82);">void</font> | <font style="color:rgb(82, 82, 82);">—</font> | <font style="color:rgb(82, 82, 82);">—</font> | <font style="color:rgb(82, 82, 82);">—</font> | <font style="color:rgb(82, 82, 82);">Void</font> |


<font style="color:rgb(82, 82, 82);">所有的数值类型都是有正/负符号的。布尔（boolean）类型的大小没有明确的规定，通常定义为取字面值 “true” 或 “false” 。基本类型有自己对应的包装类型，如果你希望在堆内存里表示基本类型的数据，就需要用到它们的包装类。代码示例：</font>

```java
char c = 'x';
Character ch = new Character(c);
```

<font style="color:rgb(82, 82, 82);">或者你也可以使用下面的形式：</font>

```java
Character ch = new Character('x');
```

<font style="color:rgb(82, 82, 82);">基本类型自动转换成包装类型（自动装箱）</font>

```java
Character ch = 'x';
```

<font style="color:rgb(82, 82, 82);">相对的，包装类型转化为基本类型（自动拆箱）：</font>

```java
char c = ch;
```

<font style="color:rgb(82, 82, 82);">个中原因将在以后的章节里解释。</font>

> <font style="color:rgb(82, 82, 82);">对于 Java 中的基础数据结构的数据范围是要存在清晰的认知的，在合理的数据范围内使用最合理的基本数据类型，同时自动装箱和拆箱也要去关注理解</font>
>

<h3 id="tVQV6"><font style="color:rgb(82, 82, 82);">高精度数值</font></h3>
<font style="color:rgb(82, 82, 82);">在 Java 中有两种类型的数据可用于高精度的计算。它们是</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">BigInteger</font>`<font style="color:rgb(82, 82, 82);">和</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">BigDecimal</font>`<font style="color:rgb(82, 82, 82);">。尽管它们大致可以划归为“包装类型”，但是它们并没有对应的基本类型。</font>

<font style="color:rgb(82, 82, 82);">这两个类包含的方法提供的操作，与对基本类型执行的操作相似。也就是说，能对 int 或 float 做的运算，在 BigInteger 和 BigDecimal 这里也同样可以，只不过必须要通过调用它们的方法来实现而非运算符。此外，由于涉及到的计算量更多，所以运算速度会慢一些。诚然，我们牺牲了速度，但换来了精度。</font>

<font style="color:rgb(82, 82, 82);">BigInteger 支持任意精度的整数。可用于精确表示任意大小的整数值，同时在运算过程中不会丢失精度。 BigDecimal 支持任意精度的定点数字。例如，可用它进行精确的货币计算。</font>

<font style="color:rgb(82, 82, 82);">关于这两个类的详细信息，请参考 JDK 官方文档。</font>

> <font style="color:rgb(82, 82, 82);">坑比较多，在银行等金融领域使用的频率还是比较高的</font>
>

<h3 id="VU7mV"><font style="color:rgb(82, 82, 82);">数组存储</font></h3>
<font style="color:rgb(82, 82, 82);">许多编程语言都支持数组类型。在 C 和 C++ 中使用数组是危险的，因为那些数组只是内存块。如果程序访问了内存块之外的数组或在初始化之前使用该段内存（常见编程错误），则结果是不可预测的。</font>

<font style="color:rgb(82, 82, 82);">Java 的设计主要目标之一是安全性，因此许多困扰 C 和 C++ 程序员的问题不会在 Java 中再现。在 Java 中，数组使用前需要被初始化，并且不能访问数组长度以外的数据。这种范围检查，是以每个数组上少量的内存开销及运行时检查下标的额外时间为代价的，但由此换来的安全性和效率的提高是值得的。（并且 Java 经常可以优化这些操作）。</font>

<font style="color:rgb(82, 82, 82);">当我们创建对象数组时，实际上是创建了一个引用数组，并且每个引用的初始值都为</font>**<font style="color:rgb(82, 82, 82);">null</font>**<font style="color:rgb(82, 82, 82);">。在使用该数组之前，我们必须为每个引用指定一个对象 。如果我们尝试使用为</font>**<font style="color:rgb(82, 82, 82);">null</font>**<font style="color:rgb(82, 82, 82);">的引用，则会在运行时报错。因此，在 Java 中就防止了数组操作的常规错误。</font>

<font style="color:rgb(82, 82, 82);">我们还可创建基本类型的数组。编译器通过将该数组的内存全部置零来保证初始化。本书稍后将详细介绍数组，特别是在数组章节中。</font>

> <font style="color:rgb(82, 82, 82);">Java 中的语法结构在设计之初就考虑到了一些安全性和可读性的问题，使用在底层设计的过程中就为了我们规避了不少的风险，保证了程序的健壮性</font>
>

<h2 id="nqlhr"><font style="color:rgb(82, 82, 82);">代码注释</font></h2>
<font style="color:rgb(82, 82, 82);">Java 中有两种类型的注释。第一种是传统的 C 风格的注释，以</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">/*</font>`<font style="color:rgb(82, 82, 82);">开头，可以跨越多行，到</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">*/</font>`<font style="color:rgb(82, 82, 82);"> </font><font style="color:rgb(82, 82, 82);">结束。注意，许多程序员在多行注释的每一行开头添加</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">*</font>`<font style="color:rgb(82, 82, 82);">，所以你经常会看到：</font>

```java
/* 这是
* 跨越多行的
* 注释
*/
```

<font style="color:rgb(82, 82, 82);">但请记住，</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">/*</font>`<font style="color:rgb(82, 82, 82);">和</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">*/</font>`<font style="color:rgb(82, 82, 82);">之间的内容都是被忽略的。所以你将其改为下面这样也是没有区别的。</font>

```java
/* 这是跨越多
行的注释 */
```

<font style="color:rgb(82, 82, 82);">第二种注释形式来自 C++ 。它是单行注释，以</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">//</font>`<font style="color:rgb(82, 82, 82);">开头并一直持续到行结束。这种注释方便且常用，因为直观简单。所以你经常看到：</font>

```java
// 这是单行注释
```

<h2 id="GijMv">对象清理</h2>
<font style="color:rgb(82, 82, 82);">在一些编程语言中，管理变量的生命周期需要大量的工作。一个变量需要存活多久？如果我们想销毁它，应该什么时候去做呢？变量生命周期的混乱会导致许多 bug，本小结向你介绍 Java 是如何通过释放存储来简化这个问题的。</font>

<h3 id="uTpOr"><font style="color:rgb(82, 82, 82);">作用域</font></h3>
<font style="color:rgb(82, 82, 82);">大多数程序语言都有作用域的概念。作用域决定了在该范围内定义的变量名的可见性和生存周期。在 C、 C++ 和 Java 中，作用域是由大括号</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">{}</font>`<font style="color:rgb(82, 82, 82);">的位置决定的。例如：</font>

```java
{
    int x = 12;
    // 仅 x 变量可用
    {
        int q = 96;
        // x 和 q 变量皆可用
    }
    // 仅 x 变量可用
    // 变量 q 不在作用域内
}
```

<font style="color:rgb(82, 82, 82);">Java 的变量只有在其作用域内才可用。缩进使得 Java 代码更易于阅读。由于 Java 是一种自由格式的语言，额外的空格、制表符和回车并不会影响程序的执行结果。在 Java 中，你不能执行以下操作，即使这在 C 和 C++ 中是合法的：</font>

```java
{
    int x = 12;
    {
        int x = 96; // Illegal
    }
}
```

<font style="color:rgb(82, 82, 82);">在上例中， Java 编译器会在提示变量 x 已经被定义过了。因此，在 C/C++ 中将一个较大作用域的变量"隐藏"起来的做法，在 Java 中是不被允许的。 因为 Java 的设计者认为这样做会导致程序混乱</font>

> <font style="color:rgb(82, 82, 82);">更为合理，不能重复定义</font>
>

<h3 id="yDCw5"><font style="color:rgb(82, 82, 82);">对象作用域</font></h3>
<font style="color:rgb(82, 82, 82);">Java 对象与基本类型具有不同的生命周期。当我们使用</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">new</font>`<font style="color:rgb(82, 82, 82);">关键字来创建 Java 对象时，它的生命周期将会超出作用域。因此，下面这段代码示例：</font>

```java
{
    String s = new String("a string");
} 
// 作用域终点
```

<font style="color:rgb(82, 82, 82);">上例中，引用 s 在作用域终点就结束了。但是，引用 s 指向的字符串对象依然还在占用内存。在这段代码中，我们无法在这个作用域之后访问这个对象，因为唯一对它的引用 s 已超出了作用域的范围。在后面的章节中，我们还会学习怎么在编程中传递和复制对象的引用。  
</font><font style="color:rgb(82, 82, 82);">只要你需要，</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">new</font>`<font style="color:rgb(82, 82, 82);">出来的对象就会一直存活下去。 相比在 C++ 编码中操作内存可能会出现的诸多问题，这些困扰在 Java 中都不复存在了。在 C++ 中你不仅要确保对象的内存在你操作的范围内存在，还必须在使用完它们之后，将其销毁。  
</font><font style="color:rgb(82, 82, 82);">那么问题来了：我们在 Java 中并没有主动清理这些对象，那么它是如何避免 C++ 中出现的内存被填满从而阻塞程序的问题呢？答案是：</font>**<font style="color:rgb(82, 82, 82);">Java 的垃圾收集器会检查所有</font>**`**<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">new</font>**`**<font style="color:rgb(82, 82, 82);">出来的对象并判断哪些不再可达，继而释放那些被占用的内存，供其他新的对象使用。也就是说，我们不必担心内存回收的问题了。你只需简单创建对象即可。当其不再被需要时，能自行被垃圾收集器释放。垃圾回收机制有效防止了因程序员忘记释放内存而造成的“内存泄漏”问题。---GC</font>**

> **<font style="color:rgb(82, 82, 82);">Java 中的 GC 垃圾回收真的很智能！</font>**
>

<h2 id="nBdld"><font style="color:rgb(82, 82, 82);">类的创建</font></h2>
<h3 id="tsYki">类型</h3>
<font style="color:rgb(82, 82, 82);">如果一切都是对象，那么是什么决定了某一类对象的外观和行为呢？换句话说，是什么确定了对象的类型？你可能很自然地想到</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">type</font>`<font style="color:rgb(82, 82, 82);">关键字。但是，事实上大多数面向对象的语言都使用</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">class</font>`<font style="color:rgb(82, 82, 82);">关键字类来描述一种新的对象。 通常在</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">class</font>`<font style="color:rgb(82, 82, 82);">关键字的后面的紧跟类的的名称。如下代码示例：</font>

```java
class ATypeName {
    // 这里是类的内部
}
```

<font style="color:rgb(82, 82, 82);">在上例中，我们引入了一个新的类型，尽管这个类里只有一行注释。但是我们一样可以通过</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">new</font>`<font style="color:rgb(82, 82, 82);">关键字来创建一个这种类型的对象。如下：</font>

```java
ATypeName a = new ATypeName();
```

<font style="color:rgb(82, 82, 82);">到现在为止，我们还不能用这个对象来做什么事（即不能向它发送任何有意义的消息），除非我们在这个类里定义一些方法。</font>

<h3 id="OnDCM">字段</h3>
<font style="color:rgb(82, 82, 82);">当我们创建好一个类之后，我们可以往类里存放两种类型的元素：方法（method）和字段（field）。类的字段可以是基本类型，也可以是引用类型。如果类的字段是对某个对象的引用，那么必须要初始化该引用将其关联到一个实际的对象上（通过之前介绍的创建对象的方法）。每个对象都有用来存储其字段的空间。通常，字段不在对象间共享。下面是一个具有某些字段的类的代码示例：</font>

```java
class DataOnly {
    int i;
    double d;
    boolean b;
}
```

<font style="color:rgb(82, 82, 82);">这个类除了存储数据之外什么也不能做。但是，我们仍然可以通过下面的代码来创建它的一个对象：</font>

```java
DataOnly data = new DataOnly();
```

<font style="color:rgb(82, 82, 82);">我们必须通过这个对象的引用来指定字段值。格式：对象名称.方法名称或字段名称。代码示例：</font>

```java
data.i = 47;
    data.d = 1.1;
    data.b = false;
```

<font style="color:rgb(82, 82, 82);">如果你想修改对象内部包含的另一个对象的数据，可以通过这样的格式修改。代码示例：</font>

```java
myPlane.leftTank.capacity = 100;
```

<font style="color:rgb(82, 82, 82);">你可以用这种方式嵌套许多对象（尽管这样的设计会带来混乱）。</font>

<h3 id="excEL">基本类型默认值</h3>
<font style="color:rgb(82, 82, 82);">如果类的成员变量（字段）是基本类型，那么在类初始化时，这些类型将会被赋予一个初始值。</font>

| 基本类型 | <font style="color:rgb(82, 82, 82);">初始值</font> |
| :---: | :---: |
| boolean | <font style="color:rgb(82, 82, 82);">false</font> |
| char | <font style="color:rgb(82, 82, 82);">\u0000 (null)</font> |
| byte | <font style="color:rgb(82, 82, 82);">(byte) 0</font> |
| short | <font style="color:rgb(82, 82, 82);">(short) 0</font> |
| int | 0 |
| <font style="color:rgb(82, 82, 82);">long</font> | <font style="color:rgb(82, 82, 82);">0L</font> |
| <font style="color:rgb(82, 82, 82);">float</font> | <font style="color:rgb(82, 82, 82);">0.0f</font> |
| <font style="color:rgb(82, 82, 82);">double</font> | <font style="color:rgb(82, 82, 82);">0.0d</font> |


<font style="color:rgb(82, 82, 82);">这些默认值仅在 Java 初始化类的时候才会被赋予。这种方式确保了基本类型的字段始终能被初始化（在 C++ 中不会），从而减少了 bug 的来源。但是，这些初始值对于程序来说并不一定是合法或者正确的。 所以，为了安全，我们最好始终显式地初始化变量。  
</font><font style="color:rgb(82, 82, 82);">这种默认值的赋予并不适用于局部变量 —— 那些不属于类的字段的变量。 因此，若在方法中定义的基本类型数据，如下：</font>

```java
int x;
```

<font style="color:rgb(82, 82, 82);">这里的变量 x 不会自动初始化为0，因而在使用变量 x 之前，程序员有责任主动地为其赋值（和 C 、C++ 一致）。如果我们忘记了这一步， Java 将会提示我们“编译时错误，该变量可能尚未被初始化”。 这一点做的比 C++ 更好，在后者中，编译器只是提示警告，而在 Java 中则直接报错。</font>

<h3 id="BYjrg"><font style="color:rgb(82, 82, 82);">方法使用</font></h3>
<font style="color:rgb(82, 82, 82);">在许多语言（如 C 和 C++）中，使用术语</font>_<font style="color:rgb(82, 82, 82);">函数</font>_<font style="color:rgb(82, 82, 82);">(function) 用来命名子程序。在 Java 中，我们使用术语</font>_<font style="color:rgb(82, 82, 82);">方法</font>_<font style="color:rgb(82, 82, 82);">（method）来表示“做某事的方式”。  
</font><font style="color:rgb(82, 82, 82);">在 Java 中，方法决定对象能接收哪些消息。方法的基本组成部分包括名称、参数、返回类型、方法体。格式如：</font>

```java
[返回类型] [方法名](/*参数列表*/){
    // 方法体
}
```

<h4 id="r90sd">返回类型</h4>
<font style="color:rgb(82, 82, 82);">方法的返回类型表明了当你调用它时会返回的结果类型。参数列表则显示了可被传递到方法内部的参数类型及名称。方法名和参数列表统称为</font>**<font style="color:rgb(82, 82, 82);">方法签名</font>**<font style="color:rgb(82, 82, 82);">（signature of the method）。签名作为方法的唯一标识。  
</font><font style="color:rgb(82, 82, 82);">Java 中的方法只能作为类的一部分创建。它只能被对象所调用</font>[<font style="color:rgb(65, 131, 196);">^4</font>](https://lingcoder.gitee.io/onjava8/#/%E9%9D%99%E6%80%81%E6%96%B9%E6%B3%95%EF%BC%8C%E6%88%91%E4%BB%AC%E5%BE%88%E5%BF%AB%E5%B0%B1%E8%83%BD%E6%8E%A5%E8%A7%A6%E5%88%B0%EF%BC%8C%E5%AE%83%E5%8F%AF%E4%BB%A5%E5%9C%A8%E6%B2%A1%E6%9C%89%E5%AF%B9%E8%B1%A1%E7%9A%84%E6%83%85%E5%86%B5%E4%B8%8B%E7%9B%B4%E6%8E%A5%E8%A2%AB%E7%B1%BB%E8%B0%83%E7%94%A8%E3%80%82)<font style="color:rgb(82, 82, 82);">，并且该对象必须有权限来执行调用。若对象调用错误的方法，则程序将在编译时报错。  
</font><font style="color:rgb(82, 82, 82);">我们可以像下面这样调用一个对象的方法：</font>

```java
[对象引用].[方法名](参数1, 参数2, 参数3);
```

<font style="color:rgb(82, 82, 82);">若方法不带参数，例如一个对象引用</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">a</font>`<font style="color:rgb(82, 82, 82);">的方法</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">f</font>`<font style="color:rgb(82, 82, 82);">不带参数并返回</font>**<font style="color:rgb(82, 82, 82);">int</font>**<font style="color:rgb(82, 82, 82);">型结果，我们可以如下表示：</font>

```java
int x = a.f();
```

<font style="color:rgb(82, 82, 82);">上例中方法</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">f</font>`<font style="color:rgb(82, 82, 82);">的返回值类型必须和变量</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">x</font>`<font style="color:rgb(82, 82, 82);">的类型兼容 。调用方法的行为有时被称为向对象发送消息。面向对象编程可以总结为：向对象发送消息。</font>

<h4 id="QmbvM"><font style="color:rgb(82, 82, 82);">参数列表</font></h4>
<font style="color:rgb(82, 82, 82);">方法参数列表指定了传递给方法的信息。正如你可能猜到的，这些信息就像 Java 中的其他所有信息 ，以对象的形式传递。参数列表必须指定每个对象的类型和名称。同样，我们并没有直接处理对象，而是在传递对象引用 [^5] 。但是引用的类型必须是正确的。如果方法需要 String 参数，则必须传入 String，否则编译器将报错。</font>

```java
int storage(String s) {
return s.length() * 2;
}
```

<font style="color:rgb(82, 82, 82);">此方法计算并返回某个字符串所占的字节数。参数</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">s</font>`<font style="color:rgb(82, 82, 82);">的类型为</font>**<font style="color:rgb(82, 82, 82);">String</font>**<font style="color:rgb(82, 82, 82);">。将 s 传递给</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">storage()</font>`<font style="color:rgb(82, 82, 82);">后，我们可以把它看作和任何其他对象一样，可以向它发送消息。在这里，我们调用</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">length()</font>`<font style="color:rgb(82, 82, 82);">方法，它是一个 String 方法，返回字符串中的字符数。字符串中每个字符的大小为 16 位或 2 个字节。你还看到了</font>**<font style="color:rgb(82, 82, 82);">return</font>**<font style="color:rgb(82, 82, 82);">关键字，它执行两项操作。首先，它意味着“方法执行结束”。其次，如果方法有返回值，那么该值就紧跟</font>**<font style="color:rgb(82, 82, 82);">return</font>**<font style="color:rgb(82, 82, 82);">语句之后。这里，返回值是通过计算</font>

```java
s.length() * 2
```

<font style="color:rgb(82, 82, 82);">产生的。在方法中，我们可以返回任何类型的数据。如果我们不想方法返回数据，则可以通过给方法标识</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">void</font>`<font style="color:rgb(82, 82, 82);">来表明这是一个无需返回值的方法。 代码示例：</font>

```java
boolean flag() { 
    return true; 
}

double naturalLogBase() { 
    return 2.718; 
}

void nothing() {
    return;
}

void nothing2() {

}
```

<font style="color:rgb(82, 82, 82);">当返回类型为</font>**<font style="color:rgb(82, 82, 82);">void</font>**<font style="color:rgb(82, 82, 82);">时，</font>**<font style="color:rgb(82, 82, 82);">return</font>**<font style="color:rgb(82, 82, 82);">关键字仅用于退出方法，因此在方法结束处的</font>**<font style="color:rgb(82, 82, 82);">return</font>**<font style="color:rgb(82, 82, 82);">可被省略。我们可以随时从方法中返回，但若方法返回类型为非</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">void</font>`<font style="color:rgb(82, 82, 82);">，则编译器会强制我们返回相应类型的值。  
</font><font style="color:rgb(82, 82, 82);">上面的描述可能会让你感觉程序只不过是一堆包含各种方法的对象，在这些方法中，将对象作为参数并发送消息给其他对象。大部分情况下确实如此。但在下一章的运算符中我们将会学习如何在方法中做出决策来完成更底层、详细的工作。对于本章，知道如何发送消息就够了。</font>

<h2 id="yPnUV"><font style="color:rgb(82, 82, 82);">程序编写</font></h2>
<font style="color:rgb(82, 82, 82);">在看到第一个 Java 程序之前，我们还必须理解其他几个问题。</font>

<h3 id="yqVIG">命名可见性</h3>
<font style="color:rgb(82, 82, 82);">命名控制在任何一门编程语言中都是一个问题。如果你在两个模块中使用相同的命名，那么如何区分这两个名称，并防止两个名称发生“冲突”呢？在 C 语言编程中这是很具有挑战性的，因为程序通常是一个无法管理的名称海洋。C++ 将函数嵌套在类中，所以它们不会和嵌套在其他类中的函数名冲突。然而，C++ 还是允许全局数据和全局函数，因此仍有可能发生冲突。为了解决这个问题，C++ 使用附加的关键字引入了</font>_<font style="color:rgb(82, 82, 82);">命名空间</font>_<font style="color:rgb(82, 82, 82);">。</font>

<font style="color:rgb(82, 82, 82);">Java 采取了一种新的方法避免了以上这些问题：为一个类库生成一个明确的名称，Java 创建者希望我们反向使用自己的网络域名，因为域名通常是唯一的。因此我的域名是</font><font style="color:rgb(82, 82, 82);"> </font>[<font style="color:rgb(65, 131, 196);">MindviewInc.com</font>](http://mindviewinc.com/)<font style="color:rgb(82, 82, 82);">，所以我将我的 foibles 类库命名为 com.mindviewinc.utility.foibles。反转域名后，</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">.</font>`<font style="color:rgb(82, 82, 82);">用来代表子目录的划分。</font>

<font style="color:rgb(82, 82, 82);">在 Java 1.0 和 Java 1.1 中，域扩展名 com、 edu、 org 和 net 等按惯例大写，因此类库中会出现这样类似的名称：Com.mindviewinc.utility.foibles。然而，在 Java 2 的开发过程中，他们发现这会导致问题，所以现在整个包名都是小写的。此机制意味着所有文件都自动存在于自己的命名空间中，文件中的每个类都具有唯一标识符。这样，Java 语言可以防止名称冲突。</font>

<font style="color:rgb(82, 82, 82);">使用反向 URL 是一种新的命名空间方法，在此之前尚未有其他语言这么做过。Java 中有许多这些“创造性”地解决问题的方法。正如你想象，如果我们未经测试就添加一个功能并用于生产，那么在将来发现该功能的问题再想纠正，通常为时已晚（有些错误太严重了就得从语言中删除新功能。）</font>

<font style="color:rgb(82, 82, 82);">使用反向 URL 将命名空间与文件路径相关联不会导致BUG，但它却给源代码管理带来麻烦。例如在</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">com.mindviewinc.utility.foibles</font>`<font style="color:rgb(82, 82, 82);">这样的目录结构中，我们创建了</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">com</font>`<font style="color:rgb(82, 82, 82);">和</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">mindviewinc</font>`<font style="color:rgb(82, 82, 82);">空目录。它们存在的唯一目的就是用来表示这个反向的 URL。</font>

<font style="color:rgb(82, 82, 82);">这种方式似乎为我们在编写 Java 程序中的某个问题打开了大门。空目录填充了深层次结构，它们不仅用于表示反向 URL，还用于捕获其他信息。这些长路径基本上用于存储有关目录中的内容的数据。如果你希望以最初设计的方式使用目录，这种方法可以从“令人沮丧”到“令人抓狂”，对于生产级的 Java 代码，你必须使用专门为此设计的 IDE 来管理代码。例如 NetBeans，Eclipse 或 IntelliJ IDEA。实际上，这些 IDE 都为我们管理和创建深层次空目录结构。</font>

<font style="color:rgb(82, 82, 82);">对于这本书中的例子，我不想让深层次结构给你的学习带来额外的麻烦，这实际上需要你在开始之前学习熟悉一种重量级的 IDE。所以，我们的每个章节的示例都位于一个浅的子目录中，以章节标题为名。这导致我偶尔会与遵循深层次方法的工具发生冲突。</font>

<h3 id="lTFgn">使用其他组件</h3>
<font style="color:rgb(82, 82, 82);">无论何时在程序中使用预先定义好的类，编译器都必须找到该类。最简单的情况下，该类存在于被调用的源代码文件中。此时我们使用该类 —— 即使该类在文件的后面才会被定义（Java 消除了所谓的“前向引用”问题）。而如果一个类位于其他文件中，又会怎样呢？你可能认为编译器应该足够智能去找到它，但这样是有问题的。想象一下，假如你要使用某个类，但目录中存在多个同名的类（可能用途不同）。或者更糟糕的是，假设你正在编写程序，在构建过程中，你想将某个新类添加到类库中，但却与已有的类名称冲突。</font>

<font style="color:rgb(82, 82, 82);">要解决此问题，你必须通过使用</font>**<font style="color:rgb(82, 82, 82);">import</font>**<font style="color:rgb(82, 82, 82);">关键字来告诉 Java 编译器具体要使用的类。</font>**<font style="color:rgb(82, 82, 82);">import</font>**<font style="color:rgb(82, 82, 82);">指示编译器导入一个包，也就是一个类库（在其他语言中，一个库不仅包含类，还可能包括函数和数据，但请记住 Java 中的所有代码都必须写在类里）。大多数时候，我们都在使用 Java 标准库中的组件。有了这些构件，你就不必写一长串的反转域名。例如：</font>

```java
import java.util.ArrayList;
```

<font style="color:rgb(82, 82, 82);">上例可以告诉编译器使用位于标准库</font>**<font style="color:rgb(82, 82, 82);">util</font>**<font style="color:rgb(82, 82, 82);">下的 ArrayList 类。但是，</font>**<font style="color:rgb(82, 82, 82);">util</font>**<font style="color:rgb(82, 82, 82);">中包含许多类，我们可以使用通配符</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">*</font>`<font style="color:rgb(82, 82, 82);">来导入其中部分类，而无需显式得逐一声明这些类。代码示例：</font>

```java
import java.util.*;
```

<font style="color:rgb(82, 82, 82);">本书中的示例很小，为简单起见，我们通常会使用</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">.*</font>`<font style="color:rgb(82, 82, 82);">形式略过导入。然而，许多教程书籍都会要求程序员逐一导入每个类。</font>

<h3 id="Ngzx8">static 关键字</h3>
<font style="color:rgb(82, 82, 82);">类是对象的外观及行为方式的描述。通常只有在使用</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">new</font>`<font style="color:rgb(82, 82, 82);">创建那个类的对象后，数据存储空间才被分配，对象的方法才能供外界调用。这种方式在两种情况下是不足的。</font>

1. <font style="color:rgb(82, 82, 82);">有时你只想为特定字段（注：也称为属性、域）分配一个共享存储空间，而不去考虑究竟要创建多少对象，甚至根本就不创建对象。</font>
2. <font style="color:rgb(82, 82, 82);">创建一个与此类的任何对象无关的方法。也就是说，即使没有创建对象，也能调用该方法。</font>

**<font style="color:rgb(82, 82, 82);">static</font>**<font style="color:rgb(82, 82, 82);">关键字（从 C++ 采用）就符合上述两点要求。当我们说某个事物是静态时，就意味着该字段或方法不依赖于任何特定的对象实例 。 即使我们从未创建过该类的对象，也可以调用其静态方法或访问其静态字段。相反，对于普通的非静态字段和方法，我们必须要先创建一个对象并使用该对象来访问字段或方法，因为非静态字段和方法必须与特定对象关联。</font>

<font style="color:rgb(82, 82, 82);">一些面向对象的语言使用类数据（class data）和类方法（class method），表示静态数据和方法只是作为类，而不是类的某个特定对象而存在的。有时 Java 文献也使用这些术语。  
</font><font style="color:rgb(82, 82, 82);">我们可以在类的字段或方法前添加</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">static</font>`<font style="color:rgb(82, 82, 82);">关键字来表示这是一个静态字段或静态方法。 代码示例：</font>

```java
class StaticTest {
    static int i = 47;
}
```

<font style="color:rgb(82, 82, 82);">现在，即使你创建了两个</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">StaticTest</font>`<font style="color:rgb(82, 82, 82);">对象，但是静态变量</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">i</font>`<font style="color:rgb(82, 82, 82);">仍只占一份存储空间。两个对象都会共享相同的变量</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">i</font>`<font style="color:rgb(82, 82, 82);">。 代码示例：</font>

```java
StaticTest st1 = new StaticTest();
StaticTest st2 = new StaticTest();
```

`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">st1.i</font>`<font style="color:rgb(82, 82, 82);">和</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">st2.i</font>`<font style="color:rgb(82, 82, 82);">指向同一块存储空间，因此它们的值都是 47。引用静态变量有两种方法。在前面的示例中，我们通过一个对象来定位它，例如</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">st2.i</font>`<font style="color:rgb(82, 82, 82);">。我们也可以通过类名直接引用它，这种方式对于非静态成员则不可行：</font>

```java
StaticTest.i++;
```

`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">++</font>`<font style="color:rgb(82, 82, 82);">运算符将会使变量结果 + 1。此时</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">st1.i</font>`<font style="color:rgb(82, 82, 82);">和</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">st2.i</font>`<font style="color:rgb(82, 82, 82);">的值都变成了 48。  
</font><font style="color:rgb(82, 82, 82);">使用类名直接引用静态变量是首选方法，因为它强调了变量的静态属性。类似的逻辑也适用于静态方法。我们可以通过对象引用静态方法，就像使用任何方法一样，也可以通过特殊的语法方式</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">Classname.method()</font>`<font style="color:rgb(82, 82, 82);">来直接调用静态字段或方法</font>[<font style="color:rgb(65, 131, 196);">^7</font>](https://lingcoder.gitee.io/onjava8/#/%E5%9C%A8%E6%9F%90%E4%BA%9B%E6%83%85%E5%86%B5%E4%B8%8B%EF%BC%8C%E5%AE%83%E8%BF%98%E4%B8%BA%E7%BC%96%E8%AF%91%E5%99%A8%E6%8F%90%E4%BE%9B%E4%BA%86%E6%9B%B4%E5%A5%BD%E7%9A%84%E4%BC%98%E5%8C%96%E5%8F%AF%E8%83%BD%E3%80%82)<font style="color:rgb(82, 82, 82);">。 代码示例：</font>

```java
class Incrementable {
    static void increment() { 
        StaticTest.i++; 
    }
}
```

<font style="color:rgb(82, 82, 82);">上例中，</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">Incrementable</font>`<font style="color:rgb(82, 82, 82);">的</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">increment()</font>`<font style="color:rgb(82, 82, 82);">方法通过</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">++</font>`<font style="color:rgb(82, 82, 82);">运算符将静态数据</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">i</font>`<font style="color:rgb(82, 82, 82);">加 1。我们依然可以先实例化对象再调用该方法。 代码示例：</font>

```java
Incrementable sf = new Incrementable();
sf.increment();
```

<font style="color:rgb(82, 82, 82);">当然了，首选的方法是直接通过类来调用它。代码示例：</font>

```java
Incrementable.increment()；
```

<font style="color:rgb(82, 82, 82);">相比非静态的对象，</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">static</font>`<font style="color:rgb(82, 82, 82);">属性改变了数据创建的方式。同样，当</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">static</font>`<font style="color:rgb(82, 82, 82);">关键字修饰方法时，它允许我们无需创建对象就可以直接通过类的引用来调用该方法。正如我们所知，</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">static</font>`<font style="color:rgb(82, 82, 82);">关键字的这些特性对于应用程序入口点的</font>`<font style="color:rgb(82, 82, 82);background-color:rgb(247, 247, 247);">main()</font>`<font style="color:rgb(82, 82, 82);">方法尤为重要。</font>

