---
title: 변환 단계 | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- translation phases
- preprocessor, translation
- translation, compiler process
- preprocessor
- file translation [C++], compiler process
- files [C++], translation
ms.assetid: a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b72e861b2639b8cf1e2cdf8293461cb8b1a00813
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808740"
---
# <a name="phases-of-translation"></a>변환 단계

C 및 C++ 프로그램은 각각 일부 프로그램의 텍스트를 포함하는 하나 이상의 소스 파일로 구성됩니다. `#include`와 같은 조건부 컴파일에서 제거된 코드 섹션을 제외하고 include 파일(`#if` 전처리기 지시문을 사용하여 포함된 파일)을 포함하는 소스 파일을 "변환 단위"라고 합니다.

소스 파일은 다른 표준 시간대에 변환될 수 있습니다. 일반적으로 오래된 파일만 변환합니다. 변환된 변환 단위는 별도의 개체 파일 또는 개체 코드 라이브러리에서 처리될 수 있습니다. 이러한 별도 변환된 변환 단위는 실행할 수 있는 프로그램 또는 동적 연결 라이브러리(DLL)의 형태로 연결됩니다.  링커에 대 한 입력으로 사용할 수 있는 파일에 대 한 자세한 내용은 참조 하세요. [LINK 입력 파일](../build/reference/link-input-files.md)합니다.

변환 단위는 다음을 사용하여 통신할 수 있습니다.

- 외부 링크가 있는 함수를 호출합니다.

- 외부 링크가 있는 클래스 멤버 함수를 호출합니다.

- 외부 링크가 있는 개체를 직접 수정합니다.

- 파일을 직접 수정합니다.

- 프로세스 간에 통신합니다(Microsoft Windows 기반 응용 프로그램만).

다음 목록은 컴파일러가 파일을 변환하는 단계를 나타냅니다.

*문자 매핑*<br/>
소스 파일 내의 문자는 내부 소스 표현과 매핑됩니다. 삼중자 시퀀스는 이 단계에서 단일 문자 내부 표현으로 변환됩니다.

*줄 결합*<br/>
모든 줄 백슬래시 (**\\**) 바로 뒤에 및 줄 바꿈으로 문자 실제 줄에서 논리적 줄을 형성 하는 소스 파일에 다음 줄과 연결 됩니다. 비어 있지 않은 경우 소스 파일은 백슬래시가 앞에 나오지 않는 줄 바꿈 문자에서 끝나야 합니다.

*토큰화*<br/>
소스 파일은 전처리 토큰 및 공백 문자로 나뉩니다. 소스 파일의 설명은 하나의 공백 문자로 각각 대체됩니다. 줄 바꿈 문자는 그대로 유지됩니다.

*전처리*<br/>
전처리 지시문이 실행되고 매크로는 소스 파일에 확장됩니다. `#include` 문은 포함된 모든 텍스트에서 이전 세 가지 변환 단계로 시작하는 변환을 호출합니다.

*문자 집합 매핑*<br/>
모든 문자 집합 멤버와 이스케이프 시퀀스는 실행 문자 집합에서 동등하게 변환됩니다. Microsoft C 및 C++의 경우 소스 및 실행 문자 집합 모두 ASCII입니다.

*문자열 연결*<br/>
모든 인접 문자열과 와이드 문자열 리터럴은 연결되어 있습니다. 예를 들어, `"String " "concatenation"`은 `"String concatenation"`이 됩니다.

*번역*<br/>
모든 토큰은 구문적 그리고 의미적으로 분석됩니다. 이러한 토큰은 개체 코드로 변환됩니다.

*링크*<br/>
모든 외부 참조는 실행 프로그램 또는 동적 연결 라이브러리를 만들기 위해 확인됩니다.

컴파일러에서 구문 오류가 발생하는 변환 단계 중 경고 또는 오류가 발생합니다.

링커는 모든 외부 참조를 확인하고 표준 라이브러리에 따라 하나 이상의 별도 처리되는 변환 단위를 결합하여 DLL 또는 실행 프로그램을 만듭니다.

## <a name="see-also"></a>참고 항목

[전처리기](../preprocessor/preprocessor.md)