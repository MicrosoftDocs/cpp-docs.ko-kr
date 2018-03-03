---
title: _variant_t::ChangeType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
dev_langs:
- C++
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5fb59090ebc4c6ff9120e813ae12a9defbe618b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType
**Microsoft 전용**  
  
 종류를 변경 하는 `_variant_t` 표시 된 개체 **VARTYPE**합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
      void ChangeType(  
   VARTYPE vartype,  
   const _variant_t* pSrc = NULL   
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `vartype`  
 **VARTYPE** 이 `_variant_t` 개체입니다.  
  
 `pSrc`  
 변환할 `_variant_t` 개체의 포인터입니다. 이 값이 **NULL**, 변환은 위치에서 수행 됩니다.  
  
## <a name="remarks"></a>설명  
 이 멤버 함수는 변환 된 `_variant_t` 개체를 지정 된 **VARTYPE**합니다. 경우 `pSrc` 은 **NULL**, 변환이 수행 되 준비, 그렇지 않으면이 `_variant_t` 개체에서 복사 된 `pSrc` 변환 합니다.  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [_variant_t 클래스](../cpp/variant-t-class.md)