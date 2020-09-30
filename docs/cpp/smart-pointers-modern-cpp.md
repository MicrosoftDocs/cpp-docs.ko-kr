---
title: 스마트 포인터(최신 C++)
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
ms.openlocfilehash: e511cc513cdb35b06b976ce022c5e4edea35040b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500679"
---
# <a name="smart-pointers-modern-c"></a>스마트 포인터(최신 C++)

최신 c + + 프로그래밍에서 표준 라이브러리에는 프로그램이 메모리 및 리소스 누수를 방지 하 고 예외를 안전 하 게 유지 하는 데 사용 되는 *스마트 포인터가*포함 되어 있습니다.

## <a name="uses-for-smart-pointers"></a>스마트 포인터 용도

스마트 포인터는 `std` 헤더 파일의 네임 스페이스에 정의 됩니다 [\<memory>](../standard-library/memory.md) . 이러한 기능은 [RAII](./object-lifetime-and-resource-management-modern-cpp.md) 또는 *리소스 획득이 초기화* 프로그래밍 방식에 중요 합니다. 이 관용구의 주요 목표는 개체의 모든 자원 생성이 한 줄의 코드에서 만들어지고 준비되어 그 개체가 초기화되는 동시에 자원 수집이 발생하는 것을 확인하는 것입니다. 실제로 RAII의 기본 원칙은 힙 할당 리소스(예: 동적 할당 메모리 또는 시스템 개체 핸들)의 소유권을 해당 소멸자가 리소스를 삭제하거나 비우는 코드 및 모든 관련 정리 코드가 포함된 스택 할당 개체에 제공하는 것입니다.

대부분의 경우 실제 리소스를 가리키도록 기본 포인터 또는 리소스 핸들을 초기화할 때는 포인터를 스마트 포인터로 즉시 전달합니다. 현대적인 C++에서 기본 포인터는 성능이 중요하며, 소유권 관련 혼동 여지가 없는 제한된 범위, 루프 또는 지원 함수의 작은 코드 블록에서만 사용됩니다.

다음 예제에서는 원시 포인터 선언을 스마트 포인터 선언과 비교합니다.

