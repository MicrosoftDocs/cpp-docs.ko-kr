---
description: '다음에 대 한 자세한 정보: __fastfail'
title: __fastfail
ms.date: 09/02/2019
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
ms.openlocfilehash: c7521f10dee7602fae3de5b2ac6fcc0245214bec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336990"
---
# <a name="__fastfail"></a>__fastfail

**Microsoft 전용**

최소한의 오버헤드로 호출 프로세스를 즉시 종료합니다.

## <a name="syntax"></a>구문

```C
void __fastfail(unsigned int code);
```

### <a name="parameters"></a>매개 변수

*code*\
진행 `FAST_FAIL_<description>` 프로세스 종료 이유를 나타내는 winnt.exe 또는 wdm의 기호화 된 상수입니다.

## <a name="return-value"></a>반환 값

`__fastfail` 내장 함수는 결과를 반환하지 않습니다.

## <a name="remarks"></a>설명

`__fastfail`내장 함수는 *빠른 실패* 요청에 대 한 메커니즘을 제공 합니다 .이 메커니즘은 잠재적으로 손상 된 프로세스에서 즉시 프로세스 종료를 요청 하는 방법입니다. 프로그램 상태와 스택을 복구할 수 없을 정도로 손상시켰을 수 있는 심각한 오류는 일반적인 예외 처리 기능을 통해 처리할 수 없습니다. 최소한의 오버헤드로 프로세스를 종료하려면 `__fastfail`을 사용합니다.

내부적으로 `__fastfail`은 다양한 아키텍처별 메커니즘을 사용하여 구현됩니다.

|Architecture|명령|코드 인수의 위치|
|------------------|-----------------|-------------------------------|
|x86|int 0x29|`ecx`|
|X64|int 0x29|`rcx`|
|ARM|Opcode 0xDEFB|`r0`|
|ARM64|Opcode 0xF003|`x0`|

빠른 실패 요청은 독립적이며 대개 두 가지 명령만 있으면 실행할 수 있습니다. 빠른 실패 요청이 실행 된 후에는 커널에서 적절 한 작업을 수행 합니다. 사용자 모드 코드에서는 빠른 실패 이벤트 발생 시 명령 포인터 자체 이외의 메모리 종속성이 없습니다. 이를 통해 심각한 메모리 손상이 발생 하는 경우에도 안정성이 극대화 됩니다.

`code` `FAST_FAIL_<description>` Winnt.sif 또는 wdm의 기호화 된 상수 중 하나인 인수는 실패 조건의 유형을 설명 합니다. 환경 관련 방식으로 오류 보고서에 통합 됩니다.

사용자 모드 빠른 실패 요청은 예외 코드 0xC0000409 및 하나 이상의 예외 매개 변수를 포함 하는 두 번째 비연속적 이외의 예외로 표시 됩니다. 첫 번째 예외 매개 변수는 `code` 값입니다. 이 예외 코드는 프로세스가 손상 되었음을 Windows 오류 보고 (WER) 및 디버깅 인프라를 나타내며, 실패에 대 한 응답으로 최소한의 in-process 작업을 수행 해야 한다는 것을 나타냅니다. 커널 모드 빠른 실패 요청은 전용 버그 검사 코드인 `KERNEL_SECURITY_CHECK_FAILURE`(0x139)를 사용하여 구현됩니다. 두 경우 모두 프로그램이 손상된 상태로 간주되므로 예외 처리기가 호출되지 않습니다. 디버거가 있는 경우 종료 하기 전에 프로그램 상태를 검사할 수 있는 기회가 제공 됩니다.

Windows 8부터는 빠른 실패 메커니즘이 기본적으로 지원됩니다. 빠른 실패 명령을 기본적으로 지원 하지 않는 Windows 운영 체제는 일반적으로 빠른 실패 요청을 액세스 위반으로 처리 하거나 오류를 확인 `UNEXPECTED_KERNEL_MODE_TRAP` 합니다. 이러한 경우에도 프로그램은 종료되지만 종료 속도는 느려질 수 있습니다.

`__fastfail`은 내장 함수로만 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__fastfail`|x86, x64, ARM, ARM64|

**헤더 파일** \<intrin.h>

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
