---
description: '자세한 정보: DEF 파일을 사용하여 DLL에서 내보내기'
title: DEF 파일을 사용하여 DLL에서 내보내기
ms.date: 05/06/2019
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: 5be5f2c4a5f6db5f1983da940d8a336f02c938f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156530"
---
# <a name="exporting-from-a-dll-using-def-files"></a>DEF 파일을 사용하여 DLL에서 내보내기

모듈 정의 또는 DEF 파일(*.def)은 DLL의 다양한 특성을 설명하는 하나 이상의 모듈 문을 포함하는 텍스트 파일입니다. DLL의 함수를 내보내는 데 **`__declspec(dllexport)`** 키워드를 사용하고 있지 않다면 DLL에 DEF 파일이 필요합니다.

최소 DEF 파일에는 다음과 같은 모듈 정의 문이 포함되어야 합니다.

- 파일의 첫 번째 문은 LIBRARY 문 이어야 합니다. 이 문은 DEF 파일을 DLL에 속하는 것으로 식별합니다. LIBRARY 문 다음에는 DLL의 이름이 나옵니다. 링커는 이 이름을 DLL의 가져오기 라이브러리에 배치합니다.

- EXPORTS 문은 DLL에서 내보낸 함수의 이름 및 서수 값(옵션)을 나열합니다. @ 기호 및 숫자를 이 함수의 이름 뒤에 사용하여 이 함수를 서수 값에 할당합니다. 서수 값을 지정하는 경우 1에서 N 사이의 범위에 있어야 합니다. 여기서 N은 DLL에서 내보낸 함수의 개수입니다. 서수로 함수를 내보내려면 이 항목뿐 아니라 [이름이 아닌 서수로 DLL에서 함수 내보내기](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)를 참조하세요.

예를 들어 이진 검색 트리를 구현하는 코드를 포함하는 DLL은 다음과 같을 수 있습니다.

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

[MFC DLL 마법사](../mfc/reference/mfc-dll-wizard.md)를 사용하여 MFC DLL을 만드는 경우 마법사는 기본 DEF 파일을 만들어 프로젝트에 자동으로 추가합니다. 이 파일로 내보낼 함수의 이름을 추가합니다. 비 MFC DLL의 경우 직접 DEF 파일을 만들어 프로젝트에 추가합니다. 그런 다음 **프로젝트** > **속성** > **링커** > **입력** > **모듈 정의 파일** 로 이동하여 DEF 파일의 이름을 입력합니다. 각 구성 및 플랫폼에 대해 이 단계를 반복하거나 **구성 = 모든 구성** 및 **플랫폼 = 모든 플랫폼** 을 선택하여 모든 구성 및 플랫폼에 대해 한 번에 이 단계를 수행합니다.

C++ 파일에서 함수를 내보내는 경우 DEF 파일에 데코레이팅된 이름을 배치하거나 extern "C"를 사용하여 표준 C 연결로 내보낸 함수를 정의해야 합니다. DEF 파일에 데코레이팅된 이름을 배치해야 하는 경우 [DUMPBIN](../build/reference/dumpbin-reference.md) 도구를 사용하거나 링커 [/MAP](../build/reference/map-generate-mapfile.md) 옵션을 사용하여 가져올 수 있습니다. 컴파일러가 생성한 데코레이팅된 이름은 컴파일러마다 다릅니다. Microsoft C++ 컴파일러(MSVC)가 생성한 데코레이팅된 이름을 DEF 파일에 배치하는 경우 호출 애플리케이션의 데코레이팅된 이름이 DLL의 DEF 파일에 있는 내보낸 이름과 일치하도록 DLL에 연결되는 애플리케이션은 동일한 버전의 MSVC를 사용하여 빌드해야 합니다.

> [!NOTE]
> Visual studio 2015로 빌드된 DLL은 Visual Studio 2017 또는 Visual Studio 2019로 빌드된 애플리케이션이 사용할 수 있습니다.

[확장 DLL](../build/extension-dlls-overview.md)을 빌드하고 DEF 파일을 사용하여 내보내는 경우 내보낸 클래스를 포함하는 헤더 파일의 시작과 끝에 다음 코드를 배치합니다.

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

이러한 줄을 통해 내부적으로 사용되거나 클래스에 추가되는 MFC 변수를 MFC 확장 DLL에서 내보내거나 가져오는 것이 보장됩니다. 예를 들어 `DECLARE_DYNAMIC`을 사용하여 클래스를 파생시키는 경우 매크로가 확장되어 `CRuntimeClass` 멤버 변수를 클래스에 추가합니다. 이 4개의 줄을 생략하면 클라이언트 애플리케이션이 DLL에 연결될 때 DLL이 올바르게 컴파일 또는 연결하지 않거나 오류가 발생할 수 있습니다.

DLL을 빌드할 때 링커는 DEF 파일을 사용하여 내보내기(.exp) 파일 및 가져오기 라이브러리(.lib) 파일을 만듭니다. 그런 다음 링커는 내보내기 파일을 사용하여 DLL 파일을 빌드합니다. DLL에 암시적으로 연결되는 실행 파일은 빌드 시 가져오기 라이브러리에 연결됩니다.

MFC 자체는 DEF 파일을 사용하여 MFCx0.dll에서 함수와 클래스를 내보냅니다.

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [__declspec(dllexport)을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-declspec-dllexport.md)

- [AFX_EXT_CLASS를 사용하여 내보내기 및 가져오기](exporting-and-importing-using-afx-ext-class.md)

- [C 언어 실행 파일에서 사용할 C++ 함수 내보내기](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [C 또는 C++ 언어 실행 파일에서 사용할 C 함수 내보내기](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [사용할 내보내기 방법 결정](determining-which-exporting-method-to-use.md)

- [__declspec(dllimport)을 사용하여 애플리케이션으로 가져오기](importing-into-an-application-using-declspec-dllimport.md)

- [DLL 초기화](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [.def 파일](reference/module-definition-dot-def-files.md)

- [모듈 정의 문의 규칙](reference/rules-for-module-definition-statements.md)

- [데코레이팅된 이름](reference/decorated-names.md)

- [인라인 함수 가져오기 및 내보내기](importing-and-exporting-inline-functions.md)

- [상호 가져오기](mutual-imports.md)

## <a name="see-also"></a>참조

[DLL에서 내보내기](exporting-from-a-dll.md)
