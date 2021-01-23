---
description: pragmaMicrosoft C/c + +의 섹션 지시문에 대해 자세히 알아보세요.
title: 여기서 pragma
ms.date: 01/22/2021
f1_keywords:
- section_CPP
- vc-pragma.section
helpviewer_keywords:
- pragma, section
- section pragma
no-loc:
- pragma
ms.openlocfilehash: 8bd55bbba65480b7345376059489d8aef945ab34
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713235"
---
# <a name="section-no-locpragma"></a>`section` pragma

OBJ 파일에 섹션을 만듭니다.

## <a name="syntax"></a>구문

> **`#pragma section( "`***섹션-이름* **`"`** [ **`,`** *특성* ]**`)`**

## <a name="remarks"></a>설명

이 문서에서 *세그먼트* 와 *섹션* 은 동일한 의미를 갖습니다.

섹션을 정의 하 고 나면 컴파일의 나머지 부분에 대해 유효한 상태로 유지 됩니다. 그러나를 사용 해야 [`__declspec(allocate)`](../cpp/allocate.md) 하거나, 섹션에 아무 것도 배치 하지 않습니다.

*섹션* 이름은 섹션 이름이 되는 필수 매개 변수입니다. 이 이름은 모든 표준 섹션 이름과 충돌하지 않아야 합니다. [`/SECTION`](../build/reference/section-specify-section-attributes.md)섹션을 만들 때 사용할 수 없는 이름 목록은를 참조 하세요.

*특성* 은 섹션에 할당할 하나 이상의 쉼표로 구분 된 특성으로 구성 된 선택적 매개 변수입니다. 가능한 *특성* 은 다음과 같습니다.

| attribute | 설명 |
|--|--|
| **`read`** | 데이터에 대한 읽기 작업을 허용합니다. |
| **`write`** | 데이터에 대한 쓰기 작업을 허용합니다. |
| **`execute`** | 코드가 실행될 수 있도록 합니다. |
| **`shared`** | 이미지를 로드하는 모든 프로세스에서 섹션을 공유합니다. |
| **`nopage`** | 섹션을 페이징할 수 없는 것으로 표시 합니다. Win32 장치 드라이버에 유용 합니다. |
| **`nocache`** | 섹션을 캐시할 수 없음으로 표시 합니다. Win32 장치 드라이버에 유용 합니다. |
| **`discard`** | 섹션을 삭제 가능한로 표시 합니다. Win32 장치 드라이버에 유용 합니다. |
| **`remove`** | 섹션을 메모리 상주 하지 않는 것으로 표시 합니다. 가상 장치 드라이버 (V *x* D)에만 해당 됩니다. |

특성을 지정 하지 않으면 섹션에 **`read`** 및 **`write`** 특성이 있습니다.

## <a name="example"></a>예제

이 예제에서 첫 번째 섹션은 pragma 섹션과 해당 특성을 식별 합니다. 정수는를 `j` `mysec` 사용 하 여 선언 되지 않았으므로에 배치 되지 않습니다 `__declspec(allocate)` . 대신, `j` 데이터 섹션으로 이동 합니다. 이 정수는 `i` `mysec` 저장소 클래스 특성 때문에로 이동 `__declspec(allocate)` 합니다.

```cpp
// pragma_section.cpp
#pragma section("mysec",read,write)
int j = 0;

__declspec(allocate("mysec"))
int i = 0;

int main(){}
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
