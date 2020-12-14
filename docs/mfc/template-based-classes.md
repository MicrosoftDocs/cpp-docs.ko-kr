---
description: Template-Based 클래스에 대해 자세히 알아보세요.
title: 템플릿 기반 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections
- CTypedPtrList class [MFC], template-based classes
- arrays [MFC], classes
- arrays [MFC], pointers
- typed pointers, collections of
- arrays [MFC], template-based
- CArray class [MFC], template-based classes
- simple template-based collections
- simple array collection classes [MFC]
- typed pointers
- collections, typed-pointer
- CList class [MFC], template-based classes
- collection classes [MFC], template-based
- CTypedPtrMap class [MFC], template-based classes
- pointers, collections of typed
- CTypedPtrArray class [MFC], template-based classes
- MFC collection classes [MFC], template-based
- template-based collection classes [MFC]
- simple list collection classes [MFC]
ms.assetid: c69fc95b-c8f6-4a99-abed-517c9898ef0c
ms.openlocfilehash: 87b03c649bfb6acf401c3ee78e6db07c1185dff5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216316"
---
# <a name="template-based-classes"></a>템플릿 기반 클래스

이 문서에서는 MFC 버전 3.0 이상에서 형식이 안전한 템플릿 기반 컬렉션 클래스에 대해 설명 합니다. 이러한 템플릿을 사용 하 여 형식 안전 컬렉션을 만드는 것이 더 편리 하며, 템플릿을 기반으로 하지 않는 컬렉션 클래스를 사용 하는 것 보다 더 효율적으로 형식 안전을 제공할 수 있습니다.

MFC는 템플릿 기반 컬렉션의 두 범주를 사전에 사용 합니다.

