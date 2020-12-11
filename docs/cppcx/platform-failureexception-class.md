---
description: '자세한 정보: Platform:: FailureException 클래스'
title: Platform::FailureException 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::FailureException::FailureException
- VCCORLIB/Platform::FailureException
helpviewer_keywords:
- Platform::FailureException
ms.assetid: 1729cd07-bfc2-448e-9db5-185d5cbf5b81
ms.openlocfilehash: 0b3f03888a92cc0c52e347ce5ee663a3e57b0b20
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161262"
---
# <a name="platformfailureexception-class"></a>Platform::FailureException 클래스

작업이 실패하면 throw됩니다. 이 지시문은 E_FAIL HRESULT에 해당합니다.

## <a name="syntax"></a>구문

```cpp
public ref class FailureException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>설명

자세한 내용은 [COMException](../cppcx/platform-comexception-class.md) 클래스를 참조하세요.

### <a name="requirements"></a>요구 사항

**지원 되는 최소 클라이언트:** Windows 8

**지원 되는 최소 서버:** Windows Server 2012

**네임스페이스:** Platform

**메타 데이터:** platform.object

## <a name="see-also"></a>참고 항목

[Platform:: COMException 클래스](../cppcx/platform-comexception-class.md)
