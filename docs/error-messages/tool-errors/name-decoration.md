---
description: '자세히 알아보기: 이름 데코레이션'
title: 이름 데코레이션
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: 36360a1e313aba17a203fd1c2c4412cb927d1591
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155139"
---
# <a name="name-decoration"></a>이름 데코레이션

이름 장식은 대개 C++ 명명 체계를 지칭하지만 다른 여러 C 사례에도 적용될 수 있습니다. C++에서는 기본적으로 함수 이름, 매개 변수 및 반환 형식을 사용하여 함수의 링커 이름을 만듭니다. 다음 함수 선언을 고려 하십시오.

`void CALLTYPE test(void);`

아래 표에는 여러 호출 규칙에 대한 링커 이름이 나와 있습니다.

|호출 규칙|`extern "C"` 또는 `.c` 파일|`.cpp`, `.cxx` 또는 `/TP`|
|------------------------|---------------------------|------------------------|
|C 명명 규칙 ( **`__cdecl`** )|`_test`|`?test@@ZAXXZ`|
|빠른 호출 명명 규칙 ( **`__fastcall`** )|`@test@0`|`?test@@YIXXZ`|
|표준 호출 명명 규칙 ( **`__stdcall`** )|`_test@0`|`?test@@YGXXZ`|
|벡터 호출 명명 규칙 ( **`__vectorcall`** )|`test@@0`|`?test@@YQXXZ`|

C `extern "C"` + +에서 c 함수를 호출 하는 데 사용 합니다. `extern "C"` 비 클래스 c + + 함수에 대해 C 명명 규칙을 강제로 사용 합니다. 컴파일러에서 파일 이름 확장명을 무시 하 고 각각 파일을 C 또는 c + +로 컴파일하도록 지시 하는 컴파일러 스위치 **/tc** 또는 **/tp** 를 알고 있어야 합니다. 이러한 옵션을 선택 하면 예기치 않은 링커 이름이 표시 될 수 있습니다.

함수 프로토타입의 매개 변수가 일치하지 않는 경우에도 이 오류가 발생할 수 있습니다. 이름 장식에서는 함수의 매개 변수가 데코레이트된 최종 함수 이름에 통합됩니다. 함수 선언과 일치 하지 않는 매개 변수 형식으로 함수를 호출 하면 LNK2001이 발생할 수도 있습니다.

현재는 컴파일러 공급 업체 또는 다른 버전의 컴파일러 간에 c + + 명명에 대 한 표준이 없습니다. 다른 컴파일러에서 컴파일된 개체 파일을 연결 하면 동일한 이름 지정 체계가 생성 되지 않을 수 있으며이로 인해 확인 되지 않은 외부에서 발생 하는 경우

## <a name="see-also"></a>참고 항목

[링커 도구 오류 LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)
