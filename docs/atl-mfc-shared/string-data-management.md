---
description: '자세한 정보: 문자열 데이터 관리'
title: 문자열 데이터 관리
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: 37a3a13dc58641cc23e8ea5c31e12a4d4d9582fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166514"
---
# <a name="string-data-management"></a>문자열 데이터 관리

Visual C++는 문자열 데이터를 관리 하는 여러 가지 방법을 제공 합니다.

- C 스타일의 null로 끝나는 문자열을 사용 하기 위한 [문자열 조작](../c-runtime-library/string-manipulation-crt.md)

- 문자열 관리를 위한 Win32 API 함수

- 유연 하 고 크기 조정 가능한 문자열 개체를 제공 하는 MFC 클래스의 [CStringT 클래스](../atl-mfc-shared/reference/cstringt-class.md)

- 클래스와 동일한 기능을 사용 하 여 MFC 독립 문자열 [개체를 제공](../atl-mfc-shared/reference/cstringt-class.md)하는 클래스 클래스 `CString`

거의 모든 프로그램은 문자열 데이터로 작동 합니다. MFC의 `CString` 클래스는 대개 유연한 문자열 처리를 위한 최상의 솔루션입니다. 버전 7.0부터, `CString` mfc 또는 mfc 독립 프로그램에서 사용할 수 있습니다. 런타임 라이브러리와는 모두 `CString` 유니코드 또는 MBCS 프로그래밍과 같이 멀티 바이트 문자를 포함 하는 문자열을 지원 합니다.

이 문서에서는 클래스 라이브러리가 문자열 조작과 관련 하 여 제공 하는 범용 서비스에 대해 설명 합니다. 이 문서에서 다루는 항목은 다음과 같습니다.

