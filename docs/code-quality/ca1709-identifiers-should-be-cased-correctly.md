---
title: CA1709:标识符的大小写应当正确
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 864918b7ce394e9f096c6fa9dea9389957983177
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921775"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709:标识符的大小写应当正确

|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|类别|Microsoft.Naming|
|是否重大更改|中断-在程序集、命名空间、类型、成员和参数上引发。<br /><br /> 不间断-当对泛型类型参数引发时。|

## <a name="cause"></a>原因

标识符的名称的大小写不正确。

\- 或 -

标识符的名称包含两个字母的首字母缩略词, 第二个字母为小写。

\- 或 -

标识符的名称包含三个或更多大写字母的首字母缩写词。

## <a name="rule-description"></a>规则说明

命名约定为面向公共语言运行时的库提供了通用的外观。 此一致性可减少新软件库所需的学习曲线, 并使客户对库开发的用户信心更有把握, 这是一位具有开发托管代码的专业技能。

按照约定, 参数名称使用 camel 大小写, 命名空间、类型和成员名称使用 Pascal 大小写。 在 camel 大小写格式的名称中, 第一个字母为小写, 名称中任何剩余单词的第一个字母为大写。 大小写大小写的名称的`packetSniffer`示例`ioFile`包括、 `fatalErrorCode`和。 在 Pascal 大小写名称中, 第一个字母为大写, 名称中任何剩余单词的第一个字母为大写。 Pascal 大小写的名称的示例`PacketSniffer`包括`IOFile`、和`FatalErrorCode`。

此规则根据大小写将名称拆分为几个词, 并根据一系列常见的双字母词 (如 "In" 或 "My") 检查任意两个字母的词。 如果找不到匹配项, 则假定该单词为首字母缩写词。 此外, 此规则假定在名称中包含四个大写字母的行或名称末尾行中的三个大写字母时, 此规则将假定为首字母缩写词。

按照约定, 两字母缩写词使用全部大写字母, 三个或更多字符的首字母缩写词使用 Pascal 大小写形式。 下面的示例使用此命名约定:"DB"、"CR"、"Cpa" 和 "Ecma"。 以下示例违反约定:"Io"、"XML" 和 "DoD" 以及非参数名称 "xp" 和 "cpl"。

"ID" 是特例, 导致违反此规则。 “Id”不是首字母缩略词，而是“identification”的缩写。

## <a name="how-to-fix-violations"></a>如何解决冲突

更改名称, 使其大小写正确。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告

如果你有自己的命名约定, 或者标识符表示正确的名称 (例如, 公司或技术的名称), 则可以安全地禁止显示此警告。

您还可以将特定的词、缩写和首字母缩写添加到代码分析自定义字典中。 自定义字典中指定的条款将不会导致违反此规则。 有关详细信息，请参阅[如何：自定义代码分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)。

## <a name="related-rules"></a>相关规则

[CA1708标识符的差别应超过大小写](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)