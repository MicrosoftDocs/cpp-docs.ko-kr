---
title: 이름 데코레이션
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: d1557f53a07a544ff4f9e5a63f905e6854fb74ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393157"
---
# <a name="name-decoration"></a>이름 데코레이션

이름 장식은 대개 C++ 명명 체계를 지칭하지만 다른 여러 C 사례에도 적용될 수 있습니다. C++에서는 기본적으로 함수 이름, 매개 변수 및 반환 형식을 사용하여 함수의 링커 이름을 만듭니다. 다음 함수 선언을 살펴보세요.

`void CALLTYPE test(void);`

아래 표에는 여러 호출 규칙에 대한 링커 이름이 나와 있습니다.

|호출 규칙|`extern "C"` 또는 `.c` 파일|`.cpp``.cxx` 또는 `/TP`|
|------------------------|---------------------------|------------------------|
|C 명명 규칙(`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|빠른 호출 명명 규칙 (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|표준 호출 명명 규칙 (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|벡터 호출 명명 규칙 (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

사용 하 여 `extern "C"` 에서 C 함수를 호출 하려면 C++합니다. `extern "C"` 비 클래스에 대해 C 명명 규칙을 사용 하도록 C++ 함수입니다. 컴파일러 스위치에 유의 **/Tc** 하거나 **/Tp**, 파일 이름 확장명을 무시 하 고 C로 파일을 컴파일하지 컴파일러에 지시 하는 또는 C++, 각각. 이러한 옵션은 하지 않을 링커 이름을 발생할 수 있습니다.

함수 프로토타입의 매개 변수가 일치하지 않는 경우에도 이 오류가 발생할 수 있습니다. 이름 장식에서는 함수의 매개 변수가 데코레이트된 최종 함수 이름에 통합됩니다. 함수 선언에 없는 일치 하지 않는 매개 변수 형식을 가진 함수를 호출 해도 lnk2001이 발생할 수도 있습니다.

현재 없는 표준에 대 한 C++ 컴파일러 공급 업체나 간에 서로 다른 버전의 컴파일러를 명명 합니다. 다른 컴파일러로 컴파일한 개체 파일을 연결 하면 동일한 명명 스키마를 생성할 수 없습니다 및 외부 참조 될 수 있습니다.

## <a name="see-also"></a>참고자료

[링커 도구 오류 LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)