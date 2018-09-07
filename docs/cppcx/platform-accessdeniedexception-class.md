---
title: 'Platform:: accessdeniedexception 클래스 | Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::AccessDeniedException
- VCCORLIB/Platform::AccessDeniedException::AccessDeniedException
dev_langs:
- C++
helpviewer_keywords:
- Platform::AccessDeniedException
ms.assetid: 6ae2155b-7b16-4587-8d2d-da05eab4c7e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c87cdc55359fbdd4855a062a3b1b56384c3be574
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104188"
---
# <a name="platformaccessdeniedexception-class"></a>Platform::AccessDeniedException 클래스

리소스 또는 기능에 대한 액세스가 거부된 경우 throw됩니다.

## <a name="syntax"></a>구문

```cpp
public ref class AccessDeniedException : COMException,    IException,    IPrintable,   IEquatable
```

### <a name="remarks"></a>설명

이 예외가 발생하면 응용 프로그램의 패키지 매니페스트에 적절한 기능을 요청했고 필요한 선언을 만들었는지 확인하세요. 자세한 내용은 [COMException](../cppcx/platform-comexception-class.md) 클래스를 참조하세요.

### <a name="requirements"></a>요구 사항

**지원 되는 최소 클라이언트:** Windows 8

**지원 되는 최소 서버:** Windows Server 2012

**네임스페이스:** Platform

**메타데이터:** platform.winmd

## <a name="see-also"></a>참고 항목

[Platform::COMException 클래스](../cppcx/platform-comexception-class.md)