---
title: to_vector 함수 | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::to_vector
dev_langs:
- C++
helpviewer_keywords:
- to_vector Function
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00ecb00a890629c69994019c9232ff559ea93c96
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609740"
---
# <a name="tovector-function"></a>to_vector 함수
지정된 IVector 또는 IVectorView 매개 변수의 기본 컬렉션과 값이 같은 `std::vector` 를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
template <typename T>  
inline ::std::vector<T> to_vector(IVector<T>^ v); 
 
template <typename T>  
inline ::std::vector<T> to_vector(IVectorView<T>^ v);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `T`  
 템플릿 형식 매개 변수입니다.  
  
 `v`  
 기본 Vector 또는 VectorView 개체에 대한 액세스를 제공하는 IVector 또는 IVectorView 인터페이스입니다.  
  
### <a name="return-value"></a>반환 값  
  
### <a name="requirements"></a>요구 사항  
 **헤더:** collection.h  
  
 **네임스페이스:** Windows::Foundation::Collections  
  
## <a name="see-also"></a>참고 항목  
 [Windows::Foundation::Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)