[!code-cpp[smart_pointers_intro#1](codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]

예제에서와 같이 스마트 포인터는 스택에서 선언되고 힙 할당 개체를 가리키는 원시 포인터를 사용하여 초기화하는 스마트 포인터입니다. 스마트 포인터가 초기화되면 원시 포인터를 소유합니다. 원시 포인터가 지정한 메모리를 스마트 포인터가 삭제해야 함을 의미합니다. 스마트 포인터 소멸자에는 삭제할 호출이 포함되며, 스마트 포인터는 스택에 선언되기 때문에 스마트 포인터가 범위를 벗어나면 스택의 다른 위치에서 예외가 throw되더라도 해당 소멸자가 호출됩니다.

스마트 포인터 클래스 오버로드가 캡슐화된 원시 포인터를 반환하는 익숙한 포인터 연산자인 `->` 및 `*`를 사용하여 캡슐화된 포인터에 액세스합니다.

C++ 스마트 포인터 관용구는 C# 같은 언어에서의 개체 생성과 유사합니다. 즉 개체를 생성한 후 시스템이 정확한 시간에 그것을 지울 수 있도록 합니다. 백그라운드에서 실행된 별도 가비지 컬렉션기는 런타임 환경을 빠르고 효율적이게 만드는 표준 C++ 범위 지정 규칙을 통해 관리되는 메모리라는 것이 차이점입니다.

> [!IMPORTANT]
> 매개 변수 목록이 아닌 별도 코드 줄에서 스마트 포인터를 만들어야 특정 매개 변수 목록 할당 규칙으로 인해 아주 작은 리소스 누수도 발생하지 않습니다.

다음 예제에서는 `unique_ptr` c + + 표준 라이브러리의 스마트 포인터 형식을 사용 하 여 여러 개체에 대 한 포인터를 캡슐화 하는 방법을 보여 줍니다.

[!code-cpp[smart_pointers_intro#2](codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]

이 예제는 다음과 같이 스마트 포인터를 사용하는 필수 단계를 보여 줍니다.

1. 스마트 포인터를 자동(지역) 변수로 선언합니다. ( **`new`** `malloc` 스마트 포인터 자체에 또는 식을 사용 하지 마십시오.)

1. 형식 매개 변수에서 캡슐화된 포인터가 가리키는 대상의 형식을 지정합니다.

1. 원시 포인터를 **`new`** 스마트 포인터 생성자의-ed 개체에 전달 합니다. (일부 유틸리티 기능 또는 스마트 포인터 생성자로 이 작업을 자동으로 수행할 수 있습니다.)

1. 오버로드된 `->` 및 `*` 연산자를 사용하여 개체에 액세스합니다.

1. 스마트 포인터로 개체를 삭제할 수 있습니다.

스마트 포인터는 메모리 및 성능 관점에서 최대한 효율적으로 사용할 수 있도록 설계되었습니다. 예를 들어, `unique_ptr`의 유일한 데이터 멤버는 캡슐화된 포인터입니다. 즉, `unique_ptr`은 해당 포인터와 정확히 동일한 크기(4바이트 또는 8바이트)입니다. 스마트 포인터 오버 로드 된 * 및-> 연산자를 사용 하 여 캡슐화 된 포인터에 액세스 하면 원시 포인터에 직접 액세스 하는 것 보다 훨씬 느립니다.

스마트 포인터에는 "점" 표기법을 사용 하 여 액세스 하는 고유한 멤버 함수가 있습니다. 예를 들어 일부 c + + 표준 라이브러리 스마트 포인터에는 포인터 소유권을 해제 하는 reset 멤버 함수가 있습니다. 다음 예에 표시된 것처럼 스마트 포인터가 범위를 벗어나기 전에 스마트 포인터에서 소유하는 메모리를 비우려는 경우에 유용합니다.

[!code-cpp[smart_pointers_intro#3](codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]

스마트 포인터는 일반적으로 원시 포인터를 직접 액세스하는 방법을 제공합니다. C + + 표준 라이브러리 스마트 포인터에는 `get` 이 목적에 대 한 멤버 함수가 있으며 `CComPtr` public `p` 클래스 멤버가 있습니다. 기본 포인터에 대한 직접 액세스를 제공하면 스마트 포인터를 사용하여 자체 코드에서 메모리를 관리하고 스마트 포인터를 지원하지 않는 코드에 원시 포인터를 전달할 수 있습니다.

[!code-cpp[smart_pointers_intro#4](codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]

## <a name="kinds-of-smart-pointers"></a>스마트 포인터의 종류

다음 섹션에서는 다양한 종류의 Windows 프로그래밍 환경에서 사용할 수 있는 스마트 포인터에 대한 정보를 요약하고 사용하는 경우에 대해 설명합니다.

### <a name="c-standard-library-smart-pointers"></a>C + + 표준 라이브러리 스마트 포인터

POCO(Plain Old C++ 개체)에 대한 포인터를 캡슐화하는 데 가장 먼저 스마트 포인터를 사용합니다.

- `unique_ptr`<br/>
   기본 포인터로 한 명의 소유자만 허용합니다. `shared_ptr`이 필요하다는 점을 확실히 알 경우 POCO의 기본 선택으로 사용합니다. 새 소유자로 이동할 수 있지만 복사하거나 공유할 수 없습니다. 사용하지 않는 `auto_ptr`을 대체합니다. `boost::scoped_ptr`과 비교합니다. `unique_ptr` 는 작고 효율적입니다. 크기는 하나의 포인터 이며, c + + 표준 라이브러리 컬렉션에서 빠른 삽입 및 검색을 위해 rvalue 참조를 지원 합니다. 헤더 파일: `<memory>`. 자세한 내용은 [방법: Unique_ptr 인스턴스](how-to-create-and-use-unique-ptr-instances.md) 및 [unique_ptr 클래스](../standard-library/unique-ptr-class.md)만들기 및 사용을 참조 하세요.

- `shared_ptr`<br/>
   참조 횟수가 계산되는 스마트 포인터입니다. 원시 포인터 하나를 여러 소유자에게 할당하려고 할 경우 사용합니다(예: 컨테이너에서 포인터 복사본을 반환할 때 원본을 유지하고 싶을 경우). 원시 포인터는 모든 `shared_ptr` 소유자가 범위를 벗어나거나 소유권을 포기할 때까지 삭제되지 않습니다. 크기는 2개의 포인터입니다. 하나는 개체용이고, 다른 하나는 참조 횟수가 포함된 공유 제어 블록용입니다. 헤더 파일: `<memory>`. 자세한 내용은 [방법: Shared_ptr 인스턴스](how-to-create-and-use-shared-ptr-instances.md) 및 [shared_ptr 클래스](../standard-library/shared-ptr-class.md)만들기 및 사용을 참조 하세요.

- `weak_ptr`<br/>
    `shared_ptr`과 함께 사용할 수 있는 특별한 경우의 스마트 포인터입니다. `weak_ptr`은 하나 이상의 `shared_ptr` 인스턴스가 소유하는 개체에 대한 액세스를 제공하지만, 참조 수 계산에 참가하지 않습니다. 개체를 관찰하는 동시에 해당 개체를 활성 상태로 유지하지 않으려는 경우 사용합니다. `shared_ptr` 인스턴스 사이의 순환 참조를 차단하기 위해 필요한 경우도 있습니다. 헤더 파일: `<memory>`. 자세한 내용은 [방법: Weak_ptr 인스턴스](how-to-create-and-use-weak-ptr-instances.md) 및 [weak_ptr 클래스](../standard-library/weak-ptr-class.md)만들기 및 사용을 참조 하세요.

### <a name="smart-pointers-for-com-objects-classic-windows-programming"></a>COM 개체의 스마트 포인터 (클래식 Windows 프로그래밍)

COM 개체를 사용하는 경우 인터페이스 포인터를 적절한 스마트 포인터 형식으로 래핑합니다. ATL(Active Template Library)은 다양한 목적을 위해 여러 스마트 포인터를 정의합니다. .tlb 파일에서 래퍼 클래스를 만들 때 컴파일러가 사용하는 `_com_ptr_t` 스마트 포인터 형식을 사용할 수도 있습니다. ATL 헤더 파일을 포함하지 않으려는 경우에 가장 좋습니다.

[CComPtr 클래스](../atl/reference/ccomptr-class.md)<br/>
ATL을 사용할 수 없는 이상 이 형식을 사용합니다. `AddRef` 및 `Release` 메서드를 사용하여 참조 수 계산을 수행합니다. 자세한 내용은 [How to: Create And Use CComPtr And CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)항목을 참조 하세요.

[CComQIPtr 클래스](../atl/reference/ccomqiptr-class.md)<br/>
`CComPtr`과 유사하지만 COM 개체에서 `QueryInterface`를 호출하는 간단한 구문을 제공합니다. 자세한 내용은 [How to: Create And Use CComPtr And CComQIPtr Instances](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)항목을 참조 하세요.

[CComHeapPtr 클래스](../atl/reference/ccomheapptr-class.md)<br/>
`CoTaskMemFree`를 사용하여 메모리를 해제하는 개체에 대한 스마트 포인터

[CComGITPtr 클래스](../atl/reference/ccomgitptr-class.md)<br/>
GIT(전역 인터페이스 테이블)에서 가져온 인터페이스에 대한 스마트 포인터입니다.

[_com_ptr_t 클래스](com-ptr-t-class.md)<br/>
기능 면에서 `CComQIPtr`과 유사하지만 ATL 헤더에 의존하지 않습니다.

### <a name="atl-smart-pointers-for-poco-objects"></a>POCO 개체에 대 한 ATL 스마트 포인터

ATL은 COM 개체에 대 한 스마트 포인터 외에도 일반적인 이전 c + + 개체 (POCO)에 대 한 스마트 포인터 및 스마트 포인터 컬렉션을 정의 합니다. 클래식 Windows 프로그래밍에서 이러한 형식은 c + + 표준 라이브러리 컬렉션에 대 한 유용한 대안이 며, 특히 코드 이식성이 필요 하지 않거나 c + + 표준 라이브러리 및 ATL의 프로그래밍 모델을 혼합 하지 않으려는 경우에 유용 합니다.

[CAutoPtr 클래스](../atl/reference/cautoptr-class.md)<br/>
복사 소유권을 전송하여 고유 소유권을 적용하는 스마트 포인터입니다. 사용되지 않는 `std::auto_ptr` 클래스에 비교할 수 있습니다.

[CHeapPtr 클래스](../atl/reference/cheapptr-class.md)<br/>
C [malloc](../c-runtime-library/reference/malloc.md) 함수를 사용 하 여 할당 된 개체에 대 한 스마트 포인터입니다.

[CAutoVectorPtr 클래스](../atl/reference/cautovectorptr-class.md)<br/>
배열을 위해 `new[]`를 사용하여 할당하는 스마트 포인터입니다.

[CAutoPtrArray 클래스](../atl/reference/cautoptrarray-class.md)<br/>
`CAutoPtr` 요소 배열을 캡슐화하는 클래스입니다.

[CAutoPtrList 클래스](../atl/reference/cautoptrlist-class.md)<br/>
`CAutoPtr` 노드 목록을 조작하기 위해 메서드를 캡슐화하는 클래스입니다.

## <a name="see-also"></a>참고 항목

[포인터](pointers-cpp.md)<br/>
[C++ 언어 참조](../cpp/cpp-language-reference.md)<br/>
[C + + 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)
