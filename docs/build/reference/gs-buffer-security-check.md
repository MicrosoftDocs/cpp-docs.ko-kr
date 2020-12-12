---
description: 자세히 알아보기:/GS (버퍼 보안 검사)
title: /GS(버퍼 보안 검사)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BufferSecurityCheck
- VC.Project.VCCLCompilerTool.BufferSecurityCheck
helpviewer_keywords:
- buffers [C++], buffer overruns
- buffer overruns, compiler /GS switch
- GS compiler option [C++]
- /GS compiler option [C++]
- security check compiler option [C++]
- -GS compiler option [C++]
- buffers [C++], avoiding overruns
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
ms.openlocfilehash: 4d7fa3c2220260914c9ff931c2f2e7c76bf12ea1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191877"
---
# <a name="gs-buffer-security-check"></a>/GS(버퍼 보안 검사)

는 함수의 반환 주소, 예외 처리기 주소 또는 특정 형식의 매개 변수를 덮어쓰는 일부 버퍼 오버런을 검색 합니다. 버퍼 오버런은 해커가 버퍼 크기 제한을 적용 하지 않는 코드를 악용 하는 데 사용 하는 기술입니다.

## <a name="syntax"></a>구문

```
/GS[-]
```

## <a name="remarks"></a>설명

**/Gs** 는 기본적으로 설정 되어 있습니다. 응용 프로그램이 보안 노출을 원하지 않는 경우 **/GS-** 를 사용 합니다. 버퍼 오버런 감지를 억제 하는 방법에 대 한 자세한 내용은 [safebuffers](../../cpp/safebuffers.md)를 참조 하세요.

## <a name="security-checks"></a>보안 검사

컴파일러가 버퍼 오버런 문제의 원인이 되는 것으로 인식 하는 함수에서 컴파일러는 반환 주소 앞에 스택에서 공간을 할당 합니다. 함수 항목에서 할당 된 공간은 모듈 로드 시 한 번 계산 되는 *보안 쿠키* 를 사용 하 여 로드 됩니다. 함수 종료 시 및 64 비트 운영 체제에서 프레임을 해제 하는 동안 쿠키의 값이 동일 하 게 유지 되도록 도우미 함수가 호출 됩니다. 다른 값은 스택 덮어쓰기가 발생 했을 수 있음을 나타냅니다. 다른 값이 검색 되 면 프로세스가 종료 됩니다.

## <a name="gs-buffers"></a>GS 버퍼

버퍼 오버런 보안 검사는 *GS 버퍼* 에 대해 수행 됩니다. GS 버퍼는 다음 중 하나일 수 있습니다.

- 4 바이트 보다 큰 배열에는 세 개 이상의 요소가 있으며 포인터 형식이 아닌 요소 형식이 있습니다.

- 크기가 8 바이트를 초과 하 고 포인터를 포함 하지 않는 데이터 구조체입니다.

- [_Alloca](../../c-runtime-library/reference/alloca.md) 함수를 사용 하 여 할당 된 버퍼입니다.

- GS 버퍼를 포함 하는 모든 클래스 또는 구조체입니다.

예를 들어 다음 문은 GS 버퍼를 선언 합니다.

```cpp
char buffer[20];
int buffer[20];
struct { int a; int b; int c; int d; } myStruct;
struct { int a; char buf[20]; };
```

그러나 다음 문은 GS 버퍼를 선언 하지 않습니다. 처음 두 선언에는 포인터 형식의 요소가 포함 되어 있습니다. 세 번째와 네 번째 문은 크기가 너무 작은 배열을 선언 합니다. 다섯 번째 문은 x86 플랫폼의 크기가 8 바이트를 넘지 않는 구조체를 선언 합니다.

```cpp
char *pBuf[20];
void *pv[20];
char buf[4];
int buf[2];
struct { int a; int b; };
```

## <a name="initialize-the-security-cookie"></a>보안 쿠키를 초기화 합니다.

**/Gs** 컴파일러 옵션을 사용 하려면 쿠키를 사용 하는 함수를 실행 하기 전에 보안 쿠키를 초기화 해야 합니다. EXE 또는 DLL에 대 한 항목에서 즉시 보안 쿠키를 초기화 해야 합니다. MainCRTStartup, wmainCRTStartup, WinMainCRTStartup, wWinMainCRTStartup 또는 _DllMainCRTStartup 기본 VCRuntime 진입점을 사용 하는 경우이 작업이 자동으로 수행 됩니다. 대체 진입점을 사용 하는 경우 [__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md)를 호출 하 여 보안 쿠키를 수동으로 초기화 해야 합니다.

