---
description: '다음에 대 한 자세한 정보: _HAS_ITERATOR_DEBUGGING'
title: _HAS_ITERATOR_DEBUGGING
ms.date: 11/04/2016
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
ms.openlocfilehash: ee1765739624fe7c6fccd41ff84f455d5f90cc42
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231994"
---
# <a name="_has_iterator_debugging"></a>_HAS_ITERATOR_DEBUGGING

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)로 교체된 이 매크로는 반복기 디버깅 기능이 디버그 빌드에서 사용하도록 설정되었는지 여부를 정의합니다. 반복기 디버깅은 기본적으로 디버그 빌드에서는 사용하도록 설정되고 정품 빌드에서는 사용하지 않도록 설정됩니다. 자세한 내용은 [디버그 반복기 지원](../standard-library/debug-iterator-support.md)을 참조 하세요.

> [!IMPORTANT]
> _HAS_ITERATOR_DEBUGGING 매크로를 직접 사용 하는 것은 더 이상 사용 되지 않습니다. 대신 _ITERATOR_DEBUG_LEVEL를 사용 하 여 반복기 디버그 설정을 제어 합니다. 자세한 내용은 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)을 참조하세요.

## <a name="remarks"></a>설명

디버그 빌드에서 반복기 디버깅을 사용 하도록 설정 하려면 _ITERATOR_DEBUG_LEVEL를 2로 설정 합니다. 이는 _HAS_ITERATOR_DEBUGGING 설정 1 또는 사용과 동일 합니다.

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

일반 정품 빌드에서는 _ITERATOR_DEBUG_LEVEL를 2로 설정할 수 없으며 _HAS_ITERATOR_DEBUGGING를 1로 설정할 수 없습니다.

디버그 빌드에서 디버그 반복기를 사용 하지 않도록 설정 하려면 _ITERATOR_DEBUG_LEVEL를 0 또는 1로 설정 합니다. 이 값은 0 또는 사용 하지 않도록 설정 된 _HAS_ITERATOR_DEBUGGING 설정에 해당 합니다.

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>참고 항목

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)\
[디버그 반복기 지원](../standard-library/debug-iterator-support.md)\
[확인 된 반복기](../standard-library/checked-iterators.md)\
[안전 라이브러리: c + + 표준 라이브러리](../standard-library/safe-libraries-cpp-standard-library.md)
