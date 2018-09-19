---
title: _com_ptr_t::GetInterfacePtr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::GetInterfacePtr
dev_langs:
- C++
helpviewer_keywords:
- GetInterfacePtr method [C++]
ms.assetid: 55e3e2c7-c939-48b5-a905-4b9cbefeea7e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9da973b6003ca564ff8dc79552be5d12e8d14e24
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081054"
---
# <a name="comptrtgetinterfaceptr"></a>_com_ptr_t::GetInterfacePtr

**Microsoft 전용**

캡슐화된 인터페이스 포인터가 반환됩니다.

## <a name="syntax"></a>구문

```
Interface* GetInterfacePtr( ) const throw( ); 
Interface*& GetInterfacePtr() throw();
```

## <a name="remarks"></a>설명

NULL 일 수 있는 캡슐화 된 인터페이스 포인터를 반환 합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고자료

[_com_ptr_t 클래스](../cpp/com-ptr-t-class.md)