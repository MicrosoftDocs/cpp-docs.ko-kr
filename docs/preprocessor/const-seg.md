---
description: pragmaMicrosoft C/c + +의 const_seg 지시문에 대해 자세히 알아보세요.
title: const_seg pragma
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
helpviewer_keywords:
- pragma, const_seg
- const_seg pragma
no-loc:
- pragma
ms.openlocfilehash: 602ef749c966f9b28d7d6fa42a2bded1148bbe0d
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98712923"
---
# <a name="const_seg-no-locpragma"></a>`const_seg` pragma

[Const](../cpp/const-cpp.md) 변수가 개체 (.obj) 파일에 저장 되는 섹션 (세그먼트)을 지정 합니다.

## <a name="syntax"></a>구문

> **`#pragma const_seg(`** ["*섹션-이름*" [ **`,`** "*섹션-클래스*"]] **`)`**\
> **`#pragma const_seg(`**{ **`push`**  |  **`pop`** } [ **`,`** *식별자* ] [ **`,`** "*섹션-이름*" [ **`,`** "*섹션-클래스*"]]**`)`**

### <a name="parameters"></a>매개 변수

**`push`**\
필드 내부 컴파일러 스택에 레코드를 넣습니다. 에는 **`push`** *식별자* 와 *섹션 이름이* 있을 수 있습니다.

**`pop`**\
필드 내부 컴파일러 스택의 맨 위에서 레코드를 제거 합니다. 에는 **`pop`** *식별자* 와 *섹션 이름이* 있을 수 있습니다. **`pop`** *식별자* 를 사용 하 여 하나의 명령만을 사용 하 여 여러 레코드를 표시할 수 있습니다. *섹션 이름* 은 pop 뒤의 활성 const 섹션 이름이 됩니다.

*identifier*\
필드 과 함께 사용 되는 경우 **`push`** 내부 컴파일러 스택의 레코드에 이름을 할당 합니다. 에서 사용 되는 경우 **`pop`** 지시문은 *식별자* 가 제거 될 때까지 내부 스택에서 레코드를 팝 합니다. 내부 스택에서 *식별자* 를 찾을 수 없는 경우 아무 것도 팝 되지 않습니다.

"*섹션-이름*" \
필드 섹션의 이름입니다. 에서 사용 하는 경우 **`pop`** 스택이 팝 되 고 *섹션 이름* 은 활성 const 섹션 이름이 됩니다.

"*섹션-클래스*" \
필드 무시 되지만 버전 2.0 이전 버전의 Microsoft c + +와의 호환성을 위해 포함 되었습니다.

## <a name="remarks"></a>설명

개체 파일의 *섹션* 은 메모리에 하나의 단위로 로드 되는 명명 된 데이터 블록입니다. *Const 섹션* 은 상수 데이터를 포함 하는 섹션입니다. 이 문서에서 *세그먼트* 와 *섹션* 이라는 용어는 동일한 의미를 갖습니다.

**`const_seg`** pragma 지시문은 변환 단위의 모든 상수 데이터 항목을 *섹션 이름* 이라는 const 섹션에 배치 하도록 컴파일러에 지시 합니다. 변수에 대 한 개체 파일의 기본 섹션 **`const`** 은 `.rdata` 입니다. **`const`** 스칼라와 같은 일부 변수는 자동으로 코드 스트림으로 인라인 됩니다. 인라인 코드는에 표시 되지 않습니다 `.rdata` . **`const_seg`** pragma *섹션 이름* 매개 변수가 없는 지시문은 이후의 데이터 항목에 대 한 섹션 이름을 **`const`** 로 다시 설정 `.rdata` 합니다.

에서 동적 초기화를 필요로 하는 개체를 정의 하는 경우 `const_seg` 결과는 정의 되지 않은 동작입니다.

섹션을 만드는 데 사용 하지 않아야 하는 이름 목록은을 참조 하십시오 [`/SECTION`](../build/reference/section-specify-section-attributes.md) .

초기화 데이터 ( [`data_seg`](../preprocessor/data-seg.md) ), 초기화 되지 않은 데이터 ( [`bss_seg`](../preprocessor/bss-seg.md) ) 및 함수 ()에 대 한 섹션도 지정할 수 있습니다 [`code_seg`](../preprocessor/code-seg.md) .

[DUMPBIN.EXE](../build/reference/dumpbin-command-line.md) 응용 프로그램을 사용 하 여 개체 파일을 볼 수 있습니다. 지원 되는 각 대상 아키텍처의 DUMPBIN 버전은 Visual Studio에 포함 되어 있습니다.

## <a name="example"></a>예제

```cpp
// pragma_directive_const_seg.cpp
// compile with: /EHsc
#include <iostream>

const int i = 7;               // inlined, not stored in .rdata
const char sz1[]= "test1";     // stored in .rdata

#pragma const_seg(".my_data1")
const char sz2[]= "test2";     // stored in .my_data1

#pragma const_seg(push, stack1, ".my_data2")
const char sz3[]= "test3";     // stored in .my_data2

#pragma const_seg(pop, stack1) // pop stack1 from stack
const char sz4[]= "test4";     // stored in .my_data1

int main() {
    using namespace std;
   // const data must be referenced to be put in .obj
   cout << sz1 << endl;
   cout << sz2 << endl;
   cout << sz3 << endl;
   cout << sz4 << endl;
}
```

```Output
test1
test2
test3
test4
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
