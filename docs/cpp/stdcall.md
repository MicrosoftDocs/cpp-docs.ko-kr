---
title: __stdcall
ms.date: 10/10/2018
f1_keywords:
- __stdcall_cpp
- __stdcall
- _stdcall
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
ms.openlocfilehash: df753241c093db75202a10b106631ce36cf73379
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857283"
---
# <a name="__stdcall"></a>__stdcall

**__Stdcall** 호출 규칙은 Win32 API 함수를 호출 하는 데 사용 됩니다. 호출 수신자가 스택을 정리 하므로 컴파일러는 **__cdecl**함수를 `vararg` 합니다. 이 호출 규칙을 사용하는 함수에는 함수 프로토타입이 필요합니다. **__Stdcall** 한정자는 Microsoft 전용입니다.

## <a name="syntax"></a>구문

> *return-type* **\_\_stdcall** *function-name*[ **(** *argument-list* **)** ]

## <a name="remarks"></a>주의

다음 목록에서는 이러한 호출 규칙의 구현을 보여 줍니다.

|요소|구현|
|-------------|--------------------|
|인수 전달 순서|오른쪽에서 왼쪽|
|인수 전달 규칙|포인터 또는 참조 형식이 전달되지 않는 경우 값으로 전달|
|스택 유지 관리 책임|호출된 함수가 스택에서 자신의 인수를 꺼냅니다.|
|이름 데코레이션 규칙|밑줄(_)이 이름 앞에 붙습니다. 이름 뒤에는 기호(@)가 오고 그 위에 인수 목록의 바이트 수(10진수)가 옵니다. 따라서 `int func( int a, double b )`로 선언된 함수는 `_func@12`로 데코레이팅됩니다.|
|대/소문자 변환 규칙|None|

[/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md) 컴파일러 옵션은 다른 호출 규칙을 사용 하 여 명시적으로 선언 되지 않은 모든 함수에 대해 **__stdcall** 를 지정 합니다.

이전 버전과의 호환성을 위해 **_stdcall** 는 컴파일러 옵션 [/za \(언어 확장 사용 안 함)](../build/reference/za-ze-disable-language-extensions.md) 이 지정 된 경우를 제외 하 고 **__stdcall** 의 동의어입니다.

**__Stdcall** 한정자를 사용 하 여 선언 된 함수는 [__cdecl](../cpp/cdecl.md)를 사용 하 여 선언 된 함수와 동일한 방식으로 값을 반환 합니다.

ARM 및 x64 프로세서에서 **__stdcall** 는 컴파일러에서 허용 되 고 무시 됩니다. ARM 및 x64 아키텍처에서 규칙에 따라 가능한 경우 인수가 레지스터에 전달 되 고 후속 인수가 스택에 전달 됩니다.

비정적 클래스 함수의 경우 함수가 아웃오브 라인으로 정의되면 호출 규칙 한정자를 아웃오브 라인 정의에서 지정하지 않아도 됩니다. 즉, 클래스 비정적 멤버 메서드의 경우 선언하는 동안 지정된 호출 규칙이 정의 시 가정됩니다. 다음과 같은 클래스 정의가 주어진 경우

```cpp
struct CMyClass {
   void __stdcall mymethod();
};
```

this

```cpp
void CMyClass::mymethod() { return; }
```

다음 코드와 동일합니다.

```cpp
void __stdcall CMyClass::mymethod() { return; }
```

## <a name="example"></a>예제

다음 예에서는 **__stdcall** 를 사용 하 여 모든 `WINAPI` 함수 형식이 표준 호출로 처리 됩니다.

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>참조

[인수 전달 및 명명 규칙](../cpp/argument-passing-and-naming-conventions.md)<br/>
[C++ 키워드](../cpp/keywords-cpp.md)