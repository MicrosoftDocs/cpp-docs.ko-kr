---
description: '자세한 정보: 전처리기'
title: 전처리기
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: dd79766777926871e7bbf849f96420ef37052eba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202082"
---
# <a name="preprocessor"></a>전처리기

전처리기는 첫 번째 변환 단계의 일부로 소스 파일의 텍스트를 조작하는 텍스트 처리기입니다. 전처리기는 소스 텍스트를 구문 분석 하지 않지만 토큰으로 구분 하 여 매크로 호출을 찾습니다. 컴파일러는 일반적으로 첫 번째 단계에서 전처리기를 호출하지만, 컴파일 없이 텍스트를 처리하기 위해 전처리기를 별도로 호출할 수도 있습니다.

전처리기에 대한 참조 자료에는 다음 단원이 포함되어 있습니다.

- [전처리기 지시문](../preprocessor/preprocessor-directives.md)

- [전처리기 연산자](../preprocessor/preprocessor-operators.md)

- [미리 정의된 매크로](../preprocessor/predefined-macros.md)

- [pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**Microsoft 전용**

[/E](../build/reference/e-preprocess-to-stdout.md) 또는 [/ep](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 컴파일러 옵션을 사용 하 여 전처리 후 소스 코드의 목록을 가져올 수 있습니다. 두 옵션 모두 전처리기를 호출 하 고 결과 텍스트를 표준 출력 장치로 보냅니다. 대부분의 경우 콘솔입니다. 두 옵션의 차이점은 `/E` 지시문을 포함 하 `#line` 고 이러한 지시문을 제거 하는 것입니다 `/EP` .

**Microsoft 전용 종료**

## <a name="special-terminology"></a><a name="_predir_special_terminology"></a> 특수 용어

전처리기 설명서에서 "인수"라는 용어는 함수에 전달되는 엔터티를 나타냅니다. 경우에 따라 함수 호출에 지정 된 인수 식 및 함수 정의에 지정 된 인수 선언을 각각 설명 하는 "actual" 또는 "공식적인"로 수정 됩니다.

"변수"라는 용어는 간단한 C 형식 데이터 개체를 나타냅니다. "Object" 라는 용어는 c + + 개체와 변수를 모두 나타냅니다. 포괄 용어입니다.

## <a name="see-also"></a>참고 항목

[C/C++ 전처리기 참조](../preprocessor/c-cpp-preprocessor-reference.md)\
[변환 단계](../preprocessor/phases-of-translation.md)
