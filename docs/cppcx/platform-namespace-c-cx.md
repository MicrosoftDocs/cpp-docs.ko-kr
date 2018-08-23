---
title: Platform 네임 스페이스 (C + + /cli CX) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- Platform/Platform
dev_langs:
- C++
helpviewer_keywords:
- Platform Namespace (C++/CX)
ms.assetid: b160e822-d424-43d2-ba60-57b0e81f259c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d88b40d53dbae737822ca31e6fa9cf15c947970
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607330"
---
# <a name="platform-namespace-ccx"></a>Platform 네임스페이스(C++/CX)
Windows 런타임과 호환되는 기본 제공 형식을 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
using namespace Platform;  
```  
  
### <a name="members"></a>멤버  
 **특성**  
  
 Platform 네임스페이스는 특성, 클래스, 열거형, 인터페이스 및 구조체를 포함합니다. Platform은 중첩된 네임스페이스도 포함합니다.  
  
|특성|설명|  
|---------------|-----------------|  
|플래그|열거형을 비트 필드 즉, 플래그 집합으로 처리할 수 있음을 나타냅니다.|  
|MTAThread|응용 프로그램의 스레딩 모델이 MTA(다중 스레드 아파트)임을 나타냅니다.|  
|STAThread|응용 프로그램에 대한 스레딩 모델이 STA(단일 스레드 아파트)임을 나타냅니다.|  
  
 **클래스**  
  
 Platform 네임스페이스에는 다음 클래스가 포함되어 있습니다.  
  
|클래스|설명|  
|-----------|-----------------|  
|[Platform::AccessDeniedException 클래스](../cppcx/platform-accessdeniedexception-class.md)|리소스 또는 기능에 대한 액세스가 거부된 경우에 발생합니다.|  
|[Platform::Agile 클래스](../cppcx/platform-agile-class.md)|Agile이 아닌 개체를 Agile 개체로 표현합니다.|  
|[Platform::Array 클래스](../cppcx/platform-array-class.md)|수정 가능한 1차원 배열을 나타냅니다.|  
|[Platform::ArrayReference 클래스](../cppcx/platform-arrayreference-class.md)|복사 작업 최소화를 위해 초기화가 최적화되는 배열을 나타냅니다.|  
|[Platform::Box 클래스](../cppcx/platform-box-class.md)|Windows::Foundation::DateTime이나 int64 등의 값 형식이 [Platform::Object^](../cppcx/platform-object-class.md)형식의 변수에 저장되거나 ABI(응용 프로그램 이진 인터페이스)를 통해 전달될 때 해당 형식 캡슐화하는 boxed 형식을 선언하는 데 사용됩니다.|  
|[Platform::ChangedStateException 클래스](../cppcx/platform-changedstateexception-class.md)|부모 컬렉션이 변경된 후 컬렉션 반복기 또는 컬렉션 뷰의 메서드가 호출되어 메서드 결과가 무효화되면 throw됩니다.|  
|[Platform::ClassNotRegisteredException 클래스](../cppcx/platform-classnotregisteredexception-class.md)|COM 클래스가 등록되지 않은 경우 throw됩니다.|  
|[Platform::COMException 클래스](../cppcx/platform-comexception-class.md)|인식할 수 없는 값이 COM 메서드 호출에서 반환된 경우에 throw되는 예외를 나타냅니다.|  
|[Platform::Delegate 클래스](../cppcx/platform-delegate-class.md)|콜백 함수의 시그니처를 나타냅니다.|  
|[Platform::DisconnectedException 클래스](../cppcx/platform-disconnectedexception-class.md)|개체가 해당 클라이언트에서 연결을 끊었습니다.|  
|[Platform::Exception 클래스](../cppcx/platform-exception-class.md)|응용 프로그램을 실행할 때 나타나는 오류를 나타냅니다. 예외에 대한 기본 클래스입니다.|  
|[Platform::FailureException 클래스](../cppcx/platform-failureexception-class.md)|작업이 실패하면 throw됩니다. 이 지시문은 E_FAIL HRESULT에 해당합니다.|  
|[Platform::Guid 값 클래스](../cppcx/platform-guid-value-class.md)|Windows 런타임 형식 시스템의 GUID를 나타냅니다.|  
|[Platform::InvalidArgumentException 클래스](../cppcx/platform-invalidargumentexception-class.md)|메서드에 제공된 인수 중 하나가 유효하지 않을 때 throw됩니다.|  
|[Platform::InvalidCastException 클래스](../cppcx/platform-invalidcastexception-class.md)|캐스트 또는 명시적 변환이 잘못된 경우 throw됩니다.|  
|[Platform::MTAThreadAttribute 클래스](../cppcx/platform-mtathreadattribute-class.md)|응용 프로그램의 스레딩 모델이 MTA(다중 스레드 아파트)임을 나타냅니다.|  
|[Platform::NotImplementedException 클래스](../cppcx/platform-notimplementedexception-class.md)|클래스에 인터페이스 메서드가 구현되어 있지 않은 경우 throw됩니다.|  
|[Platform::NullReferenceException 클래스](../cppcx/platform-nullreferenceexception-class.md)|null 개체 참조를 역참조하려고 할 때 throw됩니다.|  
|[Platform::Object 클래스](../cppcx/platform-object-class.md)|일반적인 동작을 제공하는 기본 클래스입니다.|  
|[Platform::ObjectDisposedException 클래스](../cppcx/platform-objectdisposedexception-class.md)|삭제된 개체에서 연산이 수행될 때 throw됩니다.|  
|[Platform::OperationCanceledException 클래스](../cppcx/platform-operationcanceledexception-class.md)|작업이 중단되면 throw됩니다.|  
|[Platform::OutOfBoundsException 클래스](../cppcx/platform-outofboundsexception-class.md)|작업이 유효한 범위를 벗어난 데이터에 액세스하려고 하면 throw됩니다.|  
|[Platform::OutOfMemoryException 클래스](../cppcx/platform-outofmemoryexception-class.md)|메모리가 부족하여 작업을 완료할 수 없는 경우 throw됩니다.|  
|[Platform::STAThreadAttribute 클래스](../cppcx/platform-stathreadattribute-class.md)|응용 프로그램에 대한 스레딩 모델이 STA(단일 스레드 아파트)임을 나타냅니다.|  
|[Platform::String 클래스](../cppcx/platform-string-class.md)|텍스트를 나타내는 데 사용되는 유니코드 문자의 순차적인 컬렉션입니다.|  
|[Platform::StringReference 클래스](../cppcx/platform-stringreference-class.md)|최소한의 복사 오버헤드로 문자열 버퍼에 액세스할 수 있습니다.|  
|[Platform::Type 클래스](../cppcx/platform-type-class.md)|범주 열거형으로 기본 제공 형식을 식별합니다.|  
|[Platform::ValueType 클래스](../cppcx/platform-valuetype-class.md)|값 형식 인스턴스의 기본 클래스입니다.|  
|[Platform::WeakReference 클래스](../cppcx/platform-weakreference-class.md)|참조 개수를 증가시키지 않는 ref 클래스 개체에 대한 약한 참조를 제공합니다.|  
|[Platform::WriteOnlyArray 클래스](../cppcx/platform-writeonlyarray-class.md)|FillArray 패턴을 구현하는 메서드에서 입력 매개 변수로 사용되는 1차원 쓰기 전용 배열을 나타냅니다.|  
|[Platform::WrongThreadException 클래스](../cppcx/platform-wrongthreadexception-class.md)|프록시 개체용 인터페이스 포인터를 통해 스레드의 아파트에 속하지 않는 스레드가 호출될 경우 throw됩니다.|  
  
 **인터페이스 구현**  
  
 Platform 네임스페이스는 다음 인터페이스를 정의합니다.  
  
|인터페이스|설명|  
|---------------|-----------------|  
|[Platform::IBox 인터페이스](../cppcx/platform-ibox-interface.md)|해당 매개 변수가 Platform::Object^로 형식화되는 함수에 값 형식을 전달하는 데 사용됩니다.|  
|[Platform::IBoxArray 인터페이스](../cppcx/platform-iboxarray-interface.md)|해당 매개 변수가 Platform::Array로 형식화되는 함수에 값 형식의 배열을 전달하는 데 사용되는 인터페이스입니다.|  
|[Platform::IDisposable 인터페이스](../cppcx/platform-idisposable-interface.md)|관리되지 않는 리소스를 해제하는 데 사용됩니다.|  
  
 **열거형**  
  
 Platform 네임스페이스에는 다음 열거형이 포함되어 있습니다.  
  
|인터페이스|설명|  
|---------------|-----------------|  
|[Platform::CallbackContext 열거형](../cppcx/platform-callbackcontext-enumeration.md)|대리자 생성자의 매개 변수로 사용되는 열거형입니다. 콜백을 시작 스레드로 마샬링해야 하는지 또는 호출자 스레드로 마샬링해야 하는지를 결정합니다.|  
|[Platform::TypeCode 열거형](../cppcx/platform-typecode-enumeration.md)|기본 제공 형식을 나타내는 숫자 범주를 지정합니다.|  
  
 **구조체**  
  
 Platform 네임스페이스에는 다음 구조체가 포함되어 있습니다.  
  
|구조체|설명|  
|---------------|-----------------|  
|[Platform::Enum 클래스](../cppcx/platform-enum-class.md)|명명된 상수를 나타냅니다.|  
|[Platform::Guid 값 클래스](../cppcx/platform-guid-value-class.md)|GUID를 나타냅니다.|  
|[Platform::IntPtr 값 클래스](../cppcx/platform-intptr-value-class.md)|플랫폼(32비트 또는 64비트)에 맞는 크기의 부호 있는 포인터입니다.|  
|[Platform::SizeT 값 클래스](../cppcx/platform-sizet-value-class.md)|개체의 크기를 나타내는 데 사용되는 부호 없는 데이터 형식입니다.|  
|[Platform::UIntPtr 값 클래스](../cppcx/platform-uintptr-value-class.md)|플랫폼(32비트 또는 64비트)에 맞는 크기의 부호 없는 포인터입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Platform:: collections Namespace](../cppcx/platform-collections-namespace.md)   
 [Platform::Runtime::CompilerServices Namespace](../cppcx/platform-runtime-compilerservices-namespace.md)   
 [Platform::Runtime::InteropServices Namespace](../cppcx/platform-runtime-interopservices-namespace.md)   
 [Platform::Metadata 네임스페이스](../cppcx/platform-metadata-namespace.md)