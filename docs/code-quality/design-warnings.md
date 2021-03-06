---
title: 设计警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.designrules
helpviewer_keywords:
- design warnings
- managed code analysis warnings, design warnings
- warnings, design
ms.assetid: 34e65a18-560c-423f-814f-519089e318cf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8da8b003f74b21ab0a6178742c28f85423dd2ec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816794"
---
# <a name="design-warnings"></a>设计警告
设计警告支持对.NET Framework 设计准则的遵从性。

## <a name="in-this-section"></a>本节内容

| 规则 | 描述 |
| - | - |
| [CA1000:不要在泛型类型中声明静态成员](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md) | 调用泛型类型的静态成员时，必须指定该类型的类型参数。 当调用不支持推理的泛型实例成员时，必须指定该成员的类型参数。 在上述两种情况下，用于指定类型自变量的语法不同，但很容易混淆。 |
| [CA1001：具有可释放字段的类型应该是可释放的](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md) | 一个类声明并实现 System.IDisposable 类型的实例字段和类不实现 IDisposable。 声明 IDisposable 字段的类间接拥有非托管资源，并且应该实现 IDisposable 接口。 |
| [CA1002:不要公开泛型列表](../code-quality/ca1002-do-not-expose-generic-lists.md) | System.Collections.Generic.List < (的\<(T >) >) 是专为性能，不继承的泛型集合。 因此，List 不包含任何虚拟成员。 应改为公开针对继承设计的泛型集合。 |
| [CA1003:使用泛型事件处理程序实例](../code-quality/ca1003-use-generic-event-handler-instances.md) | 一种类型包含一个委托，它返回 void，其签名包含两个参数 （一个的对象的第一个和第二个是分配给 EventArgs 的类型） 和包含程序集针对[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]。 |
| [CA1004:泛型方法应提供类型参数](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md) | 推理是指由传递给泛型方法的自变量类型来确定该方法的类型参数，而不是显式指定类型参数。 若要启用推理，泛型方法的参数签名必须包含与该方法的类型参数属于相同类型的参数。 在这种情况下，不必指定类型参数。 对所有类型参数使用推理，用于调用泛型和非泛型实例方法语法完全相同;这简化了泛型方法的可用性。 |
| [CA1005:避免泛型类型参数过多](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md) | 泛型类型包含的类型参数越多，越难以知道并记住每个类型参数各代表什么。 它是使用一个类型参数，如下所示列表通常明显\<T >，并在某些情况下，使用两个类型参数，如\<TKey，TValue >。 但是，如果存在两个以上的类型参数，则大多数用户都会感到过于困难。 |
| [CA1006:不要将嵌套在成员签名中的泛型类型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md) | 嵌套类型参数是一个类型参数，也是一个泛型类型。 若要调用签名包含嵌套类型参数的成员，用户必须实例化一个泛型类型，并将此类型传递到另一个泛型类型的构造函数。 所需的过程和语法很复杂，应当避免。 |
| [CA1007： 在适用处在适用处使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md) | 外部可见方法包含类型为 System.Object 的引用参数。 使用泛型方法使受约束的所有类型都可以传递给该方法，而比不先将类型强制转换为引用参数类型。 |
| [CA1008:枚举应具有零值](../code-quality/ca1008-enums-should-have-zero-value.md) | 像其他值类型一样，未初始化枚举的默认值为零。 无标志特性化枚举应定义一个成员，通过使用值为零，默认值枚举的有效值。 如果应用了 FlagsAttribute 特性的枚举定义值为零成员，则该成员的名称应为“None”，以指示枚举中尚未设置值。 |
| [CA1009:正确声明事件处理程序](../code-quality/ca1009-declare-event-handlers-correctly.md) | 事件处理程序方法采用两个参数。 第一个参数属于 System.Object 类型，名为“sender”。 它是引发事件的对象。 第二个参数属于 System.EventArgs 类型，名为“e”。 这是与该事件关联的数据。 事件处理程序方法不应返回值；在 C# 编程语言中，这由返回类型 void 指示。 |
| [CA1010:集合应实现泛型接口](../code-quality/ca1010-collections-should-implement-generic-interface.md) | 若要扩大集合的用途，应实现某个泛型集合接口。 然后，可以使用该集合来填充泛型集合类型。 |
| [CA1011:请考虑将基类型作为参数传递](../code-quality/ca1011-consider-passing-base-types-as-parameters.md) | 在方法声明中将基类型指定为参数时，可以将派生自基类型的任何类型作为相应的参数传递给方法。 如果不需要派生参数类型提供的其他功能，则使用基类型将使方法可以得到更广泛的使用。 |
| [CA1012:抽象类型不应具有构造函数](../code-quality/ca1012-abstract-types-should-not-have-constructors.md) | 抽象类型的构造函数只能由派生类型调用。 由于公共构造函数用于创建类型的实例，但无法为抽象类型创建实例，因此具有公共构造函数的抽象类在设计上是错误的。 |
| [CA1013:重载相等运算符，加法和减法](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md) | 公共或受保护类型实现加或减运算符时没有实现相等运算符。 |
| [CA1014:用 CLSCompliantAttribute 标记程序集](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md) | 公共语言规范 (CLS) 定义了程序集在跨编程语言使用时必须符合的命名限制、数据类型和规则。 好的设计要求所有程序集显式使用 CLSCompliantAttribute 指示 CLS 遵从性。 如果程序集没有此特性，则该程序集即不合规。 |
| [CA1016:用 AssemblyVersionAttribute 标记程序集](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md) | .NET Framework 使用版本号唯一地标识程序集，以及如何绑定到强名称程序集中的类型。 版本号与版本和发行者策略一起使用。 默认情况下，仅使用用于生成应用程序的程序集版本运行应用程序。 |
| [CA1017:用 ComVisibleAttribute 标记程序集](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md) | ComVisibleAttribute 决定 COM 客户端如何访问托管代码。 合理的设计指出程序集将显式指示 COM 可见性。 可以设置整个程序集的 COM 可见性，然后重写各个类型和类型成员的 COM 可见性。 如果此特性不存在，则程序集的内容对 COM 客户端可见。 |
| [CA1018:用 AttributeUsageAttribute 标记特性](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md) | 当定义自定义特性时，用 AttributeUsageAttribute 标记该特性，以指示源代码中可以应用自定义特性的位置。 特性的含义和预定用法将决定它在代码中的有效位置。 |
| [CA1019:定义特性参数的访问器](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) | 特性可以定义强制自变量，在对目标应用该特性时必须指定这些自变量。 这些自变量也称为位置自变量，因为它们将作为位置参数提供给特性构造函数。 对于每一个强制自变量，特性还必须提供一个相应的只读属性，以便可以在执行时检索该自变量的值。 特性还可以定义可选自变量，可选自变量也称为命名自变量。 这些变量按名称提供给特性构造函数，并且必须具有相应的读/写属性。 |
| [CA1020:避免使用类型极少的命名空间](../code-quality/ca1020-avoid-namespaces-with-few-types.md) | 请确保每个命名空间有一个逻辑组织，并且你必须将类型放入稀疏填充的命名空间的正当理由。 |
| [CA1021:避免使用 out 参数](../code-quality/ca1021-avoid-out-parameters.md) | 通过引用（使用 out 或 ref）传递类型要求具有使用指针的经验，了解值类型和引用类型的不同之处，以及能处理具有多个返回值的方法。 另外，out 和 ref 参数之间的差异没有得到广泛了解。 |
| [CA1023:索引器不应是多维](../code-quality/ca1023-indexers-should-not-be-multidimensional.md) | 索引器（即索引属性）应该使用一个索引。 多维索引器会大大降低库的可用性。 |
| [CA1024： 在适用处在适用处使用属性](../code-quality/ca1024-use-properties-where-appropriate.md) | 公共或受保护方法的名称以“Get”开头，没有采用任何参数或返回的值不是数组。 该方法可能很适于成为属性。 |
| [CA1025:用形参数组替换重复的实参](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md) | 如果参数的具体数量未知且变量参数为相同类型或可作为相同类型传递，请使用参数数组代替重复参数。 |
| [CA1026:不应使用默认参数](../code-quality/ca1026-default-parameters-should-not-be-used.md) | CLS 中允许使用默认参数的方法；但是 CLS 允许编译器忽略为这些参数分配的值。 为了跨编程语言维护所需的行为，必须使用提供默认参数的方法重载来替换使用默认参数的方法。 |
| [CA1027:用 FlagsAttribute 标记枚举](../code-quality/ca1027-mark-enums-with-flagsattribute.md) | 枚举是一种值类型，它定义一组相关的已命名常数。 如果可以按照有意义的方式组合一个枚举的已命名常数，则对该枚举应用 FlagsAttribute。 |
| [CA1028:枚举存储应为 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md) | 枚举是一种值类型，它定义一组相关的已命名常数。 默认情况下，System.Int32 数据类型用于存储常量值。 尽管可以更改此基础类型，它不要求或不推荐用于大多数方案。 |
| [CA1030： 在适用处在适用处使用事件](../code-quality/ca1030-use-events-where-appropriate.md) | 该规则检测名称通常用于事件的方法。 如果为响应明确定义的状态更改而调用一个方法，则应由事件处理程序调用该方法。 调用该方法的对象应引发事件而不是直接调用该方法。 |
| [CA1031:不要捕捉一般异常类型](../code-quality/ca1031-do-not-catch-general-exception-types.md) | 不应捕捉一般异常。 捕捉更具体的异常，或在 catch 块中重新引发一般异常作为最后一条语句。 |
| [CA1032:实现标准异常构造函数](../code-quality/ca1032-implement-standard-exception-constructors.md) | 如果不能提供完整的构造函数集，要正确处理异常将变得比较困难。 |
| [CA1033:接口方法应可由子类型调用](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md) | 未密封的外部可见类型提供了显式实现公共接口的方法，但没有提供具有相同名称的其他外部可见方法。 |
| [CA1034:嵌套的类型不应是可见](../code-quality/ca1034-nested-types-should-not-be-visible.md) | 嵌套类型是在另一个类型的范围中声明的类型。 嵌套类型用于封装包含类型的私有实现详细信息。 如果用于此用途，则嵌套类型不应是外部可见的。 |
| [CA1035:ICollection 实现含有强类型成员](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md) | 此规则要求 ICollection 实现提供强类型成员，以使用户在使用该接口提供的功能时不必将自变量强制转换成 Object 类型。 此规则假定实现 ICollection 的类型这样做是为了管理其类型强于对象的实例的集合。 |
| [CA1036:重写可比较类型的方法](../code-quality/ca1036-override-methods-on-comparable-types.md) | 公共或受保护类型实现 System.IComparable 接口。 它不重写 Object.Equals，也不重载表示相等、不等、小于或大于的语言特定运算符。 |
| [CA1038:枚举数应强类型化](../code-quality/ca1038-enumerators-should-be-strongly-typed.md) | 此规则要求 IEnumerator 实现还提供 Current 属性的强类型版本，以使用户在使用该接口提供的功能时不必将返回值强制转换为强类型。 |
| [CA1039:列表已强类型化](../code-quality/ca1039-lists-are-strongly-typed.md) | 此规则要求 IList 实现提供强类型成员，以使用户在使用该接口提供的功能时不必将自变量强制转换成 System.Object 类型。 |
| [CA1040:避免使用空接口](../code-quality/ca1040-avoid-empty-interfaces.md) | 接口定义提供某个行为或使用协定的成员。 接口所描述的功能可以被任何类型采用，而不管该类型出现在继承层次结构中的哪个位置。 类型通过实现接口的成员来实现接口。 空接口无法定义任何成员；因此，它无法定义可以实现的协定。 |
| [CA1041:提供 ObsoleteAttribute 消息](../code-quality/ca1041-provide-obsoleteattribute-message.md) | 用未指定其 ObsoleteAttribute.Message 属性的 System.ObsoleteAttribute 特性来标记类型或成员。 编译的类型或成员，用 ObsoleteAttribute 标记后，将显示该属性的消息属性，其中提供了有关已过时的类型或成员的用户信息。 |
| [CA1043:使用整型或字符串参数用于索引器](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md) | 索引器（即索引属性）应将整型或字符串类型用于索引。 这些类型一般用于为数据结构编制索引，并且提高库的可用性。 应仅限于在设计时无法指定特定整型或字符串类型的情况下使用 Object 类型。 |
| [CA1044:属性不应是只写的](../code-quality/ca1044-properties-should-not-be-write-only.md) | 虽然可以接受且经常需要使用只读属性，但设计准则禁止使用只写属性。 这是因为允许用户设置值但又禁止该用户查看这个值不能提供任何安全性。 而且，如果没有读访问，将无法查看共享对象的状态，使其用处受到限制。 |
| [CA1045:不要通过引用来传递类型](../code-quality/ca1045-do-not-pass-types-by-reference.md) | 通过引用（使用 out 或 ref）传递类型要求具有使用指针的经验，了解值类型和引用类型的不同之处，以及能处理具有多个返回值的方法。 为一般用户进行设计的库架构师不应指望用户能熟练运用 out 或 ref 参数。 |
| [CA1046:请重载相等运算符对引用类型](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md) | 对于引用类型，相等运算符的默认实现几乎始终是正确的。 默认情况下，仅当两个引用指向同一对象时，它们才相等。 |
| [CA1047:不要声明在密封类型中的受保护的成员](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md) | 类型声明受保护的成员，使继承类型可以访问或重写该成员。 按照定义，不能继承密封类型，这表示不能调用密封类型上的受保护方法。 |
| [CA1048:不要声明在密封类型中的虚拟成员](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md) | 类型将方法声明为虚方法，使继承类型可以重写虚方法的实现。 按照定义，不能继承密封类型。 这使得虚方法对于密封类型没有意义。 |
| [CA1049:拥有本机资源的类型应是可释放的](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md) | 分配非托管资源的类型应该实现 IDisposable，以使调用方可以根据需要释放这些资源，并缩短持有这些资源的对象的生存期。 |
| [CA1050:在命名空间中声明类型](../code-quality/ca1050-declare-types-in-namespaces.md) | 应在命名空间内声明类型以避免名称冲突，并作为一种在对象层次结构中组织相关类型的方式。 |
| [CA1051:不要声明可见实例字段](../code-quality/ca1051-do-not-declare-visible-instance-fields.md) | 字段的主要用途应是作为实现的详细信息。 字段应为 private 或 internal，并应通过使用属性公开这些字段。 |
| [CA1052:应密封静态容器类型](../code-quality/ca1052-static-holder-types-should-be-sealed.md) | 公共或受保护类型仅包含静态成员，并且不使用密封的 (C#) 或 NotInheritable (Visual Basic) 修饰符声明。 应使用 sealed 修饰符标记不希望被继承的类型，以免将其用作基类型。 |
| [CA1053:静态容器类型不应具有构造函数](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md) | 公共或嵌套公共类型只声明了静态成员，但具有公共或受保护的默认构造函数。 由于调用静态成员不需要类型的示例，因此没必要使用构造函数。 为安全起见，字符串重载应使用字符串自变量调用统一资源标识符 (URI) 重载。 |
| [CA1054:URI 参数不应为字符串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md) | 如果某方法采用 URI 的字符串表示形式，则应提供采用 URI 类的实例的相应重载，该重载以安全的方式提供这些服务。 |
| [CA1055:URI 返回值不应为字符串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md) | 此规则假定该方法返回 URI。 URI 的字符串表示形式容易导致分析和编码错误，并且可造成安全漏洞。 System.Uri 类以一种安全的方式提供这些服务。 |
| [CA1056:URI 属性不应为字符串](../code-quality/ca1056-uri-properties-should-not-be-strings.md) | 此规则假定该属性表示的 URI。 URI 的字符串表示形式容易导致分析和编码错误，并且可造成安全漏洞。 System.Uri 类以一种安全的方式提供这些服务。 |
| [CA1057:字符串 URI 重载调用 System.Uri 重载](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md) | 某个类型声明的方法重载与 System.Uri 参数仅在字符串参数的放置方面有所不同。 采用字符串参数的重载不调用采用 URI 参数的重载。 |
| [CA1058:类型不应扩展某些基类型](../code-quality/ca1058-types-should-not-extend-certain-base-types.md) | 外部可见的类型扩展某些基类型。 请使用某个备选项。 |
| [CA1059:成员不应公开某些具体类型](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md) | 具体类型是指具有一个完整实现因此可以实例化的类型。 若要使成员可以得到广泛使用，请使用建议的接口来替换具体类型。 |
| [CA1060:将 P/Invoke 移动到 NativeMethods 类](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md) | 平台调用方法，例如那些标有<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>或通过使用中的 Declare 关键字定义的方法[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，访问非托管的代码。 这些方法应属于 NativeMethods、SafeNativeMethods 或 UnsafeNativeMethods 类。 |
| [CA1061:不要隐藏基类方法](../code-quality/ca1061-do-not-hide-base-class-methods.md) | 如果派生方法的参数签名只是在类型方面有所不同，而且与基方法的参数签名中的对应类型相比，这些类型的派生方式更弱，则基类型中的方法由派生类型中的同名方法隐藏。 |
| [CA1062:验证公共方法的参数](../code-quality/ca1062-validate-arguments-of-public-methods.md) | 对于传递给外部可见方法的所有引用自变量，都应检查其是否为 null。 |
| [CA1063:正确实现 IDisposable](../code-quality/ca1063-implement-idisposable-correctly.md) | 所有的 IDisposable 类型都应当正确实现 Dispose 模式。 |
| [CA1064:异常应该是公共的](../code-quality/ca1064-exceptions-should-be-public.md) | 内部异常仅在其自己的内部范围内可见。 当异常超出内部范围后，只能使用基异常来捕获该异常。 如果内部异常继承自<xref:System.Exception?displayProperty=fullName>， <xref:System.SystemException?displayProperty=fullName>，或<xref:System.ApplicationException?displayProperty=fullName>，外部代码将没有足够的信息来了解应如何处理异常。 |
| [CA1065:不会引发意外的位置中的异常](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | 不应引发异常的方法引发了异常。 |
| [CA2210:程序集应具有有效的强名称](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md) | 强名称可避免客户端在不知情的情况下加载已被篡改的程序集。 除非极为有限的几种情况，否则不应部署没有强名称的程序集。 如果共享或发布未正确签名的程序集，则该程序集可能被篡改，公共语言运行时可能不会加载该程序集；而用户可能必须在他/她的计算机上禁用验证。 |