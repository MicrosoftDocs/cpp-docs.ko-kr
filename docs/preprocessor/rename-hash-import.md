---
title: (#import) 이름 바꾸기 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Rename
dev_langs:
- C++
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce1604e3ef7655d72a3ed692e27d6d6c9ae0cb12
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409079"
---
# <a name="rename-import"></a>이름 바꾸기 (#import)
**C + + 전용**  
  
이름 충돌 문제 해결 작업  
  
## <a name="syntax"></a>구문  
  
```  
rename("OldName","NewName")  
```  
  
### <a name="parameters"></a>매개 변수  
*OldName*  
형식 라이브러리에 있는 이전 이름입니다.  
  
*NewName*  
이전 이름 대신 사용할 이름입니다.  
  
## <a name="remarks"></a>설명  
 
이 특성을 지정 하는 경우 컴파일러가 모두 바꿉니다 *OldName* 사용 하 여 사용자가 제공한 형식 라이브러리에 *NewName* 결과 헤더 파일에 있습니다.  
  
형식 라이브러리에 있는 이름이 시스템 헤더 파일에 있는 매크로 정의와 일치하는 경우에 이 특성을 사용할 수 있습니다. 이 상황이 해결 되지 않으면 경우 다양 한 구문 오류가 생성 됩니다와 같은 [컴파일러 오류 C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) 하 고 [컴파일러 오류 C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md)합니다.  
  
> [!NOTE]
> 결과 헤더 파일에 사용된 이름이 아니라 형식 라이브러리에 사용된 이름이 바뀝니다.  
  
예를 들어, 이름이 `MyParent`인 속성이 형식 라이브러리에 있고 `GetMyParent` 매크로가 헤더 파일에 정의되어 `#import` 앞에 사용된다고 가정해 보겠습니다. 이후 `GetMyParent` 는 오류 처리에 대 한 래퍼 함수의 기본 이름 `get` 속성 이름 충돌이 발생 합니다. 이 문제를 해결하려면 `#import` 문에 다음 특성을 사용합니다.  
  
```  
rename("MyParent","MyParentX")  
```  
  
위의 특성은 형식 라이브러리에서 `MyParent`를 다른 이름으로 바꿉니다. `GetMyParent` 래퍼 이름을 바꾸려고 하면 오류가 발생합니다.  
  
```  
rename("GetMyParent","GetMyParentX")  
```  
  
이는 `GetMyParent`라는 이름이 결과 형식 라이브러리 헤더 파일에만 나오기 때문입니다.  
  
**C + + 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 
[#import 특성](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)