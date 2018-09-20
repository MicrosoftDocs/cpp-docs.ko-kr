---
title: AgileActivationFactory 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::AgileActivationFactory
dev_langs:
- C++
ms.assetid: fab98f32-bb93-4c0f-badb-49fbddb194b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2d6b2ff0b9b23e8e3a540cf7bbcd6ae55ebab13d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435378"
---
# <a name="agileactivationfactory-class"></a>AgileActivationFactory 클래스

구현 하는 아파트 활성화 팩터리를 나타냅니다 [FtmBase](../windows/ftmbase-class.md)합니다.
  
## <a name="syntax"></a>구문
  
```cpp
template <
   typename I0 = Details::Nil,
   typename I1 = Details::Nil,
   typename I2 = Details::Nil,
FactoryCacheFlags cacheFlagValue = FactoryCacheDefault>
class AgileActivationFactory :
   public ActivationFactory<Implements<FtmBase, I0>, I1, I2, cacheFlagValue>{};
```
  
## <a name="requirements"></a>요구 사항

**헤더:** module.h
  
**네임스페이스:** Microsoft::WRL
  
## <a name="see-also"></a>참고 항목

[Microsoft::WRL 네임스페이스](../windows/microsoft-wrl-namespace.md)<br/>
[ActivationFactory 클래스](../windows/activationfactory-class.md)