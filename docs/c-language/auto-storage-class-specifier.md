---
title: 자동 스토리지 클래스 지정자
ms.date: 11/04/2016
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
ms.openlocfilehash: 7f70ee1944e07ebcbd32b8110eee27fa6631be63
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509308"
---
# <a name="auto-storage-class-specifier"></a>`auto` 스토리지 클래스 지정자

**`auto`** 스토리지 클래스 지정자는 로컬 수명을 가진 변수인 자동 변수를 선언합니다. **`auto`** 변수는 자신이 선언된 블록에서만 표시됩니다. [초기화](../c-language/initialization.md)에서 설명한 대로 **`auto`** 변수 선언에는 이니셜라이저를 포함할 수 있습니다. **`auto`** 스토리지 클래스가 있는 변수는 자동으로 초기화되지 않으므로 이 변수를 선언할 때 명시적으로 초기화하거나 블록에 있는 명령문에서 이 변수에 초기 값을 할당해야 합니다. 초기화되지 않은 **`auto`** 변수의 값이 정의되지 않았습니다. (이니셜라이저가 제공될 경우 **`auto`** 또는 **`register`** 스토리지 클래스의 지역 변수가 범위에 도달할 때마다 초기화됩니다.)

외부 또는 **`static`** 항목의 주소를 사용하여 내부 **`static`** 변수(로컬 또는 블록 범위가 있는 정적 변수)를 초기화할 수 있지만 **`auto`** 항목 주소가 상수가 아니므로 다른 **`auto`** 항목의 주소를 사용하여 초기화할 수는 없습니다.

## <a name="see-also"></a>참조

[`auto` 키워드](../cpp/auto-cpp.md)
