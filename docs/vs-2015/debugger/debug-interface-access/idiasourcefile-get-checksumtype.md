---
title: 'Idiasourcefile:: Get_checksumtype |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd51a553cab29ac7741eaa91ada356897551e12a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47480168"
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主题的最新版本，请参阅[idiasourcefile:: Get_checksumtype](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasourcefile-get-checksumtype)。  
  
检索的校验和类型。  
  
## <a name="syntax"></a>语法  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pRetVal`  
 [out]返回校验和类型。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 校验和类型是可以映射到校验和算法的值。 例如，在标准的 PDB 文件格式可以通常具有下列值之一：  
  
|校验和类型|CryptoAPI 标签|描述|  
|-------------------|---------------------|-----------------|  
|0|\<无 >|不存在的校验和。|  
|1|`CALG_MD5`|使用 MD5 哈希算法生成的校验和。|  
|2|`CALG_SHA1`|使用 SHA1 哈希算法生成的校验和。|  
  
 `CryptoAPI`标签是从`ALG_ID`枚举。 哈希算法的详细信息，请查阅`CryptoAPI`部分中的 Microsoft [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)]。  
  
 若要获取的源文件的实际校验和字节，请调用[idiasourcefile:: Get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)方法。  
  
## <a name="see-also"></a>请参阅  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)


