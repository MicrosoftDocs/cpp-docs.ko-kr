---
title: 'Platform:: agile 클래스 | Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
dev_langs:
- C++
helpviewer_keywords:
- Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f552327156d9fc1abe5e921f3b59b1fb4132ff3d
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763434"
---
# <a name="platformagile-class"></a>Platform::Agile 클래스
MashalingBehavior=Standard를 agile 개체로 나타냅니다. 이를 통해 런타임 스레딩 예외가 발생할 가능성이 매우 감소합니다. `Agile<T>` 를 사용하여 agile이 아닌 개체가 같거나 다른 스레드를 호출하거나 해당 스레드에서 호출될 수 있습니다. 자세한 내용은 [스레딩 및 마샬링](../cppcx/threading-and-marshaling-c-cx.md)합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
template <typename T>  
class Agile;  
```  
  
#### <a name="parameters"></a>매개 변수  
 T  
 Agile이 아닌 클래스의 형식 이름입니다.  
  
### <a name="remarks"></a>설명  
 대부분의 Windows 런타임에서 클래스는 agile 합니다. Agile 개체는 같거나 다른 스레드의 in-proc 또는 out-of-proc 개체를 호출하거나 해당 개체에서 호출될 수 있습니다. 개체가 agile이 아니면 agile인 `Agile<T>` 개체에서 agile이 아닌 개체를 래핑합니다. 그러고 나서 `Agile<T>` 개체를 마샬링할 수 있고 기본 agile이 아닌 개체를 사용할 수 있습니다.  
  
 `Agile<T>` 클래스는 네이티브 표준 C++ 클래스이고 `agile.h`가 필요합니다. Agile이 아닌 개체 및 Agile 개체의 *컨텍스트*를 나타냅니다. 컨텍스트는 agile 개체의 스레딩 모델 및 마샬링 동작을 지정합니다. 운영 체제에서는 컨텍스트를 사용하여 개체를 마샬링하는 방법을 결정합니다.  
  
### <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[Agile::Agile](#ctor)|Agile 클래스의 새 인스턴스를 초기화합니다.|  
|[Agile::~Agile 소멸자](#dtor)|Agile 클래스의 현재 인스턴스를 제거합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[Agile::Get](#get)|현재 Agile 개체가 나타내는 개체에 대한 핸들을 반환합니다.|  
|[Agile::GetAddressOf](#getaddressof)|현재 Agile 개체를 다시 초기화하고 핸들 주소를 `T`형식 개체에 반환합니다.|  
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|현재 Agile 개체가 나타내는 개체에 대한 핸들의 주소를 반환합니다.|  
|[Agile::Release](#release)|현재 Agile 개체의 기본 개체 및 컨텍스트를 삭제합니다.|  
  
### <a name="public-operators"></a>Public 연산자  
  
|이름|설명|  
|----------|-----------------|  
|[Agile::operator->](#operator-arrow)|현재 Agile 개체가 나타내는 개체에 대한 핸들을 검색합니다.|  
|[Agile::operator=](#operator-assign)|지정한 값을 현재 Agile 개체에 할당합니다.|  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `Object`  
  
 `Agile`  
  
### <a name="requirements"></a>요구 사항  
 **지원 되는 최소 클라이언트:** Windows 8  
  
 **지원 되는 최소 서버:** Windows Server 2012  
  
 **네임스페이스:** Platform  
  
 **헤더:** agile.h  

## <a name="ctor"></a>  Agile:: agile 생성자
Agile 클래스의 새 인스턴스를 초기화합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
  
 Agile();  
  
Agile(T^ object);   
  
Agile(const Agile<T>& object);  
  
Agile(Agile<T>&& object);  
  
```  
  
#### <a name="parameters"></a>매개 변수  
 `T`  
 템플릿 형식 이름 매개 변수로 지정된 형식입니다.  
  
 `object`  
 이 생성자의 두 번째 버전에서 새 Agile 인스턴스를 초기화하기 위해 사용된 개체입니다. 이 생성자의 세 번째 버전에서 새 Agile 인스턴스에 복사된 개체입니다. 이 생성자의 네 번째 버전에서 새 Agile 인스턴스로 이동된 개체입니다.  
  
### <a name="remarks"></a>설명  
 이 생성자의 첫 번째 버전은 기본 생성자입니다. 두 번째 버전은 `object` 매개 변수로 지정된 개체에서 새 Agile 인스턴스 클래스를 초기화합니다. 세 번째 버전은 복사 생성자입니다. 네 번째 버전은 이동 생성자입니다. 이 생성자는 예외를 throw할 수 없습니다.  

## <a name="dtor"></a>  Agile:: ~ Agile 소멸자
Agile 클래스의 현재 인스턴스를 제거합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
  
~Agile();  
```  
  
### <a name="remarks"></a>설명  
 이 소멸자는 현재 Agile 개체가 나타내는 개체도 해제합니다.  
  
## <a name="get"></a>   Agile:: get 메서드
현재 Agile 개체가 나타내는 개체에 대한 핸들을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
  
   T^ Get() const  
;  
```  
  
