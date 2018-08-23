---
title: 'Platform:: ibox 인터페이스 | Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
dev_langs:
- C++
ms.assetid: 774df45d-f8a7-45a3-ae24-eecc3c681040
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d83afb854aaa400a02f9de95e269f85cfeba1a96
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586874"
---
# <a name="platformibox-interface"></a>Platform::IBox 인터페이스
[Platform::IBox](../cppcx/platform-ibox-interface.md) 인터페이스는 `Windows::Foundation::IReference` 인터페이스의 C++ 이름입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
template <typename T>  
interface class IBox  
```  
  
#### <a name="parameters"></a>매개 변수  
 `T`  
 boxed 값의 형식입니다.  
  
### <a name="remarks"></a>설명  
 `IBox<T>` 인터페이스는 [값 클래스 및 구조체(C++/CX)](../cppcx/value-classes-and-structs-c-cx.md)에 설명된 바와 같이 null을 허용하는 값 형식을 내부적으로 나타내는 데 주로 사용됩니다. 또한 이 인터페이스는 `Object^`형식의 매개 변수를 사용하는 C++ 메서드로 전달되는 값 형식을 boxing하는 데 사용됩니다. 입력 매개 변수를 `IBox<SomeValueType>`으로 명시적으로 선언할 수 있습니다. 예를 들어 참조 [Boxing](../cppcx/boxing-c-cx.md)합니다.  
  
### <a name="requirements"></a>요구 사항  
  
### <a name="members"></a>멤버  
 `Platform::IBox` 인터페이스는 [Platform::IValueType](../cppcx/platform-ivaluetype-interface.md) 인터페이스에서 상속합니다. `IBox` 에는 다음과 같은 멤버가 포함됩니다.  
  
 **속성**  
  
|메서드|설명|  
|------------|-----------------|  
|[값](#value)|이 `IBox` 인스턴스에 이전에 저장된 unboxed 값을 반환합니다.|  

## <a name="value"></a> Ibox:: Value 속성
이 개체에 원래 저장된 값을 반환합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp  
property T Value {T get();}  
```  
  
### <a name="parameters"></a>매개 변수  
 `T`  
 boxed 값의 형식입니다.  
  
### <a name="property-valuereturn-value"></a>속성 값/반환 값  
 이 개체에 원래 저장된 값을 반환합니다.  
  
### <a name="remarks"></a>설명  
 예를 들어 참조 [Boxing](../cppcx/boxing-c-cx.md)합니다.  
  
  
## <a name="see-also"></a>참고 항목  
 [Platform 네임 스페이스](../cppcx/platform-namespace-c-cx.md)