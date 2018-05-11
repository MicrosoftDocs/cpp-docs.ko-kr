---
title: 'Handlet:: Operator = 연산자 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9e42dcca-30fa-4e8b-8954-802fd64a5595
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6a13e8eb7e74625e185b59816b5794b0390e95e3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
---
# <a name="handletoperator-operator"></a>HandleT::operator= 연산자
현재 HandleT 개체를 지정된 된 HandleT 개체의 값을 이동합니다.  
  
## <a name="syntax"></a>구문  
  
```  
HandleT& operator=(  
   _Inout_ HandleT&& h  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `h`  
 열려 있는 핸들에 rvalue 참조입니다.  
  
## <a name="return-value"></a>반환 값  
 현재 HandleT 개체에 대 한 참조입니다.  
  
## <a name="remarks"></a>설명  
 이 작업을 매개 변수에서 지정한 HandleT 개체가 무효화 `h`합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>참고 항목  
 [HandleT 클래스](../windows/handlet-class.md)