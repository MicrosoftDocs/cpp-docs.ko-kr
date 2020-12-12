---
description: '자세한 정보: 디스크에 커밋 상수'
title: 디스크에 커밋 상수
ms.date: 11/04/2016
f1_keywords:
- vc.constants
helpviewer_keywords:
- commit-to-disk constants
ms.assetid: 0b903b23-b4fa-431e-a937-51d95f695ecf
ms.openlocfilehash: 416729f4b3b7bfdfdcb0ba11193f6c2a52691e6e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322648"
---
# <a name="commit-to-disk-constants"></a>디스크에 커밋 상수

**Microsoft 전용**

## <a name="syntax"></a>구문

```
#include <stdio.h>
```

## <a name="remarks"></a>설명

이러한 Microsoft 전용 상수는 열려 있는 파일과 연결된 버퍼가 운영 체제 버퍼 또는 디스크에 플러시되는지 여부를 지정합니다. 모드는 읽기/쓰기 액세스 형식을 지정하는 문자열에 포함됩니다(**"r"**, **"w"**, **"a"**, **"r+"**, **"w+"**, **"a+"**).

디스크에 커밋 모드는 다음과 같습니다.

- **c**

   지정된 버퍼의 기록되지 않은 내용을 디스크에 씁니다. 이 디스크에 커밋 기능은 [fflush](../c-runtime-library/reference/fflush.md) 또는 [_flushall](../c-runtime-library/reference/flushall.md) 함수를 명시적으로 호출할 때에만 발생합니다. 이 모드는 중요한 데이터를 처리할 때 유용합니다. 예를 들어 프로그램이 `fflush` 또는 `_flushall`을 호출한 후에 종료되는 경우 데이터가 운영 체제의 버퍼에 도달했음을 확인할 수 있습니다. 그러나 **c** 옵션을 사용하여 파일이 열리지 않고 운영 체제도 종료되는 경우 데이터가 디스크에 쓰이지 않을 수 있습니다.

- **n**

   지정된 버퍼의 기록되지 않은 내용을 운영 체제의 버퍼에 씁니다. 운영 체제는 데이터를 캐시한 후 디스크에 쓸 수 있는 최적의 시간을 결정합니다. 이 동작이 효율적인 프로그램 동작을 만드는 경우가 많습니다. 그러나 데이터의 보존이 중요한 경우(예: 은행 거래 또는 항공권 정보) **c** 옵션을 사용하는 것이 좋습니다. **n** 모드는 기본값입니다.

> [!NOTE]
> **c** 및 **n** 옵션은 `fopen`에 대한 ANSI 표준에 포함되어 있지 않지만 Microsoft 확장이며 ANSI 이식성이 필요한 곳에 사용될 수 없습니다.

## <a name="using-the-commit-to-disk-feature-with-existing-code"></a>기존 코드와 함께 디스크에 커밋 기능 사용

기본적으로 [fflush](../c-runtime-library/reference/fflush.md) 또는 [_flushall](../c-runtime-library/reference/flushall.md) 라이브러리 함수를 호출하면 운영 체제에 의해 유지 관리되는 버퍼에 데이터가 쓰여집니다. 운영 체제는 실제로 디스크에 데이터를 쓸 수 있는 최적의 시간을 결정합니다. 런타임 라이브러리의 디스크에 커밋 기능을 사용하면 중요한 데이터가 운영 체제의 버퍼 대신 디스크에 직접 쓰여져 있는지 확인할 수 있습니다. 개체 파일을 COMMODE.OBJ에 연결하여 다시 쓰지 않고 기존 프로그램에 이 기능을 제공할 수 있습니다.

결과 실행 파일에서 `fflush`를 호출하면 버퍼의 내용이 디스크에 직접 쓰여지고 `_flushall`을 호출하면 모든 버퍼의 내용이 디스크에 쓰여집니다. 이러한 두 기능만 COMMODE.OBJ의 영향을 받습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[스트림 I/O](../c-runtime-library/stream-i-o.md)<br/>
[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[전역 상수](../c-runtime-library/global-constants.md)
