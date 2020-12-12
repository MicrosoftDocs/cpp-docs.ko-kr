---
description: '자세히 알아보기: 컬렉션'
title: 컬렉션
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, collections
- arrays [MFC], classes
- MFC collection classes
- shapes, collection
- collection classes [MFC], MFC
- collections, about collections
- array templates [MFC]
- collection classes [MFC], template-based
- collection classes [MFC], about collection classes
- collection classes [MFC], maps
- collection classes [MFC], arrays
- shapes
- collection classes [MFC], lists
- collection classes [MFC], shapes
ms.assetid: 02586e4c-851d-41d0-a722-feb11c17c74c
ms.openlocfilehash: 63bc61b73a9ba654fd22ecf3a238f8ef89734221
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283474"
---
# <a name="collections"></a>컬렉션

Microsoft Foundation Class 라이브러리는 개체 그룹을 관리하기 위한 컬렉션 클래스를 제공합니다. 이러한 클래스는 두 가지 유형입니다.

- [C++ 템플릿에서 생성된 컬렉션 클래스](#_core_the_template_based_collection_classes)

- [템플릿에서 생성되지 않은 컬렉션 클래스](#_core_the_collection_classes_not_based_on_templates)

> [!NOTE]
> 코드에 이미 비템플릿 컬렉션 클래스가 사용되는 경우 이를 계속 사용할 수 있습니다. 고유 데이터 형식에 대해 새로운 형식 안전 컬렉션 클래스를 작성하는 경우 템플릿 기반의 신규 클래스를 사용하는 것이 좋습니다.

## <a name="collection-shapes"></a><a name="_core_collection_shapes"></a> 컬렉션 모양

컬렉션 클래스는 "모양" 및 요소의 유형에 따라 분류됩니다. 모양은 컬렉션에서 개체가 구성 및 저장되는 방법을 나타냅니다. MFC는 세 가지 컬렉션 모양으로 목록, 배열 및 맵(사전이라고도 부름)을 제공합니다. 특정 프로그래밍 문제에 가장 적합한 컬렉션 모양을 선택하면 됩니다.

제공된 세 가지 컬렉션 모양에 대해서는 이 항목의 뒷 부분에서 간단히 설명합니다. 프로그램에 가장 적합 한 것을 결정 하는 데 도움이 되는 셰이프의 기능을 비교 하려면 [컬렉션 클래스 선택에 대 한 권장 사항](recommendations-for-choosing-a-collection-class.md)을 참조 하세요.

- 목록

   목록 클래스는 이중으로 링크된 목록으로 구현되는 정렬되었고 인덱싱되지 않은 요소 목록을 제공합니다. 목록에는 "머리"와 "꼬리"가 포함되며, 머리 또는 꼬리에서 요소를 추가 또는 제거하거나, 가운데에서 요소를 삽입 또는 삭제는 작업은 속도가 매우 빠릅니다.

- 배열

   배열 클래스는 개체에 대해 동적으로 크기가 조정되고, 정렬되었으며, 정수로 인덱싱된 배열을 제공합니다.

- 맵(사전이라고도 부름)

   맵은 키 개체를 값 개체와 연결하는 컬렉션입니다.

## <a name="the-template-based-collection-classes"></a><a name="_core_the_template_based_collection_classes"></a> Template-Based 컬렉션 클래스

모든 형식의 개체를 포함하는 형식 안전 컬렉션을 구현하는 가장 쉬운 방법은 MFC 템플릿 기반 클래스 중 하나를 사용하는 것입니다. 이러한 클래스의 예제는 MFC 샘플 [수집](../overview/visual-cpp-samples.md)을 참조 하세요.

다음 표에서는 MFC 템플릿 기반의 컬렉션 클래스를 보여줍니다.

### <a name="collection-template-classes"></a>컬렉션 템플릿 클래스

|컬렉션 내용|배열|목록|지도|
|-------------------------|------------|-----------|----------|
|임의 형식의 개체의 컬렉션|`CArray`|`CList`|`CMap`|
|임의 형식의 개체에 대한 포인터 컬렉션|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|

## <a name="the-collection-classes-not-based-on-templates"></a><a name="_core_the_collection_classes_not_based_on_templates"></a> 템플릿을 기반으로 하지 않는 컬렉션 클래스

애플리케이션에서 이미 MFC 비템플릿 클래스가 사용되는 경우 이를 계속 사용할 수 있습니다. 하지만 새로운 컬렉션의 경우에는 템플릿 기반 클래스를 사용하는 것이 좋습니다. 다음 표에서는 템플릿을 기반으로 하지 않는 MFC 컬렉션 클래스를 보여줍니다.

### <a name="nontemplate-collection-classes"></a>비템플릿 컬렉션 클래스

|배열|목록|지도|
|------------|-----------|----------|
|`CObArray`|`CObList`|`CMapPtrToWord`|
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|
|`CDWordArray`|`CStringList`|`CMapStringToOb`|
|`CPtrArray`||`CMapStringToPtr`|
|`CStringArray`||`CMapStringToString`|
|`CWordArray`||`CMapWordToOb`|
|`CUIntArray`||`CMapWordToPtr`|

[컬렉션 클래스 선택에 대 한 권장 사항](recommendations-for-choosing-a-collection-class.md) 에 있는 Mfc 컬렉션 클래스의 특징은 이러한 특성 (셰이프 제외)을 기준으로 mfc 컬렉션 클래스를 설명 합니다.

- 클래스에서 C++ 템플릿이 사용되는지 여부

- 컬렉션에 저장된 요소의 serialize 가능 여부

- 컬렉션에 저장된 요소를 진단용으로 덤프할 수 있는지 여부

- 컬렉션이 형식 안전인지 여부

### <a name="what-do-you-want-to-do"></a>뭘 하고 싶으세요

#### <a name="general-collection-class-tasks"></a>일반 컬렉션 클래스 작업

- [컬렉션 클래스 선택에 대 한 권장 사항](recommendations-for-choosing-a-collection-class.md)

- [방법: Type-Safe 컬렉션 만들기](how-to-make-a-type-safe-collection.md)

- [스택 및 큐 컬렉션 만들기](creating-stack-and-queue-collections.md)

- [CArray:: Add](reference/carray-class.md#add)

#### <a name="template-based-collection-class-tasks"></a>템플릿 기반 컬렉션 클래스 작업

- [템플릿 기반 클래스](template-based-classes.md)

#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>컬렉션의 멤버에 액세스(템플릿 기반 또는 비기반)

- [컬렉션의 모든 멤버에 액세스](accessing-all-members-of-a-collection.md)

- [CObject 컬렉션의 모든 개체 삭제](deleting-all-objects-in-a-cobject-collection.md)

## <a name="see-also"></a>참고 항목

[개념](mfc-concepts.md)<br/>
[일반 MFC 항목](general-mfc-topics.md)
