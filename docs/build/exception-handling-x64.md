---
title: x64 예외 처리
description: x64 관련 Microsoft C++ 예외 처리 규칙 개요입니다.
ms.date: 10/14/2019
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: 1c55ecf8755e208b2f47acdfda185123ee0255e2
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898564"
---
# <a name="x64-exception-handling"></a>x64 예외 처리

x64에서 구조화된 예외 처리 및 C++ 예외 처리 코딩 규칙 및 동작에 대한 개요입니다. 예외 처리에 대한 일반 정보는 [Visual C++에서 예외 처리](../cpp/exception-handling-in-visual-cpp.md)를 참조하세요.

## <a name="unwind-data-for-exception-handling-debugger-support"></a>디버거 지원, 예외 처리를 위한 해제 데이터

예외 처리 및 디버깅 지원에는 몇 가지 데이터 구조가 필요합니다.

### <a name="struct-runtime_function"></a>구조체 RUNTIME_FUNCTION

테이블 기반 예외 처리에는 스택 공간을 할당하거나 다른 함수(예: 리프가 아닌 함수)를 호출하는 모든 함수에 대한 테이블 항목이 필요합니다. 함수 테이블 항목의 형식은 다음과 같습니다.

|Size|값|
|-|-|
|ULONG|함수 시작 주소|
|ULONG|함수 끝 주소|
|ULONG|해제 정보 주소|

RUNTIME_FUNCTION 구조체는 메모리에서 DWORD로 정렬되어야 합니다. 모든 주소는 이미지를 기준으로 합니다. 즉, 함수 테이블 항목을 포함하는 이미지의 시작 주소에서 32비트 오프셋입니다. 관련 항목은 정렬되어 PE32+ 이미지의 .pdata 섹션에 배치됩니다. 동적으로 생성된 함수 [JIT 컴파일러]의 경우 관련 함수를 지원하는 런타임에서는 RtlInstallFunctionTableCallback 또는 RtlAddFunctionTable을 사용하여 이 정보를 운영 체제에 제공해야 합니다. 이렇게 하지 않으면 프로세스의 예외 처리 및 디버깅이 불안정해질 수 있습니다.

### <a name="struct-unwind_info"></a>구조체 UNWIND_INFO

해제 데이터 정보 구조체는 함수에서 스택 포인터에 대한 효과를 기록하는 데 사용되며, 비휘발성 레지스터가 스택에 저장됩니다.

|Size|값|
|-|-|
|UBYTE: 3|버전|
|UBYTE: 5|플래그|
|UBYTE|프롤로그 크기|
|UBYTE|해제 코드 개수|
|UBYTE: 4|프레임 레지스터|
|UBYTE: 4|프레임 레지스터 오프셋(비율 크기 조정됨)|
|USHORT \* n|해제 코드 배열|
|변수|다음 형식 (1) 또는 (2) 중 하나를 사용할 수 있음|

(1) 예외 처리기

|Size|값|
|-|-|
|ULONG|예외 처리기의 주소|
|변수|언어별 처리기 데이터(선택 사항)|

(2) 연결된 해제 정보

|Size|값|
|-|-|
|ULONG|함수 시작 주소|
|ULONG|함수 끝 주소|
|ULONG|해제 정보 주소|

UNWIND_INFO 구조체는 메모리에서 DWORD로 정렬되어야 합니다. 각 필드의 의미는 다음과 같습니다.

- **Version**

   해제 데이터의 버전 번호(현재 1)입니다.

