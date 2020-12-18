---
description: '자세한 정보: 사용할 내보내기 방법 결정'
title: 사용할 내보내기 방법 결정
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
ms.openlocfilehash: 5d9e973d331ebd6190cd8e2a46601dfe2b057d09
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162978"
---
# <a name="determine-which-exporting-method-to-use"></a>사용할 내보내기 방법 결정

.def 파일 또는 `__declspec(dllexport)` 키워드의 두 가지 방법의 하나로 함수를 내보낼 수 있습니다. DLL에 더 적합한 방법을 결정하기 위해 다음 질문을 고려하세요.

- 나중에 더 많은 함수를 내보낼 계획인가요?

- DLL이 다시 빌드할 수 있는 애플리케이션에서만 사용되나요? 아니면 타사에서 만든 애플리케이션 등 다시 빌드할 수 없는 애플리케이션에서 사용되나요?

## <a name="pros-and-cons-of-using-def-files"></a>.def 파일 사용의 장단점

.def 파일로 함수를 내보내면 내보내기 서수를 제어할 수 있습니다. 내보낸 함수를 DLL에 추가할 때 내보낸 다른 함수보다 높은 서수 값을 할당할 수 있습니다. 이렇게 하면 암시적 링크를 사용하는 애플리케이션에서 새 함수를 포함하는 가져오기 라이브러리와 다시 연결하지 않아도 됩니다. 이 방법은 여러 애플리케이션에서 사용할 DLL을 설계할 경우 매우 편리한데, 새 기능을 추가하면서 이미 사용하는 애플리케이션에서 해당 기능이 계속 올바로 작동하도록 할 수 있기 때문입니다. 예를 들어 MFC DLL은 .def 파일을 사용하여 빌드됩니다.

.def 파일을 사용하는 또 다른 이점은 `NONAME` 특성을 사용하여 함수를 내보낼 수 있다는 것입니다. 이렇게 하면 DLL의 내보내기 테이블에 서수만 채워집니다. 내보낸 함수가 많은 DLL의 경우 `NONAME` 특성을 사용하면 DLL 파일의 크기를 줄일 수 있습니다. 모듈 정의 문을 작성하는 방법에 대한 자세한 내용은 [모듈 정의 문의 규칙](reference/rules-for-module-definition-statements.md)을 참조하세요. 서수 내보내기에 대한 자세한 내용은 [이름 대신 서수로 DLL에서 함수 내보내기](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)를 참조하세요.

.def 파일을 사용할 때의 단점은 함수를 C++ 파일로 내보내는 경우 .def 파일에 데코레이트된 이름을 저장하나 extern “C”를 사용해 내보낸 함수를 정의하여 MSVC 컴파일러에서 수행하는 이름 데코레이션을 방지해야 합니다.

.def 파일에 데코레이트된 이름을 넣는 경우 [DUMPBIN](reference/dumpbin-reference.md) 도구를 사용하거나 링커 [/MAP](reference/map-generate-mapfile.md) 옵션을 사용하여 이름을 가져올 수 있습니다. 컴파일러에서 생성되는 데코레이트된 이름은 컴파일러에 따라 다릅니다. 따라서 컴파일러에서 생성된 데코레이트된 이름을 .def 파일에 저장하는 경우 DLL에 연결되는 애플리케이션도 같은 버전의 컴파일러를 사용하여 빌드해야만 호출하는 애플리케이션의 데코레이트된 이름이 DLL의 .def 파일에 내보낸 이름과 일치합니다.

## <a name="pros-and-cons-of-using-__declspecdllexport"></a>__declspec(dllexport) 사용의 장단점

`__declspec(dllexport)`을 사용하면 .def 파일을 유지 관리하고 내보낸 함수의 데코레이트된 이름을 가져올 필요가 없으므로 간편합니다. 그러나 이 내보내기 방법의 유용성은 다시 빌드하려는 연결된 애플리케이션 수에 의해 제한을 받습니다. 새 내보내기를 사용하여 DLL을 다시 빌드하는 경우에는 애플리케이션도 다시 빌드해야 합니다. 다른 버전의 컴파일러를 사용하여 다시 빌드하는 경우 내보낸 C++ 함수의 데코레이트된 이름이 변경될 수 있기 때문입니다.

### <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [.DEF 파일을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-def-files.md)

- [__declspec(dllexport)을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-declspec-dllexport.md)

- [AFX_EXT_CLASS를 사용하여 내보내기 및 가져오기](exporting-and-importing-using-afx-ext-class.md)

- [C 언어 실행 파일에서 사용할 C++ 함수 내보내기](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [C 또는 C++ 언어 실행 파일에서 사용할 C 함수 내보내기](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [__declspec(dllimport)을 사용하여 애플리케이션으로 가져오기](importing-into-an-application-using-declspec-dllimport.md)

- [DLL 초기화](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [인라인 함수 가져오기 및 내보내기](importing-and-exporting-inline-functions.md)

- [상호 가져오기](mutual-imports.md)

- [데코레이트된 이름](reference/decorated-names.md)

## <a name="see-also"></a>참조

[DLL에서 내보내기](exporting-from-a-dll.md)
