---
title: raw_dispinterfaces | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_dispinterfaces
dev_langs:
- C++
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f2a0d91d0f0dd3d23886ade75072526e6c895f7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849456"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**C + + 전용**  
  
 호출 하는 dispinterface 메서드 및 속성에 대 한 하위 수준의 래퍼 함수를 생성 하는 컴파일러가 **idispatch:: Invoke** 다음 다시 돌아와 `HRESULT` 오류 코드입니다.  
  
## <a name="syntax"></a>구문  
  
```  
raw_dispinterfaces  
```  
  
## <a name="remarks"></a>설명  
 이 특성이 지정되지 않은 경우 실패 시 C++ 예외를 throw하는 상위 수준 래퍼만 생성됩니다.  
  
 **C + + 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [#import 특성](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 지시문](../preprocessor/hash-import-directive-cpp.md)