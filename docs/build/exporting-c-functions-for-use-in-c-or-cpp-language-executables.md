---
description: '자세한 정보: C 함수를 C 또는 C++ 언어 실행 파일에서 사용할 수 있도록 내보내기'
title: C 함수를 C 또는 C++ 언어 실행 파일에서 사용할 수 있도록 내보내기
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
ms.openlocfilehash: 9a45eb0a6f2a73f89696c03325690bc82ecd3082
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156660"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>C 함수를 C 또는 C++ 언어 실행 파일에서 사용할 수 있도록 내보내기

C로 작성된 DLL의 함수를 C 언어 또는 C++ 언어 모듈에서 액세스하려는 경우 **__cplusplus** 전처리기 매크로를 사용하여 컴파일되는 언어를 확인한 다음 C++ 언어 모듈에서 사용되는 경우 C 링크로 함수를 선언해야 합니다. 이 방법을 사용하고 DLL의 헤더 파일을 제공하는 경우 관련 함수를 C 및 C++ 사용자가 변경 없이 사용할 수 있습니다.

다음 코드에서는 C 및 C++ 클라이언트 애플리케이션에서 사용할 수 있는 헤더 파일을 보여 줍니다.

```h
// MyCFuncs.h
#ifdef __cplusplus
extern "C" {  // only need to export C interface if
              // used by C++ source code
#endif

__declspec( dllimport ) void MyCFunc();
__declspec( dllimport ) void AnotherCFunc();

#ifdef __cplusplus
}
#endif
```

C 함수를 C++ 실행 파일에 연결해야 하고 함수 선언 헤더 파일에서 위 방법을 사용하지 않은 경우 C++ 소스 파일에서 다음을 수행하여 컴파일러가 C 함수 이름을 데코레이트하지 못하도록 합니다.

```cpp
extern "C" {
#include "MyCHeader.h"
}
```

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [.def 파일을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-def-files.md)

- [__declspec(dllexport)을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-declspec-dllexport.md)

- [AFX_EXT_CLASS를 사용하여 내보내기 및 가져오기](exporting-and-importing-using-afx-ext-class.md)

- [사용할 내보내기 방법 결정](determining-which-exporting-method-to-use.md)

- [__declspec(dllimport)을 사용하여 애플리케이션으로 가져오기](importing-into-an-application-using-declspec-dllimport.md)

- [DLL 초기화](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [데코레이트된 이름](reference/decorated-names.md)

- [extern을 사용하여 링크 지정](../cpp/extern-cpp.md)

## <a name="see-also"></a>참조

[DLL에서 내보내기](exporting-from-a-dll.md)
