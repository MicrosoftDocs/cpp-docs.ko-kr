---
description: '자세한 정보: CString 사용'
title: CString 사용
ms.date: 06/18/2018
helpviewer_keywords:
- CString objects, C++ string manipulation
- CString objects, reference counting
- CString class (Visual C++)
ms.assetid: ed018aaf-8b10-46f9-828c-f9c092dc7609
ms.openlocfilehash: f0afea345f2a01d66cbb541aa2a6c958c28365a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166397"
---
# <a name="using-cstring"></a>CString 사용

이 섹션의 항목에서는 `CString`을 사용한 프로그래밍 방법에 대해 설명합니다. 클래스에 대 한 참조 설명서 `CString` 는 [CStringT](../atl-mfc-shared/reference/cstringt-class.md)설명서를 참조 하세요.

`CString`을 사용하려면 `atlstr.h` 헤더를 포함합니다.

`CString`, `CStringA` 및 클래스는 `CStringW` 지 원하는 문자 데이터의 형식에 따라 [CStringT](../atl-mfc-shared/reference/cstringt-class.md) 라는 클래스 템플릿의 특수화입니다.

`CStringW`개체는 형식을 포함 **`wchar_t`** 하며 유니코드 문자열을 지원 합니다. `CStringA`개체는 형식을 포함 **`char`** 하며 싱글바이트 및 MBCS (멀티 바이트) 문자열을 지원 합니다. `CString`개체는 **`char`** **`wchar_t`** MBCS 기호 또는 유니코드 기호가 컴파일 타임에 정의 되었는지 여부에 따라 형식 또는 형식을 지원 합니다.

`CString` 개체는 `CStringData` 개체에 문자 데이터를 보관합니다. `CString` NULL로 종료 되는 C 스타일 문자열을 허용 합니다. `CString` 는 더 빠른 성능을 위해 문자열 길이를 추적 하지만 LPCWSTR로의 변환을 지원 하기 위해 저장 된 문자 데이터에 NULL 문자를 유지 합니다. `CString` C 스타일 문자열을 내보낼 때 null 종결자를 포함 합니다. 의 다른 위치에 NULL을 삽입할 수 `CString` 있지만 예기치 않은 결과가 발생할 수 있습니다.

`CAtlString`, `CAtlStringA` 및 `CAtlStringW` 문자열 클래스 집합은 MFC 라이브러리에 연결하지 않고 사용할 수 있습니다(CRT 지원 포함/미포함).

`CString`은 네이티브 프로젝트에 사용됩니다. 관리 코드(C++/CLI) 프로젝트에는 `System::String`을 사용합니다.

`CString`, `CStringA` 또는 `CStringW`에서 현재 제공하는 것보다 많은 기능을 추가하려면 추가 기능이 포함된 `CStringT`를 만들어야 합니다.

다음 코드는 `CString`을 만들어 표준 출력으로 인쇄하는 방법을 보여줍니다.

```cpp
#include <atlstr.h>

int main() {
    CString aCString = CString(_T("A string"));
    _tprintf(_T("%s"), (LPCTSTR) aCString);
}
```

## <a name="in-this-section"></a>섹션 내용

[기본 CString 작업](../atl-mfc-shared/basic-cstring-operations.md)<br/>
C 리터럴 문자열에서 개체를 만들고, `CString`의 개별 문자에 액세스하고, 두 개체를 연결하고, `CString` 개체를 비교하는 작업을 포함한 기본 `CString` 작업을 설명합니다.

[문자열 데이터 관리](../atl-mfc-shared/string-data-management.md)<br/>
`CString`에서 유니코드 및 MBCS를 사용하는 방법을 설명합니다.

[CString 의미 체계](../atl-mfc-shared/cstring-semantics.md)<br/>
`CString` 개체를 사용하는 방법을 설명합니다.

[C 스타일 문자열과 관련 된 CString 작업](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)<br/>
C 스타일의 null로 종료되는 문자열과 같은 `CString` 개체의 콘텐츠를 조작하는 방법을 설명합니다.

[BSTR의 메모리 할당 및 해제](../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)<br/>
BSTR 및 COM 개체에 메모리를 사용 하는 방법을 설명 합니다.

[CString 예외 정리](../atl-mfc-shared/cstring-exception-cleanup.md)<br/>
MFC 3.0 이상에서는 명시적 정리가 더 이상 필요하지 않은 이유에 대해 설명합니다.

[CString 인수 전달](../atl-mfc-shared/cstring-argument-passing.md)<br/>
CString 개체를 함수에 전달하고 함수에서 `CString` 개체를 반환하는 방법을 설명합니다.

[유니코드 및 MBCS (멀티 바이트 문자 집합) 지원](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)<br/>
유니코드 및 MBCS가 지원되도록 MFC를 설정하는 방법을 설명합니다.

## <a name="reference"></a>참조

[CStringT](../atl-mfc-shared/reference/cstringt-class.md)<br/>
`CStringT` 클래스에 대한 참조 정보를 제공합니다.

[CSimpleStringT 클래스](../atl-mfc-shared/reference/csimplestringt-class.md)<br/>
`CSimpleStringT` 클래스에 대한 참조 정보를 제공합니다.

## <a name="related-sections"></a>관련 단원

[문자열 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
문자열 데이터를 관리하는 여러 방법을 설명하는 항목에 대한 링크를 제공합니다.

[문자열 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
