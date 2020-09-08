---
title: setjmp
description: Setjmp에 대 한 API 참조 프로그램의 현재 상태를 저장 합니다.
ms.date: 08/14/2018
api_name:
- setjmp
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setjmp
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
ms.openlocfilehash: 3ea08e5379433e313e08870f735322b7d985aa64
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555607"
---
# <a name="setjmp"></a>setjmp

프로그램의 현재 상태를 저장합니다.

## <a name="syntax"></a>구문

```C
int setjmp(
   jmp_buf env
);
```

### <a name="parameters"></a>매개 변수

*env*<br/>
환경이 저장되는 변수입니다.

## <a name="return-value"></a>반환 값

스택 환경에 저장한 후 0을 반환합니다. **Setjmp** 가 호출의 결과로 반환 되는 경우 `longjmp` 의 *value* 인수를 반환 `longjmp` 하거나의 *값* 인수가 0 이면 `longjmp` **setjmp** 는 1을 반환 합니다. 오류가 반환 되지 않습니다.

## <a name="remarks"></a>설명

**Setjmp** 함수는를 사용 하 여 나중에 복원할 수 있는 스택 환경을 저장 합니다 `longjmp` . 함께 사용 하는 경우 **setjmp** 를 사용 하 고 `longjmp` 로컬이 아닌를 실행 하는 방법을 제공 **`goto`** 합니다. setjmp와 longjmp는 일반 호출이나 반환 규칙을 사용하지 않고 전에 호출된 루틴에서 오류 처리 또는 복구 코드에 실행 제어를 전달하는 데 주로 사용됩니다.

**Setjmp** 에 대 한 호출은 현재 스택 환경을 *env*에 저장 합니다. 에 대 한 후속 호출은 `longjmp` 저장 된 환경을 복원 하 고 컨트롤을 해당 **setjmp** 호출 바로 다음의 지점으로 반환 합니다. 컨트롤을 받는 루틴에 액세스할 수 있는 모든 변수(레지스터 변수 제외)는 `longjmp`가 호출될 때 가지고 있던 값을 포함합니다.

**Setjmp** 를 사용 하 여 네이티브 코드에서 관리 코드로 이동할 수는 없습니다.

**Microsoft 전용**

Windows의 Microsoft c + + 코드 **에서, 명령줄** 은 예외 처리 코드와 동일한 스택 해제 의미 체계를 사용 합니다. C + + 예외를 발생 시킬 수 있는 것과 동일한 위치에서를 사용 하는 것이 안전 합니다. 그러나이 사용은 이식할 수 없으며 몇 가지 중요 한 주의 사항이 있습니다. 자세한 내용은 다음을 [참조 하세요](longjmp.md).

**Microsoft 전용 종료**

> [!NOTE]
> 이식 가능한 c + + 코드에서는 `setjmp` `longjmp` c + + 개체 의미 체계를 가정 하 고 지원할 수 없습니다. 특히 및를 `setjmp` / `longjmp` `setjmp` 통해 및를 대체 `longjmp` **`catch`** 하 여 **`throw`** 자동 개체에 대 한 특수 한 소멸자를 호출 하는 경우 호출 쌍은 정의 되지 않은 동작을 가집니다. C + + 프로그램에서는 c + + 예외 처리 메커니즘을 사용 하는 것이 좋습니다.

자세한 내용은 [setjmp 및 longjmp 사용](../../cpp/using-setjmp-longjmp.md)을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

[_fpreset](fpreset.md)에 대한 예제를 참조하세요.

## <a name="see-also"></a>참고 항목

[프로세스 및 환경 제어](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)
