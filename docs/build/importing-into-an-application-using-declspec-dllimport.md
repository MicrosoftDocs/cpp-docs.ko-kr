---
description: '자세한 정보: __declspec(dllimport)을 사용하여 애플리케이션으로 가져오기'
title: __declspec(dllimport)을 사용하여 애플리케이션으로 가져오기
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
ms.openlocfilehash: 946ec6b4b06b22dd7dd68be2478a0b0571aa641c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156179"
---
# <a name="import-into-an-application-using-__declspecdllimport"></a>__declspec(dllimport)을 사용하여 애플리케이션으로 가져오기

DLL에 정의된 공용 기호를 사용하는 프로그램은 해당 기호를 가져온다고 합니다. DLL을 사용하여 빌드하는 애플리케이션의 헤더 파일을 만드는 경우 공용 기호를 선언하는 데 **`__declspec(dllimport)`** 을 사용합니다. .def 파일을 사용하여 내보내든 **`__declspec(dllexport)`** 키워드를 사용하여 내보내든 **`__declspec(dllimport)`** 키워드가 작동합니다.

코드를 더 읽기 쉽게 만들려면 **`__declspec(dllimport)`** 에 대한 매크로를 정의한 다음 이 매크로를 사용하여 가져온 각 기호를 선언합니다.

```
#define DllImport   __declspec( dllimport )

DllImport int  j;
DllImport void func();
```

함수 선언에서 **`__declspec(dllimport)`** 사용은 선택적이지만 이 키워드를 사용하면 컴파일러가 보다 효율적인 코드를 생성합니다. 그러나 가져오는 실행 파일이 DLL의 공용 데이터 기호 및 개체에 액세스하는 데 **`__declspec(dllimport)`** 을 사용해야 합니다. DLL 사용자는 여전히 가져오기 라이브러리에 연결해야 합니다.

DLL과 클라이언트 애플리케이션 모두에 동일한 헤더 파일을 사용할 수 있습니다. 이렇게 하려면 DLL을 빌드하는지 또는 클라이언트 애플리케이션을 빌드하는지 나타내는 특수 전처리기 기호를 사용합니다. 예를 들어:

```
#ifdef _EXPORTING
   #define CLASS_DECLSPEC    __declspec(dllexport)
#else
   #define CLASS_DECLSPEC    __declspec(dllimport)
#endif

class CLASS_DECLSPEC CExampleA : public CObject
{ ... class definition ... };
```

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [DLL 초기화](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [인라인 함수 가져오기 및 내보내기](importing-and-exporting-inline-functions.md)

- [상호 가져오기](mutual-imports.md)

## <a name="see-also"></a>참조

[애플리케이션으로 가져오기](importing-into-an-application.md)
