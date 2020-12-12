---
description: '자세한 정보: ATL 컬렉션 클래스'
title: ATL 컬렉션 클래스 개요
ms.date: 11/19/2018
helpviewer_keywords:
- DestructElements function
- collection classes, choosing
- ConstructElements function
- SerializeElements function
- traits classes
- collection classes, about collection classes
- CTraits classes
- collection classes
ms.assetid: 4d619d46-5b4e-41dd-b9fd-e86b1fbc00b5
ms.openlocfilehash: 32d9fe928024d82af7031fbbb8d88aba5e3eae31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166085"
---
# <a name="atl-collection-classes"></a>ATL 컬렉션 클래스

ATL은 데이터를 저장 하 고 액세스 하기 위한 여러 클래스를 제공 합니다. 사용할 클래스는 다음을 포함 하 여 여러 가지 요인에 따라 결정 됩니다.

- 저장할 데이터의 양입니다.

- 데이터 액세스의 효율성 대비 성능

- 인덱스 또는 키로 데이터에 액세스 하는 기능

- 데이터 정렬 방법

- 개인 설정

## <a name="small-collection-classes"></a>작은 컬렉션 클래스

ATL은 적은 수의 개체를 처리 하기 위한 다음과 같은 배열 클래스를 제공 합니다. 그러나 이러한 클래스는 제한 되며 ATL에서 내부적으로 사용 하도록 설계 되었습니다. 프로그램에서 사용 하지 않는 것이 좋습니다.

|클래스|데이터 저장소 유형|
|-----------|--------------------------|
|[CSimpleArray](../atl/reference/csimplearray-class.md)|적은 수의 개체를 처리 하기 위한 배열 클래스를 구현 합니다.|
|[CSimpleMap](../atl/reference/csimplemap-class.md)|적은 수의 개체를 처리 하기 위한 매핑 클래스를 구현 합니다.|

## <a name="general-purpose-collection-classes"></a>범용 컬렉션 클래스

다음 클래스는 배열, 목록 및 맵을 구현 하며 일반적인 용도의 컬렉션 클래스로 제공 됩니다.

|클래스|데이터 저장소 유형|
|-----------|--------------------------|
|[CAtlArray](../atl/reference/catlarray-class.md)|배열을 구현 합니다.|
|[CAtlList](../atl/reference/catllist-class.md)|목록을 구현 합니다.|
|[CAtlMap](../atl/reference/catlmap-class.md)|키 또는 값을 기준으로 데이터를 참조할 수 있는 매핑 구조를 구현 합니다.|
|[CRBMap](../atl/reference/crbmap-class.md)|Red-Black 알고리즘을 사용 하 여 매핑 구조를 구현 합니다.|
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|Red-Black multimapping 구조체를 구현 합니다.|

이러한 클래스는 디버그 빌드에서 사용 될 때 많은 프로그래밍 오류를 트래핑 하지만 성능 면에서 이러한 검사가 정품 빌드에서 수행 되지 않습니다.

## <a name="specialized-collection-classes"></a>특수 컬렉션 클래스

메모리 포인터와 인터페이스 포인터를 관리 하는 데 더 특수화 된 컬렉션 클래스도 제공 됩니다.

|클래스|목적|
|-----------|-------------|
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|스마트 포인터의 배열을 생성할 때 유용한 메서드를 제공 합니다.|
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|스마트 포인터 목록을 생성할 때 유용한 메서드를 제공 합니다.|
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|포인터를 저장 하 `IUnknown` 고 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) 템플릿 클래스에 대 한 매개 변수로 사용 하도록 디자인 되었습니다.|
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|힙 포인터 목록을 생성할 때 유용한 메서드를 제공 합니다.|
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|COM 인터페이스 포인터의 배열을 생성할 때 유용한 메서드를 제공 합니다.|
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|COM 인터페이스 포인터 목록을 생성할 때 유용한 메서드를 제공 합니다.|

## <a name="choosing-a-collection-class"></a>컬렉션 클래스 선택

사용 가능한 각 컬렉션 클래스는 아래 표에 나와 있는 것 처럼 다양 한 성능 특성을 제공 합니다.

- 열 2와 3은 각 클래스의 순서 지정 및 액세스 특성을 설명 합니다. 이 표에서 "정렬 여부"는 항목이 삽입되고 삭제되는 순서가 컬렉션의 순서에 따라 결정되는 것을 의미하며 항목이 내용에 따라 정렬된다는 것을 의미하지는 않습니다. "인덱스 여부"는 컬렉션의 항목을 일반 배열의 항목처럼 정수 인덱스로 검색할 수 있음을 의미합니다.

