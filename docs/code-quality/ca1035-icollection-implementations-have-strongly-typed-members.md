---
title: CA1035:ICollection 实现含有强类型成员
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a20feb514b87f2906fd4db32dfb38d3d9b661999
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922831"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035:ICollection 实现含有强类型成员

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|类别|Microsoft.Design|
|是否重大更改|重大|

## <a name="cause"></a>原因
公共或受保护类型实现<xref:System.Collections.ICollection?displayProperty=fullName> , 但没有为<xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>提供强类型化方法。 的<xref:System.Collections.ICollection.CopyTo%2A>强类型版本必须接受两个参数, 并且不能<xref:System.Array?displayProperty=fullName>将或数组<xref:System.Object?displayProperty=fullName>作为其第一个参数。

## <a name="rule-description"></a>规则说明
此规则要求<xref:System.Collections.ICollection>实现提供强类型成员, 使用户在使用该接口提供的功能时无<xref:System.Object>需将参数转换为类型。 此规则假定实现<xref:System.Collections.ICollection>的类型执行此操作是为了管理比<xref:System.Object>更强的类型的实例集合。

 <xref:System.Collections.ICollection> 实现 <xref:System.Collections.IEnumerable?displayProperty=fullName> 接口。 如果集合中的对象已扩展<xref:System.ValueType?displayProperty=fullName>, 则必须为<xref:System.Collections.IEnumerable.GetEnumerator%2A>提供强类型成员, 以避免由装箱导致的性能降低。 当集合的对象为引用类型时, 这不是必需的。

若要实现接口成员的强类型版本, 请使用形式`InterfaceName.InterfaceMemberName`的名称 ( <xref:System.Collections.ICollection.CopyTo%2A>例如) 显式实现接口成员。 显式接口成员使用接口声明的数据类型。 使用接口成员名称 (如<xref:System.Collections.ICollection.CopyTo%2A>) 实现强类型成员。 将强类型成员声明为公共成员, 并将参数和返回值声明为集合管理的强类型。 强类型取代了接口所声明的<xref:System.Object>更<xref:System.Array>弱类型, 如和。

## <a name="how-to-fix-violations"></a>如何解决冲突
若要修复与此规则的冲突, 请显式实现接口成员 (将其<xref:System.Collections.ICollection.CopyTo%2A>声明为)。 添加已声明为`CopyTo`的 public 强类型成员, 并使其采用强类型化数组作为其第一个参数。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
如果实现新的基于对象的集合 (如二进制树, 其中扩展新集合的类型确定强类型), 则禁止显示此规则发出的警告。 这些类型应符合此规则并公开强类型成员。

## <a name="example"></a>示例
下面的示例演示了实现<xref:System.Collections.ICollection>的正确方法。

[!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>相关规则
[CA1038枚举数应强类型化](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

[CA1039列表已强类型化](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>请参阅

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>