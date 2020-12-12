---
description: '다음에 대 한 자세한 정보: 프로토콜'
title: PROTO
ms.date: 12/06/2019
f1_keywords:
- PROTO
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
ms.openlocfilehash: 34dbf9d877dbbc52484e45c5f94212108aeacb42
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97126011"
---
# <a name="proto"></a>PROTO

함수 또는 프로시저를 프로토타입 합니다. [INVOKE](invoke.md) 지시어를 사용 하 여 PROTO 지시문에 의해 프로토타입화 된 함수를 호출할 수 있습니다.

## <a name="syntax"></a>Syntax

> *label* **PROTO** ⟦*distance**⟧ ⟦ ⟧*⟦__,__ ⟦*parameter*⟧__:__*tag* ... ⟧

### <a name="parameters"></a>매개 변수

*레이블*\
프로토타입화 된 함수의 이름입니다.

*distance* (32 비트 MASM에만 해당) \
필드 16 비트 메모리 모델에서 기본값을 재정의 하 고 **NEAR** 또는 **FAR** 호출을 나타내는 데 사용 됩니다.

*언어 유형* (32 비트 MASM에만 해당) \
필드 프로시저 및 공용 기호에 대 한 호출 및 명명 규칙을 설정 합니다. 지원 되는 규칙은 다음과 같습니다.

- 32 비트 **플랫** 모델: **C**, **STDCALL**

- 16 비트 모델: **C**, **BASIC**, **포트란**, **파스칼**, **SYSCALL**, **STDCALL**

*변수에*\
함수 매개 변수의 선택적 이름입니다.

*태그가*\
함수 매개 변수의 형식입니다.

*매개 변수* 및 *태그* 매개 변수는 전달 된 각 인수에 대해 한 번씩 여러 번 나타날 수 있습니다.

## <a name="example"></a>예제

이 샘플에서는  `addup3` **NEAR** 호출을 사용 하 여 프로시저 호출에 대 한 16 비트 모델 기본값을 재정의 하 고 스택 매개 변수 및 반환 값에 대해 **C** 호출 규칙을 사용 하는 라는 함수의 프로토콜 선언을 보여 줍니다. **단어** 와 **VARARG** 라는 두 개의 인수를 사용 합니다.

```MASM
addup3 PROTO NEAR C, argcount:WORD, arg1:VARARG
```

## <a name="see-also"></a>참고 항목

[지시문 참조](directives-reference.md)\
[. 모델 참조](dot-model.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
