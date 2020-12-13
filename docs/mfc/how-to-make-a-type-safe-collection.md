---
description: '자세한 정보: 방법: Type-Safe 컬렉션 만들기'
title: '방법: 형식이 안전한 컬렉션 만들기'
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections [MFC]
- serializing collection-class elements [MFC]
- collection classes [MFC], type safety
- SerializeElements function [MFC]
- collection classes [MFC], template-based
- serialization [MFC], collection classes
- collection classes [MFC], deriving from nontemplate
ms.assetid: 7230b2db-4283-4083-b098-eb231bf5b89e
ms.openlocfilehash: 6c4e474979a6ea5e17a771e2340df71782a59bab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330176"
---
# <a name="how-to-make-a-type-safe-collection"></a>방법: 형식이 안전한 컬렉션 만들기

이 문서에서는 사용자 고유의 데이터 형식에 대해 형식이 안전한 컬렉션을 만드는 방법을 설명 합니다. 다룰 주제는 다음과 같습니다.

- [형식 안전성을 위해 템플릿 기반 클래스 사용](#_core_using_template.2d.based_classes_for_type_safety)

- [도우미 함수 구현](#_core_implementing_helper_functions)

- [비템플릿 컬렉션 클래스 사용](#_core_using_nontemplate_collection_classes)

MFC 라이브러리은 c + + 템플릿을 기반으로 하는 미리 정의 된 형식 안전 컬렉션을 제공 합니다. 이러한 클래스는 템플릿 이므로 이러한 클래스를 사용 하면 형식 캐스팅 및 비템플릿 클래스 사용과 관련 된 기타 추가 작업 없이 형식 안전 성과 사용 편의성을 향상 시킬 수 있습니다. MFC 샘플 [수집](../overview/visual-cpp-samples.md) 에서는 mfc 응용 프로그램에서 템플릿 기반 컬렉션 클래스를 사용 하는 방법을 보여 줍니다. 일반적으로 새 컬렉션 코드를 작성할 때마다 이러한 클래스를 사용 합니다.

## <a name="using-template-based-classes-for-type-safety"></a><a name="_core_using_template.2d.based_classes_for_type_safety"></a> 형식 안전성을 위해 Template-Based 클래스 사용

#### <a name="to-use-template-based-classes"></a>템플릿 기반 클래스를 사용 하려면

1. 컬렉션 클래스 형식의 변수를 선언 합니다. 예를 들어:

   [!code-cpp[NVC_MFCCollections#7](codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]

1. 컬렉션 개체의 멤버 함수를 호출 합니다. 예를 들어:

   [!code-cpp[NVC_MFCCollections#8](codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]

1. 필요한 경우 [도우미 함수](reference/collection-class-helpers.md) 및 [SerializeElements](reference/collection-class-helpers.md#serializeelements)를 구현 합니다. 이러한 함수를 구현 하는 방법에 대 한 자세한 내용은 [도우미 함수 구현](#_core_implementing_helper_functions)을 참조 하세요.

이 예제에서는 정수 목록의 선언을 보여 줍니다. 1 단계의 첫 번째 매개 변수는 목록의 요소로 저장 된 데이터의 형식입니다. 두 번째 매개 변수는 컬렉션 클래스의 멤버 함수 (예: 및)에서 데이터를 전달 하 고 반환 하는 방법을 지정 합니다 `Add` `GetAt` .

## <a name="implementing-helper-functions"></a><a name="_core_implementing_helper_functions"></a> 도우미 함수 구현

템플릿 기반 컬렉션 클래스 `CArray` , 및에서는 `CList` `CMap` 파생 컬렉션 클래스에 대해 필요에 따라 사용자 지정할 수 있는 5 개의 전역 도우미 함수를 사용 합니다. 이러한 도우미 함수에 대 한 자세한 내용은 *MFC 참조* 의 [컬렉션 클래스 도우미](reference/collection-class-helpers.md) 를 참조 하세요. 대부분의 템플릿 기반 컬렉션 클래스를 사용 하려면 serialization 함수를 구현 해야 합니다.

### <a name="serializing-elements"></a><a name="_core_serializing_elements"></a> 요소 serialize

`CArray`, `CList` 및 클래스를 호출 하 여 `CMap` `SerializeElements` 보관 파일에서 컬렉션 요소를 저장 하거나 읽습니다.

도우미 함수의 기본 구현은 개체가 보관 위치에 `SerializeElements` 저장 되는지, 아니면 보관에서 검색 되 고 있는지에 따라 보관 파일에서 개체로의 비트 쓰기를 수행 합니다. `SerializeElements`이 작업이 적절 하지 않으면를 재정의 합니다.

컬렉션에서 파생 된 개체를 저장 `CObject` 하 고 `IMPLEMENT_SERIAL` 컬렉션 요소 클래스의 구현에서 매크로를 사용 하는 경우 및에 기본 제공 되는 serialization 기능을 활용할 수 있습니다 `CArchive` `CObject` .

[!code-cpp[NVC_MFCCollections#9](codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]

`CArchive` `CObject::Serialize` 각 개체에 대 한 호출 (또는 해당 함수의 재정의)에 대해 오버 로드 된 삽입 연산자입니다 `CPerson` .

## <a name="using-nontemplate-collection-classes"></a><a name="_core_using_nontemplate_collection_classes"></a> 비템플릿 컬렉션 클래스 사용

Mfc는 MFC 버전 1.0에 도입 된 컬렉션 클래스도 지원 합니다. 이러한 클래스는 템플릿을 기반으로 하지 않습니다. 지원 되는 형식인,, 및의 데이터를 포함 하는 데 사용할 수 있습니다 `CObject*` `UINT` `DWORD` `CString` . 이러한 미리 정의 된 컬렉션 (예: `CObList` )을 사용 하 여에서 파생 된 개체의 컬렉션을 유지할 수 있습니다 `CObject` . 또한 MFC는 `UINT` 및 void 포인터 ()와 같은 기본 형식을 포함 하는 미리 정의 된 다른 컬렉션을 제공 **`void*`** 합니다. 그러나 일반적으로 보다 구체적인 클래스와 해당 파생 클래스의 개체를 저장 하는 고유한 형식 안전 컬렉션을 정의 하는 것이 유용한 경우가 많습니다. 템플릿을 기반으로 하지 않는 컬렉션 클래스를 사용 하 여이 작업을 수행 하는 것은 템플릿 기반 클래스를 사용 하는 것 보다 더 복잡 합니다.

비템플릿 컬렉션을 사용 하 여 형식이 안전한 컬렉션을 만드는 방법에는 두 가지가 있습니다.

1. 필요한 경우 형식 캐스팅을 사용 하 여 비템플릿 컬렉션을 사용 합니다. 이 방법이 더 쉬운 방법입니다.

1. 에서 파생 되 고 비템플릿 형식 안전 컬렉션을 확장 합니다.

#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>형식 캐스팅을 통해 비템플릿 컬렉션을 사용 하려면

1. 와 같이 비템플릿 클래스 중 하나를 직접 사용 `CWordArray` 합니다.

   예를 들어를 만들어 `CWordArray` 32 비트 값을 추가 하 고 검색할 수 있습니다. 수행할 작업이 없습니다. 미리 정의 된 기능을 사용 합니다.

   등의 미리 정의 된 컬렉션을 사용 하 여 `CObList` 에서 파생 된 개체를 보관할 수도 있습니다 `CObject` . 에 대 한 `CObList` 포인터를 포함 하도록 컬렉션을 정의 `CObject` 합니다. 목록에서 개체를 검색 하는 경우 함수에서에 대 한 `CObList` 포인터를 반환 하므로 결과를 적절 한 형식으로 캐스팅 해야 할 수 있습니다 `CObject` . 예를 들어 개체를 컬렉션에 저장 하는 경우 `CPerson` `CObList` 검색 된 요소를 개체에 대 한 포인터로 캐스팅 해야 `CPerson` 합니다. 다음 예제에서는 컬렉션을 사용 하 여 `CObList` 개체를 저장 합니다 `CPerson` .

   [!code-cpp[NVC_MFCCollections#10](codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]

   미리 정의 된 컬렉션 형식 및 필요에 따라 캐스트를 사용 하는이 기술은 많은 컬렉션 요구 사항에 적합할 수 있습니다. 추가 기능이 나 더 많은 형식 안전성이 필요한 경우 템플릿 기반 클래스를 사용 하거나 다음 절차를 따릅니다.

#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>비템플릿 형식 안전 컬렉션을 파생 하 고 확장 하려면

1. 미리 정의 된 비템플릿 클래스 중 하나에서 고유한 컬렉션 클래스를 파생 시킵니다.

   클래스를 파생 하는 경우 형식이 안전한 래퍼 함수를 추가 하 여 기존 함수에 형식 안전 인터페이스를 제공할 수 있습니다.

   예를 들어 개체를 보유 하기 위해에서 목록을 파생 시킨 경우 `CObList` `CPerson` 아래와 같이 래퍼 함수와를 추가할 수 있습니다 `AddHeadPerson` `GetHeadPerson` .

   [!code-cpp[NVC_MFCCollections#11](codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]

   이러한 래퍼 함수는 파생 된 목록에서 개체를 추가 하 고 검색 하는 형식이 안전한 방법을 제공 `CPerson` 합니다. 함수에 대해 단순히 형식 캐스팅을 캡슐화 하는 것을 확인할 수 있습니다 `GetHeadPerson` .

   형식 안전 래퍼에서 기존 기능을 래핑하는 대신 컬렉션의 기능을 확장 하는 새 함수를 정의 하 여 새 기능을 추가할 수도 있습니다. 예를 들어, [CObject 컬렉션의 모든 개체를 삭제](deleting-all-objects-in-a-cobject-collection.md) 하는 문서에서는 목록에 포함 된 모든 개체를 삭제 하는 함수에 대해 설명 합니다. 이 함수는 멤버 함수로 파생 된 클래스에 추가할 수 있습니다.

## <a name="see-also"></a>참고 항목

[컬렉션](collections.md)
