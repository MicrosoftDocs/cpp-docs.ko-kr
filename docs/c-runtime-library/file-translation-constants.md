---
description: '자세히 알아보기: 파일 변환 상수'
title: 파일 변환 상수
ms.date: 11/04/2016
helpviewer_keywords:
- translation constants
- file translation [C++], constants
- translation, file translation constants
- translation, constants
- constants [C++], file translation mode
- file translation [C++]
ms.assetid: 49b13bf3-442e-4d19-878b-bd1029fa666a
ms.openlocfilehash: 75bb54c7e038efd41ed22ec941d871f6fbc54b7c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332991"
---
# <a name="file-translation-constants"></a>파일 변환 상수

## <a name="syntax"></a>구문

```
#include <stdio.h>
```

## <a name="remarks"></a>설명

이러한 상수는 변환 모드(**"b"** 또는 **"t"**)를 지정합니다. 이 모드는 액세스 형식(**"r"**, **"w"**, **"a"**, **"r+"**, **"w+"**, **"a+"**)을 지정하는 문자열에 포함됩니다.

변환 모드는 다음과 같습니다.

- **t**

   텍스트(변환됨) 모드에서 엽니다. 이 모드에서는 CR-LF(캐리지 리턴 줄 바꿈) 조합은 입력 시 단일 LF(줄 바꿈)로 변환되고, LF 문자는 출력 시 CR-LF 조합으로 변환됩니다. 또한 CTRL+Z는 입력 시 파일 끝 문자로 변환됩니다. 읽기용으로나 읽기 및 쓰기용으로 열려 있는 파일에서 `fopen`은 파일 끝에 CTRL+Z가 있는지 확인하고 가능한 경우 이를 제거합니다. 이렇게 처리되는 이유는 `fseek` 및 `ftell` 함수를 사용하여 CTRL+Z로 끝나는 파일 내에서 이동하면 `fseek`가 파일 끝 부분에서 제대로 동작하지 않을 수 있기 때문입니다.

   > [!NOTE]
   > **t** 옵션은 `fopen` 및 `freopen`에 대한 ANSI 표준에 속하지 않습니다. 이 옵션은 Microsoft 확장으로, ANSI 포팅 기능을 원할 경우 사용하면 안 됩니다.

- **b**

   이진(변환되지 않음) 모드에서 엽니다. 위 변환은 표시되지 않습니다.

*mode* 에 **t** 또는 **b** 가 지정되지 않은 경우 변환 모드는 기본 모드 변수 [_fmode](../c-runtime-library/fmode.md)로 정의됩니다. 텍스트 모드와 이진 모드 사용에 대한 자세한 내용은 [텍스트 및 이진 모드 파일 I/O](../c-runtime-library/text-and-binary-mode-file-i-o.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[전역 상수](../c-runtime-library/global-constants.md)
