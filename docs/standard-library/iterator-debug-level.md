---
description: '다음에 대 한 자세한 정보: _ITERATOR_DEBUG_LEVEL'
title: _ITERATOR_DEBUG_LEVEL
ms.date: 11/04/2016
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
ms.openlocfilehash: 769b7f3a8eecd3c994ee82b67385f080f0945f33
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306640"
---
# <a name="_iterator_debug_level"></a>_ITERATOR_DEBUG_LEVEL

_ITERATOR_DEBUG_LEVEL 매크로는 확인 된 [반복기](../standard-library/checked-iterators.md) 및 [디버그 반복기 지원을](../standard-library/debug-iterator-support.md) 사용할 수 있는지 여부를 제어 합니다. 이 매크로는 이전 _SECURE_SCL 및 _HAS_ITERATOR_DEBUGGING 매크로의 기능을 대체 하 고 결합 합니다.

## <a name="macro-values"></a>매크로 값

다음 표에서는 _ITERATOR_DEBUG_LEVEL 매크로에 사용할 수 있는 값을 요약 하 여 보여 줍니다.

|컴파일 모드|매크로 값|설명|
|----------------------|----------------|-----------------|
|**디버그**|||
||0|확인된 반복기와 반복기 디버깅을 사용하지 않도록 설정합니다.|
||1|확인된 반복기를 사용하도록 설정하고 반복기 디버깅을 사용하지 않도록 설정합니다.|
||2(기본값)|반복기 디버깅을 사용하도록 설정하며 확인된 반복기는 관련이 없습니다.|
|**릴리스**|||
||0(기본값)|확인된 반복기를 사용하지 않도록 설정합니다.|
||1|확인된 반복기를 사용하도록 설정하며 반복기 디버깅은 관련이 없습니다.|

릴리스 모드에서 _ITERATOR_DEBUG_LEVEL 2로 지정 하면 컴파일러에서 오류를 생성 합니다.

## <a name="remarks"></a>설명

_ITERATOR_DEBUG_LEVEL 매크로는 확인 된 [반복기](../standard-library/checked-iterators.md) 를 사용 하도록 설정할지 여부와 디버그 모드에서 [디버그 반복기 지원](../standard-library/debug-iterator-support.md) 사용 여부를 제어 합니다. _ITERATOR_DEBUG_LEVEL 1 또는 2로 정의 된 경우 확인 된 반복기는 컨테이너의 경계를 덮어쓰지 않도록 합니다. _ITERATOR_DEBUG_LEVEL 0 인 경우 반복기가 확인 되지 않습니다. _ITERATOR_DEBUG_LEVEL 1로 정의 된 경우 안전 하지 않은 반복기 사용으로 인해 런타임 오류가 발생 하 고 프로그램이 종료 됩니다. _ITERATOR_DEBUG_LEVEL 2로 정의 된 경우 안전 하지 않은 반복기 사용으로 인해 assert 및 런타임 오류 대화 상자가 표시 되어 디버거를 중단할 수 있습니다.

_ITERATOR_DEBUG_LEVEL 매크로는 _SECURE_SCL 및 _HAS_ITERATOR_DEBUGGING 매크로와 유사한 기능을 지원 하기 때문에 특정 상황에서 사용할 매크로 및 매크로 값이 확실 하지 않을 수 있습니다. 혼동을 방지 하려면 _ITERATOR_DEBUG_LEVEL 매크로만 사용 하는 것이 좋습니다. 이 표에서는 기존 코드의 _SECURE_SCL 및 _HAS_ITERATOR_DEBUGGING에 대 한 다양 한 값에 사용할 _ITERATOR_DEBUG_LEVEL 매크로 값에 대해 설명 합니다.

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0(릴리스 기본값)|0(사용 안 함)|0(사용 안 함)|
|1|1(사용)|0(사용 안 함)|
|2(디버그 기본값)|(관련 없음)|1(디버그 모드에서 사용)|

확인된 반복기에 대한 경고를 사용하지 않도록 설정하는 방법에 대한 자세한 내용은 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)을 참조하세요.

### <a name="example"></a>예제

_ITERATOR_DEBUG_LEVEL 매크로에 대 한 값을 지정 하려면 [/d](../build/reference/d-preprocessor-definitions.md) 컴파일러 옵션을 사용 하 여 명령줄에서 정의 하거나 `#define` c + + 표준 라이브러리 헤더를 소스 파일에 포함 하기 전에를 사용 합니다. 예를 들어 명령줄에서 *sample* 을 디버그 모드로 컴파일하고 디버그 반복기 지원을 사용 하려면 _ITERATOR_DEBUG_LEVEL 매크로 정의를 지정할 수 있습니다.

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

소스 파일에서 반복기를 정의하는 표준 라이브러리 헤더 앞에 매크로를 지정합니다.

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>참고 항목

[확인 된 반복기](../standard-library/checked-iterators.md)\
[디버그 반복기 지원](../standard-library/debug-iterator-support.md)\
[안전 라이브러리: c + + 표준 라이브러리](../standard-library/safe-libraries-cpp-standard-library.md)
