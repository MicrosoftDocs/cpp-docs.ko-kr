---
description: 파일 특성 상수에 대해 자세히 알아보세요.
title: 파일 특성 상수
ms.date: 11/04/2016
f1_keywords:
- A_HIDDEN
- _A_NORMAL
- _A_SUBDIR
- _A_RDONLY
- A_NORMAL
- A_SUBDIR
- _A_SYSTEM
- c.constants.file
- _A_HIDDEN
- A_RDONLY
- _A_ARCH
- A_ARCH
helpviewer_keywords:
- constants [C++], file attributes
- file attribute constants [C++]
- _A_SYSTEM constant
- files [C++], file attribute constants
- _A_SUBDIR constant
- _A_ARCH constant
- _A_NORMAL constant
- _A_HIDDEN constant
- _A_RDONLY constant
ms.assetid: 8dc8ccb9-99f5-446b-876c-7ebecc2f764f
ms.openlocfilehash: 8b57549b4a21cc5d699f933009c575b3f3fca81d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306367"
---
# <a name="file-attribute-constants"></a>파일 특성 상수

## <a name="syntax"></a>구문

```
#include <io.h>
```

## <a name="remarks"></a>설명

이러한 상수는 함수가 지정하는 디렉터리나 파일의 현재 속성을 지정합니다.

특성은 다음 매니페스트 상수로 표시됩니다.

|상수|설명|
|-|-|
|`_A_ARCH`| 보관 파일입니다. BACKUP 명령으로 파일을 변경하고 지울 때마다 설정합니다. 값: 0x20|
|`_A_HIDDEN`| 숨김 파일입니다. /AH 옵션을 사용하지 않는 한 일반적으로 DIR 명령으로 표시되지 않습니다. 일반 파일 및 이 특성이 있는 파일에 대한 정보를 반환합니다. 값: 0x02|
|`_A_NORMAL`| 일반 파일입니다. 제한 없이 파일을 읽거나 파일에 쓸 수 있습니다. 값: 0x00|
|`_A_RDONLY`| 읽기 전용입니다. 쓰기 위해 파일을 열 수 없고 동일한 이름의 파일을 만들 수 없습니다. 값: 0x01|
|`_A_SUBDIR`| 하위 디렉터리입니다. 값: 0x10|
|`_A_SYSTEM`| 시스템 파일입니다. /AS 옵션을 사용하지 않는 한 일반적으로 DIR 명령으로 표시되지 않습니다. 값: 0x04|

여러 상수는 OR 연산자(&#124;)와 함께 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[파일 이름 검색 함수](../c-runtime-library/filename-search-functions.md)<br/>
[전역 상수](../c-runtime-library/global-constants.md)
