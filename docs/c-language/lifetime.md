---
description: '자세한 정보: 수명'
title: 수명
ms.date: 11/04/2016
helpviewer_keywords:
- local variables, lifetime
- variables, automatic
- storage classes, lifetime
- variables, lifetime
- automatic storage class
- automatic storage class, duration
- storage class specifiers, storage duration
- memory allocation, dynamic allocation
- functions [C++], lifetime
- storage duration
- dynamic memory allocation
- memory allocation, dynamic
- lifetime
- global variables, lifetime
ms.assetid: ff0b42cb-3f0f-49a3-a94f-d1d825d8ddfe
ms.openlocfilehash: 11db85cb6df76de320b78f274061499d838151da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243525"
---
# <a name="lifetime"></a>수명

"수명"은 변수나 함수가 존재하는 프로그램 실행 중의 기간입니다. 식별자의 스토리지 기간에 따라 수명이 결정됩니다.

*storage-class-specifier* **`static`** 을 사용하여 선언된 식별자에는 정적 저장 기간이 있습니다. 정적 스토리지 기간("글로벌"이라고도 함)이 있는 식별자는 프로그램의 실행 기간 동안 스토리지와 정의된 값을 갖습니다. 프로그램 시작 전에 스토리지가 예약되고 식별자의 저장된 값이 한 번만 초기화됩니다. 외부 또는 내부 링크를 사용하여 선언된 식별자에도 정적 스토리지 기간이 있습니다([링크](../c-language/linkage.md) 참조).

**`static`** 스토리지 클래스 지정자 없이 선언된 식별자는 함수 내에서 선언되는 경우 자동 스토리지 기간을 갖게 됩니다. 자동 스토리지 기간이 있는 식별자("로컬 식별자")는 해당 식별자가 정의되거나 선언된 블록 내에서만 스토리지와 정의된 값을 갖습니다. 자동 식별자의 경우 프로그램이 해당 블록에 진입할 때마다 새 스토리지가 할당되고 프로그램이 해당 블록을 나갈 때 스토리지 및 값이 손실됩니다. 링크 없이 함수에서 선언된 식별자에도 자동 스토리지 기간이 있습니다.

다음 규칙은 식별자에 전역(정적) 수명이 있는지 아니면 로컬(자동) 수명이 있는지를 지정합니다.

- 모든 함수는 정적 수명을 갖고 있으므로 프로그램 실행 중에 항상 존재합니다. 외부 수준(즉, 함수 정의와 동일한 수준에 있는 프로그램의 모든 블록 외부)에서 선언된 식별자에는 항상 전역(정적) 수명이 있습니다.

- 지역 변수는 이니셜라이저가 있는 경우 **`static`** 으로 선언되지 않는 한 만들어질 때마다 초기화됩니다. 함수 매개 변수에도 로컬 수명이 있습니다. **`static`** 스토리지 클래스 지정자를 선언에 포함하여 블록 내에서 식별자에 대한 글로벌 수명을 지정할 수 있습니다. **`static`** 으로 선언된 변수는 블록에 한 번 진입한 후 다음에 진입할 때까지 값을 유지합니다.

전역 수명이 있는 식별자(예: 외부에서 선언된 변수 또는 **`static`** 키워드를 사용하여 선언된 지역 변수)가 소스 프로그램이 실행되는 동안 계속 존재하지만 프로그램의 일부 부분에서 표시되지 않을 수 있습니다. 표시 유형에 대한 자세한 내용은 [범위 및 표시 유형](../c-language/scope-and-visibility.md)을 참조하고, *스토리지 클래스 지정자* 비터미널에 대한 설명은 [스토리지 클래스](../c-language/c-storage-classes.md)를 참조하세요.

메모리는 `malloc` 등의 특수 라이브러리 루틴을 사용하여 만들어지는 경우 필요에 따라(동적) 할당될 수 있습니다. 동적 메모리 할당은 라이브러리 루틴을 사용하므로 언어의 일부로 간주되지 않습니다. *런타임 라이브러리 참조* 에서 [malloc](../c-runtime-library/reference/malloc.md) 함수를 참조하세요.

## <a name="see-also"></a>참조

[수명, 범위, 표시 유형 및 링크](../c-language/lifetime-scope-visibility-and-linkage.md)