### <a name="return-value"></a>반환 값  
 현재 Agile 개체가 나타내는 개체에 대한 핸들입니다.  
  
 반환 값의 형식은 실제로 알려지지 않은 내부 형식입니다. 반환 값을 저장 하는 편리한 방법을 사용 하 여 선언 된 변수에 할당 하는 것은 **자동** 형식 추론 키워드입니다. 예를 들어, `auto x = myAgileTvariable->Get();`을 입력합니다.  
  
## <a name="getaddressof"></a>  Agile:: getaddressof 메서드
현재 Agile 개체를 다시 초기화하고 핸들 주소를 `T`형식 개체에 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
  
T^* GetAddressOf()   
throw();  
```  
  
#### <a name="parameters"></a>매개 변수  
 `T`  
 템플릿 형식 이름 매개 변수로 지정된 형식입니다.  
  
### <a name="return-value"></a>반환 값  
 형식의 개체에 대 한 핸들의 주소 `T`합니다.  
  
### <a name="remarks"></a>설명  
 이 작업 해제 형식의 개체의 현재 표현이 `T`있으면, Agile 개체의 데이터 멤버를 다시 초기화 하 고, 현재 스레딩 컨텍스트를 획득 하 고, 나타낼 수 있는 개체 핸들 변수의 주소를 반환을 agile이 아닌 개체입니다. 개체를 나타내는 Agile 클래스 인스턴스가 시킬 대입 연산자를 사용 하 여 ([agile:: operator =](#operator-assign)) 개체를 Agile 클래스 인스턴스에 할당 합니다.  

## <a name="getaddressofforinout"></a>  Agile::GetAddressOfForInOut Method
현재 Agile 개체가 나타내는 개체에 대한 핸들의 주소를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
  
T^* GetAddressOfForInOut()  throw();  
  
```  
  
#### <a name="parameters"></a>매개 변수  
 `T`  
 템플릿 형식 이름 매개 변수로 지정된 형식입니다.  
  
### <a name="return-value"></a>반환 값  
 현재 Agile 개체가 나타내는 개체에 대한 핸들의 주소입니다.  
  
### <a name="remarks"></a>설명  
 이 작업은 현재 스레딩 컨텍스트를 가져온 다음 내부 개체에 대한 핸들의 주소를 반환합니다.  

## <a name="release"></a>  Agile:: release 메서드
현재 Agile 개체의 기본 개체 및 컨텍스트를 삭제합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
  
void Release() throw();  
  
```  
  
### <a name="remarks"></a>설명  
 현재 Agile 개체의 기본 개체 및 컨텍스트가 삭제(있는 경우)된 다음 Agile 개체 값이 null로 설정됩니다.  

## <a name="operator-arrow"></a>  Agile::operator-&gt; Operator
현재 Agile 개체가 나타내는 개체에 대한 핸들을 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
  
T^ operator->()   
const throw();  
```  
  
### <a name="return-value"></a>반환 값  
 현재 Agile 개체가 나타내는 개체에 대한 핸들입니다.  
  
 이 연산자는 실제로 알려지지 않은 내부 형식을 반환합니다. 반환 값을 저장 하는 편리한 방법을 사용 하 여 선언 된 변수에 할당 하는 것은 **자동** 형식 추론 키워드입니다.  

## <a name="operator-assign"></a>  Agile:: operator = 연산자
지정한 개체를 현재 Agile 개체에 할당합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
  
   Agile<T> operator=(T^ object) throw();  
  
   Agile<T> operator=(  
      const Agile<T>& object  
) throw();  
  
   Agile<T> operator=(  
      Agile<T>&& object  
) throw();  
  
   T^ operator=(  
      IUnknown* lp  
) throw();  
  
```  
  
#### <a name="parameters"></a>매개 변수  
 `T`  
 템플릿 typename으로 지정된 형식입니다.  
  
 `object`  
 현재 Agile 개체로 복사되거나 이동된 개체 또는 개체의 핸들입니다.  
  
 `lp`  
 개체의 IUnknown 인터페이스 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 `T` 형식의 개체에 대한 핸들입니다.  
  
### <a name="remarks"></a>설명  
 첫 번째 버전의 할당 연산자는 참조 형식의 핸들을 현재 Agile 개체에 복사합니다. 두 번째 버전은 Agile 형식에 대한 참조를 현재 Agile 개체에 복사합니다. 세 번째 버전은 Agile 형식을 현재 Agile 개체로 이동합니다. 네 번째 버전은 COM 개체의 포인터를 현재 Agile 개체로 이동합니다.  
  
 할당 연산은 현재 Agile 개체의 컨텍스트를 자동으로 유지합니다. 
       
## <a name="see-also"></a>참고 항목  
 [플랫폼 Namespace](platform-namespace-c-cx.md)