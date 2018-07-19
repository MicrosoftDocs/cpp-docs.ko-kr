---
title: Comptr::&amp; 연산자 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0bfe8cf9091d888c33420f53f584ca5509d80527
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872408"
---
# <a name="comptroperatoramp-operator"></a>Comptr::&amp; 연산자
이 연결 된 인터페이스를 해제 `ComPtr` 다음의 주소를 검색 하 고 개체는 `ComPtr` 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## <a name="return-value"></a>반환 값  
 현재에 대 한 약한 참조 `ComPtr`합니다.  
  
## <a name="remarks"></a>설명  
 이 방법은에서 차이가 [comptr:: Getaddressof](../windows/comptr-getaddressof-method.md) 는이 메서드는 인터페이스 포인터에 대 한 참조를 해제 합니다. 사용 하 여 `ComPtr::GetAddressOf` 인터페이스 포인터의 주소를 필요로 하지만 해당 인터페이스를 해제 하지 않으려는 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** client.h  
  
 **네임스페이스:** Microsoft::WRL  
  
## <a name="see-also"></a>참고 항목  
 [ComPtr 클래스](../windows/comptr-class.md)