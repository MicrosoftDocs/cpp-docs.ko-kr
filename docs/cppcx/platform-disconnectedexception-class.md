---
title: 'Platform:: disconnectedexception 클래스 | Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::DisconnectedException
- VCCORLIB/Platform::DisconnectedException::DisconnectedException
dev_langs:
- C++
helpviewer_keywords:
- Platform::DisconnectedException
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e46ddc82f867d3c126b9a7e8d259ba0c3c22bfde
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101978"
---
# <a name="platformdisconnectedexception-class"></a>Platform::DisconnectedException 클래스

COM 프록시 개체가 더 이상 존재하지 않는 COM 서버를 참조하려고 할 때 throw됩니다.

## <a name="syntax"></a>구문

```
public ref class DisconnectedException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>설명

클래스 A가 별도의 프로세스에 있는 다른 클래스(클래스 B)를 참조하는 경우 클래스 A에서 프록시 개체는 클래스 B를 보유하는 out-of-process COM 서버와 통신해야 합니다. 때때로 서버의 메모리가 부족해지지만 클래스 A가 그 사실을 알지 못할 수 있습니다. 이 경우 RPC_E_DISCONNECTED 예외가 throw되고 Platform::DisconnectedException으로 변환됩니다. 이러한 경우가 발생하는 한 가지 시나리오는 이벤트 소스가 자신에게 전달되는 대리자를 호출하지만 대리자가 이벤트를 구독하고 난 후 특정 시점에 제거된 경우입니다. 이 경우 이벤트 소스는 해당 대리자를 호출 목록에서 제거합니다.

자세한 내용은 [COMException](../cppcx/platform-comexception-class.md) 클래스를 참조하세요.

### <a name="requirements"></a>요구 사항

**지원 되는 최소 클라이언트:** Windows 8

**지원 되는 최소 서버:** Windows Server 2012

**네임스페이스:** Platform

**메타데이터:** platform.winmd

## <a name="see-also"></a>참고 항목

[Platform::COMException 클래스](../cppcx/platform-comexception-class.md)