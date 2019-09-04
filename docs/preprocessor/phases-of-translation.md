---
title: 변환 단계
ms.date: 08/29/2019
helpviewer_keywords:
- translation phases
- preprocessor, translation
- translation, compiler process
- preprocessor
- file translation [C++], compiler process
- files [C++], translation
ms.assetid: a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db
ms.openlocfilehash: d072c9aec48d815ba85f8a12576baa6447703f8c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218299"
---
# <a name="phases-of-translation"></a>변환 단계

C 및 C++ 프로그램은 프로그램을 구성하는 개발 코드가 있는 하나 이상의 소스 파일로 구성됩니다. *포함 파일*, `#include` 전처리기 지시문을 사용 하 여 포함 된 파일,와 `#if`같은 조건부 컴파일 지시문에 의해 제거 된 코드 섹션을 포함 하지 않는 소스 파일을 라고 합니다.  *변환 단위*입니다.

원본 파일은 서로 다른 시간에 번역할 수 있습니다. 실제로 오래 된 파일만 변환 하는 것이 일반적입니다. 번역처리가 된 변환 단위는 각각의 개체 파일(Object file) 또는 개체 코드 라이브러리(Object-code Library)로 처리됩니다. 이렇게 분리된 변환 단위는 링크되어 실행 가능 프로그램 또는 동적 연결 라이브러리(DLL)가 됩니다. 링커에 대 한 입력으로 사용할 수 있는 파일에 대 한 자세한 내용은 [링크 입력 파일](../build/reference/link-input-files.md)을 참조 하세요.

변환 단위는 다음을 사용하여 통신할 수 있습니다.

- 외부 링크가 있는 함수를 호출합니다.

- 외부 링크가 있는 클래스 멤버 함수를 호출합니다.

- 외부 링크가 있는 개체를 직접 수정합니다.

- 파일을 직접 수정합니다.

- 프로세스 간에 통신합니다(Microsoft Windows 기반 응용 프로그램만 해당).

다음 목록은 컴파일러가 파일을 변환하는 단계를 나타냅니다.

*문자 매핑*\
소스 파일 내의 문자는 내부 소스 표현과 매핑됩니다. 삼중자 시퀀스는 이 단계에서 단일 문자 내부 표현으로 변환됩니다.

*줄 스플라이스*\
백슬래시 ( **\\** ) 뒤에 줄 바꿈 문자가 오는 모든 줄은 소스 파일의 다음 줄과 결합 되어 실제 줄에서 논리적 줄을 형성 합니다. 비어 있지 않으면 소스 파일은 백슬래시가 앞에 오지 않는 줄 바꿈 문자로 끝나야 합니다.

*토큰화*\
소스 파일은 전처리 토큰과 공백 문자로 나뉩니다. 소스 파일의 주석은 하나의 공백 문자로 대체됩니다. 개행 문자는 그대로 유지됩니다.

*바꾸면*\
전처리 지시문이 실행되고 매크로는 소스 파일에 적용됩니다. `#include` 문으로 포함된 모든 내용은 앞 세 가지 변환 단계로 시작하는 변환을 호출합니다.

*문자 집합 매핑*\
모든 문자 집합 멤버와 이스케이프 시퀀스는 실행 문자 집합에서 동등하게 변환됩니다. Microsoft C 및 C++의 경우 소스 및 실행 문자 집합 모두 ASCII입니다.

*문자열 연결*\
모든 인접한 문자열과 와이드 타입의 문자열 리터럴은 연결됩니다. 예를 들어, `"String " "concatenation"` 문자열은 `"String concatenation"`과 같이 연결됩니다.

*변환*\
모든 토큰은 구문적 그리고 의미적으로 분석됩니다. 이러한 토큰은 개체 코드로 변환됩니다.

*링크*\
모든 외부 참조는 실행 프로그램 또는 동적 연결 라이브러리를 만들기 위해 확인됩니다.

컴파일러에서 구문 오류가 발생하는 변환 단계 중 경고 또는 오류가 발생합니다.

링커는 모든 외부 참조를 확인하고 표준 라이브러리에 따라 하나 이상의 별도 처리되는 변환 단위를 결합하여 DLL 또는 실행 프로그램을 만듭니다.

## <a name="see-also"></a>참고자료

[전처리기](../preprocessor/preprocessor.md)
