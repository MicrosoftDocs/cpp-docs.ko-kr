---
description: '자세한 정보: 디버그 빌드를 사용한 메모리 덮어쓰기 확인'
title: 디버그 빌드를 사용한 메모리 덮어쓰기 확인
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
ms.openlocfilehash: 03981696a0314632aebb959d6fa1d986145c087c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199066"
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>디버그 빌드를 사용한 메모리 덮어쓰기 확인

디버그 빌드를 사용하여 메모리 덮어쓰기를 확인하려면 먼저 디버그를 위해 프로젝트를 다시 빌드해야 합니다. 그런 다음 애플리케이션의 `InitInstance` 함수 시작 부분으로 이동하여 다음 줄을 추가합니다.

```
afxMemDF |= checkAlwaysMemDF;
```

디버그 메모리 할당자는 모든 메모리 할당 주위에 가드 바이트를 넣습니다. 그러나 가드 바이트는 변경되었는지가 확인된 경우(메모리 덮어쓰기를 나타냄) 외에는 유용하지 않습니다. 확인된 경우에는 실제로 메모리 덮어쓰기를 수행할 수 있는 버퍼를 제공합니다.

`checkAlwaysMemDF`를 켜면 **`new`** 또는 **`delete`** 를 호출할 때마다 MFC에서 `AfxCheckMemory` 함수를 호출하도록 합니다. 메모리 덮어쓰기가 검색되면 다음과 유사한 추적 메시지를 생성합니다.

```
Damage Occurred! Block=0x5533
```

관련 메시지 중 하나가 표시되면 코드를 단계별로 실행하여 손상이 발생한 위치를 확인해야 합니다. 메모리 덮어쓰기가 발생한 위치를 더 정확하게 격리하려면 직접 `AfxCheckMemory`를 명시적으로 호출할 수 있습니다. 예를 들어:

```
ASSERT(AfxCheckMemory());
    DoABunchOfStuff();
    ASSERT(AfxCheckMemory());
```

첫 번째 ASSERT가 성공하고 두 번째 ASSERT가 실패한 경우 두 호출 사이의 함수에서 메모리 덮어쓰기가 발생했음을 의미합니다.

애플리케이션의 특성에 따라서는 `afxMemDF`로 인해 프로그램이 너무 느리게 실행되어 테스트할 수 없음을 확인할 수도 있습니다. `afxMemDF` 변수로 인해 new 및 delete를 호출할 때마다 `AfxCheckMemory`가 호출됩니다. 이 경우 위에 표시된 대로 `AfxCheckMemory`() 호출을 분산하고 해당 방식으로 메모리 덮어쓰기를 격리해야 합니다.

## <a name="see-also"></a>참조

[릴리스 빌드 문제 해결](fixing-release-build-problems.md)
