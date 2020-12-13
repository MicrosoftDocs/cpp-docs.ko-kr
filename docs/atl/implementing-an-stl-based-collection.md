---
description: '자세한 정보: c + + 표준 Library-Based 컬렉션 구현'
title: C + + 표준 Library-Based 컬렉션 구현
ms.date: 11/04/2016
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
ms.openlocfilehash: 4a403885a6fe66bf8e8578deeab05c7fc08e88a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152856"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>C + + 표준 Library-Based 컬렉션 구현

ATL은 `ICollectionOnSTLImpl` 개체에 대 한 c + + 표준 라이브러리 기반 컬렉션 인터페이스를 신속 하 게 구현할 수 있는 인터페이스를 제공 합니다. 이 클래스가 작동 하는 방식을 이해 하기 위해이 클래스를 사용 하 여 자동화 클라이언트를 대상으로 하는 읽기 전용 컬렉션을 구현 하는 간단한 예제 (아래)를 수행 합니다.

샘플 코드는 다음 코드 [예제](../overview/visual-cpp-samples.md)에서 가져온 것입니다.

이 절차를 완료 하려면 다음을 수행 합니다.

- [새 단순 개체를 생성](#vccongenerating_an_object)합니다.

- 생성 된 인터페이스에 대 한 [IDL 파일을 편집](#vcconedit_the_idl) 합니다.

- 컬렉션 항목이 저장 되는 방법과 COM 인터페이스를 통해 클라이언트에 노출 되는 방법을 설명 하는 [형식 정의 5 개를 만듭니다](#vcconstorage_and_exposure_typedefs) .

- [복사 정책 클래스에 대해 두 개의 형식 정의를 만듭니다](#vcconcopy_classes).

- [열거자 및 컬렉션 구현에 대 한 형식 정의를 만듭니다](#vcconenumeration_and_collection).

- [컬렉션 typedef를 사용 하도록 마법사에서 생성 된 c + + 코드를 편집](#vcconedit_the_generated_code)합니다.

- [컬렉션을 채우는 코드를 추가](#vcconpopulate_the_collection)합니다.

## <a name="generating-a-new-simple-object"></a><a name="vccongenerating_an_object"></a> 새 단순 개체 생성

응용 프로그램 설정 아래의 특성 상자를 선택 취소 하 여 새 프로젝트를 만듭니다. ATL 클래스 추가 대화 상자 및 단순 개체 추가 마법사를 사용 하 여 라는 간단한 개체를 생성할 수 `Words` 있습니다. 라는 이중 인터페이스가 생성 되었는지 확인 `IWords` 합니다. 생성 된 클래스의 개체는 단어 컬렉션 (즉, 문자열)을 나타내는 데 사용 됩니다.

## <a name="editing-the-idl-file"></a><a name="vcconedit_the_idl"></a> IDL 파일 편집

이제 아래와 같이 IDL 파일을 열고 읽기 전용 컬렉션 인터페이스를 설정 하는 데 필요한 세 가지 속성을 추가 합니다 `IWords` .

[!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]

이는 자동화 클라이언트를 염두에 두면 서 디자인 된 읽기 전용 컬렉션 인터페이스의 표준 형식입니다. 이 인터페이스 정의에서 번호가 매겨진 주석은 아래 설명에 해당 합니다.

1. Automation 클라이언트는를 통해 속성에 액세스 하기 때문에 컬렉션 인터페이스는 일반적으로 이중 `_NewEnum` `IDispatch::Invoke` 입니다. 그러나 자동화 클라이언트는 vtable을 통해 나머지 메서드에 액세스할 수 있으므로 dispinterface에 이중 인터페이스를 사용 하는 것이 좋습니다.

1. 이중 인터페이스 또는 사용자가 런타임에 확장 되지 않는 경우 (즉,를 통해 추가 메서드나 속성을 제공 하지 않는 경우 `IDispatch::Invoke` ) **비 확장 가능** 특성을 정의에 적용 해야 합니다. 이 특성을 사용 하면 자동화 클라이언트에서 컴파일 시간에 전체 코드 확인을 수행할 수 있습니다. 이 경우 인터페이스는 확장 되어서는 안 됩니다.

1. 자동화 클라이언트에서이 속성을 사용할 수 있도록 하려면 올바른 DISPID가 중요 합니다. DISPID_NEWENUM에는 하나의 밑줄만 있습니다.

1. 모든 값을 속성의 DISPID로 제공할 수 있습니다 `Item` . 그러나는 `Item` 일반적으로 DISPID_VALUE를 사용 하 여 컬렉션의 기본 속성으로 설정 합니다. 이를 통해 자동화 클라이언트는 명시적으로 이름을 지정 하지 않고 속성을 참조할 수 있습니다.

1. 속성의 반환 값에 사용 되는 데이터 형식은 `Item` COM 클라이언트와 관련 하 여 컬렉션에 저장 된 항목의 형식입니다. 인터페이스는 문자열을 반환 하므로 표준 COM 문자열 형식인 BSTR을 사용 해야 합니다. 잠시 후에 데이터를 다른 형식으로 저장할 수 있습니다.

1. 속성의 DISPID에 사용 되는 값은 `Count` 완전히 임의로 사용 됩니다. 이 속성에 대 한 표준 DISPID가 없습니다.

## <a name="creating-typedefs-for-storage-and-exposure"></a><a name="vcconstorage_and_exposure_typedefs"></a> 저장소 및 노출을 위한 형식 정의 만들기

컬렉션 인터페이스를 정의한 후에는 데이터가 저장 되는 방법과 열거자를 통해 데이터가 노출 되는 방법을 결정 해야 합니다.

이러한 질문에 대 한 답변은 새로 만든 클래스의 헤더 파일 위쪽에 추가할 수 있는 다양 한 형식 정의 형식으로 제공 될 수 있습니다.

[!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]

이 경우 std:: **string** s의 **std:: vector** 로 데이터를 저장 합니다. **std:: vector** 는 관리 되는 배열 처럼 동작 하는 c + + 표준 라이브러리 컨테이너 클래스입니다. **std:: string** 은 c + + 표준 라이브러리의 문자열 클래스입니다. 이러한 클래스를 사용 하면 문자열 컬렉션 작업을 쉽게 수행할 수 있습니다.

이 인터페이스의 성공에는 Visual Basic 지원이 중요 하므로 속성에서 반환 된 열거자는 `_NewEnum` 인터페이스를 지원 해야 합니다 `IEnumVARIANT` . Visual Basic에서 인식할 수 있는 유일한 열거자 인터페이스입니다.

## <a name="creating-typedefs-for-copy-policy-classes"></a><a name="vcconcopy_classes"></a> 복사 정책 클래스에 대 한 형식 정의 만들기

지금까지 만든 typedef는 열거자 및 컬렉션에서 사용할 복사 클래스에 대 한 추가 형식 정의를 만드는 데 필요한 모든 정보를 제공 합니다.

[!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]

이 예제에서는 `GenericCopy` VCUE_Copy. h 및 VCUE_CopyString에 정의 [된 사용자](../overview/visual-cpp-samples.md) 지정 클래스를 사용할 수 있습니다. 다른 코드에서이 클래스를 사용할 수 있지만 사용자 `GenericCopy` 고유의 컬렉션에서 사용 되는 데이터 형식을 지원 하기 위해의 추가 특수화를 정의 해야 할 수도 있습니다. 자세한 내용은 [ATL 복사 정책 클래스](../atl/atl-copy-policy-classes.md)를 참조 하세요.

## <a name="creating-typedefs-for-enumeration-and-collection"></a><a name="vcconenumeration_and_collection"></a> 열거 및 컬렉션에 대 한 형식 정의 만들기

이제 이러한 상황에서 및 클래스를 특수화 하는 데 필요한 모든 템플릿 매개 변수가 `CComEnumOnSTL` `ICollectionOnSTLImpl` typedef 형식으로 제공 되었습니다. 특수화의 사용을 단순화 하려면 아래와 같이 형식 정의를 두 개 더 만듭니다.

[!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]

`CollectionType`는 `ICollectionOnSTLImpl` 이전에 정의 된 인터페이스를 구현 하 고을 `IWords` 지 원하는 열거자를 제공 하는의 특수화에 대 한 동의어입니다 `IEnumVARIANT` .

## <a name="editing-the-wizard-generated-code"></a><a name="vcconedit_the_generated_code"></a> Wizard-Generated 코드 편집

이제 `CWords` `CollectionType` 아래와 같이 typedef가 나타내는 인터페이스 구현에서 파생 해야 합니다 `IWords` .

[!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]

## <a name="adding-code-to-populate-the-collection"></a><a name="vcconpopulate_the_collection"></a> 컬렉션을 채우는 코드 추가

데이터를 사용 하 여 벡터를 채우는 것만 남아 있습니다. 이 간단한 예제에서는 클래스의 생성자에서 컬렉션에 몇 가지 단어를 추가할 수 있습니다.

[!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]

이제 원하는 클라이언트를 사용 하 여 코드를 테스트할 수 있습니다.

## <a name="see-also"></a>참고 항목

[컬렉션 및 열거자](../atl/atl-collections-and-enumerators.md)<br/>
[이 컬렉션 샘플](../overview/visual-cpp-samples.md)<br/>
[ATL 복사 정책 클래스](../atl/atl-copy-policy-classes.md)
