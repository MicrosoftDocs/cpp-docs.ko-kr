---
title: 제한 된 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.restricted
dev_langs:
- C++
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: af30716208b4caf949630ba5f6965fcc6a1a54c2
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017060"
---
# <a name="restricted"></a>restricted
모듈, 인터페이스 또는 dispinterface의 멤버를 임의로 호출할 수 없습니다 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
[ restricted(  
   interfaces  
) ]  
```  
  
### <a name="parameters"></a>매개 변수  
 *interfaces*  
 호출할 수 없습니다 임의로 COM 개체에는 하나 이상의 인터페이스입니다. 이 매개 변수는 클래스에 적용 하는 경우에 유효만 합니다.  
  
## <a name="remarks"></a>설명  
 합니다 **제한** c + + 특성에 동일한 기능을 합니다 [제한](http://msdn.microsoft.com/library/windows/desktop/aa367157) MIDL 특성입니다.  
  
## <a name="example"></a>예  
 다음 코드에서는 사용 하 여 **제한** 특성:  
  
```cpp  
// cpp_attr_ref_restricted.cpp  
// compile with: /LD  
#include "windows.h"  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface a  
{  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000002")]  
__interface b  
{  
};  
  
[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]  
class c : public a, public b  
{  
};  
```  
  
## <a name="requirements"></a>요구 사항  
  
### <a name="attribute-context"></a>특성 컨텍스트  
  
|||  
|-|-|  
|**적용 대상**|인터페이스 메서드를 **인터페이스**하십시오 **클래스**, **구조체**|  
|**반복 가능**|아니요|  
|**필수 특성**|**coclass** (적용할 때 **클래스** 하거나 **구조체**)|  
|**잘못된 특성**|없음|  
  
 특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](../windows/attribute-contexts.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [IDL 특성](../windows/idl-attributes.md)   
 [인터페이스 특성](../windows/interface-attributes.md)   
 [메서드 특성](../windows/method-attributes.md)   