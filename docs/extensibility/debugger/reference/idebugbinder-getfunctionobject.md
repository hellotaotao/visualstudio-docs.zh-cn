---
title: IDebugBinder::GetFunctionObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 03078a09de94b886a659059192a5b67430cb5137
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337663"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
此方法获取[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)对象，用于创建函数的参数。

## <a name="syntax"></a>语法

```cpp
HRESULT GetFunctionObject( 
   IDebugFunctionObject **ppFunction
);
```

```csharp
int GetFunctionObject(
   out IDebugFunctionObject ppFunction
);
```

## <a name="parameters"></a>参数
`ppFunction`\
[out]返回[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)用于创建函数参数的接口。

## <a name="return-value"></a>返回值
 如果成功，则返回 S_OK;否则，返回错误代码。

## <a name="see-also"></a>请参阅
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)