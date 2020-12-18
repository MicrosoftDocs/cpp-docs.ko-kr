---
description: '자세한 정보: Visual Basic 애플리케이션에서 DLL 함수 호출'
title: Visual Basic 애플리케이션에서 DLL 함수 호출
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
ms.openlocfilehash: 3c9a66a4d6dc9a8e3cc6e8b8a80584d430f12562
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156985"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>Visual Basic 애플리케이션에서 DLL 함수 호출

Visual Basic 애플리케이션(또는 Pascal, Fortran 등 다른 언어의 애플리케이션)이 C/C++ DLL에서 함수를 호출하려면 컴파일러에서 수행하는 이름 장식 없이 올바른 호출 규칙을 사용하여 함수를 내보내야 합니다.

**`__stdcall`** 은 함수의 올바른 호출 규칙(호출된 함수가 스택을 정리하고 매개 변수가 오른쪽에서 왼쪽으로 전달됨)을 만들지만 함수 이름을 다르게 데코레이트합니다. 따라서 DLL에서 내보낸 함수에 **`__declspec(dllexport)`** 를 사용하는 경우 데코레이트된 이름을 내보냅니다.

**`__stdcall`** 이름 데코레이션에서는 기호 이름 앞에 밑줄( **\_** )을 붙이고 @ 기호( **\@** )와 인수 목록의 바이트 수(필요한 스택 공간)를 추가합니다. 따라서 다음과 같이 선언된 함수는

```C
int __stdcall func (int a, double b)
```

출력에서 `_func@12`로 데코레이트됩니다.

C 호출 규칙( **`__cdecl`** )은 이름을 `_func`로 데코레이트합니다.

데코레이트된 이름을 가져오려면 [/MAP](reference/map-generate-mapfile.md)를 사용합니다. **`__declspec(dllexport)`** 을 사용하면 다음을 수행합니다.

- C 호출 규칙( **`__cdecl`** )을 사용하여 함수를 내보내는 경우 이름을 내보낼 때 앞에 오는 밑줄( **\_** )을 제거합니다.

- 내보내는 함수에서 C 호출 규칙(예: **`__stdcall`** )을 사용하지 않는 경우 데코레이트된 이름을 내보냅니다.

스택 정리가 발생하는 위치를 재정의할 방법이 없으므로 **`__stdcall`** 을 사용해야 합니다. **`__stdcall`** 을 사용하여 이름을 데코레이트하지 않으려면 .def 파일의 EXPORTS 섹션에서 별칭을 사용하여 이름을 지정해야 합니다. 다음 함수 선언의 경우 다음과 같이 표시됩니다.

```C
int  __stdcall MyFunc (int a, double b);
void __stdcall InitCode (void);
```

.DEF 파일:

```
EXPORTS
   MYFUNC=_MyFunc@12
   INITCODE=_InitCode@0
```

Visual Basic으로 작성된 프로그램에서 DLL을 호출하려면 .def 파일에 이 항목에 나와 있는 별칭 기법을 사용해야 합니다. Visual Basic 프로그램에서 별칭을 사용한 경우 .def 파일에 별칭을 사용하지 않아도 됩니다. Visual Basic 프로그램에서 [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) 문에 별칭 절을 추가하여 이 작업을 수행할 수 있습니다.

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [DLL에서 내보내기](exporting-from-a-dll.md)

- [.DEF 파일을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-def-files.md)

- [__declspec(dllexport)을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-declspec-dllexport.md)

- [C 언어 실행 파일에서 사용할 C++ 함수 내보내기](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [사용할 내보내기 방법 결정](determining-which-exporting-method-to-use.md)

- [데코레이트된 이름](reference/decorated-names.md)

## <a name="see-also"></a>참조

[Visual Studio에서 C/C++ DLL 만들기](dlls-in-visual-cpp.md)
