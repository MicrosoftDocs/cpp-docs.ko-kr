---
description: '자세한 정보: 메모리 관리: 예제'
title: '메모리 관리: 예'
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], memory allocation
- data structures [MFC]
- arrays [MFC], allocating resources
- objects [MFC], allocating memory
- data structures [MFC], allocating memory
- examples [MFC], memory allocation
- heap allocation [MFC], examples
- memory allocation [MFC], arrays
- MFC, memory management
- struct memory allocation [MFC]
- types [MFC], memory allocation
- memory allocation [MFC], objects
- memory allocation [MFC], examples
- arrays [MFC], memory management
- frame allocation [MFC]
- memory allocation [MFC], data structures
ms.assetid: f10240f8-b698-4c83-9288-97a54318930b
ms.openlocfilehash: dcd7ba9ce5fee0af932766494f0a7afd64684e77
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222296"
---
# <a name="memory-management-examples"></a>메모리 관리: 예

이 문서에서는 다음과 같은 세 가지 일반적인 종류의 메모리 할당 각각에 대해 MFC에서 프레임 할당과 힙 할당을 수행 하는 방법을 설명 합니다.

- [바이트 배열입니다.](#_core_allocation_of_an_array_of_bytes)

- [데이터 구조](#_core_allocation_of_a_data_structure)

- [개체](#_core_allocation_of_an_object)

## <a name="allocation-of-an-array-of-bytes"></a><a name="_core_allocation_of_an_array_of_bytes"></a> 바이트 배열 할당

#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>프레임에 바이트 배열을 할당 하려면

1. 다음 코드에 표시 된 대로 배열을 정의 합니다. 배열 변수가 범위를 벗어나면 배열이 자동으로 삭제 되 고 메모리가 회수 됩니다.

   [!code-cpp[NVC_MFC_Utilities#1](codesnippet/cpp/memory-management-examples_1.cpp)]

#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>힙에서 바이트 배열 (또는 기본 데이터 형식)을 할당 하려면

1. **`new`** 이 예제에 표시 된 배열 구문과 연산자를 사용 합니다.

   [!code-cpp[NVC_MFC_Utilities#2](codesnippet/cpp/memory-management-examples_2.cpp)]

#### <a name="to-deallocate-the-arrays-from-the-heap"></a>힙에서 배열을 할당 취소 하려면

1. 다음과 같이 연산자를 사용 합니다 **`delete`** .

   [!code-cpp[NVC_MFC_Utilities#3](codesnippet/cpp/memory-management-examples_3.cpp)]

## <a name="allocation-of-a-data-structure"></a><a name="_core_allocation_of_a_data_structure"></a> 데이터 구조 할당

#### <a name="to-allocate-a-data-structure-on-the-frame"></a>프레임에 데이터 구조를 할당 하려면

1. 다음과 같이 structure 변수를 정의 합니다.

   [!code-cpp[NVC_MFC_Utilities#4](codesnippet/cpp/memory-management-examples_4.cpp)]

   구조에서 차지 하는 메모리는 해당 범위를 종료할 때 회수 됩니다.

#### <a name="to-allocate-data-structures-on-the-heap"></a>힙에서 데이터 구조를 할당 하려면

1. **`new`** 다음 예제와 같이를 사용 하 여 힙에서 데이터 구조를 할당 하 고 할당을 취소 합니다 **`delete`** .

   [!code-cpp[NVC_MFC_Utilities#5](codesnippet/cpp/memory-management-examples_5.cpp)]

## <a name="allocation-of-an-object"></a><a name="_core_allocation_of_an_object"></a> 개체 할당

#### <a name="to-allocate-an-object-on-the-frame"></a>프레임에 개체를 할당 하려면

1. 다음과 같이 개체를 선언 합니다.

   [!code-cpp[NVC_MFC_Utilities#6](codesnippet/cpp/memory-management-examples_6.cpp)]

   개체의 소멸자가 개체의 범위를 벗어나면 자동으로 호출 됩니다.

#### <a name="to-allocate-an-object-on-the-heap"></a>힙에 개체를 할당 하려면

1. **`new`** 개체에 대 한 포인터를 반환 하는 연산자를 사용 하 여 힙에 개체를 할당 합니다. 연산자를 사용 **`delete`** 하 여 삭제 합니다.

   다음 힙 및 프레임 예제에서는 생성자가 인수를 사용 하지 않는다고 가정 합니다 `CPerson` .

   [!code-cpp[NVC_MFC_Utilities#7](codesnippet/cpp/memory-management-examples_7.cpp)]

   생성자에 대 한 인수가 `CPerson` 에 대 한 포인터인 경우 **`char`** 프레임 할당에 대 한 문은 다음과 같습니다.

   [!code-cpp[NVC_MFC_Utilities#8](codesnippet/cpp/memory-management-examples_8.cpp)]

   힙 할당에 대 한 문은 다음과 같습니다.

   [!code-cpp[NVC_MFC_Utilities#9](codesnippet/cpp/memory-management-examples_9.cpp)]

## <a name="see-also"></a>참고 항목

[메모리 관리: 힙 할당](memory-management-heap-allocation.md)
