---
description: '다음에 대 한 자세한 정보: _setjmp3'
title: _setjmp3
ms.date: 11/04/2016
api_name:
- _setjmp3
api_location:
- msvcrt.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setjmp3
- _setjmp3
helpviewer_keywords:
- _setjmp3 function
- setjmp3 function
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
ms.openlocfilehash: 07a84601a6f57eca3e7dc71638a964428579b1c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277065"
---
# <a name="_setjmp3"></a>_setjmp3

내부 CRT 함수입니다. `setjmp` 함수의 새로운 구현입니다.

## <a name="syntax"></a>구문

```
int _setjmp3(
   OUT jmp_buf env,
   int count,
   (optional parameters)
);
```

#### <a name="parameters"></a>매개 변수

*env*<br/>
[out] 상태 정보 저장을 위한 버퍼 주소입니다.

*count*<br/>
[in] `optional parameters`에 저장된 정보의 추가 `DWORD` 수입니다.

*선택적 매개 변수*<br/>
[in] `setjmp` 내장 함수가 적용한 추가 데이터입니다. 첫 번째 `DWORD`는 추가 데이터를 해제한 다음 비휘발성 등록 상태로 반환하는 데 사용되는 함수 포인터입니다. 두 번째 `DWORD`는 복원할 시도 수준입니다. 모든 추가 데이터는 `jmp_buf`의 제네릭 데이터 배열에 저장됩니다.

## <a name="return-value"></a>반환 값

항상 0을 반환합니다.

## <a name="remarks"></a>설명

이 함수는 C++ 프로그램에서는 사용하지 마세요. C++을 지원하지 않는 내장 함수입니다. `setjmp`를 사용하는 방법에 대한 자세한 내용은 [setjmp/longjmp 사용](../cpp/using-setjmp-longjmp.md)을 참조하세요.

## <a name="requirements"></a>요구 사항

## <a name="see-also"></a>참고 항목

[사전순 함수 참조](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[setjmp](../c-runtime-library/reference/setjmp.md)
