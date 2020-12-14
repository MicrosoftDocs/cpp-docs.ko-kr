---
description: '자세한 정보: 심각한 오류 C1004'
title: 심각한 오류 C1004
ms.date: 11/04/2016
f1_keywords:
- C1004
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
ms.openlocfilehash: f21978f5ff314a8273dde60428dc89ca0c5767b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262687"
---
# <a name="fatal-error-c1004"></a>심각한 오류 C1004

예기치 않은 파일의 끝이 있습니다.

컴파일러가 구문을 확인 하지 않고 소스 파일의 끝에 도달 했습니다. 코드에 다음 요소 중 하나가 없을 수 있습니다.

- 닫는 중괄호

- 닫는 괄호

- 닫는 주석 표식 (*/)

- 세미콜론

이 오류를 해결 하려면 다음을 확인 하십시오.

- 기본 디스크 드라이브에 임시 파일의 공간이 부족 하 여 원본 파일 만큼 공간이 두 배 정도 필요 합니다.

- `#if`False로 평가 되는 지시문에는 닫는 `#endif` 지시문이 없습니다.

- 원본 파일이 캐리지 리턴 및 줄 바꿈으로 끝나지 않습니다.

다음 샘플에서는 C1004를 생성 합니다.

```cpp
// C1004.cpp
#if TEST
int main() {}
// C1004
```

해결 방법:

```cpp
// C1004b.cpp
#if TEST
#endif

int main() {}
```
