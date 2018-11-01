---
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
ms.openlocfilehash: f932ba2d9b229d236270eb664ac1291725471706
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493823"
---
# <a name="exporting-from-a-dll"></a>DLL에서 내보내기

DLL 파일에 중요 한 차이점을 사용 하 여.exe 파일인 경우와 매우 비슷한 레이아웃-DLL 파일로 내보내기 테이블을 포함 합니다. 내보내기 테이블에는 해당 DLL이 다른 실행 파일에 내보내는 모든 함수의 이름을 포함 합니다. 이러한 함수는 진입점 DLL; 다른 실행 파일에서 내보내기 테이블에 함수에만 액세스할 수 있습니다. DLL의 다른 함수는 private DLL입니다. 사용 하 여 DLL의 내보내기 테이블을 볼 수 있습니다 합니다 [DUMPBIN](../build/reference/dumpbin-reference.md) /EXPORTS 옵션을 사용 하 여 도구입니다.

다음과 같은 두 메서드를 사용 하 여 DLL에서 함수를 내보낼 수 있습니다.

- 모듈 정의 (.def) 파일을 만들고 DLL을 빌드할 때.def 파일을 사용 합니다. 하려는 경우이 방법을 사용 하 여 [이름 대신 서 수 여 DLL에서 함수 내보내기](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)합니다.

- 키워드를 사용 하 여 **__declspec (dllexport)** 함수 정의에서 합니다.

두 방법 중 하나를 사용 하 여 함수를 내보낼 때 사용 해야 합니다 [__stdcall](../cpp/stdcall.md) 호출 규칙입니다.

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [.Def 파일을 사용 하 여 DLL에서 내보내기](../build/exporting-from-a-dll-using-def-files.md)

- [__Declspec (dllexport)을 사용 하 여 DLL에서 내보내기](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [AFX_EXT_CLASS를 사용 하 여 가져오기 및 내보내기](../build/exporting-and-importing-using-afx-ext-class.md)

- [C 언어 실행 파일에서 사용 하기 위해 c + + 함수 내보내기](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [C 또는 c + + 언어 실행 파일에서 사용 하기 위해 내보내기 C 함수](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [이름 대신 서 수 여 DLL에서 내보내기 함수](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [사용할 내보내기 방법 결정](../build/determining-which-exporting-method-to-use.md)

- [사용할 링크 방법 결정](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [DLL 초기화](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [응용 프로그램으로 가져오기](../build/importing-into-an-application.md)

- [인라인 함수 가져오기 및 내보내기](../build/importing-and-exporting-inline-functions.md)

- [상호 가져오기](../build/mutual-imports.md)

## <a name="see-also"></a>참고 항목

[가져오기 및 내보내기](../build/importing-and-exporting.md)