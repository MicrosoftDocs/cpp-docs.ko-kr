---
description: '다음에 대 한 자세한 정보: data_seg pragma'
title: data_seg pragma
ms.date: 08/29/2019
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
ms.openlocfilehash: f7caff65273b2fc0d51c6bfd1cede42cce7103d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300790"
---
# <a name="data_seg-pragma"></a>data_seg pragma

초기화 된 변수가 개체 (.obj) 파일에 저장 되는 데이터 섹션 (세그먼트)을 지정 합니다.

## <a name="syntax"></a>Syntax

> **#pragma data_seg (** ["*섹션-이름*" [ **,** "*섹션-클래스*"]] **)**\
> **#pragma data_seg (** { **push**  |  **pop** } [ **,** *식별자* ] [ **,** "*섹션-이름*" [ **,** "*섹션-클래스*"]] **)**

### <a name="parameters"></a>매개 변수

**누르기**\
필드 내부 컴파일러 스택에 레코드를 넣습니다. **푸시** 에는 *식별자* 와 *섹션 이름이* 있을 수 있습니다.

**창을**\
필드 내부 컴파일러 스택의 맨 위에서 레코드를 제거 합니다. **Pop** 에는 *식별자* 와 *섹션 이름이* 있을 수 있습니다. *식별자* 를 사용 하 여 하나의 **pop** 명령만을 사용 하 여 여러 레코드를 표시할 수 있습니다. *섹션 이름* 은 pop 뒤의 활성 데이터 섹션 이름이 됩니다.

*identifier*\
필드 **Push** 와 함께 사용 하는 경우 내부 컴파일러 스택의 레코드에 이름을 할당 합니다. **Pop** 과 함께 사용 하면 *식별자* 가 제거 될 때까지 내부 스택에서 레코드를 팝 합니다. 내부 스택에서 *식별자* 를 찾을 수 없는 경우 아무 것도 팝 되지 않습니다.

*식별자* 를 사용 하면 단일 **pop** 명령으로 여러 레코드를 팝 할 수 있습니다.

*"섹션-이름"*\
필드 섹션의 이름입니다. **Pop** 와 함께 사용 하는 경우 스택이 팝 되 고 *섹션 이름이* 활성 데이터 섹션 이름이 됩니다.

*"섹션-클래스"*\
필드 무시 되지만 버전 2.0 이전 버전의 Microsoft c + +와의 호환성을 위해 포함 되었습니다.

## <a name="remarks"></a>설명

개체 파일의 *섹션* 은 메모리에 하나의 단위로 로드 되는 명명 된 데이터 블록입니다. *데이터 섹션* 은 초기화 된 데이터를 포함 하는 섹션입니다. 이 문서에서 *세그먼트* 와 *섹션* 이라는 용어는 동일한 의미를 갖습니다.

초기화 된 변수에 대 한 .obj 파일의 기본 섹션은 `.data` 입니다. 초기화 되지 않은 변수는 0으로 초기화 되 고에 저장 되는 것으로 간주 됩니다 `.bss` .

**Data_seg** pragma 지시문은 변환 단위의 모든 초기화 된 데이터 항목을 *섹션 이름* 이라는 데이터 섹션에 포함 하도록 컴파일러에 지시 합니다. 기본적으로 개체 파일의 초기화 된 데이터에 사용 되는 데이터 섹션의 이름은 `.data` 입니다. 초기화 되지 않은 변수는 0으로 초기화 되 고에 저장 되는 것으로 간주 됩니다 `.bss` . *섹션 이름* 매개 변수가 없는 **data_seg** pragma 지시어는 이후의 초기화 된 데이터 항목에 대 한 데이터 섹션 이름을로 다시 설정 합니다 `.data` .

**Data_seg** 를 사용 하 여 할당 한 데이터는 위치에 대 한 정보를 유지 하지 않습니다.

섹션을 만드는 데 사용 하지 않아야 하는 이름 목록은 [/SECTION](../build/reference/section-specify-section-attributes.md)를 참조 하세요.

Const 변수 ([const_seg](../preprocessor/const-seg.md)), 초기화 되지 않은 데이터 ([bss_seg](../preprocessor/bss-seg.md)) 및 함수 ([code_seg](../preprocessor/code-seg.md))에 대 한 섹션도 지정할 수 있습니다.

[DUMPBIN.EXE](../build/reference/dumpbin-command-line.md) 응용 프로그램을 사용 하 여 개체 파일을 볼 수 있습니다. 지원 되는 각 대상 아키텍처의 DUMPBIN 버전은 Visual Studio에 포함 되어 있습니다.

## <a name="example"></a>예제

```cpp
// pragma_directive_data_seg.cpp
int h = 1;                     // stored in .data
int i = 0;                     // stored in .bss
#pragma data_seg(".my_data1")
int j = 1;                     // stored in .my_data1

#pragma data_seg(push, stack1, ".my_data2")
int l = 2;                     // stored in .my_data2

#pragma data_seg(pop, stack1)   // pop stack1 off the stack
int m = 3;                     // stored in .my_data1

int main() {
}
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
