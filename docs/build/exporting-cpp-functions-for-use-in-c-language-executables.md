---
title: C++ 함수를 C 언어 실행 파일에서 사용할 수 있도록 내보내기
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
ms.openlocfilehash: 38b13c1fc9c57354ba8160f6dbe0df6546fe7b5f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506600"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>C++ 함수를 C 언어 실행 파일에서 사용할 수 있도록 내보내기

DLL에 포함된 C++로 작성된 함수를 C 언어 모듈에서 액세스하려는 경우에는 C++ 링크 대신 C 링크를 사용하여 해당 함수를 선언해야 합니다. 별도로 지정되지 않은 경우, C++ 컴파일러는 C++의 형식이 안전한 명명(이름 데코레이션이라고도 함)과 C++ 호출 규칙을 사용합니다. 이 규칙은 C에서는 호출하기 어려울 수 있습니다.

C 링크를 지정하려면 함수 선언에 대해 `extern "C"`를 지정합니다. 예를 들어:

```
extern "C" __declspec( dllexport ) int MyFunc(long parm1);
```

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [.def 파일을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-def-files.md)

- [__declspec(dllexport)을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-declspec-dllexport.md)

- [AFX_EXT_CLASS를 사용하여 내보내기 및 가져오기](exporting-and-importing-using-afx-ext-class.md)

- [C 또는 C++ 언어 실행 파일에서 사용할 C 함수 내보내기](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [사용할 내보내기 방법 결정](determining-which-exporting-method-to-use.md)

- [__declspec(dllimport)을 사용하여 애플리케이션으로 가져오기](importing-into-an-application-using-declspec-dllimport.md)

- [DLL 초기화](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [데코레이트된 이름](reference/decorated-names.md)

- [extern을 사용하여 링크 지정](../cpp/extern-cpp.md)

## <a name="see-also"></a>참조

[DLL에서 내보내기](exporting-from-a-dll.md)
