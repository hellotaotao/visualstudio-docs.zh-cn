---
title: 计算代码度量值
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 960c2b546abe3554a5912efde9bd09bb5b2189b7
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835963"
---
# <a name="code-metrics-values"></a>代码度量值

现代软件应用程序的复杂性增加了使代码保持可靠、 可维护的难度也增加。 代码度量是一组软件度量值，使开发人员可以更好地了解他们正在开发的代码。 通过利用代码度量值，开发人员可以了解哪些类型和/或方法应该返工或更全面的测试。 开发团队可以确定潜在风险、 了解项目的当前状态并在软件开发过程中跟踪进度。

开发人员可以使用 Visual Studio 生成代码度量值数据中测量的复杂性和可维护性的托管代码。 可以为整个解决方案或单个项目生成代码度量数据。

有关如何在 Visual Studio 中生成代码度量数据的信息，请参阅[如何：生成代码度量数据](../code-quality/how-to-generate-code-metrics-data.md)。

## <a name="software-measurements"></a>软件度量值

以下列表显示了代码 Visual Studio 计算的度量值结果：

- **可维护性指数**-计算表示相对轻松地维护代码的索引值介于 0 和 100 之间。 较高的值意味着更好的可维护性。 可以使用颜色编码，分级来快速确定在代码中的故障点。 绿色等级 20 到 100 之间，该值指示代码具有良好的可维护性。 黄色等级介于 10 到 19 之间，指示代码可维护性中等。 红色等级 0 到 9 之间的分级，表示可维护性低。 有关详细信息，请参阅[可维护性索引范围和含义](https://blogs.msdn.microsoft.com/codeanalysis/2007/11/20/maintainability-index-range-and-meaning/)博客文章。

- **圈复杂度**-衡量代码的结构化的复杂程度。 通过计算该程序的流中的不同代码路径数则创建它。 具有复杂的控制流的程序需要更多测试来实现良好的代码覆盖率，且不太易于维护。 有关详细信息，请参阅[圈复杂度的 Wikipedia 条目](https://wikipedia.org/wiki/Cyclomatic_complexity)。

- **继承深度**-指示从另一个，按原路返回到基类继承的不同类的数目。 继承深度是类似于类耦合度，因为在基类中的更改可能会影响任何其继承的类。 更高级此数字，更深入地继承和基类的修改，导致重大的更高版本可能更改。 继承深度，最好使用较低的值和较高的值无效。

- **类耦合**-衡量与通过参数、 局部变量、 返回类型、 方法调用、 泛型或模板实例化、 基类，这些类、 接口实现、 外部类型上定义的字段的唯一类耦合程度和特性修饰。 类型和方法应具有高度内聚和较低的耦合，决定了优秀的软件设计。 高的耦合度表示设计，很难进行重复使用和维护由于其许多其他类型相互依赖关系。 有关详细信息，请参阅[类耦合度](https://blogs.msdn.microsoft.com/zainnab/2011/05/25/code-metrics-class-coupling/)博客文章。

- **代码行**-指示的代码中的行的大致数目。 计数为基础的 IL 代码，因此不精确的源代码文件中的行数。 计数过高可能表示一个类型或方法尝试执行的操作过多的工作，应进行拆分。 它还可能指示类型或方法可能很难维护。

   > [!NOTE]
   > [命令行版本](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics)代码的指标工具计算实际行代码，因为它分析而不是 IL 的源代码。

## <a name="anonymous-methods"></a>匿名方法

*匿名方法*就是没有名称的方法。 匿名方法最常用于将代码块作为委托参数传递。 代码度量结果成员中声明的匿名方法，如方法或访问器，声明了方法的成员与相关联。 它们不会调用方法的成员与相关联。

## <a name="generated-code"></a>生成的代码

某些软件工具和编译器生成的代码的添加到项目和项目开发人员看不到或不应更改。 大多数情况下，代码度量值在计算度量值时忽略生成的代码。 这样，以反映开发人员可以查看和更改的指标值。

为 Windows 窗体生成的代码不忽略，因为它是开发人员可以查看和更改的代码。

## <a name="next-steps"></a>后续步骤

- [如何：生成代码度量数据](../code-quality/how-to-generate-code-metrics-data.md)
- [使用代码度量结果窗口](../code-quality/working-with-code-metrics-data.md)
