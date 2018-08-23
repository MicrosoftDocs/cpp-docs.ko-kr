---
title: 범주별 WRL Api 키 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b6d6bd580faf8c242ca5ac5e9b4b29ded9a7750a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612212"
---
# <a name="key-wrl-apis-by-category"></a>범주별 키 WRL API
다음 표에서 기본 Windows Runtime c + + 템플릿 라이브러리 클래스, 구조체, 함수 및 매크로 나열합니다. 도우미 네임 스페이스 및 클래스의 구문 생략 됩니다. 이 목록은 네임 스페이스에 의해 정렬 되는 API 설명서를 보강 합니다.
  
### <a name="classes"></a>클래스
  
|제목|설명|
|-----------|-----------------|
|[ActivationFactory 클래스](../windows/activationfactory-class.md)|Windows 런타임으로 활성화할 클래스를 하나 이상 사용합니다.|
|[AsyncBase 클래스](../windows/asyncbase-class.md)|Windows 런타임 비동기 상태 컴퓨터를 구현합니다.|
|[ClassFactory 클래스](../windows/classfactory-class.md)|`IClassFactory` 인터페이스의 기본 기능을 구현합니다.|
|[ComPtr 클래스](../windows/comptr-class.md)|템플릿 매개 변수로 지정된 인터페이스를 나타내는 *스마트 포인터* 형식을 만듭니다. ComPtr은 기본 인터페이스 포인터의 참조 개수를 자동으로 관리하여 참조 횟수가 0이 되면 인터페이스를 릴리스합니다.|
|[Event 클래스(Windows Runtime C++ 템플릿 라이브러리)](../windows/event-class-windows-runtime-cpp-template-library.md)|이벤트를 나타냅니다.|
|[EventSource 클래스](../windows/eventsource-class.md)|이벤트를 나타냅니다. `EventSource` 멤버 함수는 이벤트 처리기를 추가, 삭제 및 호출합니다.|
|[FtmBase 클래스](../windows/ftmbase-class.md)|자유 스레드된 마샬러 개체를 나타냅니다.|
|[HandleT 클래스](../windows/handlet-class.md)|개체에 대한 핸들을 나타냅니다.|
|[HString 클래스](../windows/hstring-class.md)|HSTRING 핸들 조작에 대 한 지원을 제공 합니다.|
|[HStringReference 클래스](../windows/hstringreference-class.md)|기존 문자열에서 생성 된 HSTRING을 나타냅니다.|
|[Module 클래스](../windows/module-class.md)|관련된 개체의 컬렉션을 나타냅니다.|
|[Module::GenericReleaseNotifier 클래스](../windows/module-genericreleasenotifier-class.md)|현재 모듈의 마지막 개체가 해제될 때 이벤트 처리기를 호출합니다. 이벤트 처리기는 람다, 함수 또는 함수 포인터에 의해 지정됩니다.|
|[Module::MethodReleaseNotifier 클래스](../windows/module-methodreleasenotifier-class.md)|현재 모듈의 마지막 개체가 해제될 때 이벤트 처리기를 호출합니다. 이벤트 처리기 개체와 해당 포인터를-a-메서드 멤버 지정 됩니다.|
|[Module::ReleaseNotifier 클래스](../windows/module-releasenotifier-class.md)|모듈의 마지막 개체가 해제될 때 이벤트 처리기를 호출합니다.|
|[RoInitializeWrapper 클래스](../windows/roinitializewrapper-class.md)|Windows 런타임을 초기화합니다.|
|[RuntimeClass 클래스](../windows/runtimeclass-class.md)|지정된 수의 인터페이스를 상속하는 인스턴스화된 클래스를 나타내고 지정된 Windows 런타임, 클래식 COM 및 약한 참조 지원을 제공합니다.|
|[SimpleActivationFactory 클래스](../windows/simpleactivationfactory-class.md)|Windows 런타임 또는 클래식 COM 기본 클래스를 만드는 기본적인 메커니즘을 제공합니다.|
|[SimpleClassFactory 클래스](../windows/simpleclassfactory-class.md)|기본 클래스를 만드는 기본적인 메커니즘을 제공합니다.|
|[WeakRef 클래스](../windows/weakref-class.md)|클래식 COM이 아닌 Windows 런타임에서만 사용할 수 있는 *약한 참조* 를 나타냅니다. 약한 참조는 액세스할 수 있거나 액세스할 수 없는 개체를 나타냅니다.|
  
### <a name="structures"></a>구조체
  
|제목|설명|
|-----------|-----------------|
|[ChainInterfaces 구조체](../windows/chaininterfaces-structure.md)|인터페이스 ID 집합에 적용할 수 있는 확인 및 초기화 함수를 지정합니다.|
|[CloakedIid 구조체](../windows/cloakediid-structure.md)|에 `RuntimeClass`, `Implements` 및 `ChainInterfaces` 지정된 된 인터페이스 IID 목록에서 액세스할 수 없는 템플릿.|
|[Implements 구조체](../windows/implements-structure.md)|구현 `QueryInterface` 고 `GetIid` 지정된 된 인터페이스에 대 한 합니다.|
|[MixIn 구조체](../windows/mixin-structure.md)|런타임 클래스가 Windows 런타임 인터페이스에서 파생되었는지 확인한 다음 있는 경우 클래식 COM 인터페이스를 확인합니다.|
  
### <a name="functions"></a>함수
  
|제목|설명|
|-----------|-----------------|
|[ActivateInstance 함수](../windows/activateinstance-function.md)|등록 하 고 ID가 지정 된 클래스에 정의 된 지정 된 형식의 인스턴스를 검색 합니다.|
|[AsWeak 함수](../windows/asweak-function.md)|지정된 인스턴스에 대한 약한 참조를 가져옵니다.|
|[콜백 함수](../windows/callback-function-windows-runtime-cpp-template-library.md)|멤버 함수가 콜백 메서드인 개체를 만듭니다.|
|[CreateActivationFactory 함수](../windows/createactivationfactory-function.md)|Windows 런타임으로 활성화할 수 있는 지정된 클래스의 인스턴스를 생성하는 팩터리를 만듭니다.|
|[CreateClassFactory 함수](../windows/createclassfactory-function.md)|지정된 클래스의 인스턴스를 생성하는 팩터리를 만듭니다.|
|[GetActivationFactory 함수](../windows/getactivationfactory-function.md)|템플릿 매개 변수로 지정 된 형식에 대 한 활성화 팩터리를 검색 합니다.|
|[Make 함수](../windows/make-function.md)|지정된 된 Windows 런타임 클래스를 초기화합니다.|
  
### <a name="macros"></a>매크로
  
|제목|설명|
|-----------|-----------------|
|[ActivatableClass 매크로](../windows/activatableclass-macros.md)|지정된 된 클래스의 인스턴스를 만들 수 있는 팩터리를 포함 하는 내부 캐시를 채웁니다.|
|[InspectableClass 매크로](../windows/inspectableclass-macro.md)|런타임 클래스 이름 및 신뢰 수준을 설정합니다.|
  
## <a name="see-also"></a>참고 항목
 [Windows 런타임 C++ 템플릿 라이브러리(WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)