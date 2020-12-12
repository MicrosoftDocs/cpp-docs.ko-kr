---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4655'
title: 컴파일러 경고(수준 1) C4655
ms.date: 08/27/2018
f1_keywords:
- C4655
helpviewer_keywords:
- C4655
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
ms.openlocfilehash: 2573ac5410114a0fe4ff4b074b83bbbb2efc8c97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318789"
---
# <a name="compiler-warning-level-1-c4655"></a>컴파일러 경고(수준 1) C4655

> '*symbol*': 변수 형식이 마지막 빌드 후 새로 만들어졌거나 다른 곳에서 다르게 정의 되었습니다.

## <a name="remarks"></a>설명

마지막으로 빌드가 성공한 이후 새 데이터 형식을 변경하거나 추가했습니다. 편집하며 계속하기는 기존 데이터 형식에 대한 변경 내용은 지원하지 않습니다.

이 경고 뒤에는 [심각한 오류 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)가 발생합니다. 자세한 내용은 [지원되는 코드 변경](/visualstudio/debugger/supported-code-changes-cpp)을 참조하세요.

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>현재 디버그 세션을 끝내지 않고 이 경고를 제거하려면

1. 데이터 형식을 오류가 발생하기 이전 상태로 다시 변경합니다.

2. **디버그** 메뉴에서 **코드 변경 내용 적용** 을 선택합니다.

### <a name="to-remove-this-warning-without-changing-your-source-code"></a>소스 코드를 변경하지 않고 이 경고를 제거하려면

1. **디버그** 메뉴에서 **디버깅 중지** 를 선택합니다.

2. **빌드** 메뉴에서 **빌드** 를 선택합니다.
