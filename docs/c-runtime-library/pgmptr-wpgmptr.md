---
description: '자세히 알아보기: _pgmptr, _wpgmptr'
title: _pgmptr, _wpgmptr
ms.date: 11/04/2016
f1_keywords:
- pgmptr
- _pgmptr
- wpgmptr
- _wpgmptr
helpviewer_keywords:
- wpgmptr function
- _wpgmptr function
- _pgmptr function
- pgmptr function
ms.assetid: 4d44b515-0eff-4136-8bc4-684195f218f5
ms.openlocfilehash: 70902be4f1c9686839a958439116fc3e28a2a315
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213444"
---
# <a name="_pgmptr-_wpgmptr"></a>_pgmptr, _wpgmptr

실행 파일의 경로입니다. 더 이상 사용되지 않습니다. [_get_pgmptr](../c-runtime-library/reference/get-pgmptr.md) 및 [_get_wpgmptr](../c-runtime-library/reference/get-wpgmptr.md)을 사용하세요.

## <a name="syntax"></a>구문

```
extern char *_pgmptr;
extern wchar_t *_wpgmptr;
```

## <a name="remarks"></a>설명

프로그램이 명령 인터프리터(Cmd.exe)에서 실행될 때 `_pgmptr`은 자동으로 실행 파일의 전체 경로로 초기화됩니다. 예를 들어 Hello.exe가 C:\BIN에 있고 C:\BIN이 경로에 있는 경우 다음을 실행하면 `_pgmptr`이 C:\BIN\Hello.exe로 설정됩니다.

```
C> hello
```

프로그램이 명령줄에서 실행되지 않을 때 `_pgmptr`은 프로그램 이름(파일 확장자를 제외한 파일의 기본 이름) 또는 파일 이름, 상대 경로 또는 전체 경로로 초기화될 수 있습니다.

`_wpgmptr`은 `_pgmptr`을 사용하는 프로그램에 사용할 `wmain`에 대응하는 와이드 문자입니다.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|

## <a name="requirements"></a>요구 사항

|변수|필수 헤더|
|--------------|---------------------|
|`_pgmptr`, `_wpgmptr`|\<stdlib.h>|

## <a name="example"></a>예제

다음 프로그램에서는 `_pgmptr`의 사용을 보여 줍니다.

```c
// crt_pgmptr.c
// compile with: /W3
// The following program demonstrates the use of _pgmptr.
//
#include <stdio.h>
#include <stdlib.h>
int main( void )
{
   printf("The full path of the executing program is : %Fs\n",
     _pgmptr); // C4996
   // Note: _pgmptr is deprecated; use _get_pgmptr instead
}
```

`_wpgmptr`를 `%Fs`로 변경하고 `%S`을 `main`으로 변경하여 `wmain`을 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[전역 변수](../c-runtime-library/global-variables.md)
