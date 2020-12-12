---
description: '다음에 대 한 자세한 정보: ARM 어셈블러 지시문'
title: ARM 어셈블리 지시문
ms.date: 08/30/2018
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
ms.openlocfilehash: 8362453f2113922c5e834d1d68583b4199cf8d4c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118120"
---
# <a name="arm-assembler-directives"></a>ARM 어셈블리 지시문

대부분의 경우 Microsoft ARM 어셈블러는 arm [컴파일러 Armasm 참조 가이드](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html)에 설명 되어 있는 arm 어셈블리 언어를 사용 합니다. 그러나 일부 어셈블리 지시문의 Microsoft 구현은 ARM 어셈블리 지시문과 다릅니다. 이 문서에서는 차이점을 설명 합니다.

## <a name="microsoft-implementations-of-arm-assembly-directives"></a>ARM 어셈블리 지시문의 Microsoft 구현

- 면적

   Microsoft ARM 어셈블러는,,,,,,,, 등의 `AREA` 특성 `ALIGN` 을 지원 `CODE` `CODEALIGN` `DATA` `NOINIT` `READONLY` `READWRITE` 합니다 `THUMB` . `ARM`

   `THUMB`및를 제외한 모든 `ARM` 는 [ARM 컴파일러 armasm 참조 가이드](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html)에 설명 된 대로 작동 합니다.

   Microsoft ARM 어셈블러에서 섹션에 `THUMB` `CODE` Thumb 코드가 포함 되어 있으며 섹션에 대 한 기본값 임을 나타냅니다 `CODE` .  `ARM` 섹션이 ARM 코드를 포함 함을 나타냅니다.

- ATTR

   지원 안 됨

- CODE16

   Microsoft ARM 어셈블러에서 허용 하지 않는 이전 UAL 엄지 구문을 암시 하기 때문에 지원 되지 않습니다.  `THUMB`UAL 구문과 함께 지시문을 대신 사용 합니다.

- 일반적인

   공통 영역에 대 한 맞춤 사양은 지원 되지 않습니다.

- DCDO

   지원 안 됨

- `DN`, `QN`, `SN`

   레지스터 별칭의 유형 또는 레인 사양은 지원 되지 않습니다.

- ENTRY

   지원 안 됨

- EQU

   정의 된 기호에 대 한 형식 지정은 지원 되지 않습니다.

- `EXPORT` 및 `GLOBAL`

   다음 구문을 사용 하 여 내보내기를 지정 합니다.

   > **내보내기** | **GLOBAL** <em>기호</em>{**[**<em>type</em>**]**}

   *기호* 는 내보낼 기호입니다.  [*type*] (지정 된 경우)은 `[DATA]` 기호가 데이터를 가리키기를 나타내거나 기호가 코드를 가리키도록 지정 하는 데 사용할 수 있습니다 `[FUNC]` . `GLOBAL` 와 `EXPORT`는 동의어입니다.

- EXPORTAS

   지원 안 됨

- 프레임씩

   지원 안 됨

- `FUNCTION` 및 `PROC`

   어셈블리 구문은 호출자가 저장 하는 레지스터와 호출 수신자를 저장 하는 레지스터를 나열 하 여 프로시저에 대 한 사용자 지정 호출 규칙의 사양을 지원 하지만, Microsoft ARM 어셈블러는 구문을 허용 하지만 레지스터 목록을 무시 합니다.  어셈블러에서 생성 되는 디버그 정보는 기본 호출 규칙만 지원 합니다.

- `IMPORT` 및 `EXTERN`

   다음 구문을 사용 하 여 가져오기를 지정 합니다.

   > **가져오기** | **EXTERN** *기호*{**, WEAK** *alias*{**, TYPE** *t*}}

   *기호* 은 가져올 기호의 이름입니다.

   `WEAK` *Alias* 를 지정 하면 *기호* 가 약한 외부 임을 나타냅니다. 링크 타임에이에 대 한 정의를 찾을 수 없는 경우이에 대 한 모든 참조는 *별칭* 대신 바인딩됩니다.

   `TYPE` *T* 를 지정 하는 경우  링커가 *기호* 확인을 시도 하는 방법을 나타냅니다.  *T* 에 대해 다음과 같은 값을 사용할 수 있습니다.

   |값|설명|
   |-|-|
   |1|*기호* 에 대 한 라이브러리 검색을 수행 하지 않습니다.|
   |2|*기호* 에 대 한 라이브러리 검색 수행|
   |3|*기호* 는 *별칭* (기본값)의 별칭입니다.|

   `EXTERN` 는 `IMPORT` 현재 어셈블리에 대 한 참조가 있는 경우에만 *기호* 를 가져오도록 제외 하면의 동의어입니다.

- MACRO

   매크로의 조건 코드를 저장 하는 변수를 사용 하는 것은 지원 되지 않습니다. 매크로 매개 변수의 기본값은 지원 되지 않습니다.

- NOFP

   지원 안 됨

- `OPT`, `TTL`, `SUBT`

   Microsoft ARM 어셈블러에서 목록을 생성 하지 않으므로 지원 되지 않습니다.

- PRESERVE8

   지원 안 됨

- .RELOC

   `RELOC n` 는 명령 또는 데이터 정의 지시문만 따를 수 있습니다. 재배치할 수 있는 "익명 기호"가 없습니다.

- 필요

   지원 안 됨

- REQUIRE8

   지원 안 됨

- THUMBX

   Microsoft ARM 어셈블러는 Thumb-2EE 명령 집합을 지원 하지 않으므로 지원 되지 않습니다.

## <a name="see-also"></a>참고 항목

[ARM 어셈블러 Command-Line 참조](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[ARM 어셈블러 진단 메시지](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
