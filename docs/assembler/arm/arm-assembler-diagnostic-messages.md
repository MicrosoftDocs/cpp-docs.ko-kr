---
description: '자세한 정보: ARM 어셈블러 진단 메시지'
title: ARM 어셈블러 진단 메시지
ms.date: 08/30/2018
f1_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
helpviewer_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
ms.openlocfilehash: 91e4640c161cbb58522c3680ae5decdb4cc1e992
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118201"
---
# <a name="arm-assembler-diagnostic-messages"></a>ARM 어셈블러 진단 메시지

Microsoft ARM 어셈블러 (*armasm*)는 발견 될 때 진단 경고 및 오류를 내보냅니다. 이 문서에서는 가장 일반적으로 발생 하는 메시지에 대해 설명 합니다.

## <a name="syntax"></a>Syntax

> <em>파일 이름</em>**(**<em>줄 번호</em>**):** \[ **오류** | **경고**] <em>번호</em>**:** *메시지*

## <a name="diagnostic-messages---errors"></a>진단 메시지-오류

> A2193:이 명령은 예측할 수 없는 동작을 생성 합니다.

ARM 아키텍처는이 명령이 실행 될 때 어떤 일이 발생 하는지 보장할 수 없습니다.  이 명령의 잘 정의 된 폼에 대 한 자세한 내용은 [ARM 아키텍처 참조 설명서](https://go.microsoft.com/fwlink/p/?linkid=246464)를 참조 하세요.

```asm
    ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior
```

> A2196: 명령을 16 비트로 인코딩할 수 없습니다.

지정 된 명령을 16 비트 Thumb 명령으로 인코딩할 수 없는 경우  32 비트 명령을 지정 하거나 코드를 다시 정렬 하 여 대상 레이블을 16 비트 명령의 범위로 가져옵니다.

32 비트 분기가 encodable 경우에도 어셈블러는 16 비트 분기를 인코딩할 수 있으며이 오류로 인해 실패 합니다. 지정자를 사용 하 여 `.W` 분기를 32 비트로 명시적으로 표시 하면이 문제를 해결할 수 있습니다.

```asm
    ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits

    B.W label             ; OK
    B.N label             ; A2196: instruction cannot be encoded in 16 bits
    SPACE 10000
label
```

> A2202: THUMB 영역에는 UAL 이전 명령 구문을 사용할 수 없습니다.

Thumb 코드는 UAL (통합 어셈블러 언어) 구문을 사용 해야 합니다.  이전 구문이 더 이상 허용 되지 않습니다.

```asm
    ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region
    ADDSEQ r0, r1         ; OK
```

> A2513: 회전 짝수 여야 합니다.

ARM 모드에는 상수를 지정 하는 대체 구문이 있습니다.  을 작성 하는 대신 `#<const>` `#<byte>,#<rot>` 값을으로 회전 하 여 얻은 상수 값을 나타내는을 작성할 수 있습니다 `<byte>` `<rot>` .  이 구문을 사용 하는 경우 값도로 설정 해야 합니다 `<rot>` .

```asm
    MOV r0, #4, #2       ; OK
    MOV r0, #4, #1       ; A2513: Rotation must be even
```

> A2557: 다시 쓸 바이트 수가 잘못 되었습니다.

NEON 구조 로드 및 저장 지침 ( `VLDn` ,)에는 `VSTn` 기본 레지스터에 쓰기 저장 (writeback)을 지정 하는 대체 구문이 있습니다.  주소 뒤에 느낌표 (!)를 배치 하는 대신 기본 레지스터에 추가할 오프셋을 나타내는 값을 직접 지정할 수 있습니다.  이 구문을 사용 하는 경우 명령에 의해 로드 되거나 저장 된 정확한 바이트 수를 지정 해야 합니다.

```asm
    VLD1.8 {d0-d3}, [r0]!         ; OK
    VLD1.8 {d0-d3}, [r0], #32     ; OK
    VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back
```

## <a name="diagnostic-messages---warnings"></a>진단 메시지-경고

> A4228: 맞춤 값이 영역 맞춤을 초과 합니다. 맞춤이 보장 되지 않음

지시문에 지정 된 맞춤이 `ALIGN` 바깥쪽의 맞춤 보다 큽니다 `AREA` .  따라서 어셈블러는 지시문이 적용 되도록 보장할 수 없습니다 `ALIGN` .

이 문제를 해결 하려면 `AREA` 지시문에서 `ALIGN` 원하는 맞춤 보다 크거나 같은 특성을 지정 하면 됩니다.

```asm
AREA |.myarea1|
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed

AREA |.myarea2|,ALIGN=3
ALIGN 8           ; OK
```

> A4508:이 회전 된 상수는 사용 되지 않습니다.

ARM 모드에는 상수를 지정 하는 대체 구문이 있습니다.  을 작성 하는 대신 `#<const>` `#<byte>,#<rot>` 값을으로 회전 하 여 얻은 상수 값을 나타내는을 작성할 수 있습니다 `<byte>` `<rot>` .  일부 컨텍스트에서 ARM은 이러한 회전 된 상수를 사용 하는 것을 더 이상 사용 하지 않습니다. 이러한 경우에는 기본 `#<const>` 구문을 대신 사용 합니다.

```asm
    ANDS r0, r0, #1                ; OK
    ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated
```

> A4509:이 형식의 조건부 명령은 더 이상 사용 되지 않습니다.

이 형식의 조건부 명령은 ARM이 ARMv8 아키텍처에서 더 이상 사용 되지 않습니다. 조건부 분기를 사용 하도록 코드를 변경 하는 것이 좋습니다. 계속 지원 되는 조건부 지침은 [ARM 아키텍처 참조 설명서](https://go.microsoft.com/fwlink/p/?linkid=246464)를 참조 하세요.

**-Oldit** 명령줄 스위치를 사용 하는 경우이 경고를 내보내지 않습니다.

```asm
    ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated
```

## <a name="see-also"></a>참고 항목

[ARM 어셈블러 Command-Line 참조](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[ARM 어셈블러 지시문](../../assembler/arm/arm-assembler-directives.md)<br/>
