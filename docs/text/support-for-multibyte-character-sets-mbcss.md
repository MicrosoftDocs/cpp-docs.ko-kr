---
description: '자세한 정보: 멀티 바이트 문자 집합 지원 (Mbcs)'
title: MBCS(멀티바이트 문자 집합) 지원
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- multibyte characters [C++]
- MBCS [C++]
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
ms.openlocfilehash: 8ab6af7aa77942b39785faf68ea6a530867abff8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335765"
---
# <a name="support-for-multibyte-character-sets-mbcss"></a>MBCS(멀티바이트 문자 집합) 지원

MBCS(멀티바이트 문자 집합)는 일본어 및 중국어와 같이 싱글바이트로 표현할 수 없는 문자 집합을 지원하기 위한 이전의 접근 방식입니다. 새 개발을 수행하는 경우 최종 사용자에게 표시되지 않는 시스템 문자열을 제외한 모든 텍스트 문자열에 유니코드를 사용해야 합니다. MBCS는 이전 기술이며 새로운 개발에는 사용하지 않는 것이 좋습니다.

가장 일반적인 MBCS 구현은 DBCS(더블바이트 문자 집합)입니다. DBCS에 대해 일반적으로 Visual C++ 및 특별히 MFC가 완전히 사용하도록 설정됩니다.

샘플에 대해서는 MFC 소스 코드 파일을 참조하세요.

언어에 큰 문자 집합이 사용되는 지역/국가에서 사용되는 플랫폼의 경우 유니코드 대신 MBCS를 사용하는 것이 가장 좋습니다. MFC에서는 국제화 가능한 데이터 형식 및 C 런타임 함수를 사용하여 MBCS를 지원합니다. 코드에서 같은 작업을 수행해야 합니다.

MBCS에서 문자는 1 또는 2바이트로 인코딩됩니다. 2바이트 문자에서 첫 번째 또는 선행 바이트는 해당 바이트 및 후행 바이트가 한 문자로 해석되도록 신호를 보냅니다. 첫 번째 바이트는 선행 바이트로 사용하도록 예약된 코드 범위에서 가져옵니다. 선행 바이트가 될 수 있는 바이트 범위는 사용 중인 코드 페이지에 따라 다릅니다. 예를 들어 일본어 코드 페이지 932에는 0x81~0x9F 범위가 선행 바이트로 사용되지만, 한국어 코드 페이지 949에는 다른 범위가 사용됩니다.

MBCS 프로그래밍에서는 다음을 모두 고려하세요.

환경에서 mbcs 문자는 파일 및 디렉터리 이름과 같은 문자열에 표시 될 수 있습니다.

### <a name="editing-operations"></a>편집 작업

MBCS 애플리케이션의 편집 작업은 바이트가 아니라 문자 단위로 수행되어야 합니다. 캐럿은 문자를 분할 하지 않아야 합니다. **오른쪽 화살표** 키는 한 문자 오른쪽으로 이동 해야 합니다. **Delete** 는 문자를 삭제 해야 합니다. **실행 취소** 를 다시 삽입 해야 합니다.

### <a name="string-handling"></a>문자열 처리

MBCS를 사용하는 애플리케이션에서 문자열 처리 시 특수한 문제가 발생합니다. 두 너비의 문자는 단일 문자열로 결합되므로 선행 바이트를 확인해야 합니다.

### <a name="run-time-library-support"></a>런타임 라이브러리 지원

C 런타임 라이브러리 및 MFC는 단일 바이트, MBCS 및 유니코드 프로그래밍을 지원합니다. 단일 바이트 문자열은 런타임 함수 제품군을 사용 하 여 처리 되 `str` 고 MBCS 문자열은 해당 함수를 사용 하 여 처리 되며 `_mbs` 유니코드 문자열은 해당 함수를 사용 하 여 처리 됩니다 `wcs` . "MBCS/유니코드 이식성"의 설명대로 MFC 클래스 멤버 함수 구현에는 적합한 환경에서 함수의 일반 `str` 패밀리, MBCS 함수 또는 유니코드 함수에 매핑되는 이식 가능한 런타임 함수가 사용됩니다.

### <a name="mbcsunicode-portability"></a>MBCS/유니코드 이식성

Tchar.h 헤더 파일을 사용 하 여 동일한 원본에서 싱글바이트, MBCS 및 유니코드 응용 프로그램을 빌드할 수 있습니다. Tchar.h는, 또는 함수에 적절 하 게 매핑되는 *_tcs* 접두사가 붙은 매크로를 정의 `str` `_mbs` `wcs` 합니다. MBCS를 빌드하려면 기호를 정의 `_MBCS` 합니다. 유니코드를 빌드하려면 기호를 정의 `_UNICODE` 합니다. 기본적으로 `_UNICODE` 는 MFC 응용 프로그램에 대해 정의 됩니다. 자세한 내용은 [tchar.h의 제네릭 텍스트 매핑](../text/generic-text-mappings-in-tchar-h.md)을 참조 하세요.

> [!NOTE]
> 및를 둘 다 정의 하는 경우 동작이 정의 되지 않습니다 `_UNICODE` `_MBCS` .

Mbctype.h 및 Mbstring.h 헤더 파일에서는 특정 경우에 필요할 수 있는 MBCS 특정 함수 및 매크로를 정의합니다. 예를 들어 `_ismbblead`는 문자열의 특정 바이트가 선행 바이트인지를 알립니다.

국제 이식성을 위해 [유니코드](../text/support-for-unicode.md) 또는 mbcs (멀티 바이트 문자 집합)를 사용 하 여 프로그램을 코딩 합니다.

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [프로그램에서 MBCS 사용](../text/international-enabling.md)

- [프로그램에서 유니코드 및 MBCS 둘 다 사용](../text/internationalization-strategies.md)

- [MBCS를 사용하여 국제화된 프로그램 만들기](../text/mbcs-programming-tips.md)

- [MBCS 프로그래밍 요약 참조](../text/mbcs-programming-tips.md)

- [바이트 너비 이식성을 위한 제네릭 텍스트 매핑에 대해 알아보기](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>참고 항목

[텍스트 및 문자열](../text/text-and-strings-in-visual-cpp.md)<br/>
[Visual C++에서 MBCS 지원](../text/mbcs-support-in-visual-cpp.md)
