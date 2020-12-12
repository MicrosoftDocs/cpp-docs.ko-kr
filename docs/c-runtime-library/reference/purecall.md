---
description: '다음에 대 한 자세한 정보: _purecall'
title: _purecall
ms.date: 4/2/2020
api_name:
- _purecall
- _o__purecall
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- purecall
- _purecall
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
ms.openlocfilehash: df52d7383685f3ce183562d8789b710fd7587acd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209453"
---
# <a name="_purecall"></a>_purecall

기본 순수 가상 함수 호출 오류 처리기입니다. 순수 가상 구성원 함수를 호출하면 컴파일러가 이 함수를 호출하는 코드를 생성합니다.

## <a name="syntax"></a>구문

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>설명

**_Purecall** 함수는 Microsoft c + + 컴파일러의 microsoft 관련 구현 세부 정보입니다. 이 함수는 코드에서 직접 호출할 수는 없으며 공용 헤더 선언을 포함하지 않습니다. 하지만 C 런타임 라이브러리의 공용 내보내기이므로 이 문서에 포함되어 있습니다.

순수 가상 함수에 대한 호출은 구현이 없으므로 오류입니다. 컴파일러는 순수 가상 함수를 호출할 때 **_purecall** 오류 처리기 함수를 호출 하는 코드를 생성 합니다. 기본적으로 **_purecall** 는 프로그램을 종료 합니다. 종료 하기 전에 **_purecall** 함수는 프로세스에 대해 설정 된 경우 **_purecall_handler** 함수를 호출 합니다. 순수 가상 함수 호출을 위해 고유한 오류 처리기 함수를 설치하여 디버깅 또는 보고용으로 이러한 호출을 catch할 수 있습니다. 사용자 고유의 오류 처리기를 사용 하려면 **_purecall_handler** 서명이 있는 함수를 만든 다음 [_set_purecall_handler](get-purecall-handler-set-purecall-handler.md) 를 사용 하 여 현재 처리기로 만듭니다.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

**_Purecall** 함수에 헤더 선언이 없습니다. **_Purecall_handler** typedef는에 정의 되어 \<stdlib.h> 있습니다.

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler, _set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