- **플래그**

   현재 세 개의 플래그가 정의되어 있습니다.

   |플래그|설명|
   |-|-|
   |`UNW_FLAG_EHANDLER`| 함수에는 예외를 검사해야 하는 함수를 찾을 때 호출해야 하는 예외 처리기가 있습니다.|
   |`UNW_FLAG_UHANDLER`| 함수에는 예외를 해제할 때 호출해야 하는 종료 처리기가 있습니다.|
   |`UNW_FLAG_CHAININFO`| 이 해제 정보 구조체는 프로시저에 대한 기본 구조가 아닙니다. 대신, 연결된 해제 정보 항목은 RUNTIME_FUNCTION 이전 항목의 콘텐츠입니다. 자세한 내용은 [연결된 해제 정보 구조체](#chained-unwind-info-structures)를 참조하세요. 이 플래그가 설정되면 UNW_FLAG_EHANDLER 및 UNW_FLAG_UHANDLER 플래그 선택을 취소해야 합니다. 또한 프레임 레지스터 및 고정 스택 할당 필드의 값은 기본 해제 정보의 값과 같아야 합니다.|

- **프롤로그 크기**

   함수 프롤로그의 길이(바이트)입니다.

- **해제 코드 개수**

   해제 코드 배열의 슬롯 수입니다. UWOP_SAVE_NONVOL과 같은 일부 해제 코드에는 배열에 두 개 이상의 슬롯이 필요합니다.

- **프레임 레지스터**

   0이 아닌 경우 함수는 FP(프레임 포인터)를 사용합니다. 이 필드는 프레임 포인터로 사용되는 비휘발성 레지스터의 번호로서 UNWIND_CODE 노드의 작업 정보 필드에 대해 동일한 인코딩을 사용합니다.

- **프레임 레지스터 오프셋(비율 크기 조정됨)**

   프레임 레지스터 필드가 0이 아닌 경우 이 필드는 설정 시 FP 레지스터에 적용되는 RSP의 비율 크기가 조정된 오프셋입니다. 실제 FP 레지스터는 RSP + 16 \* 이 숫자로 설정되며, 0에서 240까지의 오프셋을 허용합니다. 이 오프셋을 사용하면 동적 스택 프레임에 대한 로컬 스택 할당 중간에 FP 레지스터를 가리킬 수 있어서 더 짧은 명령으로 코드 밀도를 향상할 수 있습니다. (즉, 더 많은 명령이 부호 있는 8비트 오프셋 형식을 사용할 수 있음)

- **해제 코드 배열**

   비휘발성 레지스터 및 RSP에서 프롤로그의 효과를 설명하는 항목의 배열입니다. 개별 항목의 의미는 UNWIND_CODE에 대한 섹션을 참조하세요. 정렬 목적인 경우 이 배열에는 항상 짝수 개의 항목이 있으며 최종 항목은 사용되지 않을 가능성이 있습니다. 이 경우 배열은 해제 코드 필드 수에 지정된 것보다 더 깁니다.

- **예외 처리기의 주소**

   UNW_FLAG_CHAININFO 플래그가 명확하고 UNW_FLAG_EHANDLER 또는 UNW_FLAG_UHANDLER 플래그 중 하나를 설정하는 경우 함수의 언어별 예외 또는 종료 처리기에 대한 이미지 기준 포인터입니다.

- **언어별 처리기 데이터**

   함수의 언어별 예외 처리기 데이터입니다. 이 데이터의 형식은 지정되지 않고 사용 중인 특정 예외 처리기에 의해 전적으로 결정됩니다.

- **연결된 해제 정보**

   UNW_FLAG_CHAININFO 플래그가 설정된 경우 UNWIND_INFO 구조체는 세 개의 UWORD로 끝납니다.  UWORD는 연결된 해제의 함수에 대한 RUNTIME_FUNCTION 정보를 나타냅니다.

### <a name="struct-unwind_code"></a>구조체 UNWIND_CODE

해제 코드 배열은 비휘발성 레지스터 및 RSP에 영향을 주는 프롤로그의 작업 시퀀스를 기록하는 데 사용됩니다. 각 코드 항목의 형식은 다음과 같습니다.

|Size|값|
|-|-|
|UBYTE|프롤로그의 오프셋|
|UBYTE: 4|해제 연산 코드|
|UBYTE: 4|작업 정보|

배열은 프롤로그에서 오프셋의 내림차순으로 정렬됩니다.

#### <a name="offset-in-prolog"></a>프롤로그의 오프셋

이 작업을 수행하는 명령의 끝에 대한 오프셋(프롤로그의 시작)에 1(즉, 다음 명령의 시작 오프셋)을 더한 값입니다.

#### <a name="unwind-operation-code"></a>해제 연산 코드

참고: 특정 연산 코드에는 로컬 스택 프레임의 값에 대한 부호 없는 오프셋이 필요합니다. 이 오프셋은 시작, 즉 고정 스택 할당의 가장 아래 주소에서 온 것입니다. UNWIND_INFO의 프레임 레지스터 필드가 0인 경우 이 오프셋은 RSP에서 나온 것입니다. 프레임 레지스터 필드가 0이 아닌 경우 이 오프셋은 FP 레지스터가 설정되었을 때 RSP가 있었던 위치에서 온 것입니다. 이 값은 FP 레지스터에서 FP 레지스터 오프셋을 뺀 값과 동일합니다(16 \* UNWIND_INFO의 배율 크기 조정된 프레임 레지스터 오프셋). FP 레지스터가 사용되는 경우 프롤로그에서 FP 레지스터가 설정된 후에만 오프셋을 사용한 해제 코드를 사용해야 합니다.

`UWOP_SAVE_XMM128` 및 `UWOP_SAVE_XMM128_FAR`을 제외한 모든 opcode에 대해 오프셋은 항상 8의 배수입니다. 왜냐하면 모든 대상 스택 값은 8바이트 경계에 저장되기 때문입니다(스택 자체는 항상 16바이트로 정렬됨). 짧은 오프셋(512K 미만)을 사용하는 연산 코드의 경우 이 코드의 노드에 있는 최종 USHORT는 오프셋을 8로 나눈 값을 포함합니다. 긴 오프셋(512K <= 오프셋 < 4GB)을 사용하는 연산 코드의 경우 이 코드에 대한 두 개의 최종 USHORT 노드에는 오프셋(little-endian 형식)이 포함됩니다.

opcode `UWOP_SAVE_XMM128` 및 `UWOP_SAVE_XMM128_FAR`의 경우 모든 128비트 XMM 작업은 16바이트 정렬 메모리에서 발생해야 하므로 오프셋은 항상 16의 배수입니다. 따라서 배율 16은 1M 미만의 오프셋을 허용하는 `UWOP_SAVE_XMM128`에 사용됩니다.

해제 연산 코드는 다음 값 중 하나입니다.

- `UWOP_PUSH_NONVOL` (0) 1 노드

  비휘발성 정수 레지스터를 푸시하여 RSP를 8씩 감소시킵니다. 작업 정보는 레지스터의 번호입니다. `UWOP_PUSH_NONVOL` 에필로그에 대한 제약 조건으로 인해 해제 코드가 프롤로그에는 처음에 표시되고, 이에 상응하여 해제 코드 배열에서는 마지막에 표시되어야 합니다. 이 상대 순서 지정은 `UWOP_PUSH_MACHFRAME`을 제외한 다른 모든 해제 코드에 적용됩니다.

- `UWOP_ALLOC_LARGE` (1) 2 또는 3 노드

  스택에서 큰 크기의 영역을 할당합니다. 두 가지 형태가 있습니다. 작업 정보가 0인 경우 할당의 크기를 8로 나눈 값이 다음 슬롯에 기록되어 최대 512K-8까지 할당할 수 있습니다. 작업 정보가 1이면 배율 크기 미조정 할당 크기는 little-endian 형식으로 다음 두 개의 슬롯에 기록되어 최대 4GB-8까지 할당할 수 있습니다.

- `UWOP_ALLOC_SMALL` (2) 1 노드

  스택에서 작은 크기의 영역을 할당합니다. 할당 크기는 작업 정보 필드 \* 8 + 8이므로 8에서 128바이트까지 할당할 수 있습니다.

  스택 할당에 대한 해제 코드는 항상 가능한 한 가장 짧은 인코딩을 사용해야 합니다.

  |**할당 크기**|**해제 코드**|
  |-|-|
  |8~128바이트|`UWOP_ALLOC_SMALL`|
  |136~512K-8바이트|`UWOP_ALLOC_LARGE`, 작업 정보 = 0|
  |512K ~ 4G-8바이트|`UWOP_ALLOC_LARGE`, 작업 정보 = 1|

- `UWOP_SET_FPREG` (3) 1 노드

  레지스터를 현재 RSP의 일부 오프셋으로 설정하여 프레임 포인터 레지스터를 설정합니다. 오프셋은 UNWIND_INFO의 프레임 레지스터 오프셋(비율 크기 조정됨) 필드 \* 16과 같으며 0에서 240 사이의 오프셋을 허용합니다. 오프셋을 사용하면 고정 스택 할당의 중간을 가리키는 프레임 포인터를 설정할 수 있습니다. 이로써 더 많은 액세스를 통해 짧은 명령 형식을 사용하게 되어 코드 밀도에 도움이 됩니다. 작업 정보 필드는 예약되어 있으므로 사용할 수 없습니다.

- `UWOP_SAVE_NONVOL` (4) 2 노드

  PUSH 대신 MOV를 사용하여 스택에 비휘발성 정수 레지스터를 저장합니다. 이 코드는 주로 비휘발성 레지스터가 이전에 할당된 위치에서 스택에 저장되는 ‘축소 래핑’에 사용됩니다. 작업 정보는 레지스터의 번호입니다. 위의 참고 사항에 설명된 대로, 8로 비율 크기 조정된 스택 오프셋은 다음 해제 연산 코드 슬롯에 기록됩니다.

- `UWOP_SAVE_NONVOL_FAR` (5) 3 노드

  PUSH 대신 MOV를 사용하여 긴 오프셋을 가진 스택에 비휘발성 정수 레지스터를 저장합니다. 이 코드는 주로 비휘발성 레지스터가 이전에 할당된 위치에서 스택에 저장되는 ‘축소 래핑’에 사용됩니다. 작업 정보는 레지스터의 번호입니다. 위의 참고 사항에 설명된 대로, 비율 크기 미조정 스택 오프셋은 두 개의 다음 해제 연산 코드 슬롯에 기록됩니다.

- `UWOP_SAVE_XMM128` (8) 2 노드

  스택에 비휘발성 XMM 레지스터의 128비트를 모두 저장합니다. 작업 정보는 레지스터의 번호입니다. 16으로 비율 크기 조정된 스택 오프셋은 다음 슬롯에 기록됩니다.

- `UWOP_SAVE_XMM128_FAR` (9) 3 노드

  긴 오프셋을 가진 스택에 비휘발성 XMM 레지스터의 128비트를 모두 저장합니다. 작업 정보는 레지스터의 번호입니다. 비율 크기 미조정 스택 오프셋은 다음 두 개의 슬롯에 기록됩니다.

- `UWOP_PUSH_MACHFRAME` (10) 1 노드

  컴퓨터 프레임을 푸시합니다.  이 해제 코드는 하드웨어 중단 또는 예외 효과를 기록하는 데 사용됩니다. 두 가지 형태가 있습니다. 작업 정보가 0인 경우 해당 프레임 중 하나가 스택으로 푸시됩니다.

  |위치|값|
  |-|-|
  |RSP+32|SS|
  |RSP+24|이전 RSP|
  |RSP+16|EFLAGS|
  |RSP+8|CS|
  |RSP|RIP|

  작업 정보가 1인 경우 해당 프레임 중 하나가 푸시됩니다.

  |위치|값|
  |-|-|
  |RSP+40|SS|
  |RSP+32|이전 RSP|
  |RSP+24|EFLAGS|
  |RSP+16|CS|
  |RSP+8|RIP|
  |RSP|오류 코드|

  이 해제 코드는 실제로 실행되지 않는 더미 프롤로그에 항상 표시되지만, 대신 중단 루틴의 실제 진입점 앞에 표시되며 컴퓨터 프레임의 푸시를 시뮬레이션하는 위치를 제공하기 위해서만 존재합니다. `UWOP_PUSH_MACHFRAME`은 해당 시뮬레이션을 기록하여 컴퓨터가 개념적으로 해당 작업을 수행했음을 표시합니다.

  1. 스택의 맨 위에서 *Temp*로 RIP 반환 주소 표시
  
  1. SS 푸시

  1. 이전 RSP 푸시

  1. EFLAGS 푸시

  1. CS 푸시

  1. *Temp* 푸시

  1. 오류 코드 푸시(op 정보가 1인 경우)

  시뮬레이션된 `UWOP_PUSH_MACHFRAME` 작업은 RSP를 40(op 정보 0) 또는 48(op 정보 1)씩 감소시킵니다.

#### <a name="operation-info"></a>작업 정보

작업 정보 비트의 의미는 연산 코드에 따라 달라집니다. 범용(정수) 레지스터를 인코딩하려면 다음 매핑이 사용됩니다.

|bit|등록|
|-|-|
|0|RAX|
|1|RCX|
|2|RDX|
|3|RBX|
|4|RSP|
|5|RBP|
|6|RSI|
|7|RDI|
|8~15|R8~R15|

### <a name="chained-unwind-info-structures"></a>연결된 해제 정보 구조체

UNW_FLAG_CHAININFO 플래그가 설정되면 해제 정보 구조체는 보조가 되고, 공유된 예외 처리기/연결된 정보 주소 필드에 기본 해제 정보가 포함됩니다. 이 샘플 코드는 주요 해제 정보를 검색하며 `unwindInfo`는 UNW_FLAG_CHAININFO 플래그가 설정된 구조체로 가정합니다.

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

연결된 정보는 두 가지 상황에서 유용합니다. 첫째, 연속되지 않은 코드 세그먼트에 사용할 수 있습니다. 연결된 정보를 사용하면 기본 해제 정보에서 해제 코드 배열을 복제할 필요가 없으므로 필요한 해제 정보의 크기를 줄일 수 있습니다.

또한 연결된 정보를 사용하여 휘발성 레지스터 저장을 그룹화할 수 있습니다. 컴파일러가 함수 항목 프롤로그의 외부에 있게 될 때까지 휘발성 레지스터의 저장을 연기할 수 있습니다. 그룹화된 코드 앞의 함수 부분에 대한 기본 해제 정보가 있으면 휘발성 레지스터를 기록한 다음 크기가 0이 아닌 프롤로그를 포함한 연결된 정보를 설정할 수 있습니다. 이 경우 연결된 정보의 해제 코드는 비휘발성 레지스터의 저장을 반영합니다. 이 경우 해제 코드는 UWOP_SAVE_NONVOL의 모든 인스턴스입니다. PUSH를 사용하여 비휘발성 레지스터를 저장하거나 추가 고정 스택 할당을 사용하여 RSP 레지스터를 수정하는 그룹화는 지원되지 않습니다.

UNW_FLAG_CHAININFO가 설정된 UNWIND_INFO 항목에는 역시 UNWIND_INFO 항목이 설정된 RUNTIME_FUNCTION 항목이 포함될 수 있으며, 이를 ‘다중 축소 래핑’이라고도 부르기도 합니다. 결국 연결된 해제 정보 포인터는 UNW_FLAG_CHAININFO가 지워진 UNWIND_INFO 항목에 도착합니다. 이 항목은 실제 프로시저 진입점을 가리키는 기본 UNWIND_INFO 항목입니다.

## <a name="unwind-procedure"></a>해제 프로시저

해제 코드 배열은 내림차순으로 정렬됩니다. 예외가 발생하는 경우 전체 컨텍스트는 운영 체제에 의해 컨텍스트 레코드에 저장됩니다. 그런 다음 예외 디스패치 논리가 호출되어 예외 처리기를 찾기 위해 다음과 같은 단계를 반복적으로 실행합니다.

1. 컨텍스트 레코드에 저장된 최신 RIP를 사용하여 최신 함수(또는 연결된 UNWIND_INFO 항목에 대한 함수 부분)를 설명하는 RUNTIME_FUNCTION 테이블 항목을 검색합니다.

1. 검색된 함수 테이블 항목이 없는 경우 이는 리프 함수에 있으며, RSP가 반환 포인터를 직접 해결합니다. [RSP]에 있는 반환 포인터는 업데이트된 컨텍스트에 저장되고, 시뮬레이션된 RSP는 8씩 증가하며, 1단계가 반복됩니다.

1. 함수 테이블 항목이 검색되는 경우 RIP는 다음 세 가지 지역 내에 있습니다. 즉, a) 에필로그 안, b) 프롤로그 안 또는 c) 예외 처리기로 커버될 수 있는 코드 안입니다.

   - 사례 a) RIP가 에필로그 내에 있으면 컨트롤이 함수를 종료하며, 이 함수에 대해 이 예외와 연결된 예외 처리기가 없을 수 있고, 에필로그의 효과는 호출자 함수의 컨텍스트를 계산하기 위해 계속되어야 합니다. RIP가 에필로그 내에 있는지 확인하려면 RIP 이후부터 코드 스트림을 검사합니다. 해당 코드 스트림을 합법적인 에필로그의 후행 부분과 일치시킬 수 있는 경우 이는 에필로그 안에 있으며, 에필로그의 나머지 부분이 시뮬레이션되고, 각 명령이 처리되면서 컨텍스트 레코드가 업데이트됩니다. 이 처리 후 1단계가 반복됩니다.

   - 사례 b) RIP가 프롤로그 내에 있는 경우 컨트롤은 함수를 입력하지 않았고, 이 함수에 대해 이 예외와 연결된 예외 처리기가 없을 수 있으며, 프롤로그의 효과는 호출자 함수의 컨텍스트를 계산하기 위해 취소되어야 합니다. 함수 시작부터 RIP까지의 거리가 해제 정보에 인코딩된 프롤로그 크기보다 작거나 같은 경우에는 RIP가 프롤로그 내에 있습니다. 함수 시작에서 RIP의 오프셋보다 작거나 같은 오프셋을 가진 첫 번째 항목에 대한 해제 코드 배열을 통해 앞으로 스캔한 다음 해제 코드 배열에서 나머지 모든 항목의 영향을 취소하여 프롤로그의 효과를 해제합니다. 그런 다음 1단계를 반복합니다.

   - 사례 c) RIP가 프롤로그 또는 에필로그 내에 있지 않고 함수에 예외 처리기가 있는 경우(UNW_FLAG_EHANDLER 설정됨) 언어별 처리기가 호출됩니다. 처리기는 해당 데이터를 스캔하고 필터 함수를 적절하게 호출합니다. 언어별 처리기는 예외가 처리되었음 또는 검색이 계속됨을 반환합니다. 또한 해제를 직접 시작할 수 있습니다.

