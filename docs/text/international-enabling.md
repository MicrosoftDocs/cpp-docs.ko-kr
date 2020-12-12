---
description: '자세히 알아보기: 국가별 설정'
title: 국가별 사용
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
ms.openlocfilehash: 15db7e27b65f4225917945820c936e572fc5da94
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207269"
---
# <a name="international-enabling"></a>국가별 사용

대부분의 기존 C 및 c + + 코드는 국가별 응용 프로그램에서 제대로 작동 하지 않는 문자 및 문자열 조작에 대 한 가정을 만듭니다. MFC와 런타임 라이브러리는 모두 유니코드 또는 MBCS를 지원 하지만 여전히 작업을 수행할 수 있습니다. 이 섹션에서는 Visual C++의 "국가별 설정"의 의미에 대해 설명 합니다.

- 유니코드와 MBCS는 모두 MFC 함수 매개 변수 목록 및 반환 형식에서 이식 가능한 데이터 형식으로 설정 됩니다. 이러한 형식은 빌드에서 기호 `_UNICODE` 또는 기호 (DBCS)를 정의 하는지 여부에 따라 적절 한 방법으로 조건부로 정의 됩니다 `_MBCS` . 빌드에서 정의 하는 이러한 두 기호에 따라 MFC 라이브러리의 여러 변형이 응용 프로그램에 자동으로 연결 됩니다.

- 클래스 라이브러리 코드는 이식 가능한 런타임 함수와 기타 방법을 사용 하 여 올바른 유니코드 또는 MBCS 동작을 보장 합니다.

- 여전히 코드에서 특정 유형의 국제화 작업을 처리 해야 합니다.

  - 두 환경에서 MFC를 이식 가능 하 게 하는 동일한 이식 가능한 런타임 함수를 사용 합니다.

  - 매크로를 사용 하 여 두 환경에서 리터럴 문자열 및 문자를 이식 가능 하 게 만듭니다 `_T` . 자세한 내용은 [tchar.h의 제네릭 텍스트 매핑](../text/generic-text-mappings-in-tchar-h.md)을 참조 하세요.

  - MBCS를 사용 하 여 문자열을 구문 분석할 때는 예방 조치를 취해야 합니다. 이러한 예방 조치는 유니코드에서 필요 하지 않습니다. 자세한 내용은 [MBCS 프로그래밍 팁](../text/mbcs-programming-tips.md)을 참조 하세요.

  - 응용 프로그램에서 ANSI (8 비트)와 유니코드 (16 비트) 문자를 혼합 하 여 사용 하는 경우 주의 해야 합니다. 프로그램의 일부에 ANSI 문자를 사용 하 고 다른 부분에서는 유니코드 문자를 사용할 수 있지만 동일한 문자열에서 혼합할 수 없습니다.

  - 응용 프로그램에서 문자열을 하드 코딩 하지 마십시오. 대신 응용 프로그램의 .rc 파일에 추가 하 여이를 STRINGTABLE 리소스로 만듭니다. 그러면 소스 코드를 변경 하거나 다시 컴파일하지 않아도 응용 프로그램을 지역화할 수 있습니다. STRINGTABLE 리소스에 대 한 자세한 내용은 [문자열 편집기](../windows/string-editor.md)를 참조 하십시오.

> [!NOTE]
> 유럽 및 MBCS 문자 집합에는 문자 코드가 0x80 보다 큰 일부 문자가 포함 됩니다 (예: 악센트가 있는 문자). 대부분의 코드는 부호 있는 문자를 사용 하기 때문에 0x80 보다 큰 이러한 문자는로 변환 될 때 부호가 확장 됩니다 **`int`** . 이는 부호 확장 문자가 음수 이며 배열 외부의 인덱스 이기 때문에 배열 인덱싱에 문제가 발생 합니다. MBCS를 사용 하는 언어 (예: 일본어)도 고유 합니다. 문자는 1 또는 2 바이트로 구성 될 수 있으므로 항상 두 바이트를 동시에 모두 조작 해야 합니다.

## <a name="see-also"></a>참고 항목

[유니코드 및 멀티바이트 문자 집합(MBCS)](../text/unicode-and-mbcs.md)<br/>
[국제화 전략](../text/internationalization-strategies.md)
