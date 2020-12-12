---
description: '다음에 대 한 자세한 정보: code_seg pragma'
title: code_seg pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.code_seg
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
ms.openlocfilehash: c303d7e86dc94be3c3d76368b92915cd06010567
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300842"
---
# <a name="code_seg-pragma"></a>code_seg pragma

함수가 개체 (.obj) 파일에 저장 되는 텍스트 섹션 (세그먼트)을 지정 합니다.

## <a name="syntax"></a>Syntax

> **#pragma code_seg (** ["*섹션-이름*" [ **,** "*섹션-클래스*"]] **)**\
> **#pragma code_seg (** { **push**  |  **pop** } [ **,** *식별자* ] [ **,** "*섹션-이름*" [ **,** "*섹션-클래스*"]] **)**

### <a name="parameters"></a>매개 변수

**누르기**\
필드 내부 컴파일러 스택에 레코드를 넣습니다. **푸시** 에는 *식별자* 와 *섹션 이름이* 있을 수 있습니다.

**창을**\
필드 내부 컴파일러 스택의 맨 위에서 레코드를 제거 합니다. **Pop** 에는 *식별자* 와 *섹션 이름이* 있을 수 있습니다. *식별자* 를 사용 하 여 하나의 **pop** 명령만을 사용 하 여 여러 레코드를 표시할 수 있습니다. *섹션 이름* 은 pop 뒤의 활성 텍스트 섹션 이름이 됩니다.

*identifier*\
필드 **Push** 와 함께 사용 하는 경우 내부 컴파일러 스택의 레코드에 이름을 할당 합니다. **Pop** 에서 사용 하는 경우 지시문은 *식별자* 가 제거 될 때까지 내부 스택에서 레코드를 팝 합니다. 내부 스택에서 *식별자* 를 찾을 수 없는 경우 아무 것도 팝 되지 않습니다.

"*섹션-이름*" \
필드 섹션의 이름입니다. **Pop** 와 함께 사용 하는 경우 스택이 팝 되 고 *섹션 이름* 은 활성 텍스트 섹션 이름이 됩니다.

"*섹션-클래스*" \
필드 무시 되지만 버전 2.0 이전 버전의 Microsoft c + +와의 호환성을 위해 포함 되었습니다.

## <a name="remarks"></a>설명

개체 파일의 *섹션* 은 메모리에 하나의 단위로 로드 되는 명명 된 데이터 블록입니다. *텍스트 섹션* 은 실행 코드를 포함 하는 섹션입니다. 이 문서에서 *세그먼트* 와 *섹션* 이라는 용어는 동일한 의미를 갖습니다.

**Code_seg** pragma 지시문은 변환 단위의 모든 후속 개체 코드를 *section-name* 이라는 텍스트 섹션에 포함 하도록 컴파일러에 지시 합니다. 기본적으로 개체 파일의 함수에 사용 되는 텍스트 섹션의 이름은 `.text` 입니다. *섹션 이름* 매개 변수가 없는 **code_seg** pragma 지시문은 후속 개체 코드의 텍스트 섹션 이름을로 다시 설정 합니다 `.text` .

**Code_seg** pragma 지시문은 인스턴스화된 템플릿에 대해 생성 된 개체 코드의 배치를 제어 하지 않습니다. 특수 멤버 함수와 같이 컴파일러에 의해 암시적으로 생성 된 코드도 제어 하지 않습니다. 해당 코드를 제어 하려면 [__declspec (code_seg (...))](../cpp/code-seg-declspec.md) 특성을 대신 사용 하는 것이 좋습니다. 컴파일러에서 생성 된 코드를 포함 하 여 모든 개체 코드의 배치를 제어할 수 있습니다.

섹션을 만드는 데 사용 하지 않아야 하는 이름 목록은 [/SECTION](../build/reference/section-specify-section-attributes.md)를 참조 하세요.

초기화 되는 데이터에 대 한 섹션 ([data_seg](../preprocessor/data-seg.md)), 초기화 되지 않은 데이터 ([bss_seg](../preprocessor/bss-seg.md)) 및 const 변수 ([const_seg](../preprocessor/const-seg.md))를 지정할 수도 있습니다.

[DUMPBIN.EXE](../build/reference/dumpbin-command-line.md) 응용 프로그램을 사용 하 여 개체 파일을 볼 수 있습니다. 지원 되는 각 대상 아키텍처의 DUMPBIN 버전은 Visual Studio에 포함 되어 있습니다.

## <a name="example"></a>예제

이 예제에서는 **code_seg** pragma 지시문을 사용 하 여 개체 코드가 배치 되는 위치를 제어 하는 방법을 보여 줍니다.

```cpp
// pragma_directive_code_seg.cpp
void func1() {                  // stored in .text
}

#pragma code_seg(".my_data1")
void func2() {                  // stored in my_data1
}

#pragma code_seg(push, r1, ".my_data2")
void func3() {                  // stored in my_data2
}

#pragma code_seg(pop, r1)      // stored in my_data1
void func4() {
}

int main() {
}
```

## <a name="see-also"></a>참고 항목

[code_seg (__declspec)](../cpp/code-seg-declspec.md)\
[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
