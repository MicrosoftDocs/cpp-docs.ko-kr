---
title: '방법: unique_ptr 인스턴스 만들기 및 사용'
ms.custom: how-to
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
ms.openlocfilehash: 4b3362f71d1ccab0efb03d7e8705c6b3f25f9780
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246533"
---
# <a name="how-to-create-and-use-unique_ptr-instances"></a>방법: unique_ptr 인스턴스 만들기 및 사용

[Unique_ptr](../standard-library/unique-ptr-class.md) 는 포인터를 공유 하지 않습니다. 다른 `unique_ptr`로 복사 하거나, 함수에 값으로 전달 하거나, 복사본을 만들어야 하는 C++ 표준 라이브러리 알고리즘에서 사용할 수 없습니다. `unique_ptr`은 이동만 할 수 있습니다. 즉, 메모리 리소스의 소유권이 다른 `unique_ptr`로 이전되어 원래 `unique_ptr`이 더 이상 소유하지 않습니다. 소유권이 여러 개이면 프로그램 논리가 복잡해지기 때문에 개체를 하나의 소유자로 제한하는 것이 좋습니다. 따라서 일반 C++ 개체에 대 한 스마트 포인터가 필요한 경우 `unique_ptr`를 사용 하 고 `unique_ptr`을 생성할 때 [make_unique](../standard-library/memory-functions.md#make_unique) 도우미 함수를 사용 합니다.

다음 다이어그램은 두 `unique_ptr` 인스턴스 사이의 소유권 이전을 보여 줍니다.

![고유한&#95;ptr의 소유권 이동](media/unique_ptr.png "고유한&#95;ptr의 소유권 이동")

`unique_ptr`는 C++ 표준 라이브러리의 `<memory>` 헤더에 정의 되어 있습니다. 정확 하 게 원시 포인터 만큼 효율적이 고 C++ 표준 라이브러리 컨테이너에서 사용할 수 있습니다. `unique_ptr`의 이동 생성자는 복사 C++ 작업을 수행 하지 않아도 되므로 표준 라이브러리 컨테이너에 `unique_ptr` 인스턴스를 추가 하는 것이 효율적입니다.

## <a name="example-1"></a>예 1

다음 예제에서는 `unique_ptr` 인스턴스를 어떻게 만들고 이를 함수 사이에서 어떻게 전달하는지를 보여 줍니다.

[!code-cpp[stl_smart_pointers#210](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]

이러한 예는 `unique_ptr`의 기본적인 특징을 보여 주며 이동은 가능하지만 복사되지 않을 수 있습니다. "이동"이 소유권을 새 `unique_ptr`로 이전하고 이전 `unique_ptr`을 다시 설정합니다.

## <a name="example-2"></a>예 2

다음 예제에서는 `unique_ptr` 인스턴스를 만들고 이를 벡터에 사용하는 방법을 보여 줍니다.

[!code-cpp[stl_smart_pointers#211](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]

루프 범위에서 `unique_ptr`이 참조로 전달됩니다. 여기에서 값으로 전달하려는 경우 `unique_ptr` 복사 생성자가 삭제되기 때문에 컴파일러는 오류를 throw합니다.

## <a name="example-3"></a>예 3

다음 예제에서는 클래스 멤버인 `unique_ptr`을 초기화하는 방법을 보여 줍니다.

[!code-cpp[stl_smart_pointers#212](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]

## <a name="example-4"></a>예제 4

[Make_unique](../standard-library/memory-functions.md#make_unique) 를 사용 하 여 배열에 대 한 `unique_ptr`를 만들 수 있지만 `make_unique`를 사용 하 여 배열 요소를 초기화할 수는 없습니다.

[!code-cpp[stl_smart_pointers#213](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]

더 많은 예제를 보려면 [make_unique](../standard-library/memory-functions.md#make_unique)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[스마트 포인터(모던 C++)](smart-pointers-modern-cpp.md)<br/>
[make_unique](../standard-library/memory-functions.md#make_unique)