- [유니코드 및 MBCS에서 이식성 제공](#_core_unicode_and_mbcs_provide_portability)

- [CStrings 및 const char 포인터](#_core_cstrings_and_const_char_pointers)

- [CString 참조 계산](#_core_cstring_reference_counting)

[CStringT 클래스](../atl-mfc-shared/reference/cstringt-class.md) 클래스는 문자열 조작을 지원 합니다. C 런타임 라이브러리 문자열 패키지에서 일반적으로 제공 하는 기능을 대체 하 고 확장 하기 위한 것입니다. `CString`클래스는 Basic에서 발견 된 것과 비슷한 간소화 된 문자열 처리를 위한 멤버 함수 및 연산자를 제공 합니다. 또한 클래스는 `CString` 및 표준 c + + 문자열 데이터 형식을 생성, 할당 및 비교 하기 위한 생성자와 연산자를 제공 합니다. `CString`는에서 파생 되지 않으므로 `CObject` `CString` 대부분의 MFC 라이브러리 (MFC)와는 독립적으로 개체를 사용할 수 있습니다.

`CString` 개체는 "값 의미 체계"를 따릅니다. `CString`개체는 고유한 값을 나타냅니다. 는 `CString` 문자열에 대 한 포인터가 아닌 실제 문자열로 간주 됩니다.

`CString`개체는 가변 문자 수의 시퀀스를 나타냅니다. `CString` 개체는 문자 배열로 간주할 수 있습니다.

## <a name="unicode-and-mbcs-provide-portability"></a><a name="_core_unicode_and_mbcs_provide_portability"></a> 유니코드 및 MBCS에서 이식성 제공

MFC 버전 3.0 이상에서는 `CString` 유니코드 및 MBCS (멀티 바이트 문자 집합) 모두에를 포함 하 여 mfc를 사용할 수 있습니다. 이러한 지원을 통해 유니코드 또는 ANSI 문자에 대해 빌드할 수 있는 이식 가능한 응용 프로그램을 쉽게 작성할 수 있습니다. 이러한 이식성을 사용 하도록 설정 하기 위해 개체의 각 문자 `CString` 는 tchar.h 형식입니다 .이 형식은 **`wchar_t`** 응용 프로그램을 빌드할 때 _UNICODE 기호를 정의 하는 것 처럼 정의 되 고 그렇지 않은 경우로 정의 됩니다 **`char`** . **`wchar_t`** 문자는 16 비트 너비입니다. _MBCS 정의 된 기호를 사용 하 여 빌드하면 MBCS를 사용할 수 있습니다. MFC 자체는 _MBCS 기호 (NAFX 라이브러리의 경우) 또는 정의 된 _UNICODE 기호 (UAFX 라이브러리의 경우) 중 하나를 사용 하 여 빌드됩니다.

> [!NOTE]
> `CString`이 문서의 예제 및 문자열에 대 한 해당 문서의 예제에서는 리터럴 문자열을 형식으로 변환 하는 _T 매크로를 사용 하 여 유니코드 이식성을 위해 올바른 형식의 리터럴 문자열을 보여 줍니다.

`L"literal string"`

> [!NOTE]
> 컴파일러가 유니코드 문자열로 처리 합니다. 예를 들어, 다음 코드는

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
> _UNICODE 정의 된 경우 유니코드 문자열로 변환 되 고, 그렇지 않으면 ANSI 문자열로 변환 됩니다. 자세한 내용은 [유니코드 및 MBCS (멀티 바이트 문자 집합) 지원](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)문서를 참조 하세요.

`CString`개체는 최대 INT_MAX (2147483647) 자를 저장할 수 있습니다. TCHAR.H 데이터 형식은 개체 내의 개별 문자를 가져오거나 설정 하는 데 사용 됩니다 `CString` . 문자 배열과 달리 클래스에는 `CString` 기본 제공 메모리 할당 기능이 있습니다. 이렇게 하면 `CString` 필요한 경우 개체가 자동으로 증가할 수 있습니다. 즉, `CString` 더 긴 문자열에 맞게 개체를 증가 시키는 것에 대해 걱정할 필요가 없습니다.

## <a name="cstrings-and-const-char-pointers"></a><a name="_core_cstrings_and_const_char_pointers"></a> CStrings 및 const char 포인터

`CString`또한 개체는 리터럴 C 스타일 문자열 ( `PCXSTR` 유니코드 아래에 있지 않은 경우 **const char** 와 동일) 처럼 동작할 수 있습니다 <strong>\*</strong> . [CSimpleStringT:: operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) 변환 연산자를 사용 하면 `CString` 함수 호출에서 문자 포인터에 대 한 개체를 자유롭게 대체할 수 있습니다. **CString (lpcwstr** `pszSrc` **)** 생성자를 사용 하 여 개체에 대 한 문자 포인터를 대체할 수 있습니다 `CString` .

개체를 접기 하려고 하지 않습니다 `CString` . 예를 들어를 포함 하는 두 개의 개체를 만드는 경우 `CString` `Chicago` 의 문자는 `Chicago` 두 위치에 저장 됩니다. 이는 MFC의 이후 버전에는 적용 되지 않을 수 있으므로이에 종속 되지 않아야 합니다.

> [!NOTE]
> 문자에 대 한 비상수 포인터로에 직접 액세스 해야 하는 경우 [CSimpleStringT:: getbuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) 및 [CSimpleStringT:: releasebuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) 멤버 함수를 사용 합니다 `CString` .

> [!NOTE]
> [Cstringt:: allocsysstring](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) 및 [Cstringt:: setsysstring](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) 멤버 함수를 사용 하 여 자동화 (이전의 OLE 자동화)에서 사용 되는 BSTR 개체를 할당 하 고 설정 합니다.

> [!NOTE]
> 가능 하면 `CString` 힙이 아닌 프레임에 개체를 할당 합니다. 이렇게 하면 메모리를 절약 하 고 매개 변수 전달이 간단해 집니다.

`CString` `CString` 개체는 컬렉션의 요소로 저장 될 수 있지만 클래스는 MFC 라이브러리 컬렉션 클래스로 구현 되지 않습니다.

## <a name="cstring-reference-counting"></a><a name="_core_cstring_reference_counting"></a> CString 참조 계산

MFC 버전 4.0을 통해, [CStringT 클래스](../atl-mfc-shared/reference/cstringt-class.md) 개체가 복사 될 때 mfc는 데이터를 복사 하는 대신 참조 횟수를 증가 시킵니다. 이렇게 하면 매개 변수를 값으로 전달 하 고 `CString` 값을 기준으로 개체를 보다 효율적으로 반환할 수 있습니다. 이러한 작업을 수행 하면 복사 생성자가 두 번 이상 호출 됩니다. 참조 횟수를 증가 시키면 이러한 일반 작업에 대 한 오버 헤드가 줄어들고 `CString` 보다 매력적인 옵션을 사용 하 게 됩니다.

각 복사본이 소멸 되 면 원래 개체의 참조 횟수가 감소 합니다. 원본 `CString` 개체의 참조 횟수가 0이 될 때까지 삭제 되지 않습니다.

`CString`멤버 함수 [CSimpleStringT:: lockbuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) 및 [CSimpleStringT:: unlockbuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) 를 사용 하 여 참조 횟수를 사용 하지 않거나 사용 하도록 설정할 수 있습니다.

## <a name="see-also"></a>참고 항목

[일반 MFC 항목](../mfc/general-mfc-topics.md)
