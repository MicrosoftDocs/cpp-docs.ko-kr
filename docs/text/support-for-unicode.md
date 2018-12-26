---
title: 유니코드 지원
ms.date: 1/09/2018
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
ms.openlocfilehash: fea49bff2a4563b8617e19636e27afbae1c55811
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501688"
---
# <a name="support-for-unicode"></a>유니코드 지원

유니코드는 1바이트만으로는 표현할 수 없는(대부분의 경우에 해당) 모든 문자 집합을 지원합니다. 전 세계를 대상으로 배포할 애플리케이션을 프로그래밍하는 경우 유니코드나 [멀티바이트 문자 집합(MBCS, Multibyte character set)](../text/support-for-multibyte-character-sets-mbcss.md) 중 하나를 사용하거나 스위치를 변경하여 두 가지 모두를 위해 빌드할 수 있도록 개발하는 것을 추천합니다.

와이드 문자는 2바이트 다국어 문자 코드입니다. 기술 기호 및 특별한 게시 문자를 포함하여 전 세계의 현대적인 컴퓨팅 환경에서 사용되는 거의 모든 문자열을 구성하는 수만 개의 문자는 UTF-16을 사용하여 인코딩된 하나의 와이드 문자로 유니코드 사양에 따라 표현될 수 있습니다. 하나의 와이드 문자로 표현할 수 없는 문자는 유니코드 서로게이트 쌍(Unicode surrogate pair)을 이용하여 하나의 유니코드 쌍으로 표현할 수 있습니다. 일반적으로 사용되는 거의 모든 문자가 하나의 16비트 크기의 와이드 문자 UTF-16으로 표현되므로, 와이드 문자를 사용하면 국가별 문자 집합을 사용하는 프로그래밍을 단순화시킬 수 있습니다. 리틀엔디안(Little endian)용인 UTF-16LE를 사용하여 인코딩된 와이드 문자는 Windows용 기본 문자 형식입니다.

와이드 문자열은 `wchar_t[]` 배열로 표현되며 `wchar_t*` 포인터가 가리킵니다. 모든 ASCII 문자는 문자 앞에 접두사로 문자 L을 붙여 와이드 문자로 표현할 수 있습니다. 예를 들어, L'\ \0'는 NULL 종결 와이드 (16 비트) 문자입니다. 마찬가지로, ASCII 문자열 리터럴은 ASCII 리터럴에 접두사로 문자 L을 붙여(예: L"Hello") 와이드 문자열 리터럴로 표현할 수 있습니다.

일반적으로 와이드 문자는 멀티바이트 문자보다 더 많은 메모리 공간을 차지하지만 처리 속도는 더 빠릅니다. 뿐만 아니라, 멀티바이트 인코딩에서는 한 번에 하나의 로캘만 표현할 수 있는 반면, 유니코드는 세계의 모든 문자 집합을 동시에 표현할 수 있습니다.

MFC 프레임워크 전체에서 유니코드를 사용할 수 있으며 MFC에서는 다음 테이블에 표시된 것처럼 이식 가능한 매크로를 사용하여 유니코드를 사용할 수 있습니다.

## <a name="portable-data-types-in-mfc"></a>MFC의 이식 가능한 데이터 형식

|이식 불가능한 데이터 형식|다음 매크로로 바뀜|
|-----------------------------|----------------------------|
|`char`, `wchar_t`|`_TCHAR`|
|`char*``LPSTR` (Win32 데이터 형식) `LPWSTR`|`LPTSTR`|
|`const char*``LPCSTR` (Win32 데이터 형식) `LPCWSTR`|`LPCTSTR`|

클래스 `CString` 사용 하 여 `_TCHAR` 기준으로 하 고 쉬운 변환을 위해 생성자 및 연산자를 제공 합니다. 유니코드에 대한 대부분의 문자열 작업은 Windows ANSI 문자 집합을 처리하는 데 사용되는 것과 동일한 논리를 사용하여 작성할 수 있습니다. 이러한 논리는 작업의 기본 단위가 8비트 바이트 대신 16비트 문자라는 점이 다릅니다. 멀티바이트 문자 집합을 사용하는 것과 달리 유니코드 문자를 별도의 2바이트인 것처럼 처리할 필요가 없습니다. 그러나 가능성을 와이드 문자 서로게이트 쌍으로 표현 하는 단일 문자를 사용 하 여 처리를 수행 해야 합니다. 일반적으로 반각 또는 전각에 포함 되어 있는지 여부를 문자열의 길이 문자의 번호와 동일을 가정 하는 코드를 쓰지 않습니다.

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [MFC의 유니코드 및 멀티 바이트 문자 집합 (MBCS) 지원 사용](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [프로그램에서 유니코드 사용](../text/international-enabling.md)

- [프로그램에서 유니코드 및 MBCS를 사용하도록 설정](../text/internationalization-strategies.md)

- [유니코드를 사용하여 국제화된 프로그램을 만들려면](../text/unicode-programming-summary.md)

- [유니코드의 이점에 대하여 알아봅니다](../text/benefits-of-character-set-portability.md)

- [와이드 문자 인수를 프로그램에 전달할 수 있도록 wmain 사용하기](../text/support-for-using-wmain.md)

- [유니코드 프로그래밍 요약 보기](../text/unicode-programming-summary.md)

- [바이트 크기에 따른 이식성을 고려한 일반 텍스트 매핑에 대해 알아보기](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>참고자료

[텍스트 및 문자열](../text/text-and-strings-in-visual-cpp.md)<br/>
[wmain 사용 지원](../text/support-for-using-wmain.md)