---
description: '자세한 정보: 컴파일러 제한'
title: 컴파일러 한계
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: 7471b6e161f6e1f1466fdc27266249cefc17f7ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318158"
---
# <a name="compiler-limits"></a>컴파일러 한계

C++ 표준에서는 다양한 언어 구문에 대한 한도를 권장합니다. 다음은 Microsoft c + + 컴파일러가 권장 된 제한을 구현 하지 않는 경우의 목록입니다. 첫 번째 숫자는 ISO c + + 11 표준 (INCITS/ISO/IEC 14882-2011 [2012], 부록 B)에서 설정 된 한도이 고 두 번째 숫자는 Microsoft c + + 컴파일러에서 구현 하는 제한입니다.

- 복합 문, 반복 제어 구조 및 선택 컨트롤 구조의 중첩 수준-c + + 표준: 256, Microsoft c + + 컴파일러: 중첩 된 문의 조합에 따라 다르지만 일반적으로 100과 110 사이에 있습니다.

- 단일 매크로 정의의 매개 변수-c + + 표준: 256, Microsoft c + + 컴파일러: 127.

- 한 매크로 호출의 인수-c + + standard: 256, Microsoft c + + 컴파일러 127.

- 문자열 리터럴 또는 와이드 문자열 리터럴의 문자 (연결 후)-c + + 표준: 65536, Microsoft c + + 컴파일러: 65535 싱글바이트 문자 (NULL 종결자 포함) 및 32767 더블 바이트 문자 (NULL 종결자 포함)

- 단일 c + + 표준에서 중첩 된 클래스, 구조체 또는 공용 구조체 정의의 수준 `struct-declaration-list` : 256, Microsoft c + + 컴파일러: 16.

- 생성자 정의의 멤버 이니셜라이저-c + + 표준: 6144, Microsoft c + + 컴파일러: 6144 이상

- 한 식별자의 범위 자격-c + + 표준: 256, Microsoft c + + 컴파일러: 127.

- 중첩 된 **`extern`** 사양-c + + 표준: 1024, Microsoft c + + 컴파일러: 9 (전역 범위에서 암시적 사양을 계산 하지 않음 **`extern`** , **`extern`** 전역 범위에서 암시적 사양의 수를 계산 하는 경우 10).

- 템플릿 선언의 템플릿 인수-c + + standard: 1024, Microsoft c + + 컴파일러: 2046.

## <a name="see-also"></a>참고 항목

[비표준 동작](../cpp/nonstandard-behavior.md)
