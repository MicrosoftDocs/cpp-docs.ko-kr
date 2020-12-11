---
description: '자세히 알아보기: CComBSTR를 사용한 프로그래밍 (ATL)'
title: CComBSTR을 사용한 프로그래밍(ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
ms.openlocfilehash: 6c348d703aeaeba40f1f47b8f6fd0ee858b7babd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159221"
---
# <a name="programming-with-ccombstr-atl"></a>CComBSTR을 사용한 프로그래밍(ATL)

ATL 클래스 [CComBSTR](../atl/reference/ccombstr-class.md) 는 BSTR 데이터 형식에 대 한 래퍼를 제공 합니다. `CComBSTR`는 유용한 도구 이지만 주의 해야 하는 여러 가지 상황이 있습니다.

- [변환 문제](#programmingwithccombstr_conversionissues)

- [범위 문제](#programmingwithccombstr_scopeissues)

- [명시적으로 CComBSTR 개체 해제](#programmingwithccombstr_explicitlyfreeing)

- [루프에서 CComBSTR 개체 사용](#programmingwithccombstr_usingloops)

- [메모리 누수 문제](#programmingwithccombstr_memoryleaks)

## <a name="conversion-issues"></a><a name="programmingwithccombstr_conversionissues"></a> 변환 문제

여러 `CComBSTR` 메서드에서 ANSI 문자열 인수를 자동으로 유니코드로 변환 하지만이 메서드는 항상 유니코드 형식 문자열을 반환 합니다. 출력 문자열을 다시 ANSI로 변환 하려면 ATL 변환 클래스를 사용 합니다. ATL 변환 클래스에 대 한 자세한 내용은 [atl 및 MFC 문자열 변환 매크로](reference/string-conversion-macros.md)를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]

문자열 리터럴을 사용 하 여 개체를 수정 하는 경우에는 `CComBSTR` 와이드 문자열을 사용 합니다. 이렇게 하면 불필요 한 변환이 줄어듭니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]

## <a name="scope-issues"></a><a name="programmingwithccombstr_scopeissues"></a> 범위 문제

잘 작동 하는 모든 클래스와 마찬가지로는 `CComBSTR` 범위를 벗어나면 리소스를 해제 합니다. 함수에서 문자열에 대 한 포인터를 반환 하면 `CComBSTR` 포인터가 이미 해제 된 메모리를 참조 하므로 문제가 발생할 수 있습니다. 이러한 경우에는 `Copy` 아래와 같이 메서드를 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]

## <a name="explicitly-freeing-the-ccombstr-object"></a><a name="programmingwithccombstr_explicitlyfreeing"></a> 명시적으로 CComBSTR 개체 해제

개체가 `CComBSTR` 범위를 벗어나기 전에 개체에 포함 된 문자열을 명시적으로 해제할 수 있습니다. 문자열이 해제 된 경우에는 `CComBSTR` 개체가 유효 하지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]

## <a name="using-ccombstr-objects-in-loops"></a><a name="programmingwithccombstr_usingloops"></a> 루프에서 CComBSTR 개체 사용

`CComBSTR`클래스가 연산자나 메서드와 같은 특정 작업을 수행 하기 위해 버퍼를 할당 하므로 `+=` `Append` , 근접 루프 내에서 문자열 조작을 수행 하지 않는 것이 좋습니다. 이러한 상황에서는 `CStringT` 더 나은 성능을 제공 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]

## <a name="memory-leak-issues"></a><a name="programmingwithccombstr_memoryleaks"></a> 메모리 누수 문제

함수에 초기화 된의 주소를 `CComBSTR` **[out]** 매개 변수로 전달 하면 메모리 누수가 발생 합니다.

아래 예제에서는 함수에서 문자열을 대체할 때 문자열을 포함 하도록 할당 된 문자열이 `"Initialized"` 유출 됩니다 `MyGoodFunction` .

[!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]

누수를 방지 하려면 `Empty` `CComBSTR` 주소를 **[out]** 매개 변수로 전달 하기 전에 기존 개체에서 메서드를 호출 합니다.

함수의 매개 변수가 **[in, out]** 인 경우 동일한 코드에서 누수를 발생 시 키 지 않습니다.

## <a name="see-also"></a>참고 항목

[개념](../atl/active-template-library-atl-concepts.md)<br/>
[CStringT 클래스](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[wstring](../standard-library/basic-string-class.md)<br/>
[문자열 변환 매크로](../atl/reference/string-conversion-macros.md)
