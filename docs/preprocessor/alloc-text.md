---
description: pragmaMicrosoft C/c + +의 alloc_text 지시문에 대해 자세히 알아보세요.
title: alloc_text pragma
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
helpviewer_keywords:
- alloc_text pragma
- pragma, alloc_text
no-loc:
- pragma
ms.openlocfilehash: f20cbf90952c6ac5793c5bdf4d2ef1c533be2126
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713131"
---
# <a name="alloc_text-no-locpragma"></a>`alloc_text` pragma

지정 된 함수 정의가 배치 되는 코드 섹션의 이름을 지정 합니다. 는 pragma 함수 선언 자와 명명 된 함수에 대 한 함수 정의 간에 발생 해야 합니다.

## <a name="syntax"></a>구문

> **`#pragma alloc_text(`** "*텍스트-섹션*" **`,`** *function_1* [ **`,`** *function_2* ...] **`)`**

## <a name="remarks"></a>설명

는 **`alloc_text`** pragma c + + 멤버 함수 또는 오버 로드 된 함수를 처리 하지 않습니다. C 링크를 사용 하 여 선언 된 함수, 즉 링크 사양을 사용 하 여 선언 된 함수에만 적용할 수 **`extern "C"`** 있습니다. pragmaC + + 링크가 있는 함수에서이를 사용 하려고 하면 컴파일러 오류가 발생 합니다.

를 사용 하 여 함수 주소를 지정 하 **`__based`** 는 것은 지원 되지 않으므로 섹션 위치를 지정 하려면를 사용 해야 합니다 **`alloc_text`** pragma . *텍스트 섹션* 으로 지정 된 이름은 큰따옴표로 묶어야 합니다.

는 **`alloc_text`** pragma 지정 된 함수의 선언 뒤와 이러한 함수의 정의 앞에 나타나야 합니다.

에서 참조 되는 함수는 **`alloc_text`** pragma 와 동일한 모듈에서 정의 되어야 합니다 pragma . 그렇지 않고 나중에 정의 되지 않은 함수가 다른 텍스트 섹션으로 컴파일될 경우 오류가 catch 될 수도 있고 그렇지 않을 수도 있습니다. 일반적으로 프로그램은 제대로 실행 되지만 함수는 의도 한 섹션에 할당 되지 않습니다.

의 기타 제한 사항은 다음과 같습니다 **`alloc_text`** .

- 함수 내에서 사용할 수 없습니다.

- 함수가 선언된 후, 그리고 함수가 정의되기 전에 사용되어야 합니다.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