1. 언어별 처리기가 처리된 상태를 반환하는 경우 원래 컨텍스트 레코드를 사용하여 실행이 계속됩니다.

1. 언어별 처리기가 없거나 처리기가 “검색 계속” 상태를 반환하는 경우 컨텍스트 레코드를 호출자의 상태로 해제해야 합니다. 이는 모든 해제 코드 배열 요소를 처리하고 각 효과를 취소하여 수행됩니다. 그런 다음 1단계를 반복합니다.

연결된 해제 정보를 포함하는 경우에도 해당 기본 단계를 계속 따릅니다. 유일한 차이점은 프롤로그의 효과를 해제하기 위해 해제 코드 배열 워크를 진행하는 동안 배열의 끝에 도달한 다음 부모 해제 정보에 연결되며 거기에 있는 전체 해제 코드 배열 워크가 진행된다는 것입니다. 해당 연결은 UNW_CHAINED_INFO 플래그 없이 해제 정보에 도착할 때까지 계속되며, 그런 다음 해제 코드 배열 워크를 완료합니다.

해제 데이터의 가장 작은 집합은 8바이트입니다. 이는 128바이트의 스택 이하만 할당했고 비휘발성 레지스터 하나를 저장할 수 있는 함수를 나타냅니다. 또한 해제 코드 없이 길이가 0인 프롤로그에 대한 연결된 해제 정보 구조의 크기이기도 합니다.

