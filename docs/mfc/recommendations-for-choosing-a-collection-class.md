---
description: '자세히 알아보기: 컬렉션 클래스 선택에 대 한 권장 사항'
title: 컬렉션 클래스 선택에 대한 권장 사항
ms.date: 11/04/2016
helpviewer_keywords:
- type safety of collection classes [MFC]
- collection classes [MFC], serialization
- collection classes [MFC], speed
- collection classes [MFC], type safety
- collection classes [MFC], choosing
- collection classes [MFC], functionality
- shapes, collection
- collection classes [MFC], template-based
- MFC collection classes [MFC], characteristics
- collection classes [MFC], about collection classes [MFC]
- serialization [MFC], collection classes
- collection classes [MFC], duplicates allowed
- collection classes [MFC], shapes
ms.assetid: a82188cd-443f-40d8-a244-edf292a53db4
ms.openlocfilehash: 47cf0cc1f52a10d641dba9eecbd49190d9820f41
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248533"
---
# <a name="recommendations-for-choosing-a-collection-class"></a>컬렉션 클래스 선택에 대한 권장 사항

이 문서에서는 특정 애플리케이션 요구 사항에 적합한 컬렉션을 선택하는 데 도움이 되는 자세한 정보를 제공합니다.

어떤 컬렉션 클래스를 선택할 것인가는 다음과 같은 다양한 요인에 따라 달라집니다.

- 클래스 모양의 특징: 이 항목 뒤에 나오는 [컬렉션 모양 특징](#_core_collection_shape_features) 표에서 설명하는 순서, 인덱싱 및 성능

- 클래스에서 C++ 템플릿이 사용되는지 여부

- 컬렉션에 저장된 요소의 serialize 가능 여부

- 컬렉션에 저장된 요소를 진단용으로 덤프할 수 있는지 여부

- 컬렉션이 형식 안전인지 여부

다음 [컬렉션 모양 특징](#_core_collection_shape_features)표에는 사용 가능한 컬렉션 모양의 특성이 요약되어 있습니다.

- 2번 및 3번 열에서는 각 모양의 순서와 액세스 특성에 대해 설명합니다. 이 표에서 "정렬 여부"는 항목이 삽입되고 삭제되는 순서가 컬렉션의 순서에 따라 결정되는 것을 의미하며 항목이 내용에 따라 정렬된다는 것을 의미하지는 않습니다. "인덱스 여부"는 컬렉션의 항목을 일반 배열의 항목처럼 정수 인덱스로 검색할 수 있음을 의미합니다.

- 4번 및 5번 열에서는 각 모양의 성능에 대해 설명합니다. 컬렉션에 항목을 많이 삽입해야 하는 애플리케이션에서는 삽입 속도가 특히 중요합니다. 다른 애플리케이션에서는 조회 속도가 더 중요할 수도 있습니다.

- 6번 열에서는 각 모양에 요소가 중복될 수 있는지 여부에 대해 설명합니다.

### <a name="collection-shape-features"></a><a name="_core_collection_shape_features"></a> 컬렉션 모양 기능

|셰이프|주문됨|인덱싱|요소 삽입|지정된 요소 검색|중복 요소|
|-----------|--------------|--------------|-----------------------|----------------------------------|-------------------------|
|목록|예|아니요|빠름|느림|예|
|Array|예|정수 기준|느림|느림|예|
|맵|아니요|키 기준|빠름|빠름|아니요(키) 예(값)|

다음 [MFC 컬렉션 클래스의 특징](#_core_characteristics_of_mfc_collection_classes)표에는 선택할 때 도움을 줄 수 있는 특정 MFC 컬렉션 클래스의 다른 중요한 특성이 요약되어 있습니다. 어떤 클래스를 선택할 것인가는 클래스가 C++ 템플릿에 기반을 두는지 여부, MFC의 문서 [serialization](../mfc/serialization-in-mfc.md) 메커니즘에 따라 요소를 serialize할 수 있는지 여부, MFC의 진단 덤핑 메커니즘에 따라 요소를 덤프할 수 있는지 여부 또는 클래스가 형식 안전 상태인지 여부, 즉 요소의 형식이 해당 클래스에 기반한 컬렉션에 저장되어 있고 여기에서 검색되는지 여부 등에 따라 달라집니다.

### <a name="characteristics-of-mfc-collection-classes"></a><a name="_core_characteristics_of_mfc_collection_classes"></a> MFC 컬렉션 클래스의 특징

|클래스|C++ 사용<br /><br /> 템플릿|가능 여부<br /><br /> serialize됨|가능 여부<br /><br /> 가능 여부|예<br /><br /> 형식 안전(type-safe)|
|-----------|------------------------------|---------------------------|-----------------------|-----------------------|
|`CArray`|예|예 1|예 1|아니요|
|`CByteArray`|아니요|예|예|예 3|
|`CDWordArray`|아니요|예|예|예 3|
|`CList`|예|예 1|예 1|아니요|
|`CMap`|예|예 1|예 1|아니요|
|`CMapPtrToPtr`|아니요|아니요|예|아니요|
|`CMapPtrToWord`|아니요|아니요|예|아니요|
|`CMapStringToOb`|아니요|예|예|아니요|
|`CMapStringToPtr`|아니요|아니요|예|아니요|
|`CMapStringToString`|아니요|예|예|예 3|
|`CMapWordToOb`|아니요|예|예|아니요|
|`CMapWordToPtr`|아니요|아니요|예|아니요|
|`CObArray`|아니요|예|예|아니요|
|`CObList`|아니요|예|예|아니요|
|`CPtrArray`|아니요|아니요|예|아니요|
|`CPtrList`|아니요|아니요|예|아니요|
|`CStringArray`|아니요|예|예|예 3|
|`CStringList`|아니요|예|예|예 3|
|`CTypedPtrArray`|예|상황에 따라 다름 2|예|예|
|`CTypedPtrList`|예|상황에 따라 다름 2|예|예|
|`CTypedPtrMap`|예|상황에 따라 다름 2|예|예|
|`CUIntArray`|아니요|아니요|예|예 3|
|`CWordArray`|아니요|예|예|예 3|

1. Serialize하려면 컬렉션 개체의 `Serialize` 함수를 명시적으로 호출해야 합니다. 마찬가지로 덤프하려면 `Dump` 함수를 명시적으로 호출해야 합니다. `ar << collObj`Serialize 하거나 덤프할 폼을 사용할 수 없습니다 `dmp` `<< collObj` .

2. Serialize 가능성은 기본 컬렉션 유형에 따라 다릅니다. 예를 들어, 형식화된 포인터 배열이 `CObArray`에 기반을 두는 경우 이 배열은 serialize할 수 있지만 `CPtrArray`에 기반을 두는 경우에는 serialize할 수 없습니다. 일반적으로 "Ptr" 클래스는 serialize할 수 없습니다.

3. 이 열에서 예로 표시된 경우 원래의 목적대로 사용하면 비템플릿 컬렉션 클래스는 형식 안전 상태입니다. 예를 들어 바이트를 `CByteArray`에 저장하면 배열은 형식 안전 상태가 됩니다. 그러나 이 배열을 문자를 저장하는 데 사용하면 형식 안정성이 불확실해집니다.

## <a name="see-also"></a>참고 항목

[컬렉션](../mfc/collections.md)<br/>
[템플릿 기반 클래스](../mfc/template-based-classes.md)<br/>
[방법: Type-Safe 컬렉션 만들기](../mfc/how-to-make-a-type-safe-collection.md)<br/>
[컬렉션의 모든 멤버에 액세스](../mfc/accessing-all-members-of-a-collection.md)
