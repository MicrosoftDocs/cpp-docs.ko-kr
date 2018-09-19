---
title: DEF 파일을 사용 하 여 DLL에서 내보내기 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22bcca929d687ef3b10ee65bcb2230c03bfb0a11
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706006"
---
# <a name="exporting-from-a-dll-using-def-files"></a>DEF 파일을 사용하여 DLL에서 내보내기

모듈 정의 (.def) 파일은 DLL의 다양 한 특성을 설명 하는 하나 이상의 모듈 문이 들어 있는 텍스트 파일입니다. 사용 하지 않는 경우는 **__declspec (dllexport)** DLL의 함수를 내보내려면 키워드 DLL.def 파일이 필요 합니다.

.Def 파일에 다음 모듈 정의 문을 포함 해야 합니다.

- 파일의 첫째 문은 LIBRARY 문 이어야 합니다. 이 문은 해당.def 파일이 DLL에 속한다는 것을 나타냅니다. LIBRARY 문 DLL의 이름이 옵니다. 링커는이 이름을 DLL의 가져오기 라이브러리입니다.

- EXPORTS 문은 이름과, 필요에 따라 해당 DLL에서 내보내기 함수의 서 수 값을 나열 합니다. 함수 이름을 사용 하 여 수행 하 여 함수가 서 수 값을 할당할는 at 기호 (@) 및 번호입니다. 서 수 값을 지정 하면 N, 여기서 N은 해당 DLL에서 내보내기 함수의 수 ~ 1 범위에 있어야 합니다. 참조 서 수로 함수를 내보내려면 [이름 대신 서 수를 사용 하 여 DLL에서 함수 내보내기](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) 도 합니다.

예를 들어, 이진 검색 트리를 구현 하는 코드를 포함 하는 DLL은 다음과 같습니다.

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

사용 하는 경우는 [MFC DLL 마법사](../mfc/reference/mfc-dll-wizard.md) MFC DLL을 만들려면 마법사 대신 기초.def 파일을 만들고 프로젝트에 자동으로 추가 합니다. 이 파일에 내보낼 함수의 이름을 추가 합니다. 비 MFC Dll의 경우 직접.def 파일을 만들어 하며 프로젝트에 추가 합니다.

C + + 파일에서 함수를 내보내는 경우 데코레이팅된 이름을.def 파일에 배치 또는 extern "C"를 사용 하 여 내보낸된 함수를 표준 C 링크로 정의 해야 합니다. 데코레이팅된 이름을.def 파일에 배치 해야 하는 경우 사용 하 여 가져올 수 있습니다 합니다 [DUMPBIN](../build/reference/dumpbin-reference.md) 도구 또는 링커를 사용 하 여 [/map](../build/reference/map-generate-mapfile.md) 옵션입니다. 특정 컴파일러는 컴파일러에서 생성 된 데코레이팅된 이름이 참고 합니다. .Def 파일에는 Visual c + + 컴파일러에서 생성 된 데코레이팅된 이름을 포함 하는 경우, DLL에 링크 되는 응용 프로그램 빌드해야 호출 응용 프로그램의 데코레이팅된 이름과 DLL의.de의 내보낸된 이름과 일치 하도록 동일한 버전의 Visual c + +를 사용 하 여 f 파일입니다.

빌드하는 경우는 [확장 DLL](../build/extension-dlls-overview.md)는 내보내는 클래스가 들어 있는 헤더 파일의 시작과 끝에 다음 코드를 추가.def 파일을 사용 하 여 내보내기 및:

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

이러한 줄 내부적으로 사용 되는 또는 클래스에 추가 된 MFC 변수 인지 확인 (내보내거나 가져올) MFC 확장 DLL에서에서. 예를 들어, 사용 하 여 클래스를 파생 하는 경우 `DECLARE_DYNAMIC`를 추가할 매크로 확장을 `CRuntimeClass` 클래스에 멤버 변수입니다. 이러한 네 줄에 DLL을 컴파일, 제대로 연결 또는 클라이언트 응용 프로그램이 DLL에 연결 하는 경우 오류가 발생 될 수 있습니다.

DLL을 빌드하는 경우 링커는.def 파일을 내보내기 (.exp) 파일 만들기 및 가져오기 라이브러리 (.lib) 파일을 사용 합니다. 다음 링커 내보내기 파일을 사용 하 여 DLL 파일을 빌드합니다. 실행 파일은 빌드 시 가져오기 라이브러리에 DLL 링크에 암시적으로 링크 합니다.

MFC 자체는 함수 및 클래스를 MFCx0.dll에서 내보내려면.def 파일 note 합니다.

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [__Declspec (dllexport)을 사용 하 여 DLL에서 내보내기](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [AFX_EXT_CLASS를 사용 하 여 가져오기 및 내보내기](../build/exporting-and-importing-using-afx-ext-class.md)

- [C 언어 실행 파일에서 사용 하기 위해 c + + 함수 내보내기](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [C 또는 c + + 언어 실행 파일에서 사용 하기 위해 내보내기 C 함수](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [사용할 내보내기 방법 결정](../build/determining-which-exporting-method-to-use.md)

- [__Declspec (dllimport)을 사용 하 여 응용 프로그램으로 가져오기](../build/importing-into-an-application-using-declspec-dllimport.md)

- [DLL 초기화](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [.def 파일](../build/reference/module-definition-dot-def-files.md)

- [모듈 정의 문의 규칙](../build/reference/rules-for-module-definition-statements.md)

- [트 데코 레이 된 이름](../build/reference/decorated-names.md)

- [인라인 함수 가져오기 및 내보내기](../build/importing-and-exporting-inline-functions.md)

- [상호 가져오기](../build/mutual-imports.md)

## <a name="see-also"></a>참고 항목

[DLL에서 내보내기](../build/exporting-from-a-dll.md)