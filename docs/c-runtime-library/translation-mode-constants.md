---
description: '다음에 대 한 자세한 정보: 변환 모드 상수'
title: 변환 모드 상수
ms.date: 11/04/2016
f1_keywords:
- _O_BINARY
- _O_TEXT
- _O_RAW
helpviewer_keywords:
- O_BINARY constant
- O_TEXT constant
- O_RAW constant
- _O_TEXT constant
- _O_RAW constant
- translation constants
- _O_BINARY constant
- translation, constants
- translation, modes
- translation modes (file I/O)
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
ms.openlocfilehash: 4be3b24344a61d4aa8d5ea76ab623ee275afb399
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162325"
---
# <a name="translation-mode-constants"></a>변환 모드 상수

## <a name="syntax"></a>구문

```
#include <fcntl.h>
```

## <a name="remarks"></a>설명

`_O_BINARY` 및 `_O_TEXT` 매니페스트 상수는 파일(`_open` 및 `_sopen`)에 대한 변환 모드 또는 스트림(`_setmode`)에 대한 변환 모드를 결정합니다.

허용되는 값은 다음과 같습니다.

|값|설명|
|-|-|
`_O_TEXT`  | 파일을 텍스트(변환됨) 모드에서 엽니다. 캐리지 리턴-줄 바꿈(CR-LF) 조합은 입력 시 단일 줄 바꿈(LF)으로 변환됩니다. 줄 바꿈 문자는 출력 시 CR-LF 조합으로 변환됩니다. 또한 CTRL+Z는 입력 시 파일 끝 문자로 변환됩니다. 읽기용 및 읽기/쓰기용으로 열려 있는 파일에서 `fopen`은 파일 끝에 CTRL+Z가 있는지 확인하고 가능한 경우 이를 제거합니다. 이렇게 처리되는 이유는 `fseek` 및 `ftell` 함수를 사용하여 CTRL+Z로 끝나는 파일 내에서 이동하면 `fseek`가 파일 끝 부분에서 제대로 동작하지 않을 수 있기 때문입니다.
`_O_BINARY`  | 파일을 이진(변환되지 않음) 모드에서 엽니다. 위 변환은 표시되지 않습니다.
`_O_RAW`  | `_O_BINARY`와 동일합니다. C 2.0 호환성을 지원합니다.

자세한 내용은 [텍스트 및 이진 모드 파일 I/O](../c-runtime-library/text-and-binary-mode-file-i-o.md) 및 [파일 변환](../c-runtime-library/file-translation-constants.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_pipe](../c-runtime-library/reference/pipe.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_setmode](../c-runtime-library/reference/setmode.md)<br/>
[전역 상수](../c-runtime-library/global-constants.md)