- 4 열과 5 열은 각 클래스의 성능을 설명 합니다. 컬렉션에 항목을 많이 삽입해야 하는 애플리케이션에서는 삽입 속도가 특히 중요합니다. 다른 애플리케이션에서는 조회 속도가 더 중요할 수도 있습니다.

- 6번 열에서는 각 모양에 요소가 중복될 수 있는지 여부에 대해 설명합니다.

- 지정 된 컬렉션 클래스 작업의 성능은 작업을 완료 하는 데 필요한 시간과 컬렉션의 요소 수 간의 관계를 기준으로 표현 됩니다. 요소 수가 증가할수록 시간을 많이 차지 하는 작업은 O (n) 알고리즘으로 설명 됩니다. 이와 대조적으로 요소 수가 증가할수록 시간을 더 작게 하는 작업은 O (로그 n) 알고리즘으로 설명 됩니다. 따라서 성능 측면에서 O (로그 n) 알고리즘은 요소 수가 증가할수록 내지만 O (n) 알고리즘을 더 많이 사용 합니다.

### <a name="collection-shape-features"></a>컬렉션 모양 특징

|셰이프|주문됨|인덱싱|다음을 삽입 합니다.<br /><br /> element|검색 대상<br /><br /> 지정 된 요소|중복<br /><br /> 요소|
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|
|목록|예|아니요|Fast (일정 한 시간)|저속 O (n)|예|
|Array|예|Int (일정 시간)|끝에 삽입 하는 경우 (이 경우에는 상수 시간)를 제외 하 고 O (n)가 느려집니다.|저속 O (n)|예|
|맵|아니요|키 기준 (일정 시간)|Fast (일정 한 시간)|Fast (일정 한 시간)|아니요(키) 예(값)|
|Red-Black 맵|예 (키로)|키 O (로그 n)|Fast O (로그 n)|Fast O (로그 n)|아니요|
|Red-Black Multimap|예 (키로)|키 O (로그 n) (키 당 여러 값)|Fast O (로그 n)|Fast O (로그 n)|예 (키 당 여러 값)|

## <a name="using-ctraits-objects"></a>CTraits 개체 사용

ATL 컬렉션 클래스를 사용 하 여 광범위 한 사용자 정의 데이터 형식을 저장할 수 있으므로 비교와 같은 중요 한 함수를 재정의 하는 것이 유용할 수 있습니다. 이는 CTraits 클래스를 사용 하 여 이루어집니다.

CTraits 클래스는 MFC 컬렉션 클래스 도우미 함수 보다 더 유연 하지만 유연 합니다. 자세한 내용은 [컬렉션 클래스 도우미](../mfc/reference/collection-class-helpers.md) 를 참조 하세요.

컬렉션 클래스를 생성할 때 CTraits 클래스를 지정 하는 옵션이 있습니다. 이 클래스에는 컬렉션 클래스를 구성 하는 다른 메서드에서 호출 하는 경우 비교와 같은 작업을 수행 하는 코드가 포함 됩니다. 예를 들어 목록 개체에 고유한 사용자 정의 구조가 포함 되어 있는 경우 특정 멤버 변수만 비교 하도록 같음 테스트를 다시 정의할 수 있습니다. 이러한 방식으로 목록 개체의 Find 메서드는 보다 유용한 방식으로 작동 합니다.

## <a name="example"></a>예제

### <a name="code"></a>코드

[!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]

## <a name="comments"></a>주석

CTraits의 클래스 목록은 [컬렉션 클래스](../atl/collection-classes.md)를 참조 하세요.

다음 다이어그램에서는 CTraits 클래스의 클래스 계층 구조를 보여 줍니다.

![컬렉션 클래스 특성 계층 구조](../atl/media/vctraitscollectionclasseshierarchy.gif "컬렉션 클래스 특성 계층 구조")

## <a name="collection-classes-samples"></a>컬렉션 클래스 샘플

다음 샘플에서는 컬렉션 클래스를 보여 줍니다.

- [MMXSwarm 샘플](../overview/visual-cpp-samples.md)

- [DynamicConsumer 샘플](../overview/visual-cpp-samples.md)

- [UpdatePV 샘플](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

- [Marquee 샘플](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>참고 항목

[개념](../atl/active-template-library-atl-concepts.md)<br/>
[컬렉션 클래스](../atl/collection-classes.md)
