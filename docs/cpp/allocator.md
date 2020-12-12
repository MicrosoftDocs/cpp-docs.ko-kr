---
description: 다음에 대해 자세히 알아보세요. `allocator`
title: allocator
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: 20ca879259c49f01f5283a867b4e562cfddcc058
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288271"
---
# `allocator`

**Microsoft 전용**

**`allocator`** 선언 지정자는 사용자 지정 메모리 할당 함수에 적용 되어 ETW(Windows용 이벤트 추적) (ETW)를 통해 할당을 표시할 수 있습니다.

## <a name="syntax"></a>구문

> **`__declspec(allocator)`**

## <a name="remarks"></a>설명

Visual Studio의 네이티브 메모리 프로파일러는 런타임 중 내보낸 할당 ETW 이벤트 데이터를 수집 하는 방식으로 작동 합니다. CRT 및 Windows SDK의 할당자가 해당 할당 데이터를 캡처할 수 있도록 원본 수준에서 주석이 추가되었습니다. 사용자 고유의 할당자를 작성 하는 경우 `__declspec(allocator)` myMalloc에 대 한 다음 예제 처럼 새로 할당 된 힙 메모리에 대 한 포인터를 반환 하는 모든 함수를로 데코레이팅 할 수 있습니다.

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

자세한 내용은 [Visual Studio의 메모리 사용 측정](/visualstudio/profiling/memory-usage) 및 [사용자 지정 네이티브 ETW 힙 이벤트](/visualstudio/profiling/custom-native-etw-heap-events)를 참조 하세요.

**Microsoft 전용 종료**
