---
description: '자세히 알아보기: 파일 상수'
title: 파일 상수
ms.date: 11/04/2016
f1_keywords:
- _O_EXCL
- _O_RDWR
- _O_APPEND
- _O_RDONLY
- _O_TRUNC
- _O_CREAT
- _O_WRONLY
helpviewer_keywords:
- _O_RDWR constant
- O_EXCL constant
- O_RDWR constant
- O_WRONLY constant
- O_APPEND constant
- O_CREAT constant
- _O_CREAT constant
- _O_APPEND constant
- _O_EXCL constant
- O_TRUNC constant
- _O_RDONLY constant
- _O_TRUNC constant
- O_RDONLY constant
- _O_WRONLY constant
ms.assetid: c8fa5548-9ac2-4217-801d-eb45e86f2fa4
ms.openlocfilehash: a174a9bd8924f4d209f937187614863ce7111b3b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296604"
---
# <a name="file-constants"></a>파일 상수

## <a name="syntax"></a>구문

```
#include <fcntl.h>
```

## <a name="remarks"></a>설명

이러한 상수 중 하나 이상을 사용하여 만든 정수 식에 따라 허용되는 읽기 또는 쓰기 작업의 형식이 결정됩니다. 이 식은 하나 이상의 상수를 변환 모드 상수와 결합하여 만듭니다.

파일 상수는 다음과 같습니다.

|상수|설명|
|-|-|
| `_O_APPEND`  | 매번 쓰기 작업 전에 파일 포인터의 위치를 파일의 끝으로 변경합니다.  |
| `_O_CREAT`  | 쓰기용 새 파일을 만들고 엽니다. *filename* 으로 지정한 파일이 있을 경우에는 이 상수가 적용되지 않습니다.  |
| `_O_EXCL`  | *filename* 으로 지정한 파일이 있을 경우 오류 값을 반환합니다. `_O_CREAT`와 함께 사용할 때만 적용됩니다.  |
| `_O_RDONLY`  | 파일을 읽기 전용으로 엽니다. 이 플래그를 지정할 경우 `_O_RDWR`과 `_O_WRONLY`를 모두 지정할 수 없습니다.  |
| `_O_RDWR`  | 파일을 읽기 및 쓰기용으로 엽니다. 이 플래그를 지정할 경우 `_O_RDONLY`와 `_O_WRONLY`를 모두 지정할 수 없습니다.  |
| `_O_TRUNC`  | 기존 파일을 열고 길이를 0으로 자릅니다. 파일에 쓰기 권한이 있어야 합니다. 파일의 내용은 제거됩니다. 이 플래그를 지정할 경우 `_O_RDONLY`를 지정할 수 없습니다.  |
| `_O_WRONLY`  | 파일을 쓰기 전용으로 엽니다. 이 플래그를 지정할 경우 `_O_RDONLY`와 `_O_RDWR`을 모두 지정할 수 없습니다.  |

## <a name="see-also"></a>참고 항목

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[전역 상수](../c-runtime-library/global-constants.md)
