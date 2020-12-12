---
description: '자세히 알아보기: 컬렉션의 모든 멤버에 액세스'
title: 컬렉션의 모든 멤버에 액세스
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, collections
- enumerations [MFC]
- enumerating collections [MFC]
- collections [MFC], accessing
- collection classes [MFC]
- ', '
- ', '
- ', '
- ', '
- ', '
- ', '
- ', '
ms.assetid: 7bbae518-062e-4393-81f9-b22abd2e5f59
ms.openlocfilehash: 0207c082f17cf1a02da1829d5e04ea3eccae3b40
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169582"
---
# <a name="accessing-all-members-of-a-collection"></a>컬렉션의 모든 멤버에 액세스

템플릿 기반이든 아니든 MFC 배열 컬렉션 클래스는 인덱스를 사용하여 해당 요소에 액세스합니다. 템플릿 기반이든 아니든 MFC 목록 및 맵 컬렉션 클래스는 **POSITION** 형식의 표시기를 사용하여 컬렉션 내의 지정된 위치를 설명합니다. 이러한 컬렉션의 멤버 하나 이상에 액세스하려면 먼저 위치 표시기를 초기화한 다음 해당 위치를 컬렉션에 반복적으로 전달하고 다음 요소를 반환하도록 요청합니다. 컬렉션은 반복 진행률에 대한 상태 정보를 유지하는 역할을 담당하지 않습니다. 이 정보는 위치 표시기에 유지됩니다. 그러나 특정 위치가 지정된 경우 컬렉션은 다음 요소를 반환합니다.

다음 절차에서는 MFC와 함께 제공되는 세 가지 주요 형식의 컬렉션을 반복하는 방법을 보여 줍니다.

- [배열 반복](#_core_to_iterate_an_array)

- [목록 반복](#_core_to_iterate_a_list)

- [맵 반복](#_core_to_iterate_a_map)

### <a name="to-iterate-an-array"></a><a name="_core_to_iterate_an_array"></a> 배열을 반복하려면

1. `GetAt` 멤버 함수에서 순차적인 인덱스 번호를 사용합니다.

   [!code-cpp[NVC_MFCCollections#12](codesnippet/cpp/accessing-all-members-of-a-collection_1.cpp)]

   이 예제에서는 `CPerson` 개체에 대한 포인터를 포함하는 형식화된 포인터 배열을 사용합니다. 이 배열은 미리 정의된 비템플릿 클래스 중 하나인 `CObArray`클래스에서 파생됩니다. `GetAt` 는 `CPerson` 개체에 대한 포인터를 반환합니다. 형식화된 포인터 컬렉션 클래스(배열 또는 목록)의 경우 첫 번째 매개 변수는 기본 클래스를 지정하고, 두 번째 매개 변수는 저장할 형식을 지정합니다.

   `CTypedPtrArray`또한 클래스는 일반적인 배열 첨자 구문을 사용 하 여 배열의 요소에 액세스할 수 있도록 **[]** 연산자를 오버 로드 합니다. 위의 루프 본문에서 문 대신 사용할 수 있습니다. **`for`**

   [!code-cpp[NVC_MFCCollections#13](codesnippet/cpp/accessing-all-members-of-a-collection_2.cpp)]

   이 연산자는 **`const`** 및 이외 버전에 모두 있습니다 **`const`** . **`const`** 배열에 대해 호출 되는 버전은 **`const`** 대입문의 오른쪽에만 나타날 수 있습니다.

### <a name="to-iterate-a-list"></a><a name="_core_to_iterate_a_list"></a> 목록을 반복하려면

1. `GetHeadPosition` 및 `GetNext` 멤버 함수를 사용하여 목록 작업을 수행합니다.

   [!code-cpp[NVC_MFCCollections#14](codesnippet/cpp/accessing-all-members-of-a-collection_3.cpp)]

   이 예제에서는 형식화된 포인터 목록을 사용하여 `CPerson` 개체에 대한 포인터를 포함합니다. 목록 선언은 [배열을 반복하려면](#_core_to_iterate_an_array) 절차의 배열에 대한 선언과 유사하지만 `CObList`클래스에서 파생됩니다. `GetNext` 는 `CPerson` 개체에 대한 포인터를 반환합니다.

### <a name="to-iterate-a-map"></a><a name="_core_to_iterate_a_map"></a> 맵을 반복하려면

1. 다음 예제와 같이 `GetStartPosition` 을 사용하여 맵을 시작 부분을 가져오고 `GetNextAssoc` 를 사용하여 맵에서 다음 키 및 값을 반복적으로 가져옵니다.

   [!code-cpp[NVC_MFCCollections#15](codesnippet/cpp/accessing-all-members-of-a-collection_4.cpp)]

   이 예제에서는 형식화된 포인터 컬렉션 대신, `CString` 키를 사용하고 `CPerson` 개체에 대한 포인터를 저장하는 단순 맵 템플릿을 사용합니다. `GetNextAssoc`와 같은 액세스 함수를 사용하는 경우 클래스는 `CPerson` 개체에 대한 포인터를 제공합니다. 대신 비템플릿 맵 컬렉션 중 하나를 사용하는 경우에는 반환된 `CObject` 포인터를 `CPerson`에 대한 포인터로 캐스팅해야 합니다.

    > [!NOTE]
    >  비템플릿 맵의 경우 컴파일러는 `CObject` 의 마지막 매개 변수에 `GetNextAssoc`포인터에 대한 참조를 필요로 합니다. 다음 예제와 같이 입력에서 포인터를 해당 형식으로 캐스팅해야 합니다.

   템플릿 솔루션은 보다 간단하며 더 나은 형식 안전성을 제공하는 데 도움이 됩니다. 비템플릿 코드는 여기에서 볼 수 있듯이 더 복잡합니다.

   [!code-cpp[NVC_MFCCollections#16](codesnippet/cpp/accessing-all-members-of-a-collection_5.cpp)]

자세한 내용은 [CObject 컬렉션의 모든 개체 삭제](deleting-all-objects-in-a-cobject-collection.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[컬렉션](collections.md)
