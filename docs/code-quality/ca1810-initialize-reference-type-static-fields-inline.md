---
title: CA1810:以内联方式初始化引用类型的静态字段
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8838de46c6b14f698194f343aebec30402452970
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921531"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810:以内联方式初始化引用类型的静态字段

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|类别|Microsoft.Performance|
|是否重大更改|不间断|

## <a name="cause"></a>原因
引用类型声明显式静态构造函数。

## <a name="rule-description"></a>规则说明
当一个类型声明显式静态构造函数时，实时 (JIT) 编译器会向该类型的每个静态方法和实例构造函数中添加一项检查，以确保之前已调用该静态构造函数。 当访问任何静态成员或创建类型的实例时, 将触发静态初始化。 但是, 如果您声明一个类型的变量, 但不使用它, 则不会触发静态初始化, 如果初始化更改全局状态, 这可能很重要。

当所有静态数据都以内联方式初始化并且未声明显式静态构造函数时, Microsoft 中间语言 (MSIL) 编译器`beforefieldinit`会将标志和隐式静态构造函数 (该构造函数初始化静态数据) 添加到 MSIL 类型定义. 当 JIT 编译器遇到`beforefieldinit`标志时, 大多数情况下不会添加静态构造函数检查。 在访问静态方法之前, 但在调用静态方法或实例构造函数之前, 不能保证静态初始化在访问任何静态字段之前发生。 请注意, 在声明类型的变量后, 可能会随时发生静态初始化。

静态构造函数检查会降低性能。 通常, 静态构造函数仅用于初始化静态字段, 在这种情况下, 必须仅确保在首次访问静态字段之前发生静态初始化。 此`beforefieldinit`行为适用于这些类型和大多数其他类型。 仅当静态初始化影响全局状态并且满足以下任一条件时, 它才是不适当的:

- 全局状态的影响非常昂贵, 如果未使用该类型, 则不需要这样做。

- 可以在不访问类型的任何静态字段的情况下访问全局状态效果。

## <a name="how-to-fix-violations"></a>如何解决冲突
要修复与该规则的冲突，请在声明它时初始化所有静态数据并移除静态构造函数。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
如果性能不是问题, 则可以安全地禁止显示此规则发出的警告;或者, 如果静态初始化导致的全局状态更改很昂贵, 或者必须保证在调用类型的静态方法或创建类型的实例之前发生。

## <a name="example"></a>示例

下面的示例演示了一个类型`StaticConstructor`, 该类型违反了规则和一个类型`NoStaticConstructor`, 该类型使用内联初始化替换静态构造函数来满足规则。

[!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
[!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]

请注意, 在`beforefieldinit` `NoStaticConstructor`类的 MSIL 定义上添加标志。

```
.class public auto ansi StaticConstructor
extends [mscorlib]System.Object
{
} // end of class StaticConstructor

.class public auto ansi beforefieldinit NoStaticConstructor
extends [mscorlib]System.Object
{
} // end of class NoStaticConstructor
```

## <a name="related-rules"></a>相关规则

- [CA2207以内联方式初始化值类型的静态字段](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)