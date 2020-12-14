---
description: '자세한 정보: 전처리기 연산자'
title: 전처리기 연산자
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
ms.openlocfilehash: 960531a32dd8b4f834117fb01272e2ed45fecf92
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202095"
---
# <a name="preprocessor-operators"></a>전처리기 연산자

지시문의 컨텍스트에서는 네 가지 전처리기 관련 연산자가 사용 됩니다 `#define` . 각에 대 한 요약은 다음 표를 참조 하세요. 문자열 화, charizing 및 토큰 붙여넣기 연산자는 다음 세 섹션에서 설명 합니다. 연산자에 대 한 자세한 내용은 `defined` [#if, #elif, #else 및 #endif 지시문](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)을 참조 하십시오.

|연산자|작업|
|--------------|------------|
|[문자열화 연산자(#)](../preprocessor/stringizing-operator-hash.md)|해당 하는 실제 인수를 큰따옴표로 묶는 원인이 됩니다.|
|[Charizing 연산자(#@)](../preprocessor/charizing-operator-hash-at.md)|해당 인수를 작은따옴표로 묶어 문자 (Microsoft 전용)로 처리 하도록 합니다.|
|[토큰 붙여넣기 연산자(##)](../preprocessor/token-pasting-operator-hash-hash.md)|실제 인수로 사용 되는 토큰을 연결 하 여 다른 토큰을 형성할 수 있습니다.|
|[defined 연산자](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|특정 매크로 지시문의 복합 식 작성을 간소화 합니다.|

## <a name="see-also"></a>참고 항목

[전처리기 지시문](../preprocessor/preprocessor-directives.md)\
[미리 정의 된 매크로](../preprocessor/predefined-macros.md)\
[c/c + + 전처리기 참조](../preprocessor/c-cpp-preprocessor-reference.md)
