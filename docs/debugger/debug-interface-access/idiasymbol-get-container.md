---
title: 'Idiasymbol:: Get_container |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23b8d43931b880ff61ec9871f9f5984b98833c28
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2019
ms.locfileid: "64787892"
---
# <a name="idiasymbolgetcontainer"></a>IDiaSymbol::get_container
此函数检索指向表示父/容器的此符号的符号。

## <a name="syntax"></a>语法

```C++
HRESULT get_container(
   IDiaSymbol **pRetVal
);
```

#### <a name="parameters"></a>参数
 `pRetVal`

[out]返回一个指向`IDiaSymbol`包含有关容器的此符号的信息。

## <a name="return-value"></a>返回值
 如果成功，则返回 S_OK;否则，返回 S_FALSE 或错误代码。

> [!NOTE]
> 返回值为 S_FALSE 表示该属性不是可用于符号。

## <a name="requirements"></a>要求

|需求|描述|
|-----------------|-----------------|
|标头：|dia2.h|
|版本：|DIA SDK v8.0|

## <a name="see-also"></a>请参阅
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)