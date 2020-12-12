---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4657'
title: 컴파일러 경고(수준 1) C4657
ms.date: 11/04/2016
f1_keywords:
- C4657
helpviewer_keywords:
- C4657
ms.assetid: eb750050-cea6-4ead-b80c-d5dcd4971cfc
ms.openlocfilehash: b0a1af53c145495e4daacfa09247ea8cc6fb5697
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318792"
---
# <a name="compiler-warning-level-1-c4657"></a>컴파일러 경고(수준 1) C4657

최근 빌드 후 새로 만들어진 데이터 형식이 식에 들어 있습니다.

데이터 형식을 추가하거나 변경하여 마지막으로 성공한 빌드 후 소스 코드에 대해 새롭게 만들었습니다. 편집하며 계속하기는 기존 데이터 형식에 대한 변경 내용은 지원하지 않습니다.

이 경고는 뒤에 항상 [심각한 오류 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)가 옵니다. 자세한 내용은 [지원되는 코드 변경](/visualstudio/debugger/supported-code-changes-cpp)을 참조하세요.

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>현재 디버그 세션을 끝내지 않고 이 경고를 제거하려면

1. 데이터 형식을 오류가 발생하기 이전 상태로 다시 변경합니다.

1. **디버그** 메뉴에서 **코드 변경 내용 적용** 을 선택합니다.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>소스 코드를 변경하지 않고 이 오류를 제거하려면

1. **디버그** 메뉴에서 **디버깅 중지** 를 선택합니다.

1. **빌드** 메뉴에서 **빌드** 를 선택합니다.