## <a name="language-specific-handler"></a>언어별 처리기

UNW_FLAG_EHANDLER 또는 UNW_FLAG_UHANDLER 플래그가 설정될 때마다 UNWIND_INFO에 언어별 처리기의 상대 주소가 표시됩니다. 이전 섹션에서 설명한 것처럼 언어별 처리기는 예외 처리기 검색의 일부 또는 해제 일부로 호출됩니다. 다음과 같은 프로토타입을 갖습니다.

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord**는 표준 Win64 정의를 포함하는 예외 레코드에 대한 포인터를 제공합니다.

**EstablisherFrame**은 이 함수에 대한 고정 스택 할당의 기본 주소입니다.

**ContextRecord**는 예외가 발생한 시점의 예외 컨텍스트(예외 처리기의 경우) 또는 현재 “해제” 컨텍스트(종료 처리기의 경우)를 가리킵니다.

**DispatcherContext**는 이 함수에 대한 디스패처 컨텍스트를 가리킵니다. 다음과 같은 정의를 갖습니다.

```cpp
typedef struct _DISPATCHER_CONTEXT {
    ULONG64 ControlPc;
    ULONG64 ImageBase;
    PRUNTIME_FUNCTION FunctionEntry;
    ULONG64 EstablisherFrame;
    ULONG64 TargetIp;
    PCONTEXT ContextRecord;
    PEXCEPTION_ROUTINE LanguageHandler;
    PVOID HandlerData;
} DISPATCHER_CONTEXT, *PDISPATCHER_CONTEXT;
```

