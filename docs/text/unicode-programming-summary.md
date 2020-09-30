---
title: 유니코드 프로그래밍 요약
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], programming with
- Unicode [C++], MFC and C run-time functions
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
ms.openlocfilehash: 5095e1c58db3e5c35eb9215367f2fbb064bc228a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504710"
---
# <a name="unicode-programming-summary"></a>유니코드 프로그래밍 요약

유니코드에 대 한 MFC 및 C 런타임 지원을 활용 하려면 다음을 수행 해야 합니다.

- `_UNICODE`을 정의 합니다.

   프로그램을 빌드하기 전에 기호를 정의 `_UNICODE` 합니다.

- 진입점을 지정 하십시오.

   프로젝트의 [속성 페이지](../build/reference/property-pages-visual-cpp.md) 대화 상자에 있는 **링커** 폴더의 **고급** 페이지에서 **진입점** 기호를로 설정 `wWinMainCRTStartup` 합니다.

- 이식 가능한 런타임 함수 및 형식을 사용 합니다.

   유니코드 문자열 처리에 적절 한 C 런타임 함수를 사용 합니다. `wcs`함수 패밀리를 사용할 수 있지만 완전히 이식 가능한 (국제적으로 설정 된) 매크로를 사용 하는 것이 좋습니다 `_TCHAR` . 이러한 매크로는 모두 접두사로 사용 되며 `_tcs` `str` 함수 패밀리에 대해 하나를 대체 합니다. 이러한 함수는 *런타임 라이브러리 참조*의 [국제화](../c-runtime-library/internationalization.md) 섹션에 자세히 설명 되어 있습니다. 자세한 내용은 [tchar.h의 제네릭 텍스트 매핑](../text/generic-text-mappings-in-tchar-h.md)을 참조 하세요.

   `_TCHAR`및 [유니코드 지원](../text/support-for-unicode.md)에 설명 된 관련 이식 가능한 데이터 형식을 사용 합니다.

- 리터럴 문자열을 올바르게 처리 합니다.

   Visual C++ 컴파일러는로 코딩 된 리터럴 문자열을 해석 합니다.

    ```cpp
    L"this is a literal string"
    ```

   유니코드 문자 문자열을 의미 합니다. 리터럴 문자에 동일한 접두사를 사용할 수 있습니다. `_T`일반적으로 매크로를 사용 하 여 리터럴 문자열을 코딩 합니다. 유니코드 문자열 또는 유니코드를 사용 하지 않는 ANSI 문자열 (MBCS 포함)로 컴파일합니다. 예를 들어 다음 식을 사용하는 대신

    ```cpp
    pWnd->SetWindowText( "Hello" );
    ```

   사용

    ```cpp
    pWnd->SetWindowText( _T("Hello") );
    ```

   가 `_UNICODE` 정의 된 경우 `_T` 리터럴 문자열을 l 접두사가 붙은 형식으로 변환 하 고, 그렇지 않으면 `_T` l 접두사 없이 문자열을 변환 합니다.

    > [!TIP]
    >  매크로는 `_T` 매크로와 동일 `_TEXT` 합니다.

- 문자열 길이를 함수에 전달 하는 것이 주의 해야 합니다.

   일부 함수는 문자열의 문자 수를 사용할 수 있습니다. 나머지는 바이트 수를 원합니다. 예를 들어 `_UNICODE` 가 정의 된 경우 개체에 대 한 다음 호출이 `CArchive` 작동 하지 않습니다 ( `str` 는 `CString` ).

    ```cpp
    archive.Write( str, str.GetLength( ) );    // invalid
    ```

   유니코드 응용 프로그램에서 길이는 문자 수를 제공 하지만, 각 문자는 너비가 2 바이트 이기 때문에 올바른 바이트 수를 제공 하지 않습니다. 대신 다음을 사용 해야 합니다.

    ```cpp
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid
    ```

   쓸 바이트 수를 지정 합니다.

   그러나 바이트 지향적이 아니라 문자 지향적인 MFC 멤버 함수는이 추가 코딩 없이도 작동 합니다.

    ```cpp
    pDC->TextOut( str, str.GetLength( ) );
    ```

   `CDC::TextOut` 는 바이트 수가 아닌 많은 문자를 사용 합니다.

- [Fopen_s _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) 를 사용 하 여 유니코드 파일을 엽니다.

요약 하자면, MFC 및 런타임 라이브러리는 유니코드 프로그래밍에 대 한 다음 지원을 제공 합니다.

- 데이터베이스 클래스 멤버 함수를 제외 하 고 모든 MFC 함수는를 포함 하 여 유니코드를 사용 `CString` 합니다. `CString` 는 유니코드/ANSI 변환 함수도 제공 합니다.

- 런타임 라이브러리는 모든 문자열 처리 함수의 유니코드 버전을 제공 합니다. 또한 런타임 라이브러리는 유니코드 또는 MBCS에 적합 한 이식 가능한 버전을 제공 합니다. 이러한 매크로는 다음과 같습니다 `_tcs` .

- tchar.h는 이식 가능한 데이터 형식 및 리터럴 문자열과 문자를 변환 하는 매크로를 제공 합니다 `_T` . 자세한 내용은 [tchar.h의 제네릭 텍스트 매핑](../text/generic-text-mappings-in-tchar-h.md)을 참조 하세요.

- 런타임 라이브러리는의 와이드 문자 버전을 제공 합니다 `main` . `wmain`를 사용 하 여 응용 프로그램을 유니코드를 인식 하도록 합니다.

## <a name="see-also"></a>참고 항목

[유니코드 지원](../text/support-for-unicode.md)
