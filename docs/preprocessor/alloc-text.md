---
description: '다음에 대 한 자세한 정보: alloc_text pragma'
title: alloc_text pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
ms.openlocfilehash: 496a083c251684ebba004eef00bf466e72211ada
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301063"
---
# <a name="alloc_text-pragma"></a>alloc_text pragma

지정한 함수 정의가 상주하는 코드 섹션의 이름을 지정합니다. pragma는 명명된 함수의 함수 선언자와 함수 정의 간에 발생해야 합니다.

## <a name="syntax"></a>Syntax

> **#pragma alloc_text (** "*textsection*" **,** *function1* [**,** *function2* ...] **)**

## <a name="remarks"></a>설명

**Alloc_text** Pragma는 c + + 멤버 함수 또는 오버 로드 된 함수를 처리 하지 않습니다. C 링크를 사용 하 여 선언 된 함수, 즉 **extern "C"** 링크 사양으로 선언 된 함수에만 적용할 수 있습니다. C++ 링크가 있는 함수에 pragma를 사용하려고 하면 컴파일러 오류가 발생합니다.

를 사용 하 여 함수 주소를 지정 하 **`__based`** 는 기능은 지원 되지 않으므로 섹션 위치를 지정 하려면 **alloc_text** pragma를 사용 해야 합니다. *Textsection* 으로 지정 된 이름은 큰따옴표로 묶어야 합니다.

**Alloc_text** pragma는 지정 된 함수의 선언 뒤와 이러한 함수의 정의 앞에 나타나야 합니다.

**Alloc_text** pragma에서 참조 되는 함수는 pragma와 동일한 모듈에서 정의 되어야 합니다. 그렇지 않고 나중에 정의 되지 않은 함수가 다른 텍스트 섹션으로 컴파일될 경우 오류가 catch 될 수도 있고 그렇지 않을 수도 있습니다. 프로그램은 보통 올바르게 실행되더라도 함수는 원하는 섹션에서 할당되지 않습니다.

**Alloc_text** 에 대 한 다른 제한 사항은 다음과 같습니다.

- 함수 내에서 사용할 수 없습니다.

- 함수가 선언된 후, 그리고 함수가 정의되기 전에 사용되어야 합니다.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
