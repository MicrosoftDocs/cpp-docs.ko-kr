---
description: '자세히 알아보기: _endthread, _endthreadex'
title: _endthread, _endthreadex
ms.date: 4/2/2020
api_name:
- _endthread
- _endthreadex
- _o__endthread
- _o__endthreadex
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _endthread
- endthreadex
- _endthreadex
- endthread
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
ms.openlocfilehash: ef74cac4cbe23a021ed8d796f92f2767695eb08e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332837"
---
# <a name="_endthread-_endthreadex"></a>_endthread, _endthreadex

스레드를 종료 합니다. **_endthread** **_beginthread** 에서 만든 스레드를 종료 하 고  **_endthreadex** **_beginthreadex** 에서 만든 스레드를 종료 합니다.

## <a name="syntax"></a>구문

```C
void _endthread( void );
void _endthreadex(
   unsigned retval
);
```

### <a name="parameters"></a>매개 변수

*retval*<br/>
스레드 종료 코드입니다.

## <a name="remarks"></a>설명

**_Endthread** 또는 **_endthreadex** 를 명시적으로 호출 하 여 스레드를 종료할 수 있습니다. 그러나 스레드가 **_beginthread** 또는 **_beginthreadex** 에 대 한 매개 변수로 전달 된 루틴에서 반환 되는 경우 **_endthread** 또는 **_endthreadex** 자동으로 호출 됩니다. **Endthread** 또는 **_endthreadex** 에 대 한 호출로 스레드를 종료 하면 스레드에 할당 된 리소스의 적절 한 복구를 보장 하는 데 도움이 됩니다.

> [!NOTE]
> Libcmt.lib로 연결된 실행 파일의 경우 런타임 시스템이 할당된 리소스를 회수하지 않도록 Win32 [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) API를 호출하지 마세요. 할당 된 스레드 리소스를 **_endthread** 및 **_endthreadex** 회수 한 다음 **exitthread** 를 호출 합니다.

**_endthread** 는 스레드 핸들을 자동으로 닫습니다. 이 동작은 Win32 **Exitthread** API와 다릅니다. 따라서 **_beginthread** 및 **_endthread** 를 사용 하는 경우 Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) API를 호출 하 여 스레드 핸들을 명시적으로 닫지 마세요.

Win32 **exitthread** API와 마찬가지로 **_endthreadex** 는 스레드 핸들을 닫지 않습니다. 따라서 **_beginthreadex** 및 **_endthreadex** 를 사용할 때는 Win32 **CloseHandle** API를 호출 하 여 스레드 핸들을 닫아야 합니다.

> [!NOTE]
> **_endthread** 및 **_endthreadex** 는 호출 되지 않은 스레드에서 c + + 소멸자가 보류 되도록 합니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|함수|필수 헤더|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

다중 스레드 버전의 유일한 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md) 입니다.

## <a name="example"></a>예제

[_beginthread](beginthread-beginthreadex.md)에 대한 예를 참조하세요.

## <a name="see-also"></a>참고 항목

[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
