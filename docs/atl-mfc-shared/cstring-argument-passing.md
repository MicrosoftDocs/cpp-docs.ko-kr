---
description: '자세한 정보: CString 인수 전달'
title: CString 인수 전달
ms.date: 11/04/2016
helpviewer_keywords:
- strings [C++], as function input/output
- argument passing [C++]
- arguments [C++], passing
- functions [C++], strings as input/output
- argument passing [C++], C strings
- passing arguments, C strings
- CString objects, passing arguments
- string arguments
ms.assetid: a67bebff-edf1-4cf4-bbff-d1cc6a901099
ms.openlocfilehash: ee47898ffdfc5129b11b0f9480669fa142d12818
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167177"
---
# <a name="cstring-argument-passing"></a>CString 인수 전달

이 문서에서는 [CString](../atl-mfc-shared/reference/cstringt-class.md) 개체를 함수에 전달 하는 방법과 함수에서 개체를 반환 하는 방법을 설명 `CString` 합니다.

## <a name="cstring-argument-passing-conventions"></a><a name="_core_cstring_argument.2d.passing_conventions"></a> CString Argument-Passing 규칙

클래스 인터페이스를 정의할 때 멤버 함수에 대 한 인수 전달 규칙을 결정 해야 합니다. 개체를 전달 하 고 반환 하기 위한 몇 가지 표준 규칙이 있습니다 `CString` . [문자열에서 함수 입력](#_core_strings_as_function_inputs) 및 문자열로 설명 된 규칙을 [함수 출력](#_core_strings_as_function_outputs)으로 따르는 경우 효율적이 고 올바른 코드를 갖게 됩니다.

## <a name="strings-as-function-inputs"></a><a name="_core_strings_as_function_inputs"></a> 함수 입력으로 서의 문자열

호출 된 함수에서 개체를 사용 하는 가장 효율적이 고 안전한 방법은 `CString` 개체를 함수에 전달 하는 것입니다 `CString` . 이름에도 불구 하 고, `CString` 개체는 내부적으로 문자열을 null 종결자를 포함 하는 C 스타일 문자열로 저장 하지 않습니다. 대신 `CString` 개체가 보유 하 고 있는 문자 수를 신중히 추적 합니다. `CString`Null로 종료 되는 문자열에 대 한 LPCTSTR 포인터를 제공 하는 것은 코드에서 지속적으로 수행 해야 하는 경우 상당한 양의 작업입니다. 내용이 변경 되 면 `CString` LPCTSTR 포인터의 이전 복사본이 무효화 되기 때문에 결과는 일시적일 수 있습니다.

일부 경우에는 C 스타일 문자열을 제공 해야 합니다. 예를 들어 호출 된 함수가 C로 작성 되 고 개체를 지원 하지 않는 상황이 발생할 수 있습니다. 이 경우 `CString` 매개 변수를 LPCTSTR로 강제 변환 합니다. 그러면 함수는 C 스타일의 null로 끝나는 문자열을 가져옵니다. 다른 방향으로 이동 하 여 `CString` `CString` C 스타일 문자열 매개 변수를 허용 하는 생성자를 사용 하 여 개체를 만들 수도 있습니다.

문자열 내용이 함수에 의해 변경 되는 경우 매개 변수를 비상수 `CString` 참조 ()로 선언 합니다 `CString&` .

## <a name="strings-as-function-outputs"></a><a name="_core_strings_as_function_outputs"></a> 함수 출력으로 서의 문자열

일반적으로 개체는 `CString` `CString` 기본 형식과 같은 값 의미 체계를 따르기 때문에 함수에서 개체를 반환할 수 있습니다. 읽기 전용 문자열을 반환 하려면 상수 `CString` 참조 ()를 사용 `const CString&` 합니다. 다음 예제에서는 `CString` 매개 변수 및 반환 형식을 사용 하는 방법을 보여 줍니다.

[!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]

## <a name="see-also"></a>참고 항목

[문자열 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
