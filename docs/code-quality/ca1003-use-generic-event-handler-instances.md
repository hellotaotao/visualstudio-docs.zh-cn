---
title: CA1003:使用泛型事件处理程序实例
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a1ef4258d1b095395be34c7004e3f783b973897d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547875"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003:使用泛型事件处理程序实例

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|类别|Microsoft.Design|
|是否重大更改|重大|

## <a name="cause"></a>原因

类型包含一个委托, 该委托返回 void, 其签名包含两个参数 (第一个对象, 第二个参数是可分配给 EventArgs 的类型), 并且包含程序集面向 .NET。

默认情况下, 此规则仅查看外部可见类型, 但这是[可配置](#configurability)的。

## <a name="rule-description"></a>规则说明

在 .net 之前, 若要将自定义信息传递到事件处理程序, 必须将新委托声明为指定派生自<xref:System.EventArgs?displayProperty=fullName>类的类。 在 .net 中, 泛型<xref:System.EventHandler%601?displayProperty=fullName>委托允许将派生自<xref:System.EventArgs>的任何类与事件处理程序一起使用。

## <a name="how-to-fix-violations"></a>如何解决冲突

若要修复与此规则的冲突, 请删除委托, 并使用<xref:System.EventHandler%601?displayProperty=fullName>委托替换其使用。

如果委托由 Visual Basic 编译器自动生成, 请更改事件声明的语法以使用<xref:System.EventHandler%601?displayProperty=fullName>委托。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告

不禁止显示此规则发出的警告。

## <a name="configurability"></a>配置

如果从[FxCop 分析器](install-fxcop-analyzers.md)(而不是传统分析) 运行此规则, 则可以根据其可访问性, 将基本代码的哪些部分配置为在上运行此规则。 例如, 若要指定规则只应针对非公共 API 图面运行, 请在项目中的 editorconfig 文件中添加以下键/值对:

```ini
dotnet_code_quality.ca1003.api_surface = private, internal
```

您可以为此规则、所有规则或此类别中的所有规则 (设计) 配置此选项。 有关详细信息, 请参阅[配置 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>示例

下面的示例演示了违反规则的委托。 在 Visual Basic 示例中, 注释说明了如何修改示例以满足规则。 C#例如, 下面的示例演示了修改后的代码。

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

下面的代码片段将从上一个示例中删除满足规则的委托声明。 它通过使用`ClassThatRaisesEvent` `ClassThatHandlesEvent` 委托替换和方法中的使用<xref:System.EventHandler%601?displayProperty=fullName> 。

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>相关规则

- [CA1005避免泛型类型的参数过多](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010集合应实现泛型接口](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000不要在泛型类型中声明静态成员](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002不要公开泛型列表](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006不要将泛型类型嵌套在成员签名中](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004泛型方法应提供类型参数](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007在适当的位置使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>请参阅

- [泛型](/dotnet/csharp/programming-guide/generics/index)