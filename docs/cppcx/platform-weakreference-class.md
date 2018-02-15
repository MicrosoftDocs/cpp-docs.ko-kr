---
title: "Platform:: weakreference 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Platform::WeakReference
ms.assetid: 8cfe1977-a8c7-4b7b-b539-25c77ed4c5f1
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 59d87d2e00ef567c0273e71410ad58ebf0a5c061
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="platformweakreference-class"></a>Platform::WeakReference 클래스
ref 클래스 인스턴스에 대한 약한 참조를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp 
class WeakReference  
```  
  
#### <a name="parameters"></a>매개 변수  
  
### <a name="members"></a>멤버  
  
### <a name="constructors"></a>생성자  
  
|멤버|설명|  
|------------|-----------------|  
|[WeakReference::WeakReference](#ctor)|WeakReference 클래스의 새 인스턴스를 초기화합니다.|  
  
### <a name="methods"></a>메서드  
  
|멤버|설명|  
|------------|-----------------|  
|[WeakReference::Resolve](#resolve)|기본 ref 클래스에 대한 핸들 또는 nullptr(개체가 더 이상 존재하지 않는 경우)을 반환합니다.|  
  
### <a name="operators"></a>연산자  
  
|멤버|설명|  
|------------|-----------------|  
|[WeakReference::operator=](#operator-assign)|WeakReference 개체에 새 값을 할당합니다.|  
|[WeakReference::operator BoolType](#booltype)|안전 bool 패턴을 구현합니다.|  
  
### <a name="remarks"></a>설명  
 WeakReference 클래스 자체는 ref 클래스가 아니므로 Platform::Object^에서 상속하지 않으며 public 메서드의 시그니처에 사용될 수 없습니다.  

## <a name="operator-assign"></a> WeakReference::operator=
WeakReference에 값을 할당합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp  
WeakReference& operator=(decltype(__nullptr));    
WeakReference& operator=(const WeakReference& otherArg);   
WeakReference& operator=(WeakReference&& otherArg);    
WeakReference& operator=(const volatile ::Platform::Object^ const otherArg); 
```  
  
### <a name="remarks"></a>설명  
 위의 목록에서 마지막 오버로드를 사용하면 WeakReference 변수에 ref 클래스를 할당할 수 있습니다. 이 경우 ref 클래스는으로 다운 캐스팅 [platform:: object](../cppcx/platform-object-class.md)^ 합니다. 형식 매개 변수에 대 한 인수로 지정 하 여 원래 형식을 나중에 복원 된 [weakreference:: Resolve\<T >](#resolve) 멤버 함수입니다.  
  
## <a name="booltype"></a> WeakReference::operator BoolType
WeakReference 클래스에 대한 안전 bool 패턴을 구현합니다. 코드에서 명시적으로 호출하면 안 됩니다.  
  
### <a name="syntax"></a>구문  
  
```cpp  
BoolType BoolType()  
```  

## <a name="resolve"></a> Weakreference:: Resolve 메서드 (Platform 네임 스페이스)
원래 ref 클래스에 대한 핸들 또는 `nullptr`(개체가 더 이상 존재하지 않는 경우)을 반환합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp  
  
template<typename T>  
T^ Resolve() const  
```  
  
### <a name="parameters"></a>매개 변수  
  
### <a name="property-valuereturn-value"></a>속성 값/반환 값  
 WeakReference 개체가 이전에 연결되었던 ref 클래스에 대한 핸들 또는 nullptr입니다.  
  
### <a name="example"></a>예  
 코드 예제에 대한 설명입니다.  
  
```  
  
Bar^ bar = ref new Bar();  
//use bar...  
  
if (bar != nullptr)  
{  
    WeakReference wr(bar);  
    Bar^ newReference = wr.Resolve<Bar>();  
}  
```  
  
 형식 매개 변수는 T^이 아니라 T입니다.  
  
 
## <a name="ctor"></a> Weakreference:: Weakreference 생성자
WeakReference를 생성하는 다양한 방법을 제공합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp  
WeakReference();  
WeakReference(decltype(__nullptr));  
WeakReference(const WeakReference& otherArg);  
WeakReference(WeakReference&& otherArg);  
explicit WeakReference(const volatile ::Platform::Object^ const otherArg);  
```  
### <a name="example"></a>예  
  
```cpp    
MyClass^ mc = ref new MyClass();  
WeakReference wr(mc);  
MyClass^ copy2 = wr.Resolve<MyClass>();    
```  
  
## <a name="see-also"></a>참고 항목  
 [Platform 네임 스페이스](../cppcx/platform-namespace-c-cx.md)