## <a name="what-is-protected"></a>보호 되는 항목

**/Gs** 컴파일러 옵션은 다음 항목을 보호 합니다.

- 함수 호출의 반환 주소입니다.

- 함수에 대 한 예외 처리기의 주소입니다.

- 취약 한 함수 매개 변수

모든 플랫폼에서 **/gs** 는 반환 주소로 버퍼 오버런을 검색 하려고 시도 합니다. 버퍼 오버런은 x86 및 x 64와 같은 플랫폼에서 더 쉽게 사용할 수 있습니다 .이는 스택에 대 한 함수 호출의 반환 주소를 저장 하는 호출 규칙을 사용 합니다.

X 86에서 함수에 예외 처리기가 사용 되는 경우 컴파일러는 예외 처리기의 주소를 보호 하기 위해 보안 쿠키를 삽입 합니다. 쿠키는 프레임 해제 중에 검사 됩니다.

**/Gs** 는 함수에 전달 되는 *취약 한 매개 변수* 를 보호 합니다. 취약 한 매개 변수는 포인터, c + + 참조, 포인터 또는 GS 버퍼를 포함 하는 C 구조체 (c + + POD 형식)입니다.

취약 한 매개 변수는 쿠키 및 지역 변수 앞에 할당 됩니다. 버퍼 오버런은 이러한 매개 변수를 덮어쓸 수 있습니다. 이러한 매개 변수를 사용 하는 함수의 코드는 함수를 반환 하 고 보안 검사를 수행 하기 전에 공격을 일으킬 수 있습니다. 이러한 위험을 최소화 하기 위해 컴파일러는 함수 프롤로그 중에 취약 한 매개 변수의 복사본을 만들어 모든 버퍼의 저장소 영역 아래에 배치 합니다.

컴파일러는 다음과 같은 상황에서 취약 한 매개 변수의 복사본을 만들지 않습니다.

- GS 버퍼를 포함 하지 않는 함수입니다.

- 최적화 ([/o 옵션](o-options-optimize-code.md))를 사용할 수 없습니다.

- 가변 인수 목록이 있는 함수 (...)

- [Naked](../../cpp/naked-cpp.md)로 표시 되는 함수입니다.

- 첫 번째 문의 인라인 어셈블리 코드를 포함 하는 함수입니다.

- 매개 변수는 버퍼 오버런이 발생할 경우 악용 될 가능성이 낮은 방법 으로만 사용 됩니다.

## <a name="what-is-not-protected"></a>보호 되지 않는 항목

**/Gs** 컴파일러 옵션은 모든 버퍼 오버런 보안 공격 으로부터 보호 하지 않습니다. 예를 들어 개체에 버퍼와 vtable이 있으면 버퍼 오버런이 발생 하 여 vtable이 손상 될 수 있습니다.

**/Gs** 를 사용 하는 경우에도 항상 버퍼 오버런이 없는 보안 코드를 작성 하려고 합니다.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Visual Studio에서 이 컴파일러 옵션을 설정하려면

1. **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성** 을 클릭 합니다.

   자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **속성 페이지** 대화 상자에서 **C/c + +** 폴더를 클릭 합니다.

1. **코드 생성** 속성 페이지를 클릭 합니다.

1. **Buffer Security Check** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>을 참조하세요.

## <a name="example"></a>예제

이 샘플은 버퍼를 오버런 합니다. 이렇게 하면 런타임에 응용 프로그램이 실패 합니다.

```C
// compile with: /c /W1
#include <cstring>
#include <stdlib.h>
#pragma warning(disable : 4996)   // for strcpy use

// Vulnerable function
void vulnerable(const char *str) {
   char buffer[10];
   strcpy(buffer, str); // overrun buffer !!!

   // use a secure CRT function to help prevent buffer overruns
   // truncate string to fit a 10 byte buffer
   // strncpy_s(buffer, _countof(buffer), str, _TRUNCATE);
}

int main() {
   // declare buffer that is bigger than expected
   char large_buffer[] = "This string is longer than 10 characters!!";
   vulnerable(large_buffer);
}
```

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
