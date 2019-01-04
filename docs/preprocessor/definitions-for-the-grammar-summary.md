---
title: 문법 요약 정의
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
ms.openlocfilehash: 133000c0cc8ef636a3f9752d2f6fc7f1934bd831
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521127"
---
# <a name="definitions-for-the-grammar-summary"></a>문법 요약 정의

터미널은 구문 정의에서 끝점입니다. 다른 방법은 없습니다. 터미널에는 예약어와 사용자 정의 식별자가 포함됩니다.

넌터미널은 구문에서 자리를 표시합니다. 대부분은 이 구문 요약의 다른 곳에서 정의되어 있습니다. 정의는 재귀적일 수 있습니다. 다음 넌터미널 함수는 *C++ 언어 레퍼런스*의 [어휘 규칙](../cpp/lexical-conventions.md) 섹션에 정의되어 있습니다:

`constant`, *constant-expression*, *identifier*, *keyword*, `operator`, `punctuator`

선택적 구성 요소는 아래첨자 <sub>opt</sub>로 표시됩니다. 예를 들어 다음은 중괄호로 묶인 선택적 표현식을 나타냅니다.

**{** *표현식*<sub></sub> **}**

## <a name="see-also"></a>참고 항목

[문법 요약(C/C++)](../preprocessor/grammar-summary-c-cpp.md)