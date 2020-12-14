---
description: '자세한 정보: Microsoft:: WRL::D etails 네임 스페이스'
title: Microsoft::WRL::Details 네임스페이스
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
ms.openlocfilehash: c82d7389c80d35aa041dccc7c6bc8d202fba9c29
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195114"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details 네임스페이스

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
namespace Microsoft::WRL::Details;
```

## <a name="members"></a>멤버

### <a name="classes"></a>클래스

|이름|설명|
|----------|-----------------|
|[ComPtrRef 클래스](comptrref-class.md)|ComPtr 형식의 개체에 대 한 참조를 나타냅니다 \<T> .|
|[ComPtrRefBase 클래스](comptrrefbase-class.md)|[Comptrref](comptrref-class.md) 클래스의 기본 클래스를 나타냅니다.|
|[DontUseNewUseMake 클래스](dontusenewusemake-class.md)|에서 연산자를 사용할 수 없습니다 `new` `RuntimeClass` . 따라서 대신이 [함수](make-function.md) 를 사용 해야 합니다.|
|[EventTargetArray 클래스](eventtargetarray-class.md)|이벤트 처리기의 배열을 나타냅니다.|
|[MakeAllocator 클래스](makeallocator-class.md)|약한 참조 지원을 사용 하거나 사용 하지 않고 활성화 가능한 클래스에 대해 메모리를 할당 합니다.|
|[ModuleBase 클래스](modulebase-class.md)|[모듈](module-class.md) 클래스의 기본 클래스를 나타냅니다.|
|[RemoveIUnknown 클래스](removeiunknown-class.md)|는 `IUnknown` 기반 형식과 동일 하지만 비가상 `QueryInterface` , 및 메서드를 포함 하는 형식을 만듭니다 `AddRef` `Release` .|
|[WeakReference 클래스](weakreference-class.md)|Windows 런타임 또는 클래식 COM과 함께 사용할 수 있는 *약한 참조* 를 나타냅니다. 약한 참조는 액세스할 수 있거나 액세스할 수 없는 개체를 나타냅니다.|

### <a name="structures"></a>구조체

|Name|설명|
|----------|-----------------|
|[ArgTraits 구조체](argtraits-structure.md)|지정 된 대리자 인터페이스와 지정 된 수의 매개 변수를 포함 하는 익명 멤버 함수를 선언 합니다.|
|[ArgTraitsHelper 구조체](argtraitshelper-structure.md)|대리자 인수의 일반적인 특성을 정의 하는 데 도움이 됩니다.|
|[BoolStruct 구조체](boolstruct-structure.md)|가 `ComPtr` 인터페이스의 개체 수명을 관리 하는지 여부를 정의 합니다. `BoolStruct` 은 [BoolType ()](comptr-class.md#operator-microsoft-wrl-details-booltype) 연산자에 의해 내부적으로 사용 됩니다.|
|[CreatorMap 구조체](creatormap-structure.md)|개체를 초기화, 등록 및 등록 취소 하는 방법에 대 한 정보를 포함 합니다.|
|[DerefHelper 구조체](derefhelper-structure.md)|템플릿 매개 변수에 대 한 역참조 된 포인터를 나타냅니다 `T*` .|
|[EnableIf 구조체](enableif-structure.md)|첫 번째 템플릿 매개 변수가로 평가 될 경우 두 번째 템플릿 매개 변수로 지정 된 형식의 데이터 멤버를 정의 합니다 **`true`** .|
|[FactoryCache 구조체](factorycache-structure.md)|클래스 팩터리의 위치 및 등록 된 Windows 런타임 또는 COM 클래스 개체를 식별 하는 값을 포함 합니다.|
|[ImplementsBase 구조체](implementsbase-structure.md)|[구현 구조](implements-structure.md)에서 템플릿 매개 변수 형식의 유효성을 검사 하는 데 사용 됩니다.|
|[ImplementsHelper 구조체](implementshelper-structure.md)|[구현](implements-structure.md) 구조를 구현 하는 데 도움이 됩니다.|
|[InterfaceList 구조체](interfacelist-structure.md)|재귀 인터페이스 목록을 만드는 데 사용 됩니다.|
|[InterfaceListHelper 구조체](interfacelisthelper-structure.md)|지정 된 `InterfaceList` 템플릿 매개 변수 인수를 재귀적으로 적용 하 여 형식을 빌드합니다.|
|[InterfaceTraits 구조체](interfacetraits-structure.md)|인터페이스의 공통 특성을 구현 합니다.|
|[InvokeHelper 구조체](invokehelper-structure.md)|`Invoke()`지정 된 인수 개수 및 형식을 기반으로 하는 메서드의 구현을 제공 합니다.|
|[IsBaseOfStrict 구조체](isbaseofstrict-structure.md)|형식 하나가 다른 형식의 기본 형식인지 테스트합니다.|
|[IsSame 구조체](issame-structure.md)|지정 된 형식이 다른 지정 된 형식과 동일한 지 테스트 합니다.|
|[Nil 구조체](nil-structure.md)|지정 되지 않은 선택적 템플릿 매개 변수를 나타내는 데 사용 됩니다.|
|[RemoveReference 구조체](removereference-structure.md)|지정 된 클래스 템플릿 매개 변수에서 참조 또는 rvalue 참조 특성을 제거 합니다.|
|[RuntimeClassBase 구조체](runtimeclassbase-structure.md)|함수에서를 검색 하는 데 사용 `RuntimeClass` 됩니다. [](make-function.md)|
|[RuntimeClassBaseT 구조체](runtimeclassbaset-structure.md)|작업 및 인터페이스 Id 가져오기에 대 한 도우미 메서드를 제공 `QueryInterface` 합니다.|
|[VerifyInheritanceHelper 구조체](verifyinheritancehelper-structure.md)|한 인터페이스가 다른 인터페이스에서 파생 되는지 테스트 합니다.|
|[VerifyInterfaceHelper 구조체](verifyinterfacehelper-structure.md)|템플릿 매개 변수로 지정 된 인터페이스가 특정 요구 사항을 충족 하는지 확인 합니다.|

### <a name="enumerations"></a>열거형

|Name|설명|
|----------|-----------------|
|[AsyncStatusInternal 열거형](asyncstatusinternal-enumeration.md)|비동기 작업의 상태와 열거형의 내부 열거형 간 매핑을 지정 합니다 `Windows::Foundation::AsyncStatus` .|

### <a name="functions"></a>함수

|Name|설명|
|----------|-----------------|
|[ActivationFactoryCallback 함수](activationfactorycallback-function.md)|지정 된 활성화 ID에 대 한 활성화 팩터리를 가져옵니다.|
|[Move 함수](move-function.md)|지정 된 인수를 한 위치에서 다른 위치로 이동 합니다.|
|[RaiseException 함수](raiseexception-function.md)|호출 스레드에서 예외를 발생 시킵니다.|
|[Swap 함수 (WRL)](swap-function-wrl.md)|지정 된 두 인수 값을 교환 합니다.|
|[TerminateMap 함수](terminatemap-function.md)|지정 된 모듈에서 클래스 팩터리를 종료 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** async. .h, client.msi, corewrappers.h, ftm,. h, internal. h, node.js, node.js

**네임 스페이스:** Microsoft:: WRL::D etails

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL 네임 스페이스](microsoft-wrl-namespace.md)<br/>
[Microsoft:: WRL:: 래퍼 네임 스페이스](microsoft-wrl-wrappers-namespace.md)
