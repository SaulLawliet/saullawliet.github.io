---
layout: post
title: "《重构》目录"
category: book
comments: true
share: false
image:
  feature:

modified:
---

{% include _toc.html %}

> 如果想读《重构》[^1]的时候，发现手边没有书，是不是会很纠结？<br>
> 那时，记得打开这个页面噢！也许你会获得一些灵感。

# 重新组织函数
- Extract Method （提炼函数）
- Inline Method （内联函数）
- Inline Temp （内联变量）
- Replace Temp with Query （以查询取代临时变量）
- Introduce Explaining Variable （引入解释性变量）
- Split Temporary Variable （分解临时变量）
- Remove Assignments to Parameters （移除对参数的赋值）
- Replace Method with Method Object （以函数对象取代函数）
- Substitute Algorithm （替换算法）

# 在对象之间搬移特性
- Move Method （搬移函数）
- Move Field （搬移字段）
- Extract Class （提炼类）
- Inline Class （将类内联化）
- Hide Delegate （隐藏“委托关系”）
- Remove Middle Man （移除中间人）
- Introduce Foreign Method （引入外加函数）
- Introduce Local Extension （引入本地扩展）

# 重新组织数据
- Self Encapsulate Field （自封装字段）
- Replace Data Value with Object （以对象取代数据值）
- Change Value to Reference （将值对象改为引用对象）
- Change Reference to Value （将引用对象改为值对象）
- Replace Array with Object （以对象取代数组）
- Duplicate Observed Data （复制“被监视数据”）
- Change Unidirectional Association to Bidirectional （将单向关联改为双向关联）
- Change Bidirectional Association to Unidirectional （将双向关联改为单向关联）
- Replace Magic Number with Symbolic Constant （以字面常量取代魔法数）
- Encapsulate Field （封住字段）
- Encapsulate Collection （封装集合）
- Replace Record with Data Class （以数据类取代纪录）
- Replace Type Code with Class （以类取代类型码）
- Replace Type Code with Subclasses （以子类取代类型码）
- Replace Type Code with State/Strategy （以 State/Strategy 取代类型码）
- Replace Subclass with Fields （以字段取代子类）

# 简化条件表达式
- Decompose Conditional （分解条件表达式）
- Consolidate Conditional Expression （合并条件表达式）
- Consolidate Duplicate Conditional Fragments （合并重复的条件片段）
- Remove Control Flag （移除控制标记）
- Replace Nested Conditional with Guard Clauses （以卫语句取代嵌套条件表达式）
- Replace Conditional with Polymorphism （以多态取代条件表达式）
- Introduce Null Object （引入 Null 对象）
- Introduce Assertion （引入断言）

# 简化函数调用
- Rename Method （函数改名）
- Add Parameter （添加参数）
- Remove Parameter （移除函数）
- Separate Query from Modifier （将查询函数和修改函数分离）
- Parameterize Method （令函数携带参数）
- Replace Parameter with Explicit Methods （以明确函数取代参数）
- Preserve Whole Object （保持对象函数）
- Replace Parameter with Methods （以函数取代参数）
- Introduce Parameter Object （引入参数对象）
- Remove Setting Method （移除设值函数）
- Hide Method （隐藏函数）
- Replace Constructor with Factory Method （以工厂函数取代构造函数）
- Encapsulate Downcast （封装向下转型）
- Replace Error Code with Exception （以异常取代错误码）
- Replace Exception with Test （以测试取代异常）

# 处理概括关系
- Pull Up Field （字段上移）
- Pull Up Method （函数上移）
- Pull Up Constructor Body （构造函数本体上移）
- Push Down Method （函数下移）
- Push Down Field （字段下移）
- Extract Subclass （提炼子类）
- Extract Superclass （提炼超类）
- Extract Interface （提炼接口）
- Collapse Hierarchy （折叠继承体系）
- Form Template Plate Method （塑造模版函数）
- Replace Inheritance with Delegation （以委托取代继承）
- Replace Delegation with Inheritance （以继承取代委托）

# 大型重构
- Tease Apart Inheritance （梳理并分解继承体系）
- Convert Procedural Design to Objects （将过程化设计转化为对象设计）
- Separate Domain from Presentation （将领域和表述／显示分离）
- Extract Hierarchy （提炼继承结构）

# 附录 - 代码的坏味道
- Duplicated Code （重复代码）
- Long Method （过长函数）
- Large Class （过大的类）
- Long Parameter List （过长的函数列）
- Divergent Change （发散式变化）
- Shotgun Surgery （霰弹式变化）
- Feature Envy （依恋情结）
- Data Clumps （数据泥团）
- Primitive Obsession （基本类型偏执）
- Switch Statements （ switch 惊悚现身）
- Parallel Inheritance Hierarchies （平行继承体系）
- Lazy Class （冗赘类）
- Speculative Generality （夸夸其谈未来性）
- Temporary Field （令人迷惑的暂时字段）
- Message Chains （过度耦合的消息链）
- Middle Man （中间人）
- Inappropriate Intimacy （狎昵关系）
- Alternative Classes with Different Interfaces （异曲同工的类）
- Incomplete Library Class （不完美的库类）
- Data Class （纯稚的数据类）
- Refused Bequest （被拒绝的遗赠）
- Comments （过多的注释）


[^1]: 《重构 改善既有代码的设计》人民邮电出版社
