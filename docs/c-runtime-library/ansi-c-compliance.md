---
title: ANSI C 규격
description: ANSI C 규격에 대 한 Microsoft C 런타임 명명 규칙의 개요입니다.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Ansi
helpviewer_keywords:
- underscores, leading
- compatibility [C++], ANSI C
- compliance with ANSI C
- conventions [C++], Microsoft extensions
- underscores
- naming conventions [C++], Microsoft library
- ANSI [C++], C standard
- Microsoft extensions naming conventions
ms.assetid: 6be271bf-eecf-491a-a928-0ee2dd60e3b9
ms.openlocfilehash: 39a3f9299be7dbef4783faa8e6d08fe6ad8461f5
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590305"
---
# <a name="ansi-c-compliance"></a>ANSI C 규격

런타임 시스템의 모든 Microsoft 고유 식별자(함수, 매크로, 상수, 변수 및 형식 정의 등)의 명명 규칙은 ANSI와 호환됩니다. 이 설명서에서는 ANSI/ISO C 표준을 따르는 런타임 함수는 ANSI와 호환되는 것으로 기술되어 있습니다. ANSI 호환 애플리케이션은 이러한 ANSI 호환 함수를 사용해야 합니다.

Microsoft 고유의 함수 및 전역 변수 이름은 한개의 밑줄로 시작합니다. 이러한 이름은 코드의 범위 내에서 로컬로만 재정의될 수 있습니다. 예를들어 Microsoft 런타임 헤더 파일을 포함하면 동일한 이름의 지역 변수를 선언함으로써 `_open`이라는 이름의 Microsoft 고유의 함수를 재정의하여 로컬로 무시할 수 있습니다. 그러나 고유한 전역 함수나 전역 변수에는 이 이름을 사용할 수 없습니다.

Microsoft 매크로 및 매니페스트 상수의 이름은 두 개의 밑줄로 시작하거나 하나의 밑줄을 붙이고 대문자로 시작합니다. 이러한 식별자의 범위는 전체적으로 영향을 받습니다. 예를 들어 이러한 이유로 Microsoft 식별자 **_UPPER**를 사용할 수 없습니다.

## <a name="see-also"></a>참고 항목

[호환성](../c-runtime-library/compatibility.md)
