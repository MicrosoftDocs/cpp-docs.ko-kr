---
description: '자세히 알아보기: 국제화 전략'
title: 국제화 전략
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- language-portable code [C++]
- MBCS [C++], internationalization strategies
- Windows API [C++], international programming strategies
- Win32 [C++], international programming strategies
- Unicode [C++], globalizing applications
- character sets [C++], international programming strategies
- localization [C++], character sets
ms.assetid: b09d9854-0709-4b9a-a00c-b0b8bc4199b1
ms.openlocfilehash: 51570a3e340a8af0a9f16f8212aa11f6bf3119b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331177"
---
# <a name="internationalization-strategies"></a>국제화 전략

대상 운영 체제 및 시장에 따라 다음과 같은 여러 가지 국제화 전략이 있습니다.

- 응용 프로그램에서 유니코드를 사용 합니다.

   유니코드 관련 기능을 사용 하 고 모든 문자는 16 비트 너비입니다 (특수 목적으로 프로그램의 일부 부분에서 ANSI 문자를 사용할 수 있음). C 런타임 라이브러리는 유니코드 전용 프로그래밍에 대 한 함수, 매크로 및 데이터 형식을 제공 합니다. MFC는 완전히 유니코드를 사용할 수 있습니다.

- 응용 프로그램은 MBCS를 사용 하며 모든 Win32 플랫폼에서 실행할 수 있습니다.

   MBCS 관련 기능을 사용 합니다. 문자열에는 싱글바이트 문자, 더블 바이트 문자 또는 둘 다를 사용할 수 있습니다. C 런타임 라이브러리는 MBCS 전용 프로그래밍에 대 한 함수, 매크로 및 데이터 형식을 제공 합니다. MFC는 완전히 MBCS를 사용할 수 있습니다.

- 응용 프로그램에 대 한 소스 코드는 전체 이식성을 위해 작성 되었습니다. 즉, 기호 또는 기호를 정의 하 여 다시 컴파일하면 `_UNICODE` `_MBCS` 하나를 사용 하는 버전을 생성할 수 있습니다. 자세한 내용은 [tchar.h의 제네릭 텍스트 매핑](../text/generic-text-mappings-in-tchar-h.md)을 참조 하세요.

   완전히 이식 가능한 C 런타임 함수, 매크로 및 데이터 형식을 사용 합니다. MFC의 유연성이 이러한 전략을 지원 합니다.

이러한 항목의 나머지 부분에서는 유니코드 나 MBCS로 빌드할 수 있는 완전히 이식 가능한 코드를 작성 하는 데 중점을 둡니다.

## <a name="see-also"></a>참고 항목

[유니코드 및 멀티바이트 문자 집합(MBCS)](../text/unicode-and-mbcs.md)<br/>
[로캘 및 코드 페이지](../text/locales-and-code-pages.md)
