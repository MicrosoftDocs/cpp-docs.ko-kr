---
description: '자세한 정보: 인라인 함수 가져오기 및 내보내기'
title: 인라인 함수 가져오기 및 내보내기
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
ms.openlocfilehash: 053280685edf8fa88c969399e7905582534c7493
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156192"
---
# <a name="importing-and-exporting-inline-functions"></a>인라인 함수 가져오기 및 내보내기

가져온 함수를 인라인으로 정의할 수 있습니다. 효과는 표준 함수 인라인을 정의하는 것과 거의 동일 합니다. 함수 호출은 매크로와 매우 유사한 인라인 코드로 확장됩니다. 이는 주로 효율성을 위해 일부 멤버 함수를 인라인할 수 있는 DLL의 C++ 클래스를 지원하기 위한 방법으로 유용합니다.

가져온 인라인 함수의 한 가지 기능은 C++에서 그 주소를 가져올 수 있다는 것입니다. 컴파일러는 DLL에 있는 인라인 함수 복사본의 주소를 반환합니다. 가져온 인라인 함수의 또 다른 기능은 가져온 전역 데이터와 달리 가져온 함수의 정적 로컬 데이터를 초기화하는 것입니다.

> [!CAUTION]
> 가져온 인라인 함수를 제공할 때는 버전 충돌이 발생할 수 있으므로 주의 해야 합니다. 인라인 함수는 애플리케이션 코드로 확장됩니다. 따라서 나중에 함수를 다시 작성하는 경우 애플리케이션 자체를 다시 컴파일하지 않는 한 함수는 업데이트되지 않습니다. (일반적으로 DLL 함수는 이 함수를 사용하는 애플리케이션을 다시 빌드하지 않고도 업데이트할 수 있습니다.)

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [DLL에서 내보내기](exporting-from-a-dll.md)

- [.DEF 파일을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-def-files.md)

- [__declspec(dllexport)을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-declspec-dllexport.md)

- [AFX_EXT_CLASS를 사용하여 내보내기 및 가져오기](exporting-and-importing-using-afx-ext-class.md)

- [C 언어 실행 파일에서 사용할 C++ 함수 내보내기](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [사용할 내보내기 방법 결정](determining-which-exporting-method-to-use.md)

- [__declspec(dllimport)을 사용하여 애플리케이션으로 가져오기](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>참조

[가져오기 및 내보내기](importing-and-exporting.md)
