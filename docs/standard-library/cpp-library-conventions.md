---
description: '자세한 정보: c + + 라이브러리 규칙'
title: C++ 라이브러리 규칙
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, conventions
- classes [C++]
- functions [C++], library naming conventions
- naming conventions [C++], C++ Standard Library
- conventions [C++], C++ Standard Library
- function names [C++]
- coding conventions, C++ Standard Library
- naming conventions [C++], C++ library
ms.assetid: bf41b79a-2d53-4f46-8d05-779358335146
ms.openlocfilehash: 4426996b7420c056a964378655c72c43b99fcf97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233372"
---
# <a name="c-library-conventions"></a>C++ 라이브러리 규칙

C++ 라이브러리는 표준 C 라이브러리와 동일한 규칙 외에도 여기에 설명된 몇 가지 추가 규칙도 적절히 준수합니다.

구현 시에는 C++ 라이브러리의 형식 및 함수를 선언하는 방법과 관련하여 다음과 같은 약간의 자유재량도 있습니다.

- 표준 C 라이브러리의 함수 이름에는 extern "c + +" 또는 extern "C" 링크가 있을 수 있습니다. 라이브러리 엔터티 인라인을 선언하지 않고 적절한 표준 C 헤더를 포함합니다.

- 이 문서에 나열된 함수 시그니처 이상의 추가 함수 시그니처가 라이브러리 클래스의 멤버 함수 이름에 있을 수 있습니다. 여기에 설명된 함수 호출이 예상대로 동작할 것을 확신할 수 있지만, 라이브러리 멤버 함수의 주소를 안정적으로 가져올 수는 없습니다. 형식이 예상과 다를 수 있습니다.

- 라이브러리 클래스가 기본 클래스(비가상)를 문서화하지 않을 수 있습니다. 다른 클래스에서 파생되는 것으로 문서화된 클래스가 실제로 문서화되지 않은 다른 클래스를 통해 해당 클래스에서 파생될 수 있습니다.

- 일부 정수 형식에 대한 동의어로 정의된 형식이 다른 여러 정수 형식 중 하나와 동일할 수 있습니다.

- 비트 마스크 형식이 정수 형식 또는 열거형으로 구현될 수 있습니다. 어떠한 경우에도 동일한 비트 마스크 형식의 값에 대해 비트 연산(예: `AND` 및 `OR`)을 수행할 수 있습니다. 비트 마스크 형식의 요소 `A` 및 `B`는 `A` & `B`가 0이 되도록 0이 아닌 값입니다.

- 예외 사양이 없는 라이브러리 함수는 해당 정의가 이러한 가능성을 명확하게 제한하지 않는 한 임의의 예외를 throw할 수 있습니다.

반면에 다음과 같은 몇 가지 제한 사항이 있습니다.

- 표준 C 라이브러리에서 마스킹 매크로를 사용하지 않습니다. 함수 자체의 이름이 아니라 특정 함수 시그니처만 예약됩니다.

- 클래스 외부의 라이브러리 함수 이름에는 문서화되지 않은 추가 함수 시그니처가 없습니다. 해당 주소를 안정적으로 가져올 수 있습니다.

- 가상으로 설명된 기본 클래스 및 멤버 함수는 확실히 가상이고, 비가상으로 설명된 기본 클래스 및 멤버 함수는 확실히 비가상입니다.

- 이 문서에서 달리 명시적으로 제시하지 않는 한 C++ 라이브러리로 정의된 두 가지 형식은 항상 서로 다릅니다.

- 대체 가능한 함수의 기본 버전을 비롯하여 라이브러리에서 제공한 함수는 *최대한* 모든 예외 사양에 나열된 해당 예외를 throw할 수 있습니다. 라이브러리에서 제공한 소멸자는 예외를 throw하지 않습니다. 표준 C 라이브러리의 함수는 `qsort`에서 예외를 throw하는 비교 함수를 호출할 때와 같이 예외를 전파할 수 있지만, 예외를 throw하지는 않습니다.

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리 개요](../standard-library/cpp-standard-library-overview.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
