---
description: '자세한 정보: 기본 CString 작업'
title: 기본 CString 작업
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
ms.openlocfilehash: abd64445efbfd6afb26dc023b3a0451bedcc1e5e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142521"
---
# <a name="basic-cstring-operations"></a>기본 CString 작업

이 항목에서는 다음과 같은 기본 [CString](../atl-mfc-shared/reference/cstringt-class.md) 작업에 대해 설명 합니다.

- [표준 C 리터럴 문자열에서 CString 개체 만들기](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [CString의 개별 문자에 액세스](#_core_accessing_individual_characters_in_a_cstring)

- [두 CString 개체 연결](#_core_concatenating_two_cstring_objects)

- [CString 개체 비교](#_core_comparing_cstring_objects)

- [CString 개체 변환](#_core_converting_cstring_objects)

`Class CString` 는 클래스 템플릿 [CStringT 클래스](../atl-mfc-shared/reference/cstringt-class.md)를 기반으로 합니다. `CString` 은 **`typedef`** 의입니다 `CStringT` . 보다 정확 하 게는 클래스 `CString` **`typedef`** 템플릿을 사용 하 여 클래스를 정의 하는 일반적인 방법인의 *명시적 특수화* 입니다 `CStringT` . 이와 유사 하 게 정의 된 클래스는 `CStringA` 및 `CStringW` 입니다.

`CString`, `CStringA` 및은 (는)이 `CStringW` 에 정의 되어 있습니다. `CStringT` 는 cstringt. h에 정의 되어 있습니다.

`CString`, `CStringA` 및은 `CStringW` 에서 `CStringT` 지 원하는 문자열 데이터와 함께 사용 하기 위해에 정의 된 메서드 및 연산자 집합을 가져옵니다. 일부 메서드는 C 런타임 라이브러리의 문자열 서비스를 복제 하 고 일부 경우에는 초과할 합니다.

참고: `CString` 는 네이티브 클래스입니다. C + +/CLI 관리 되는 프로젝트에서 사용할 문자열 클래스의 경우를 사용 `System.String` 합니다.

## <a name="creating-cstring-objects-from-standard-c-literal-strings"></a><a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a> 표준 C 리터럴 문자열에서 CString 개체 만들기

`CString`한 `CString` 개체를 다른 개체에 할당할 수 있는 것과 마찬가지로 C 스타일 리터럴 문자열을에 할당할 수 있습니다.

- C 리터럴 문자열 값을 개체에 할당 합니다 `CString` .

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- 값 하나 `CString` 를 다른 개체에 할당 `CString` 합니다.

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   개체의 내용은 `CString` 한 `CString` 개체가 다른 개체에 할당 될 때 복사 됩니다. 따라서 두 문자열은 문자열을 구성 하는 실제 문자에 대 한 참조를 공유 하지 않습니다. 개체를 값으로 사용 하는 방법에 대 한 자세한 내용은 `CString` [CString 의미 체계](../atl-mfc-shared/cstring-semantics.md)를 참조 하세요.

   > [!NOTE]
   > 유니코드 또는 ANSI 용으로 컴파일할 수 있도록 응용 프로그램을 작성 하려면 _T 매크로를 사용 하 여 코드 리터럴 문자열을 작성 합니다. 자세한 내용은 [유니코드 및 MBCS (멀티 바이트 문자 집합) 지원](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)을 참조 하세요.

## <a name="accessing-individual-characters-in-a-cstring"></a><a name="_core_accessing_individual_characters_in_a_cstring"></a> CString의 개별 문자에 액세스

`CString`및 메서드를 사용 하 여 개체의 개별 문자에 액세스할 수 있습니다 `GetAt` `SetAt` . 대신 배열 요소 또는 첨자, 연산자 ([])를 사용 `GetAt` 하 여 개별 문자를 가져올 수도 있습니다. 이는 표준 C 스타일 문자열과 같이 인덱스 별로 배열 요소에 액세스 하는 것과 유사 합니다. 문자에 대 한 인덱스 값 `CString` 은 0부터 시작 합니다.

## <a name="concatenating-two-cstring-objects"></a><a name="_core_concatenating_two_cstring_objects"></a> 두 CString 개체 연결

두 개체를 연결 하려면 `CString` 다음과 같이 연결 연산자 (+ 또는 + =)를 사용 합니다.

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

연결 연산자 (+ 또는 + =)에 대 한 인수는 하나 이상 개체 여야 `CString` 하지만, 다른 인수에는 상수 문자열 (예: `"big"` ) 또는 **`char`** (예: ' x ')를 사용할 수 있습니다.

## <a name="comparing-cstring-objects"></a><a name="_core_comparing_cstring_objects"></a> CString 개체 비교

`Compare`메서드와에 대 한 = = 연산자는 `CString` 동일 합니다. `Compare`, **operator = =** 및 `CompareNoCase` 는 MBCS와 유니코드를 인식 하며 `CompareNoCase` 는 대/소문자를 구분 하지 않습니다. `Collate`의 메서드는 `CString` 로캘에 따라 구분 되며 일반적으로 보다 느립니다 `Compare` . `Collate`현재 로캘로 지정 된 정렬 규칙을 준수 해야 하는 경우에만를 사용 합니다.

다음 표에서는 C 런타임 라이브러리에서 사용 가능한 [CString](../atl-mfc-shared/reference/cstringt-class.md) 비교 함수와 해당 하는 유니코드/MBCS 이식 가능 함수를 보여 줍니다.

|CString 함수|MBCS 함수|유니코드 함수|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

`CStringT`클래스 템플릿은에서 사용할 수 있는 관계형 연산자 (<, \<=, > =, >, = = 및! =)를 정의 합니다 `CString` . `CStrings`다음 예제와 같이 이러한 연산자를 사용 하 여 두 가지를 비교할 수 있습니다.

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

## <a name="converting-cstring-objects"></a><a name="_core_converting_cstring_objects"></a> CString 개체 변환

CString 개체를 다른 문자열 형식으로 변환 하는 방법에 대 한 자세한 내용은 [방법: 다양 한 문자열 형식 간 변환](../text/how-to-convert-between-various-string-types.md)을 참조 하세요.

## <a name="using-cstring-with-wcout"></a>Wcout와 함께 CString 사용

에서 CString을 사용 하려면 `wcout` 다음 예제와 같이 개체를로 명시적으로 캐스팅 해야 합니다 `const wchar_t*` .

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

캐스트가 없으면 `cs` 은로 처리 되 **`void*`** 고 `wcout` 개체의 주소를 인쇄 합니다. 이 동작은 자신에 게 정확 하 고 c + + 표준과 호환 되는 템플릿 인수 추론 및 오버 로드 확인 간의 미묘한 상호 작용으로 인해 발생 합니다.

## <a name="see-also"></a>참고 항목

[문자열 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT 클래스](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[템플릿 특수화](../cpp/template-specialization-cpp.md)<br/>
[방법: 다양 한 문자열 형식 간 변환](../text/how-to-convert-between-various-string-types.md)
