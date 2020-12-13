---
description: '자세한 정보: 샘플 컨테이너 클래스'
title: Sample Container 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- container classes [C++]
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
ms.openlocfilehash: 728cec44462a8e09aad7f87000520f0fa5a15b3a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148878"
---
# <a name="sample-container-class"></a>Sample Container 클래스

> [!NOTE]
> 이 항목은 c + + 표준 라이브러리에서 사용 되는 컨테이너의 작동 하지 않는 예제로 Microsoft c + + 설명서에 있습니다. 자세한 내용은 [C++ 표준 라이브러리 컨테이너](../standard-library/stl-containers.md)를 참조하세요.

일반적으로 형식의 다양 한 길이의 요소 시퀀스를 제어 하는 개체에 대해 설명 합니다 `Ty` . 시퀀스는 실제 컨테이너에 따라 다른 방식으로 저장됩니다.

컨테이너 생성자 또는 구성원 함수는 생성자 **Ty**(**const Ty&**) 또는 함수 **Ty::operator=**(**const Ty&**)를 호출할 수 있습니다. 이러한 호출에서 예외가 throw되면 container 개체는 무결성을 유지하고 catch하는 예외를 다시 throw해야 합니다. container 개체가 이러한 예외 중 하나를 throw한 후에도 해당 개체를 안전하게 교환, 할당, 제거하거나 지울 수 있습니다. 그러나 일반적으로는 container 개체가 제어하는 시퀀스의 상태를 예측할 수 없습니다.

이와 관련한 몇 가지 추가 주의 사항은 다음과 같습니다.

- 식이 예외를 `~Ty` throw 하는 경우 컨테이너 개체의 결과 상태는 정의 되지 않습니다.

- 컨테이너가 할당자 개체 *al* 을 저장 하 고 *al* 이에 대 한 호출의 결과로 예외를 throw 하는 경우 `al.allocate` 컨테이너 개체의 결과 상태는 정의 되지 않습니다.

- 컨테이너가 제어되는 시퀀스의 순서를 지정할 방법을 결정하기 위해 function 개체 *comp* 를 저장하는 경우 *comp* 가 종류와 관계없이 예외를 throw하면 container 개체의 결과 상태는 정의되지 않습니다.

다음 단락에서 설명하는 것처럼, C++ 표준 라이브러리를 통해 정의되는 container 클래스는 여러 가지 추가 요구 사항을 충족합니다.

컨테이너 클래스 템플릿 [목록](../standard-library/list-class.md) 위에 설명 된 예외가 있는 경우에도 결정적이 고 유용한 동작을 제공 합니다. 예를 들어 요소 하나 이상을 삽입하는 동안 예외가 throw되어도 컨테이너는 변경되지 않고 그대로 유지되며 예외가 다시 throw됩니다.

C + + 표준 라이브러리에 의해 정의 된 *모든* 컨테이너 클래스에 대해,, 또는 멤버 함수를 호출 하는 동안 예외가 throw 되 면 `insert` 컨테이너는 `push_back` `push_front` 변경 되지 않은 상태로 유지 되며 예외가 다시 throw 됩니다.

C + + 표준 라이브러리에 의해 정의 된 *모든* 컨테이너 클래스에 대해 다음 멤버 함수를 호출 하는 동안 예외가 throw 되지 않습니다. `pop_back` , `pop_front` .

구성원 함수 [erase](../standard-library/container-class-erase.md)는 복사 작업(할당 또는 복사본 생성)에서 예외가 throw되는 경우에만 예외를 throw합니다.

또한 구성원 함수가 반환하는 반복기를 복사하는 동안에는 예외가 throw되지 않습니다.

구성원 함수 [swap](../standard-library/container-class-swap.md)은 C++ 표준 라이브러리를 통해 정의되는 *모든* 컨테이너 클래스에 대해 다음과 같은 사항을 추가로 보장합니다.

- 구성원 함수는 컨테이너가 allocator 개체 al을 저장하며 복사 시에 `al`이 예외를 throw하는 경우에만 예외를 throw합니다.

- 교환 중에 제어되는 시퀀스의 요소를 지정하는 참조, 포인터 및 반복기는 유효한 상태로 유지됩니다.

C++ 표준 라이브러리를 통해 정의되는 컨테이너 클래스의 개체는 `Alloc` 형식의 저장된 개체(대개 템플릿 매개 변수)를 통해 제어하는 시퀀스용 스토리지를 할당하고 확보합니다. 이러한 할당자 개체에는 클래스의 개체와 동일한 외부 인터페이스가 있어야 합니다 `allocator<Ty>` . 특히는 `Alloc` 와 동일한 형식 이어야 합니다. `Alloc::rebind<value_type>::other`

C + + 표준 라이브러리에 의해 정의 된 *모든* 컨테이너 클래스에 대해 멤버 함수는 `Alloc get_allocator const;` 저장 된 할당자 개체의 복사본을 반환 합니다. 컨테이너 개체를 할당 하는 경우 저장 된 할당자 개체는 복사 *되지 않습니다* . `allocator` `Alloc` 생성자에 할당자 매개 변수가 포함 되어 있지 않은 경우 모든 생성자는에 저장 된 값을로 초기화 합니다.

C++ 표준에 따라 C++ 표준 라이브러리를 통해 정의되는 컨테이너 클래스에 대해서는 다음 사항을 가정할 수 있습니다.

- `Alloc` 클래스의 모든 개체는 비교 시 동일합니다.

- 형식은 `Alloc::const_pointer` 와 같습니다 `const Ty *` .

- 형식은 `Alloc::const_reference` 와 같습니다 `const Ty&` .

- 형식은 `Alloc::pointer` 와 같습니다 `Ty *` .

- 형식은 `Alloc::reference` 와 같습니다 `Ty&` .

그러나 이 구현에서 컨테이너는 이와 같이 단순한 가정을 하지 않습니다. 따라서 보다 복잡한 allocator 개체와도 적절하게 연동됩니다.

- 클래스 `Alloc`의 모든 개체는 비교 시 같을 필요가 없습니다. (여러 스토리지 풀을 유지 관리하면 되기 때문입니다.)

- 형식은 `Alloc::const_pointer` 와 같을 필요가 없습니다 `const Ty *` . const 포인터는 클래스일 수도 있습니다.

- 형식은 `Alloc::pointer` 와 같을 필요가 없습니다 `Ty *` . 포인터는 클래스일 수도 있습니다.

## <a name="requirements"></a>요구 사항

**헤더**: \<sample container>

## <a name="see-also"></a>참고 항목

[\<sample container>](../standard-library/sample-container.md)
