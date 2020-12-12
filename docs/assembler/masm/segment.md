---
description: ': 세그먼트에 대 한 자세한 정보'
title: SEGMENT
ms.date: 12/16/2019
f1_keywords:
- SEGMENT
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
ms.openlocfilehash: aeb99080043cbfb13fdec1c2e82df3a6d16b306d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97125595"
---
# <a name="segment"></a>SEGMENT

세그먼트 특성이 있는 *이름* 이라는 프로그램 세그먼트를 정의 합니다.

## <a name="syntax"></a>Syntax

> *이름* **세그먼트** ⟦**READONLY**⟧ ⟦*align*⟧ ⟦*combine*⟧ ⟦*use*⟧ ⟦*특징*⟧ **ALIAS (**_string_**)** ⟦__'__*class*__'__⟧ \
> *할당문*\
> *이름* **끝**

#### <a name="parameters"></a>매개 변수

*않아*\
세그먼트의 시작 주소를 선택할 수 있는 메모리 주소 범위입니다. 맞춤 유형은 다음 중 하나일 수 있습니다.

|정렬 유형|시작 주소|
|----------------|----------------------|
|**BYTE**|사용 가능한 다음 바이트 주소입니다.|
|**WORD**|사용 가능한 다음 word 주소 (word 당 2 바이트)|
|**DWORD**|다음 사용 가능한 이중 단어 주소 (이중 단어 당 4 바이트)|
|**이전**|사용 가능한 다음 단락 주소 (단락 당 16 바이트)입니다.|
|**페이지**|다음 사용 가능한 페이지 주소 (페이지당 256 바이트)|
|**ALIGN**(*n*)|사용할 수 있는 다음 *n* 번째 바이트 주소입니다. 자세한 내용은 설명 부분을 참조 하세요.|

이 매개 변수를 지정 하지 않으면 기본적으로 **단락** 을 사용 합니다.

*combine* (32 비트 MASM에만 해당) \
**공용**, **스택**, **공용**, **메모리**, <em>주소</em>, **개인**

*use* (32 비트 MASM에만 해당) \
**USE16**, **USE32**, **FLAT**

*적인*\
**정보**, **읽기**, **쓰기**, **실행**, **공유**, **nopage**, **NOCACHE** 및 **취소**

이러한 기능은 COFF 에서만 지원 되며 유사한 이름의 COFF 섹션 특성에 해당 합니다. 예를 들어 **SHARED** 는 IMAGE_SCN_MEM_SHARED에 해당 합니다. 읽기 IMAGE_SCN_MEM_READ 플래그를 설정 합니다. 사용 되지 않는 READONLY 플래그는 섹션을 사용 하 여 IMG_SCN_MEM_WRITE 플래그를 지웁니다. *특성이* 설정 되 면 기본 특성이 사용 되지 않으며 프로그래머 지정 플래그만 적용 됩니다.

_문자열_\
이 문자열은 내보낸 COFF 개체의 섹션 이름으로 사용 됩니다.  고유한 MASM 세그먼트 이름을 사용 하 여 동일한 외부 이름으로 여러 섹션을 만듭니다.

**/Omf** 에서 지원 되지 않습니다.

*클래스*\
어셈블된 파일에서 세그먼트를 결합 하 고 정렬 하는 방법을 지정 합니다. 일반적인 값은, `'DATA'` , `'CODE'` `'CONST'` 및입니다. `'STACK'`

## <a name="remarks"></a>설명

의 `ALIGN(n)` 경우 *n* 은 1에서 8192 사이에 2의 거듭제곱이 될 수 있습니다. **/omf** 에서 지원 되지 않습니다.

## <a name="see-also"></a>참고 항목

[지시문 참조](directives-reference.md)\
[MASM BNF 문법](masm-bnf-grammar.md)
