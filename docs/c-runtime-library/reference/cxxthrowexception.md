---
description: '다음에 대 한 자세한 정보: _CxxThrowException'
title: _CxxThrowException
ms.date: 11/04/2016
api_name:
- _CxxThrowException
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CxxThrowException
- _CxxThrowException
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
ms.openlocfilehash: df4b1b30ba70ebf34bdb3cb4ae1c51a210f95a07
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327036"
---
# <a name="_cxxthrowexception"></a>_CxxThrowException

예외 레코드를 작성하고 런타임 환경을 호출하여 예외 처리를 시작합니다.

## <a name="syntax"></a>구문

```C
extern "C" void __stdcall _CxxThrowException(
   void* pExceptionObject
   _ThrowInfo* pThrowInfo
);
```

### <a name="parameters"></a>매개 변수

*pExceptionObject*<br/>
예외를 생성한 개체입니다.

*pThrowInfo*<br/>
예외를 처리하는 데 필요한 정보입니다.

## <a name="remarks"></a>설명

이 메서드는 컴파일러에서 예외를 처리하는 데 사용하는 컴파일러 전용 파일에 포함됩니다. 코드에서 직접 메서드를 호출하면 안 됩니다.

## <a name="requirements"></a>요구 사항

**소스:** Throw.cpp

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](crt-alphabetical-function-reference.md)<br/>
