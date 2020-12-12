---
description: '다음에 대 한 자세한 정보: __cdecl'
title: __cdecl
ms.date: 10/09/2018
f1_keywords:
- __cdecl_cpp
- __cdecl
- _cdecl
- cdecl
helpviewer_keywords:
- __cdecl keyword [C++]
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
ms.openlocfilehash: de6d34aa70353f65191c0c36c790d517a1fbbf0e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308577"
---
# <a name="__cdecl"></a>__cdecl

**`__cdecl`** 는 C 및 c + + 프로그램의 기본 호출 규칙입니다. 스택은 호출자에 의해 정리 되기 때문에 함수를 수행할 수 있습니다 `vararg` . **`__cdecl`** 호출 규칙은 각 함수 호출에서 스택 정리 코드를 포함 해야 하기 때문에 [__stdcall](../cpp/stdcall.md)보다 큰 실행 파일을 만듭니다. 다음 목록에서는 이러한 호출 규칙의 구현을 보여 줍니다. **`__cdecl`** 한정자는 Microsoft 전용입니다.

|요소|구현|
|-------------|--------------------|
|인수 전달 순서|오른쪽에서 왼쪽|
|스택 유지 관리 책임|호출하는 함수가 스택에서 인수를 꺼냅니다.|
|이름 데코레이션 규칙|밑줄 문자 (_)는 \_ C 링크를 사용 하는 _cdecl 함수를 내보내는 경우를 제외 하 고 이름 앞에 붙습니다.|
|대/소문자 변환 규칙|대/소문자 변환은 수행되지 않습니다.|

> [!NOTE]
> 관련 내용은 [데코 레이트 된 이름](../build/reference/decorated-names.md)을 참조 하세요.

**`__cdecl`** 변수 또는 함수 이름 앞에 한정자를 추가 합니다. C 명명 및 호출 규칙은 기본값 이므로 **`__cdecl`** `/Gv` (vectorcall), `/Gz` (stdcall) 또는 `/Gr` (fastcall) 컴파일러 옵션을 지정한 경우에만 x86 코드에서를 사용 해야 합니다. [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) 컴파일러 옵션은 호출 규칙을 강제로 적용 합니다 **`__cdecl`** .

ARM 및 x64 프로세서에서 **`__cdecl`** 는 허용 되지만 일반적으로 컴파일러에서 무시 됩니다. ARM 및 x64에서는 규칙에 따라 인수는 가능한 경우 레지스터로 전달되고 이후 인수는 스택에 전달됩니다. X64 코드에서를 사용 **`__cdecl`** 하 여 **/Gv** 컴파일러 옵션을 재정의 하 고 기본 x64 호출 규칙을 사용 합니다.

비정적 클래스 함수의 경우 함수가 아웃오브 라인으로 정의되면 호출 규칙 한정자를 아웃오브 라인 정의에서 지정하지 않아도 됩니다. 즉, 클래스 비정적 멤버 메서드의 경우 선언하는 동안 지정된 호출 규칙이 정의 시 가정됩니다. 다음의 클래스 정의를 가정해 봅니다.

```cpp
struct CMyClass {
   void __cdecl mymethod();
};
```

다음 코드는

```cpp
void CMyClass::mymethod() { return; }
```

다음 코드 조각과 일치합니다.

```cpp
void __cdecl CMyClass::mymethod() { return; }
```

이전 버전과의 호환성을 위해 **cdecl** 및 **_cdecl** 는 **`__cdecl`** 컴파일러 옵션 [/Za \( 사용 안 함 언어 확장 사용 안 함)](../build/reference/za-ze-disable-language-extensions.md) 이 지정 되지 않은 경우의 동의어입니다.

## <a name="example"></a>예제

다음 예제에서 컴파일러는 `system` 함수에 대해 C 명명 규칙 및 호출 규칙을 사용하도록 지시되었습니다.

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>참고 항목

[인수 전달 및 명명 규칙](../cpp/argument-passing-and-naming-conventions.md)<br/>
[키워드](../cpp/keywords-cpp.md)
