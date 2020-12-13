---
description: '자세한 정보: 매크로 (C/c + +)'
title: 매크로 (C/C++)
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- preprocessor, macros
- Visual C++, preprocessor macros
ms.assetid: a7bfc5d4-2537-4fe0-bef0-70cec0b43388
ms.openlocfilehash: 460fd993ae27ab2603c3d2f832481c07713f4f98
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333413"
---
# <a name="macros-cc"></a>매크로 (C/C++)

전처리기는 *전처리기 지시문* 을 제외한 모든 줄에서 매크로를 확장 하 고, 첫 번째 공백이 아닌 문자를 포함 하는 줄을 포함 **#** 합니다. 조건부 컴파일의 일부로 건너뛰지 않는 일부 지시문의 일부에서 매크로를 확장 합니다. *조건부 컴파일 지시문* 을 사용 하면 소스 파일의 일부에 대 한 컴파일을 표시 하지 않을 수 있습니다. 상수 식 또는 식별자를 테스트 하 여 컴파일러에 전달할 텍스트 블록과 전처리 중에 소스 파일에서 제거할 텍스트 블록을 결정 합니다.

`#define` 지시문은 일반적으로 의미 있는 식별자와 자음, 키워드, 자주 사용되는 명령문 또는 수식과 연결하는 데 사용합니다. 상수를 나타내는 식별자는 기호화 된 *상수* 또는 *매니페스트 상수* 라고도 합니다. 문이나 식을 나타내는 식별자를 *매크로* 라고 합니다. 이 전처리기 설명서에서는 "매크로" 용어만 사용됩니다.

프로그램 소스 텍스트 또는 다른 전처리기 명령의 인수에서 매크로 이름이 인식 되 면 해당 매크로에 대 한 호출로 처리 됩니다. 매크로 이름은 매크로 본문의 복사본으로 교체됩니다. 매크로에서 인수를 수락할 경우 매크로 이름 다음의 실제 인수가 매크로 본문의 정식 매개 변수 대신 사용됩니다. 매크로 호출을 본문의 처리 된 복사본으로 바꾸는 프로세스를 매크로 호출의 *확장* 이라고 합니다.

실질적으로 두 가지 유형의 매크로가 있습니다. *개체와 유사한* 매크로는 인수를 사용 하지 않습니다. *함수 호출 매크로는* 함수 호출 처럼 표시 되 고 작동 하도록 인수를 허용 하도록 정의할 수 있습니다. 매크로가 실제 함수 호출을 생성 하지 않기 때문에 함수 호출을 매크로로 바꿔서 프로그램의 실행 속도를 높일 수 있습니다. C + +에서 인라인 함수는 종종 선호 되는 방법입니다. 그러나 매크로를 정의 하 고 사용 하지 않는 경우에는 문제가 발생할 수 있습니다. 괄호 안에 인수를 갖는 매크로 정의의 식에 적절한 우선 순위를 유지하기 위해 사용할 수 있습니다. 또한 매크로는 파생 작업이 있는 식을 올바르게 처리할 수 없습니다. 자세한 내용은 `getrandom` [#define 지시문](../preprocessor/hash-define-directive-c-cpp.md)의 예제를 참조 하세요.

매크로를 정의한 후에는 원래 정의를 먼저 제거 하지 않고 다른 값으로 다시 정의할 수 없습니다. 하지만 매크로를 정확히 동일한 정의로 재정의할 수 있습니다. 따라서 동일한 정의가 프로그램에서 두 번 이상 나타날 수 있습니다.

`#undef`지시문은 매크로의 정의를 제거 합니다. 정의를 제거한 후에는 매크로를 다른 값으로 다시 정의할 수 있습니다. [#Define 지시문](../preprocessor/hash-define-directive-c-cpp.md) 과 [#undef 지시문](../preprocessor/hash-undef-directive-c-cpp.md) 은 `#define` `#undef` 각각 및 지시문을 설명 합니다.

자세한 내용은 다음 항목을 참조하세요.

- [매크로 및 C++](../preprocessor/macros-and-cpp.md)

- [Variadic 매크로](../preprocessor/variadic-macros.md)

- [미리 정의된 매크로](../preprocessor/predefined-macros.md)

## <a name="see-also"></a>참고 항목

[C/C++ 전처리기 참조](../preprocessor/c-cpp-preprocessor-reference.md)