- [단순 배열, 목록 및 맵 클래스](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [형식화 된 포인터의 배열, 목록 및 맵](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

단순 컬렉션 클래스는 모두 클래스에서 파생 `CObject` 되므로의 serialization, 동적 생성 및 기타 속성을 상속 합니다 `CObject` . 형식화 된 포인터 컬렉션 클래스를 사용할 경우에서 파생 되는 클래스를 지정 해야 합니다 .이 클래스는 또는와 같은 MFC에서 미리 정의 된 비템플릿 포인터 컬렉션 중 하나 여야 합니다 `CPtrList` `CPtrArray` . 새 컬렉션 클래스는 지정 된 기본 클래스에서 상속 되며 새 클래스의 멤버 함수는 기본 클래스 멤버에 캡슐화 된 호출을 사용 하 여 형식 안전성을 적용 합니다.

C + + 템플릿에 대 한 자세한 내용은 *c + + 언어 참조* 의 [템플릿](../cpp/templates-cpp.md) 을 참조 하세요.

## <a name="using-simple-array-list-and-map-templates"></a><a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a> 단순 배열, 목록 및 맵 템플릿 사용

간단한 컬렉션 템플릿을 사용 하려면 이러한 컬렉션에 저장할 수 있는 데이터의 종류와 컬렉션 선언에 사용할 매개 변수를 알고 있어야 합니다.

### <a name="simple-array-and-list-usage"></a><a name="_core_simple_array_and_list_usage"></a> 단순 배열 및 목록 사용법

단순 배열 및 목록 클래스인 [CArray](../mfc/reference/carray-class.md) 및 [CList](../mfc/reference/clist-class.md)는 두 개의 매개 *변수인 및를* 사용 `ARG_TYPE` 합니다. 이러한 클래스는 *형식* 매개 변수에서 지정 하는 모든 데이터 형식을 저장할 수 있습니다.

- 기본 c + + 데이터 형식 (예: **`int`** , **`char`** 및) **`float`**

- C + + 구조체 및 클래스

- 정의 하는 기타 형식

편의성과 효율성을 위해 *ARG_TYPE* 매개 변수를 사용 하 여 함수 인수의 형식을 지정할 수 있습니다. 일반적으로 *ARG_TYPE* 를 *형식* 매개 변수에 지정 된 형식에 대 한 참조로 지정 합니다. 예를 들어:

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

첫 번째 예제에서는 s를 포함 하는 배열 컬렉션를 선언 합니다 `myArray` **`int`** . 두 번째 예제에서는 개체를 저장 하는 목록 컬렉션를 선언 합니다 `myList` `CPerson` . 컬렉션 클래스의 특정 멤버 함수는 *ARG_TYPE* 템플릿 매개 변수로 지정 된 형식을 가진 인수를 사용 합니다. 예를 들어 `Add` 클래스의 멤버 함수는 `CArray` *ARG_TYPE* 인수를 사용 합니다.

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

### <a name="simple-map-usage"></a><a name="_core_simple_map_usage"></a> 단순 맵 사용

Simple map 클래스 [Cmap](../mfc/reference/cmap-class.md)은 *키*, *ARG_KEY*, *값* 및 *ARG_VALUE* 의 네 가지 매개 변수를 사용 합니다. 배열 및 목록 클래스와 마찬가지로 map 클래스는 모든 데이터 형식을 저장할 수 있습니다. 저장 하는 데이터의 인덱스와 순서를 지정 하는 배열 및 목록과 달리 지도에는 키와 값이 연결 됩니다. 값의 연결 된 키를 지정 하 여 map에 저장 된 값에 액세스 합니다. *키* 매개 변수는 맵에 저장 된 데이터에 액세스 하는 데 사용 되는 키의 데이터 형식을 지정 합니다. *키* 형식이 구조체 또는 클래스인 경우 *ARG_KEY* 매개 변수는 일반적으로 *키* 에 지정 된 형식에 대 한 참조입니다. *VALUE* 매개 변수는 맵에 저장 된 항목의 유형을 지정 합니다. *ARG_VALUE* 형식이 구조체 또는 클래스인 경우 *ARG_VALUE* 매개 변수는 일반적으로 *값* 에 지정 된 형식에 대 한 참조입니다. 예를 들어:

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

첫 번째 예제에서는 `MY_STRUCT` 값을 저장 하 고, 키로 액세스 하 **`int`** 고, 참조를 통해 액세스 한 항목을 반환 합니다 `MY_STRUCT` . 두 번째 예제에서는 `CPerson` 값을 저장 하 고, 키로 액세스 하 `CString` 고, 액세스 한 항목에 대 한 참조를 반환 합니다. 이 예는 성을 기준으로 사람을 조회 하는 간단한 주소록을 나타낼 수 있습니다.

*키* 매개 변수는 형식이 `CString` 고 *KEY_TYPE* 매개 변수는 형식 이므로 `LPCSTR` 키는 형식 항목으로 맵에 저장 `CString` 되지만 형식의 포인터를 통해와 같은 함수에서 참조 됩니다 `SetAt` `LPCSTR` . 예를 들어:

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

## <a name="using-typed-pointer-collection-templates"></a><a name="_core_using_typed.2d.pointer_collection_templates"></a> Typed-Pointer 컬렉션 템플릿 사용

형식화 된 포인터 컬렉션 템플릿을 사용 하려면 이러한 컬렉션에 저장할 수 있는 데이터의 종류와 컬렉션 선언에 사용할 매개 변수를 알고 있어야 합니다.

### <a name="typed-pointer-array-and-list-usage"></a><a name="_core_typed.2d.pointer_array_and_list_usage"></a> Typed-Pointer 배열 및 목록 사용법

형식화 된 포인터 배열 및 목록 클래스인 [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) 및 [CTypedPtrList](../mfc/reference/ctypedptrlist-class.md)는 두 개의 매개 변수 *BASE_CLASS* 와 *형식* 을 사용 합니다. 이러한 클래스는 *형식* 매개 변수에서 지정 하는 모든 데이터 형식을 저장할 수 있습니다. 포인터를 저장 하는 비템플릿 컬렉션 클래스 중 하나에서 파생 됩니다. *BASE_CLASS* 에서이 기본 클래스를 지정 합니다. 배열의 경우 또는 중 하나를 사용 `CObArray` `CPtrArray` 합니다. 목록의 경우 또는 중 하나를 사용 `CObList` `CPtrList` 합니다.

실제로에 따라 컬렉션을 선언 하는 경우 `CObList` 새 클래스는 기본 클래스의 멤버를 상속할 뿐만 아니라 기본 클래스 멤버에 대 한 호출을 캡슐화 하 여 형식 안전성을 제공 하는 데 도움이 되는 다양 한 추가 형식 안전 멤버 함수 및 연산자를 선언 합니다. 이러한 캡슐화는 필요한 모든 형식 변환을 관리 합니다. 예를 들어:

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

첫 번째 예제에서는에서 파생 된 형식화 된 포인터 배열을 선언 합니다 `myArray` `CObArray` . 배열은 개체에 대 한 포인터를 저장 하 고 반환 `CPerson` `CPerson` 합니다. 여기서은에서 파생 된 클래스 `CObject` 입니다. 모든 `CObArray` 멤버 함수를 호출 하거나, 새 형식 안전 `GetAt` 및 함수를 호출 `ElementAt` 하거나 형식이 안전한 **[]** 연산자를 사용할 수 있습니다.

두 번째 예제에서는에서 파생 된 형식화 된 포인터 목록을 선언 합니다 `myList` `CPtrList` . 목록은 개체에 대 한 포인터를 저장 하 고 반환 `MY_STRUCT` 합니다. 을 기반으로 하는 클래스는 `CPtrList` 에서 파생 되지 않은 개체에 대 한 포인터를 저장 하는 데 사용 됩니다 `CObject` . `CTypedPtrList` 에는,,,,, `GetHead` `GetTail` `RemoveHead` `RemoveTail` `GetNext` `GetPrev` 및와 `GetAt` 같은 다양 한 형식 안전 멤버 함수가 있습니다.

### <a name="typed-pointer-map-usage"></a><a name="_core_typed.2d.pointer_map_usage"></a> Typed-Pointer 맵 사용

형식화 된 포인터 맵 클래스인 [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md)는 *BASE_CLASS*, *키* 및 *값* 의 세 가지 매개 변수를 사용 합니다. *BASE_CLASS* 매개 변수는 새 클래스를 파생 시킬 클래스 (,,,, 등)를 지정 합니다 `CMapPtrToWord` `CMapPtrToPtr` `CMapStringToPtr` `CMapWordToPtr` `CMapStringToOb` . *키는* 의 *키* 와 비슷하며 `CMap` 조회에 사용 되는 키의 유형을 지정 합니다. *값* 은의 *값* 과 유사 합니다 `CMap` . 맵에 저장 된 개체의 형식을 지정 합니다. 예를 들어:

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

첫 번째 예제는를 기반으로 하는 맵으로 `CMapPtrToPtr` , `CString` 에 대 한 포인터에 매핑된 키를 사용 `MY_STRUCT` 합니다. 형식이 안전한 멤버 함수를 호출 하 여 저장 된 포인터를 조회할 수 있습니다 `Lookup` . **[]** 연산자를 사용 하 여 저장 된 포인터를 조회 하 고 찾을 수 없는 경우 추가할 수 있습니다. 형식 안전 함수를 사용 하 여 맵을 반복할 수 있습니다 `GetNextAssoc` . 클래스의 다른 멤버 함수를 호출할 수도 있습니다 `CMapPtrToPtr` .

두 번째 예는을 기반으로 하는 맵입니다 `CMapStringToOb` . 여기에는 개체에 대 한 저장 된 포인터에 매핑된 문자열 키가 사용 됩니다 `CMyObject` . 이전 단락에서 설명한 것과 동일한 형식이 안전한 멤버를 사용 하거나 클래스의 멤버를 호출할 수 있습니다 `CMapStringToOb` .

> [!NOTE]
> 형식에 대 한 **`class`** **`struct`** 포인터나 참조가 아닌 *값* 매개 변수에 대해 또는 형식을 지정 하는 경우 클래스 또는 구조체에 복사 생성자가 있어야 합니다.

자세한 내용은 [Type-Safe 컬렉션을 만드는 방법](../mfc/how-to-make-a-type-safe-collection.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[컬렉션](../mfc/collections.md)