**ControlPc**는 이 함수 내의 RIP 값입니다. 이 값은 예외 주소이거나 제어가 설정 함수를 떠난 주소입니다. RIP는 컨트롤이 이 함수 내의 일부 보호된 구문 내에 있는지 확인하는 데 사용됩니다(예: **`__try`** / **`__except`** 또는 **`__try`** / **`__finally`** 에 대한 **`__try`** 블록).

**ImageBase**는 이 함수에 포함된 모듈의 이미지 기반(로드 주소)으로서 함수 항목 및 해제 정보에 사용되는 32비트 오프셋에 추가되어 상대 주소를 기록합니다.

**FunctionEntry**는 함수를 포함하는 RUNTIME_FUNCTION 함수 항목에 대한 포인터 및 이 함수에 대한 해제 정보 이미지-기본 상대 주소를 제공합니다.

**EstablisherFrame**은 이 함수에 대한 고정 스택 할당의 기본 주소입니다.

**TargetIp**는 해제의 연속 주소를 지정하는 선택적 명령 주소를 제공합니다. **EstablisherFrame**이 지정되지 않은 경우 이 주소는 무시됩니다.

**ContextRecord**는 시스템 예외 디스패치/해제 코드에서 사용할 예외 컨텍스트를 가리킵니다.

