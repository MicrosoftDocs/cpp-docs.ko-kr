---
description: '자세한 정보: 가져오기 및 내보내기'
title: 가져오기 및 내보내기
ms.date: 05/06/2019
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
ms.openlocfilehash: e2045b41450881056fb109f059e9c3202d93cab3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162523"
---
# <a name="importing-and-exporting"></a>가져오기 및 내보내기

다음 두 가지 방법을 사용하여 퍼블릭 기호를 애플리케이션으로 가져오거나 DLL에서 함수를 내보낼 수 있습니다.

- DLL을 빌드할 때 모듈 정의(.def) 파일 사용

- 주 애플리케이션의 함수 정의에서 **`__declspec(dllimport)`** 또는 **`__declspec(dllexport)`** 키워드 사용

## <a name="using-a-def-file"></a>.def 파일 사용

모듈 정의(.def) 파일은 DLL의 다양한 특성을 설명하는 하나 이상의 모듈 문을 포함하는 텍스트 파일입니다. **`__declspec(dllimport)`** 또는 **`__declspec(dllexport)`** 을 사용하지 않고 DLL의 함수를 내보내는 경우 DLL에 .def 파일이 필요합니다.

.def 파일을 사용하여 [애플리케이션으로 가져오거나](importing-using-def-files.md) [DLL에서 내보낼 수 있습니다](exporting-from-a-dll-using-def-files.md).

## <a name="using-__declspec"></a>__declspec 사용

**`__declspec(dllimport)`** 을 사용하지 않아도 코드를 올바로 컴파일할 수 있지만 사용할 경우 컴파일러에서 더 나은 코드를 생성할 수 있습니다. 컴파일러에서 함수가 DLL에 있는지를 확인하여 DLL 경계를 벗어난 함수 호출에서 일반적으로 발생하는 간접 참조 수준을 건너뛰는 코드를 생성할 수 있으므로 컴파일러에서 더 나은 코드를 생성할 수 있습니다. 그러나 **`__declspec(dllimport)`** 을 사용하여 DLL에서 사용되는 변수를 가져와야 합니다.

적절한 .def 파일 EXPORTS 섹션이 있으면 **`__declspec(dllexport)`** 이 필요하지 않습니다. **`__declspec(dllexport)`** 은 .def 파일을 사용하지 않고도 .exe 또는 .dll 파일에서 함수를 쉽게 내보내는 방법을 제공하기 위해 추가되었습니다.

Win32 이식 가능 실행 파일 형식은 가져오기를 해결하기 위해 수정해야 하는 페이지 수를 최소화하기 위한 것입니다. 이렇게 하려면 이 파일 형식은 모든 프로그램의 가져오기 주소를 가져오기 주소 테이블이라는 한 곳에 저장합니다. 따라서 로더에서 관련 가져오기에 액세스할 때 1~2페이지만 수정하면 됩니다.

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [애플리케이션으로 가져오기](importing-into-an-application-using-declspec-dllimport.md)

- [DLL에서 내보내기](exporting-from-a-dll.md)

## <a name="see-also"></a>참조

[Visual Studio에서 C/C++ DLL 만들기](dlls-in-visual-cpp.md)
