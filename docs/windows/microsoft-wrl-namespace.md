---
title: 'Microsoft:: wrl Namespace | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL
- module/Microsoft::WRL
- async/Microsoft::WRL
- internal/Microsoft::WRL
- event/Microsoft::WRL
- ftm/Microsoft::WRL
- client/Microsoft::WRL
- corewrappers/Microsoft::WRL
dev_langs:
- C++
helpviewer_keywords:
- WRL namespace
ms.assetid: 01118a8f-f564-4859-b87e-9444848585a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 37d4d5391da4dfb6e25754eb1350224acb97e972
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
---
# <a name="microsoftwrl-namespace"></a>Microsoft::WRL 네임스페이스
Windows 런타임 c + + 템플릿 라이브러리를 구성 하는 기본 형식을 정의 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
namespace Microsoft::WRL;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="typedefs"></a>형식 정의  
  
|이름|설명|  
|----------|-----------------|  
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt &#124; InhibitWeakReference>`|  
  
### <a name="classes"></a>클래스  
  
|이름|설명|  
|----------|-----------------|  
|[ActivationFactory 클래스](../windows/activationfactory-class.md)|Windows 런타임으로 활성화할 클래스를 하나 이상 사용합니다.|  
|[AsyncBase 클래스](../windows/asyncbase-class.md)|Windows 런타임 비동기 상태 컴퓨터를 구현합니다.|  
|[ClassFactory 클래스](../windows/classfactory-class.md)|`IClassFactory` 인터페이스의 기본 기능을 구현합니다.|  
|[ComPtr 클래스](../windows/comptr-class.md)|템플릿 매개 변수로 지정된 인터페이스를 나타내는 *스마트 포인터* 형식을 만듭니다. ComPtr은 기본 인터페이스 포인터의 참조 개수를 자동으로 관리하여 참조 횟수가 0이 되면 인터페이스를 릴리스합니다.|  
|[DeferrableEventArgs 클래스](../windows/deferrableeventargs-class.md)|지연에 대한 이벤트 인수 형식에 사용되는 템플릿 클래스입니다.|  
|[EventSource 클래스](../windows/eventsource-class.md)|이벤트를 나타냅니다. `EventSource` 멤버 함수는 이벤트 처리기를 추가, 삭제 및 호출합니다.|  
|[FtmBase 클래스](../windows/ftmbase-class.md)|자유 스레드된 마샬러 개체를 나타냅니다.|  
|[Module 클래스](../windows/module-class.md)|관련된 개체의 컬렉션을 나타냅니다.|  
|[RuntimeClass 클래스](../windows/runtimeclass-class.md)|지정된 수의 인터페이스를 상속하는 인스턴스화된 클래스를 나타내고 지정된 Windows 런타임, 클래식 COM 및 약한 참조 지원을 제공합니다.|  
|[SimpleActivationFactory 클래스](../windows/simpleactivationfactory-class.md)|Windows 런타임 또는 클래식 COM 기본 클래스를 만드는 기본적인 메커니즘을 제공합니다.|  
|[SimpleClassFactory 클래스](../windows/simpleclassfactory-class.md)|기본 클래스를 만드는 기본적인 메커니즘을 제공합니다.|  
|[WeakRef 클래스](../windows/weakref-class.md)|클래식 COM이 아닌 Windows 런타임에서만 사용할 수 있는 *약한 참조* 를 나타냅니다. 약한 참조는 액세스할 수 있거나 액세스할 수 없는 개체를 나타냅니다.|  
  
### <a name="structures"></a>구조체  
  
|이름|설명|  
|----------|-----------------|  
|[ChainInterfaces 구조체](../windows/chaininterfaces-structure.md)|인터페이스 ID 집합에 적용할 수 있는 확인 및 초기화 함수를 지정합니다.|  
|[CloakedIid 구조체](../windows/cloakediid-structure.md)|IID 목록에서 지정된 인터페이스가 액세스할 수 없는 RuntimeClass, Implements 및 ChainInterfaces 템플릿에 대해 나타냅니다.|  
|[Implements 구조체](../windows/implements-structure.md)|지정된 인터페이스에 대해 QueryInterface 및 GetIid를 구현합니다.|  
|[MixIn 구조체](../windows/mixin-structure.md)|런타임 클래스가 Windows 런타임 인터페이스에서 파생되었는지 확인한 다음 있는 경우 클래식 COM 인터페이스를 확인합니다.|  
|[RuntimeClassFlags 구조체](../windows/runtimeclassflags-structure.md)|인스턴스에 대 한 형식을 포함 한 [RuntimeClass](../windows/runtimeclass-class.md)합니다.|  
  
### <a name="enumerations"></a>열거형  
  
|이름|설명|  
|----------|-----------------|  
|[AsyncResultType 열거형](../windows/asyncresulttype-enumeration.md)|GetResults 메서드에서 반환되는 결과 형식을 지정합니다.|  
|[ModuleType 열거형](../windows/moduletype-enumeration.md)|모듈이 in-process 서버를 지원하는지 out-of-process 서버를 지원해야 하는지 여부를 지정합니다.|  
|[RuntimeClassType 열거형](../windows/runtimeclasstype-enumeration.md)|유형을 지정 [RuntimeClass](../windows/runtimeclass-class.md) 지원 되는 인스턴스.|  
  
### <a name="functions"></a>함수  
  
|이름|설명|  
|----------|-----------------|  
|[AsWeak 함수](../windows/asweak-function.md)|지정된 인스턴스에 대한 약한 참조를 가져옵니다.|  
|[콜백 함수](../windows/callback-function-windows-runtime-cpp-template-library.md)|멤버 함수가 콜백 메서드인 개체를 만듭니다.|  
|[CreateActivationFactory 함수](../windows/createactivationfactory-function.md)|Windows 런타임으로 활성화할 수 있는 지정된 클래스의 인스턴스를 생성하는 팩터리를 만듭니다.|  
|[CreateClassFactory 함수](../windows/createclassfactory-function.md)|지정된 클래스의 인스턴스를 생성하는 팩터리를 만듭니다.|  
|[Make 함수](../windows/make-function.md)|지정된 된 Windows 런타임 클래스를 초기화합니다.|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** async.h, client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h  
  
 **네임스페이스:** Microsoft::WRL  
  
## <a name="see-also"></a>참고 항목  
 [Microsoft::WRL::Wrappers 네임스페이스](../windows/microsoft-wrl-wrappers-namespace.md)