**LanguageHandler**는 호출되는 언어별 언어 처리기 루틴을 가리킵니다.

**HandlerData**는 이 함수에 대한 언어별 처리기 데이터를 가리킵니다.

## <a name="unwind-helpers-for-masm"></a>MASM에 대한 해제 도우미

적절한 어셈블리 루틴을 작성하기 위해 실제 어셈블리 명령과 병렬로 사용하여 적절한 .pdata 및 .xdata를 만들 수 있는 의사 작업 집합이 있습니다. 그리고 가장 일반적으로 사용되는 의사 작업을 간단하게 사용할 때 제공되는 매크로 집합이 있습니다.

### <a name="raw-pseudo-operations"></a>원시 의사 작업

|의사 작업|설명|
|-|-|
|PROC FRAME \[:*ehandler*]|MASM에서 함수의 구조화된 예외 처리 해제 동작에 대한 .xdata에서 .pdata 및 해제 정보의 함수 테이블 항목을 생성하도록 합니다.  *ehandler*가 있는 경우 이 proc은 언어별 처리기로 .xdata에 입력됩니다.<br /><br /> FRAME 특성을 사용하는 경우 ENDPROLOG 지시문 뒤에 와야 합니다.  함수가 리프 함수([함수 형식](../build/stack-usage.md#function-types))인 경우 의사 연산의 나머지와 마찬가지로 FRAME 특성이 필요하지 않습니다.|
|.PUSHREG *register*|프롤로그의 현재 오프셋을 사용하여 지정된 레지스터 번호에 대한 UWOP_PUSH_NONVOL 해제 코드 항목을 생성합니다.<br /><br /> 비휘발성 정수 레지스터에서만 사용합니다.  비휘발성 레지스터 푸시의 경우 대신 ALLOCSTACK 8을 사용합니다.|
|.SETFRAME *register*, *offset*|지정된 레지스터 및 오프셋을 사용하여 해제 정보에서 프레임 레지스터 필드와 오프셋을 채웁니다. 오프셋은 16의 배수여야 하며 240보다 작거나 같아야 합니다. 이 지시문은 현재 프롤로그 오프셋을 사용하여 지정된 레지스터에 대한 UWOP_SET_FPREG 해제 코드 항목을 생성합니다.|
|.ALLOCSTACK *size*|프롤로그에서 현재 오프셋의 지정된 크기를 사용하여 UWOP_ALLOC_SMALL 또는 UWOP_ALLOC_LARGE를 생성합니다.<br /><br /> ‘크기’ 피연산자는 8의 배수여야 합니다.|
|.SAVEREG *register*, *offset*|현재 프롤로그 오프셋을 사용하여 지정된 레지스터 및 오프셋에 대한 UWOP_SAVE_NONVOL 또는 UWOP_SAVE_NONVOL_FAR 해제 코드 항목 중 하나를 생성합니다. MASM은 가장 효율적인 인코딩을 선택합니다.<br /><br /> ‘오프셋’은 양수여야 하며 8의 배수여야 합니다. ‘오프셋’은 프로시저 프레임의 베이스를 기준으로 하는데, 이는 RSP에 있거나 프레임 포인터를 사용하는 경우 배율 크기 조정이 되지 않은 프레임 포인터에 있습니다.|
|.SAVEXMM128 *register*, *offset*|현재 프롤로그 오프셋을 사용하여 지정된 XMM 레지스터 및 오프셋에 대한 UWOP_SAVE_XMM128 또는 UWOP_SAVE_XMM128_FAR 해제 코드 항목 중 하나를 생성합니다. MASM은 가장 효율적인 인코딩을 선택합니다.<br /><br /> ‘오프셋’은 양수여야 하며 16의 배수여야 합니다.  ‘오프셋’은 프로시저 프레임의 베이스를 기준으로 하는데, 이는 RSP에 있거나 프레임 포인터를 사용하는 경우 배율 크기 조정이 되지 않은 프레임 포인터에 있습니다.|
|.PUSHFRAME \[*code*]|UWOP_PUSH_MACHFRAME 해제 코드 항목을 생성합니다. 선택적 ‘코드’가 지정된 경우 해제 코드 항목에는 한정자 1이 지정됩니다. 그러지 않으면 한정자 0이 지정됩니다.|
|.ENDPROLOG|프롤로그 선언의 끝을 신호로 보냅니다.  함수의 처음 255바이트에서 발생해야 합니다.|

대부분의 opcode를 적절하게 사용하는 샘플 함수 프롤로그는 다음과 같습니다.

```MASM
sample PROC FRAME
    db      048h; emit a REX prefix, to enable hot-patching
    push rbp
    .pushreg rbp
    sub rsp, 040h
    .allocstack 040h
    lea rbp, [rsp+020h]
    .setframe rbp, 020h
    movdqa [rbp], xmm7
    .savexmm128 xmm7, 020h ;the offset is from the base of the frame
                           ;not the scaled offset of the frame
    mov [rbp+018h], rsi
    .savereg rsi, 038h
    mov [rsp+010h], rdi
    .savereg rdi, 010h ; you can still use RSP as the base of the frame
                       ; or any other register you choose
    .endprolog

; you can modify the stack pointer outside of the prologue (similar to alloca)
; because we have a frame pointer.
; if we didn't have a frame pointer, this would be illegal
; if we didn't make this modification,
; there would be no need for a frame pointer

    sub rsp, 060h

; we can unwind from the next AV because of the frame pointer

    mov rax, 0
    mov rax, [rax] ; AV!

; restore the registers that weren't saved with a push
; this isn't part of the official epilog, as described in section 2.5

    movdqa xmm7, [rbp]
    mov rsi, [rbp+018h]
    mov rdi, [rbp-010h]

; Here's the official epilog

    lea rsp, [rbp+020h] ; deallocate both fixed and dynamic portions of the frame
    pop rbp
    ret
sample ENDP
```

에필로그 예제에 대한 자세한 내용은 [x64 프롤로그 및 에필로그](prolog-and-epilog.md)의 [에필로그 코드](prolog-and-epilog.md#epilog-code)를 참조하세요.

### <a name="masm-macros"></a>MASM 매크로

[원시 의사 작업](#raw-pseudo-operations)의 사용을 간소화하기 위해 일반적인 프로시저 프롤로그 및 에필로그를 만드는 데 사용할 수 있는 ksamd64에 정의된 매크로 집합이 있습니다.

|매크로|설명|
|-|-|
|alloc_stack(n)|`sub rsp, n`을 사용하여 n바이트의 스택 프레임을 할당하고 적절한 해제 정보(.allocstack n)를 내보냅니다.|
|save_reg *reg*, *loc*|RSP 오프셋 *loc*의 스택에 비휘발성 레지스터 *reg*를 저장하고 적절한 해제 정보를 내보냅니다. (.savereg reg, loc)|
|push_reg *reg*|스택에서 비휘발성 레지스터 *reg*를 푸시하고 적절한 해제 정보를 내보냅니다. (.pushreg reg)|
|rex_push_reg *reg*|2바이트 푸시를 사용하여 스택에 비휘발성 레지스터를 저장하고 적절한 해제 정보(.pushreg reg)를 내보냅니다.  푸시가 함수의 첫 번째 명령인 경우 이 매크로를 사용하여 함수가 핫 패치 가능하도록 합니다.|
|save_xmm128 *reg*, *loc*|RSP 오프셋 *loc*의 스택에 비휘발성 XMM 레지스터 *reg*를 저장하고 적절한 해제 정보(.savexmm128 reg, loc)를 내보냅니다.|
|set_frame *reg*, *offset*|프레임 레지스터 *reg*를 RSP + *offset*(`mov` 또는 `lea` 사용)으로 설정하고 적절한 해제 정보(.set_frame reg, offset)를 내보냅니다.|
|push_eflags|`pushfq` 명령으로 eflags를 푸시하고 적절한 해제 정보(.alloc_stack 8)를 내보냅니다.|

매크로를 적절하게 사용하는 샘플 함수 프롤로그는 다음과 같습니다.

```MASM
sampleFrame struct
    Fill     dq ?; fill to 8 mod 16
    SavedRdi dq ?; Saved Register RDI
    SavedRsi dq ?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
    alloc_stack(sizeof sampleFrame)
    save_reg rdi, sampleFrame.SavedRdi
    save_reg rsi, sampleFrame.SavedRsi
    .end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here's the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="unwind-data-definitions-in-c"></a>C의 해제 데이터 정의

다음은 해제 데이터에 대한 설명 C입니다.

```C
typedef enum _UNWIND_OP_CODES {
    UWOP_PUSH_NONVOL = 0, /* info == register number */
    UWOP_ALLOC_LARGE,     /* no info, alloc size in next 2 slots */
    UWOP_ALLOC_SMALL,     /* info == size of allocation / 8 - 1 */
    UWOP_SET_FPREG,       /* no info, FP = RSP + UNWIND_INFO.FPRegOffset*16 */
    UWOP_SAVE_NONVOL,     /* info == register number, offset in next slot */
    UWOP_SAVE_NONVOL_FAR, /* info == register number, offset in next 2 slots */
    UWOP_SAVE_XMM128 = 8, /* info == XMM reg number, offset in next slot */
    UWOP_SAVE_XMM128_FAR, /* info == XMM reg number, offset in next 2 slots */
    UWOP_PUSH_MACHFRAME   /* info == 0: no error-code, 1: error-code */
} UNWIND_CODE_OPS;

typedef union _UNWIND_CODE {
    struct {
        UBYTE CodeOffset;
        UBYTE UnwindOp : 4;
        UBYTE OpInfo   : 4;
    };
    USHORT FrameOffset;
} UNWIND_CODE, *PUNWIND_CODE;

#define UNW_FLAG_EHANDLER  0x01
#define UNW_FLAG_UHANDLER  0x02
#define UNW_FLAG_CHAININFO 0x04

typedef struct _UNWIND_INFO {
    UBYTE Version       : 3;
    UBYTE Flags         : 5;
    UBYTE SizeOfProlog;
    UBYTE CountOfCodes;
    UBYTE FrameRegister : 4;
    UBYTE FrameOffset   : 4;
    UNWIND_CODE UnwindCode[1];
/*  UNWIND_CODE MoreUnwindCode[((CountOfCodes + 1) & ~1) - 1];
*   union {
*       OPTIONAL ULONG ExceptionHandler;
*       OPTIONAL ULONG FunctionEntry;
*   };
*   OPTIONAL ULONG ExceptionData[]; */
} UNWIND_INFO, *PUNWIND_INFO;

typedef struct _RUNTIME_FUNCTION {
    ULONG BeginAddress;
    ULONG EndAddress;
    ULONG UnwindData;
} RUNTIME_FUNCTION, *PRUNTIME_FUNCTION;

#define GetUnwindCodeEntry(info, index) \
    ((info)->UnwindCode[index])

#define GetLanguageSpecificDataPtr(info) \
    ((PVOID)&GetUnwindCodeEntry((info),((info)->CountOfCodes + 1) & ~1))

#define GetExceptionHandler(base, info) \
    ((PEXCEPTION_HANDLER)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetChainedFunctionEntry(base, info) \
    ((PRUNTIME_FUNCTION)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetExceptionDataPtr(info) \
    ((PVOID)((PULONG)GetLanguageSpecificData(info) + 1)
```

## <a name="see-also"></a>참조

[x64 소프트웨어 규칙](../build/x64-software-conventions.md)
