---
description: 에 대해 자세히 알아보세요. 모델 (32 비트 MASM)
title: .MODEL
ms.date: 11/05/2019
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: a4324b89f1194227edd7f1d5b7bd70560eca16be
ms.sourcegitcommit: 6183207b11575d7b44ebd7c18918e916a0d8c63d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97951422"
---
# <a name="model-32-bit-masm"></a>. 모델 (32 비트 MASM)

프로그램 메모리 모델을 초기화합니다. (32 비트 MASM에만 해당)

## <a name="syntax"></a>구문

> **. 모델** *메모리-모델* ⟦__,__ *⟧ ⟦*__,__ *stack option*⟧

### <a name="parameters"></a>매개 변수

*메모리 모델*\
코드 및 데이터 포인터의 크기를 결정하는 필수 매개 변수입니다.

*언어 유형*\
프로시저 및 공용 기호에 대한 호출 및 명명 규칙을 설정하는 선택적 매개 변수입니다.

*stack 옵션*\
선택적 매개 변수입니다.

*메모리 모델이* **FLAT** 인 경우에는 *stack 옵션이* 사용 되지 않습니다.

**NEARSTACK** 를 지정 하면 스택 세그먼트가 데이터와 함께 단일 물리적 세그먼트 (**차원 그룹**)로 그룹화 됩니다. 스택 세그먼트 레지스터 (**SS**)는 데이터 세그먼트 레지스터 (**DS**)와 동일한 주소를 보유 하는 것으로 간주 됩니다. **FARSTACK** 는 ' d **group**'로 스택을 그룹화 하지 않습니다. 따라서 **SS** 는 **DS** 와 같지 않습니다.

## <a name="remarks"></a>설명

**. 모델** 은 x [64 용 MASM (ml64.exe)](masm-for-x64-ml64-exe.md)에서 사용 되지 않습니다.

다음 표에는 16비트 및 32비트 플랫폼을 대상으로 할 때 각 매개 변수에 대해 가능한 값이 나열되어 있습니다.

|매개 변수|32비트 값|16비트 값(이전 16비트 개발에 대한 지원)|
|---------------|--------------------|----------------------------------------------------------------|
|*메모리 모델*|**일반**|매우 **작음**, **작음**, **압축**, **보통**, **크게**, **매우 큼**, **플랫**|
|*언어 유형*|**C**, **STDCALL**|**C**, **BASIC**, **포트란**, **파스칼**, **SYSCALL**, **STDCALL**|
|*stack 옵션*|사용되지 않음|**NEARSTACK**, **FARSTACK**|

## <a name="code"></a>코드

MASM 관련 샘플의 경우 [Visual C++ 샘플 및 Visual Studio 2010용 관련 설명서](https://github.com/Microsoft/vcsamples)에서 컴파일러 샘플을 다운로드합니다.

다음 예제에서는 `.MODEL` 지시문을 사용하는 방법을 보여줍니다.

## <a name="example"></a>예제

```asm
; file simple.asm
; For x86 (32-bit), assemble with debug information:
;   ml -c -Zi simple.asm
; For x64 (64-bit), assemble with debug information:
;   ml64 -c -DX64 -Zi simple.asm
;
; In this sample, the 'X64' define excludes source not used
;  when targeting the x64 architecture

ifndef X64
.686p
.XMM
.model flat, C
endif

.data
; user data

.code
; user code

fxn PROC public
  xor eax, eax ; zero function return value
  ret
fxn ENDP

end
```

## <a name="see-also"></a>참조

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
