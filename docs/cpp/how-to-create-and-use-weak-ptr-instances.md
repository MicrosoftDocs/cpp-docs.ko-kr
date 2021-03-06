---
description: '자세한 정보: 방법: weak_ptr 인스턴스 만들기 및 사용'
title: '방법: weak_ptr 인스턴스 만들기 및 사용'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
ms.openlocfilehash: 1c28ca6d759be513347885ead82498877e935a60
ms.sourcegitcommit: c0c9cdae79f19655e809a4979227c51bb19cff63
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102236753"
---
# <a name="how-to-create-and-use-weak_ptr-instances"></a>방법: weak_ptr 인스턴스 만들기 및 사용

경우에 따라 개체가 참조 횟수를 증가 시 키 지 않고 [shared_ptr](../standard-library/shared-ptr-class.md) 의 기본 개체에 액세스 하는 방법을 저장 해야 합니다. 일반적으로 인스턴스 사이에 순환 참조가 있는 경우 이러한 상황이 발생 `shared_ptr` 합니다.

가능 하면 언제 든 지 포인터의 공유 소유권을 방지 하는 것이 가장 좋습니다. 그러나 인스턴스의 공유 소유권이 있어야 하는 경우에는 `shared_ptr` 두 항목 사이에 순환 참조를 사용 하지 마십시오. 순환 참조가 피할 수 없는 경우 또는 어떤 이유로 든 더 유용한 경우 [weak_ptr](../standard-library/weak-ptr-class.md) 를 사용 하 여 하나 이상의 소유자에 게 다른 소유자에 대 한 약한 참조를 제공 합니다 `shared_ptr` . 를 사용 하 여 `weak_ptr` `shared_ptr` 기존 관련 인스턴스 집합에 조인 하는을 만들 수 있습니다. 단, 기본 메모리 리소스가 여전히 유효 합니다. `weak_ptr`자체는 참조 횟수에 참여 하지 않기 때문에 참조 횟수를 0으로 이동 하는 것을 방지할 수 없습니다. 그러나를 사용 하 여 `weak_ptr` 이 초기화 된의 새 복사본을 가져오려고 시도할 수 있습니다 `shared_ptr` . 메모리가 이미 삭제 된 경우 `weak_ptr` 의 bool 연산자는를 반환 **`false`** 합니다. 메모리가 여전히 유효한 경우 새 공유 포인터는 참조 횟수를 증가 시키고 `shared_ptr` 변수가 범위 내에 있는 한 메모리를 유효 하 게 유지 하도록 보장 합니다.

## <a name="example"></a>예

다음 코드 예제에서는 `weak_ptr` 순환 종속성이 있는 개체를 적절 하 게 삭제 하기 위해가 사용 되는 경우를 보여 줍니다. 예제를 검토할 때 대체 솔루션이 고려 된 후에만 생성 된 것으로 가정 합니다. `Controller`개체는 컴퓨터 프로세스의 일부 측면을 나타내며 독립적으로 작동 합니다. 각 컨트롤러는 언제 든 지 다른 컨트롤러의 상태를 쿼리할 수 있어야 하며 각 컨트롤러 `vector<weak_ptr<Controller>>` 에는이 목적에 대 한 개인이 포함 되어 있습니다. 각 벡터에는 순환 참조가 포함 되므로 `weak_ptr` 인스턴스가 대신 사용 됩니다 `shared_ptr` .

[!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]

```Output
Creating Controller0
Creating Controller1
Creating Controller2
Creating Controller3
Creating Controller4
push_back to v[0]: 1
push_back to v[0]: 2
push_back to v[0]: 3
push_back to v[0]: 4
push_back to v[1]: 0
push_back to v[1]: 2
push_back to v[1]: 3
push_back to v[1]: 4
push_back to v[2]: 0
push_back to v[2]: 1
push_back to v[2]: 3
push_back to v[2]: 4
push_back to v[3]: 0
push_back to v[3]: 1
push_back to v[3]: 2
push_back to v[3]: 4
push_back to v[4]: 0
push_back to v[4]: 1
push_back to v[4]: 2
push_back to v[4]: 3
use_count = 1
Status of 1 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 2 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 2 = On
Status of 3 = On
Destroying Controller0
Destroying Controller1
Destroying Controller2
Destroying Controller3
Destroying Controller4
Press any key
```

실험으로 벡터를로 수정 하 `others` `vector<shared_ptr<Controller>>` 고 출력에서가 반환 될 때 소멸자가 호출 되지 않는지 확인 `RunTest` 합니다.

## <a name="see-also"></a>참고 항목

[스마트 포인터 (최신 c + +)](../cpp/smart-pointers-modern-cpp.md)
