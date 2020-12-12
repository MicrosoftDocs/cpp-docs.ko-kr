---
description: '다음에 대 한 자세한 정보: _SECURE_SCL'
title: _SECURE_SCL
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
ms.openlocfilehash: 1a0e32ada449709a60eb601138ce0bb8b7ae9123
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197103"
---
# <a name="_secure_scl"></a>_SECURE_SCL

[확인된 반복기](../standard-library/checked-iterators.md)가 사용하도록 설정되었는지를 정의하는 이 매크로는 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)로 교체되었습니다. 확인된 반복기는 기본적으로 디버그 빌드에서는 사용하도록 설정되고 정품 빌드에서는 사용하지 않도록 설정됩니다.

> [!IMPORTANT]
> _SECURE_SCL 매크로를 직접 사용 하는 것은 더 이상 사용 되지 않습니다. 대신 _ITERATOR_DEBUG_LEVEL를 사용 하 여 확인 된 반복기 설정을 제어 합니다. 자세한 내용은 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)을 참조하세요.

## <a name="remarks"></a>설명

확인된 반복기를 사용하는 경우에는 안전하지 않은 반복기 사용으로 인해 런타임 오류가 발생하며 프로그램이 종료됩니다. 확인 된 반복기를 사용 하도록 설정 하려면 _ITERATOR_DEBUG_LEVEL을 1 또는 2로 설정 합니다. 이는 _SECURE_SCL 설정 1 또는 사용과 동일 합니다.

```cpp
#define _ITERATOR_DEBUG_LEVEL 1
```

확인 된 반복기를 사용 하지 않도록 설정 하려면 _ITERATOR_DEBUG_LEVEL를 0으로 설정 합니다. 이 값은 0 또는 사용 하지 않도록 설정 된 _SECURE_SCL 설정에 해당 합니다.

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

확인된 반복기에 대한 경고를 사용하지 않도록 설정하는 방법에 대한 자세한 내용은 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)\
[확인 된 반복기](../standard-library/checked-iterators.md)\
[디버그 반복기 지원](../standard-library/debug-iterator-support.md)\
[안전 라이브러리: c + + 표준 라이브러리](../standard-library/safe-libraries-cpp-standard-library.md)
