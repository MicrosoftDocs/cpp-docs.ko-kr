---
description: '자세한 정보: 유니코드 및 MBCS (멀티 바이트 문자 집합) 지원'
title: 유니코드 및 멀티바이트 문자 집합(MBCS) 지원
ms.date: 01/09/2017
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
ms.openlocfilehash: 9e9a09777e835872a5c8bc6613460478acf9be9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166410"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>유니코드 및 멀티바이트 문자 집합(MBCS) 지원

일본어 및 중국어와 같은 일부 언어에는 많은 문자 집합이 있습니다. 이러한 시장에 대 한 프로그래밍을 지원 하기 위해 MFC 라이브러리 (MFC)에서는 두 가지 방법으로 대량 문자 집합을 처리할 수 있습니다.

- [유니코드](#mfc-support-for-unicode-strings), **`wchar_t`** 와이드 문자 및 u t f-16으로 인코딩된 문자열

- [MBCS (멀티 바이트 문자 집합)](#mfc-support-for-mbcs-strings), **`char`** 단일 또는 더블 바이트 문자 및 로캘별 문자 집합으로 인코딩된 문자열

Microsoft는 모든 새 개발을 위해 MFC 유니코드 라이브러리를 권장 하며 MBCS 라이브러리는 Visual Studio 2013 및 Visual Studio 2015에서 더 이상 사용 되지 않습니다. 더 이상 그렇지 않습니다. Visual Studio 2017에서 MBCS 사용 중단 경고가 제거 되었습니다.

## <a name="mfc-support-for-unicode-strings"></a>유니코드 문자열에 대 한 MFC 지원

전체 MFC 클래스 라이브러리는 유니코드 문자 및 와이드 문자 (u t f-16)로 저장 된 문자열에 대해 조건부로 사용 됩니다. 특히 [CString](../atl-mfc-shared/reference/cstringt-class.md) 클래스는 유니코드를 사용 하도록 설정 되어 있습니다.

이러한 라이브러리, 디버거 및 DLL 파일은 MFC에서 유니코드를 지 원하는 데 사용 됩니다.

:::row:::
   :::column span="":::
      MFC *버전*..lib \
      MFC *버전* UD. LIB
      MFCM *버전*# .lib \
      MFCM *버전* UD. LIB
      MFCS *버전*# .lib \
      MFCS *버전* UD. LIB
      UAFXCW. LIB
      UAFXCWD. LIB
   :::column-end:::
   :::column span="":::
      MFC *버전* U .pdb \
      MFC *버전* UD. .PDB
      MFCM *버전* U .pdb \
      MFCM *버전* UD. .PDB
      MFCS *버전* U .pdb \
      MFCS *버전* UD. .PDB
      UAFXCW. .PDB
      UAFXCWD. .PDB
   :::column-end:::
   :::column span="":::
      MFC *버전* U.DLL \
      MFC *버전* UD.DLL \
      MFCM *버전* U.DLL \
      MFCM *버전* UD.DLL
   :::column-end:::
:::row-end:::

*버전* 은 파일의 버전 번호를 나타냅니다. 예를 들어 ' 140 '은 버전 14.0을 의미 합니다.

`CString` 는 TCHAR.H 데이터 형식을 기반으로 합니다. 프로그램 빌드에 대 한 기호 _UNICODE 정의 된 경우 TCHAR.H는 **`wchar_t`** 16 비트 문자 인코딩 형식인 형식으로 정의 됩니다. 그렇지 않으면 **`char`** 표준 8 비트 문자 인코딩으로 tchar.h가 정의 됩니다. 따라서 유니코드에서는 `CString` 16 비트 문자로 구성 됩니다. 유니코드를 사용 하지 않으면 형식의 문자로 구성 됩니다 **`char`** .

응용 프로그램의 유니코드 프로그래밍을 완료 하려면 다음을 수행 해야 합니다.

- _T 매크로를 사용 하 여 유니코드로 이식할 리터럴 문자열을 조건부로 코딩 합니다.

- 문자열을 전달 하는 경우 함수 인수에 문자 길이 또는 길이 (바이트)가 필요한 지에 주의 해야 합니다. 유니코드 문자열을 사용 하는 경우 차이점은 중요 합니다.

- 이식 가능한 버전의 C 런타임 문자열 처리 함수를 사용 합니다.

- 문자 및 문자 포인터에는 다음 데이터 형식을 사용 합니다.

  - 사용할 TCHAR.H를 사용 **`char`** 합니다.

  - 사용할 LPTSTR를 사용 **`char`** <strong>\*</strong> 합니다.

  - 을 사용 하는 LPCTSTR를 사용 **`const char`** <strong>\*</strong> 합니다. `CString` 와 LPCTSTR 간에 변환할 LPCTSTR 연산자를 제공 합니다 `CString` .

`CString` 는 유니코드 인식 생성자, 할당 연산자 및 비교 연산자도 제공 합니다.

[런타임 라이브러리 참조](../c-runtime-library/c-run-time-library-reference.md) 는 모든 문자열 처리 함수의 이식 가능한 버전을 정의 합니다. 자세한 내용은 [국제화](../c-runtime-library/internationalization.md)범주를 참조 하세요.

## <a name="mfc-support-for-mbcs-strings"></a>MBCS 문자열에 대 한 MFC 지원

클래스 라이브러리는 멀티 바이트 문자 집합에 대해서도 사용할 수 있지만 DBCS (더블 바이트 문자 집합)에 대해서만 사용할 수 있습니다.

멀티 바이트 문자 집합에서 문자는 1 ~ 2 바이트가 될 수 있습니다. 너비가 2 바이트 이면 사용 중인 코드 페이지에 따라 첫 번째 바이트는 특정 범위에서 선택 되는 특별 한 "선행 바이트"입니다. 선행 및 "후행 바이트"는 고유한 문자 인코딩을 지정 합니다.

프로그램의 빌드에 대 한 기호 _MBCS 정의 된 경우을 기반으로 하는 TCHAR.H를 입력 `CString` 하 고에 매핑합니다 **`char`** . 에서 선행 바이트와 후행 바이트의 바이트를 확인할 수 있습니다 `CString` . C 런타임 라이브러리는이를 결정 하는 데 도움이 되는 함수를 제공 합니다.

DBCS에서 지정 된 문자열은 모든 싱글바이트 ANSI 문자, 모든 더블 바이트 문자 또는 둘의 조합을 포함할 수 있습니다. 이러한 가능성을 위해서는 문자열을 구문 분석할 때 특히 주의 해야 합니다. 여기에는 개체가 포함 됩니다 `CString` .

> [!NOTE]
> MFC의 유니코드 문자열 serialization은 실행 중인 응용 프로그램의 버전에 관계 없이 유니코드 및 MBCS 문자열을 모두 읽을 수 있습니다. 데이터 파일은 프로그램의 유니코드 및 MBCS 버전 간에 이식 가능 합니다.

`CString` 멤버 함수는 호출 하는 C 런타임 함수의 특수 "일반 텍스트" 버전을 사용 하거나 유니코드 인식 함수를 사용 합니다. 따라서 예를 들어 `CString` 함수가 일반적으로를 호출 하는 경우 `strcmp` 해당 제네릭 텍스트 함수를 `_tcscmp` 대신 호출 합니다. _MBCS 및 _UNICODE 기호가 정의 된 방식에 따라은 다음과 같이 `_tcscmp` 매핑됩니다.

|기호|함수|
|-|-|
|_MBCS 정의됨|`_mbscmp`|
|_UNICODE 정의됨|`wcscmp`|
|기호가 정의 되지 않았습니다.|`strcmp`|

> [!NOTE]
> _MBCS 및 _UNICODE 기호는 함께 사용할 수 없습니다.

모든 런타임 문자열 처리 루틴에 대 한 일반 텍스트 함수 매핑은 [C Run-Time 라이브러리 참조](../c-runtime-library/c-run-time-library-reference.md)에 설명 되어 있습니다. 목록은 [국제화](../c-runtime-library/internationalization.md)를 참조 하세요.

마찬가지로 `CString` 메서드는 제네릭 데이터 형식 매핑을 사용 하 여 구현 됩니다. MBCS와 유니코드를 모두 사용 하도록 설정 하기 위해 MFC는 또는에 대해 TCHAR.H를 사용 하 고, 또는에 대해 LPTSTR를 사용 하 **`char`** **`wchar_t`** **`char`** <strong>\*</strong> `wchar_t*` 고, **const char** <strong>\*</strong> 또는에 LPCTSTR `const wchar_t*` MBCS 또는 유니코드에 대 한 올바른 매핑을 보장 합니다.

## <a name="see-also"></a>참고 항목

[문자열 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[문자열 조작](../c-runtime-library/string-manipulation-crt.md)
