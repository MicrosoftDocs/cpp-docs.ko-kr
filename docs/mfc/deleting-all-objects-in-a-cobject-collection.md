---
description: '자세한 정보: CObject 컬렉션의 모든 개체 삭제'
title: CObject 컬렉션의 모든 개체 삭제
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], deleting in collections
- objects in CObject collections, deleting
- CObject class [MFC], deleting in collection
- collection classes [MFC], deleting all objects
- CObject class collection
- objects in CObject collections
- collection classes [MFC], shared objects
ms.assetid: 81d2c1d5-a0a5-46e1-8ab9-82b45cf7afd2
ms.openlocfilehash: 674253d06925bdf29e5606692a73911878f6c393
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291014"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>CObject 컬렉션의 모든 개체 삭제

이 문서에서는 컬렉션 개체 자체를 삭제 하지 않고 컬렉션의 모든 개체를 삭제 하는 방법을 설명 합니다.

컬렉션 (또는에서 파생 된 개체)의 모든 개체를 삭제 하려면 `CObject` `CObject` [컬렉션의 모든 멤버에 액세스](accessing-all-members-of-a-collection.md) 문서에 설명 된 반복 기술 중 하나를 사용 하 여 각 개체를 차례로 삭제 합니다.

> [!CAUTION]
> 컬렉션의 개체는 공유할 수 있습니다. 즉, 컬렉션은 개체에 대 한 포인터를 유지 하지만 프로그램의 다른 부분에도 동일한 개체에 대 한 포인터가 있을 수 있습니다. 모든 파트의 개체 사용이 완료 될 때까지 공유 되는 개체를 삭제 하지 않도록 주의 해야 합니다.

이 문서에서는에서 개체를 삭제 하는 방법을 보여 줍니다.

- [목록](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)

- [배열](#_core_to_delete_all_elements_in_an_array)

- [지도](#_core_to_delete_all_elements_in_a_map)

#### <a name="to-delete-all-objects-in-a-list-of-pointers-to-cobject"></a><a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a> CObject에 대 한 포인터 목록의 모든 개체를 삭제 하려면

1. `GetHeadPosition`및 `GetNext` 를 사용 하 여 목록을 반복 합니다.

1. **`delete`** 반복에서 발생 한 각 개체를 삭제 하려면 연산자를 사용 합니다.

1. 함수를 호출 `RemoveAll` 하 여 해당 요소와 연결 된 개체가 삭제 된 후 목록에서 모든 요소를 제거 합니다.

다음 예제에서는 개체 목록에서 모든 개체를 삭제 하는 방법을 보여 줍니다 `CPerson` . 목록의 각 개체는 처음에 힙에 할당 된 개체에 대 한 포인터입니다 `CPerson` .

[!code-cpp[NVC_MFCCollections#17](codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]

마지막 함수 호출 인는 목록 `RemoveAll` 에서 모든 요소를 제거 하는 목록 멤버 함수입니다. 멤버 함수는 `RemoveAt` 단일 요소를 제거 합니다.

요소의 개체를 삭제 하 고 요소 자체를 제거할 때의 차이점을 확인 합니다. 목록에서 요소를 제거 하기만 하면 개체에 대 한 목록 참조가 제거 됩니다. 개체가 여전히 메모리에 있습니다. 개체를 삭제 하면 개체가 존재 하지 않게 되 고 해당 메모리가 회수 됩니다. 따라서 요소가 더 이상 존재 하지 않는 개체에 대 한 액세스를 시도 하지 않도록 요소의 개체가 삭제 된 직후에 요소를 제거 하는 것이 중요 합니다.

#### <a name="to-delete-all-elements-in-an-array"></a><a name="_core_to_delete_all_elements_in_an_array"></a> 배열의 모든 요소를 삭제 하려면

1. `GetSize`및 정수 인덱스 값을 사용 하 여 배열 전체를 반복 합니다.

1. **`delete`** 반복에서 발생 하는 각 요소를 삭제 하려면 연산자를 사용 합니다.

1. 함수를 호출 `RemoveAll` 하 여 배열의 모든 요소를 삭제 한 후 제거 합니다.

   배열의 모든 요소를 삭제 하는 코드는 다음과 같습니다.

   [!code-cpp[NVC_MFCCollections#18](codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]

위의 목록 예제와 마찬가지로 `RemoveAll` 를 호출 하 여 배열의 모든 요소를 제거 하거나 `RemoveAt` 개별 요소를 제거할 수 있습니다.

#### <a name="to-delete-all-elements-in-a-map"></a><a name="_core_to_delete_all_elements_in_a_map"></a> Map의 모든 요소를 삭제 하려면

1. `GetStartPosition`및 `GetNextAssoc` 를 사용 하 여 배열을 반복 합니다.

1. **`delete`** 반복에서 발생 하는 각 지도 요소에 대 한 키 및/또는 값을 삭제 하려면 연산자를 사용 합니다.

1. 함수를 호출 `RemoveAll` 하 여 맵에서 삭제 된 모든 요소를 제거 합니다.

   컬렉션의 모든 요소를 삭제 하는 코드는 `CMap` 다음과 같습니다. 맵의 각 요소는 문자열을 키로, `CPerson` 개체 (에서 파생 됨 `CObject` )를 값으로 가집니다.

   [!code-cpp[NVC_MFCCollections#19](codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]

`RemoveAll`를 호출 하 여 map의 모든 요소를 제거 하거나 `RemoveKey` 지정 된 키를 가진 개별 요소를 제거할 수 있습니다.

## <a name="see-also"></a>참고 항목

[컬렉션의 모든 멤버에 액세스](accessing-all-members-of-a-collection.md)
