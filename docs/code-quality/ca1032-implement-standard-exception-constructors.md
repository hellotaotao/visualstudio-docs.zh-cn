---
title: CA1032:实现标准异常构造函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b294b267aa7bb1a2912ed42807ac0f878c87838
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547655"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032:实现标准异常构造函数

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|类别|Microsoft.Design|
|是否重大更改|不间断|

## <a name="cause"></a>原因

类型扩展<xref:System.Exception?displayProperty=fullName>但不声明所有必需的构造函数。

## <a name="rule-description"></a>规则说明

异常类型必须实现以下三个构造函数:

- public NewException ()

- public NewException (字符串)

- public NewException (string, Exception)

此外, 如果您运行的是旧的 FxCop 分析, 而不是[基于 .NET Compiler Platform 的 fxcop 分析器](../code-quality/roslyn-analyzers-overview.md), 则缺少第四个构造函数也会生成冲突:

- protected 或 private NewException (SerializationInfo, StreamingContext)

如果不能提供完整的构造函数集，要正确处理异常将变得比较困难。 例如, 具有签名`NewException(string, Exception)`的构造函数用于创建由其他异常导致的异常。 如果不使用此构造函数, 则不能创建和引发包含内部 (嵌套) 异常的自定义异常的实例, 在这种情况下, 托管代码应执行此操作。

前三个异常构造函数按约定公开。 第四个构造函数在非密封类中受保护, 在密封类中是私有的。 有关详细信息, 请[参阅 CA2229:实现序列化](../code-quality/ca2229-implement-serialization-constructors.md)构造函数。

## <a name="how-to-fix-violations"></a>如何解决冲突

若要修复与此规则的冲突, 请将缺少的构造函数添加到异常, 并确保它们具有正确的可访问性。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告

如果冲突是通过对公共构造函数使用不同访问级别引起的, 则可以安全地禁止显示此规则发出的警告。 此外, 如果您要生成可移植类库 (PCL `NewException(SerializationInfo, StreamingContext)` ), 则可以取消构造函数的警告。

## <a name="example"></a>示例

下面的示例包含违反此规则的异常类型以及正确实现的异常类型。

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>请参阅

[CA2229：实现序列化构造函数](../code-quality/ca2229-implement-serialization-constructors.md)