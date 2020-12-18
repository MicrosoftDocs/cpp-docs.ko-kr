---
description: '자세한 정보: DLL에서 내보내기'
title: DLL에서 내보내기
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [C++], about exporting from DLLs
- exporting functions [C++], DLLs (exporting from)
- exporting DLLs [C++]
- DLLs [C++], exporting from
- DLL exports [C++]
- functions [C++], exporting
- exports table [C++]
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
ms.openlocfilehash: 324ca733eab48973dc9ca902f81abfe4ce52a5c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162939"
---
# <a name="exporting-from-a-dll"></a>DLL에서 내보내기

DLL 파일의 레이아웃은 .exe 파일과 매우 유사합니다. 한 가지 중요한 차이점은 DLL 파일에는 내보내기 테이블이 포함되어 있습니다. 내보내기 테이블에는 DLL이 다른 실행 파일로 내보내는 모든 함수의 이름이 포함됩니다. 관련 함수는 DLL로의 진입점이므로, 내보내기 테이블에 포함된 함수만 다른 실행 파일에서 액세스할 수 있습니다. DLL의 다른 모든 함수는 DLL에만 공개됩니다. DLL의 내보내기 테이블은 [DUMPBIN](reference/dumpbin-reference.md) 도구에 /EXPORTS 옵션을 사용하여 볼 수 있습니다.

다음 두 가지 방법을 사용하여 DLL에서 함수를 내보낼 수 있습니다.

- 모듈 정의(.def) 파일을 만든 다음 DLL을 빌드할 때 .def 파일을 사용합니다. [DLL에서 함수를 이름이 아닌 서수로 내보내](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)려면 이 방법을 사용합니다.

- 함수 정의에 **`__declspec(dllexport)`** 키워드를 사용합니다.

두 가지 방법으로 함수를 내보내는 경우 [__stdcall](../cpp/stdcall.md) 호출 규칙을 사용해야 합니다.

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [.def 파일을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-def-files.md)

- [__declspec(dllexport)을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-declspec-dllexport.md)

- [AFX_EXT_CLASS를 사용하여 내보내기 및 가져오기](exporting-and-importing-using-afx-ext-class.md)

- [C 언어 실행 파일에서 사용할 C++ 함수 내보내기](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [C 또는 C++ 언어 실행 파일에서 사용할 C 함수 내보내기](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [이름 대신 서수로 DLL에서 함수 내보내기](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [사용할 내보내기 방법 결정](determining-which-exporting-method-to-use.md)

- [DLL에 실행 파일 링크](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [DLL 초기화](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [애플리케이션으로 가져오기](importing-into-an-application.md)

- [인라인 함수 가져오기 및 내보내기](importing-and-exporting-inline-functions.md)

- [상호 가져오기](mutual-imports.md)

## <a name="see-also"></a>참조

[가져오기 및 내보내기](importing-and-exporting.md)
