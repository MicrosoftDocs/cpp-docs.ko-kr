---
description: '자세한 정보: 경로 필드 제한'
title: 경로 필드 제한
ms.date: 11/04/2016
f1_keywords:
- _MAX_EXT
- _MAX_DIR
- _MAX_PATH
- _MAX_FNAME
- _MAX_DRIVE
helpviewer_keywords:
- path field constants
- MAX_FNAME constant
- _MAX_DIR constant
- _MAX_DRIVE constant
- paths, maximum limit
- _MAX_PATH constant
- MAX_DRIVE constant
- _MAX_FNAME constant
- _MAX_EXT constant
- MAX_DIR constant
- MAX_EXT constant
ms.assetid: 2b5d0e43-1347-45b4-8397-24a8a45c444e
ms.openlocfilehash: 41698d946e45a78f9b89f40fdd3c7c58af5d4354
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213483"
---
# <a name="path-field-limits"></a>경로 필드 제한

## <a name="syntax"></a>구문

```cpp
#include <stdlib.h>
```

## <a name="remarks"></a>설명

이러한 상수는 경로 및 경로 내 개별 필드의 최대 길이를 정의합니다.

|상수|의미|
|--------------|-------------|
|`_MAX_DIR`|디렉터리 구성 요소의 최대 길이입니다.|
|`_MAX_DRIVE`|드라이브 구성 요소의 최대 길이입니다.|
|`_MAX_EXT`|확장명 구성 요소의 최대 길이입니다.|
|`_MAX_FNAME`|파일 이름 구성 요소의 최대 길이입니다.|
|`_MAX_PATH`|전체 경로의 최대 길이입니다.|

> [!NOTE]
> C 런타임은 최대 32,768자의 경로 길이를 지원하지만 운영 체제, 특히 파일 시스템에서는 해당 길이보다 긴 경로를 지원합니다. 필드 합계는 FAT32 파일 시스템과의 전체 이전 버전 호환성을 위해 `_MAX_PATH`를 초과할 수 없습니다. Windows Vista NTFS 파일 시스템은 유니코드 API를 사용하는 경우에만 최대 32768자의 경로 길이를 지원합니다. 긴 경로 이름을 사용하는 경우 경로 앞에 \\\\?\ 문자를 붙이고 유니코드 버전의 C 런타임 함수를 사용합니다.

## <a name="see-also"></a>참고 항목

[전역 상수](../c-runtime-library/global-constants.md)
