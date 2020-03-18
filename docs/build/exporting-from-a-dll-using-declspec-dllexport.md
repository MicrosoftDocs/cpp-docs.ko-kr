---
title: __declspec(dllexport)을 사용하여 DLL에서 내보내기
ms.date: 05/06/2019
f1_keywords:
- dllexport
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
ms.openlocfilehash: c84a8eca25c90e0790ec8c4991d9d5a116afa59f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442531"
---
# <a name="exporting-from-a-dll-using-__declspecdllexport"></a>__declspec(dllexport)을 사용하여 DLL에서 내보내기

**__Declspec (dllexport)** 키워드를 사용 하 여 DLL에서 데이터, 함수, 클래스 또는 클래스 멤버 함수를 내보낼 수 있습니다. **__declspec (dllexport)** 는 .def 파일을 사용할 필요가 없도록 내보내기 지시어를 개체 파일에 추가 합니다.

이 편의는 데코레이팅된 C++ 함수 이름을 내보내려고 할 때 가장 뚜렷하게 나타납니다. 이름 데코레이션에 대 한 표준 사양이 없기 때문에 내보낸 함수의 이름은 컴파일러 버전 간에 변경 될 수 있습니다. **__Declspec (dllexport)** 를 사용 하는 경우 DLL 및 종속 .exe 파일을 다시 컴파일하는 것은 명명 규칙 변경 내용을 고려 하는 경우에만 필요 합니다.

서 수, NONAME, PRIVATE 등의 많은 내보내기 지시문은 .def 파일 에서만 만들 수 있으며 .def 파일 없이 이러한 특성을 지정할 수 있는 방법은 없습니다. 그러나 .def 파일을 사용 하는 것 외에도 **__declspec (dllexport)** 를 사용 하면 빌드 오류가 발생 하지 않습니다.

함수를 내보내려면 키워드를 지정 하는 경우 **__declspec (dllexport)** 키워드가 호출 규칙 키워드의 왼쪽에 표시 되어야 합니다. 다음은 그 예입니다.

```
__declspec(dllexport) void __cdecl Function1(void);
```

클래스에서 모든 public 데이터 멤버와 멤버 함수를 내보내려면 키워드는 클래스 이름 왼쪽에 다음과 같이 표시 되어야 합니다.

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
>  `__declspec(dllexport)`은 `__clrcall` 호출 규칙을 사용 하 여 함수에 적용할 수 없습니다.

DLL을 빌드할 때 일반적으로 내보내는 함수 프로토타입 및/또는 클래스를 포함 하는 헤더 파일을 만들고 헤더 파일의 선언에 **__declspec (dllexport)** 을 추가 합니다. 코드를 더 읽기 쉽게 만들려면 **__declspec (dllexport)** 에 대 한 매크로를 정의 하 고 내보낼 각 기호에 매크로를 사용 합니다.

```
#define DllExport   __declspec( dllexport )
```

**dllexport (__declspec)** 는 함수 이름을 DLL의 내보내기 테이블에 저장 합니다. 테이블 크기를 최적화 하려면 [이름 대신 서 수로 DLL에서 함수 내보내기](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)를 참조 하세요.

## <a name="what-do-you-want-to-do"></a>수행 작업

- [.Def 파일을 사용 하 여 DLL에서 내보내기](exporting-from-a-dll-using-def-files.md)

- [AFX_EXT_CLASS를 사용 하 여 내보내기 및 가져오기](exporting-and-importing-using-afx-ext-class.md)

- [C C++ 언어 실행 파일에서 사용할 함수 내보내기](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [C 함수를 C 또는 C++언어 실행 파일에 사용 하기 위해 내보내기](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [사용할 내보내기 방법 결정](determining-which-exporting-method-to-use.md)

- [__declspec(dllimport)을 사용하여 애플리케이션으로 가져오기](importing-into-an-application-using-declspec-dllimport.md)

- [DLL 초기화](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [__Declspec 키워드](../cpp/declspec.md)

- [인라인 함수 가져오기 및 내보내기](importing-and-exporting-inline-functions.md)

- [상호 가져오기](mutual-imports.md)

## <a name="see-also"></a>참고 항목

[DLL에서 내보내기](exporting-from-a-dll.md)
