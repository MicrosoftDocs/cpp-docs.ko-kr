---
title: __declspec(dllimport)을 사용하여 데이터 가져오기
ms.date: 11/04/2016
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: 341912b53301c3a11df4285167d66c8c1493d2fd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223995"
---
# <a name="importing-data-using-__declspecdllimport"></a>__declspec(dllimport)을 사용하여 데이터 가져오기

데이터의 경우 **`__declspec(dllimport)`** 을 사용하는 것은 간접 참조 계층을 제거하는 편의 항목입니다. DLL에서 데이터를 가져올 때 가져오기 주소 테이블을 거쳐야 합니다. **`__declspec(dllimport)`** 전에는 DLL에서 내보낸 데이터에 액세스할 때 추가 수준의 간접 참조 수행을 기억해야 함을 의미했습니다.

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

그런 다음, DEF 파일에서 다음과 같이 데이터를 내보냅니다.

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

그리고 다음과 같이 DLL 외부에서 이 데이터에 액세스합니다.

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

데이터를 **`__declspec(dllimport)`** 으로 표시하면 컴파일러가 간접 참조 코드를 자동으로 생성합니다. 더 이상 위 단계를 걱정하지 않아도 됩니다. 앞서 설명한 것처럼 DLL을 빌드할 때 데이터에 **`__declspec(dllimport)`** 선언을 사용하지 마세요. DLL 내의 함수는 가져오기 주소 테이블을 사용하여 데이터 개체에 액세스하지 않습니다. 따라서 추가 수준의 간접 참조가 표시되지 않습니다.

DLL에서 데이터를 자동으로 내보내려면 다음 선언을 사용하세요.

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>참조

[애플리케이션으로 가져오기](importing-into-an-application.md)
