---
description: '자세한 정보: ATL 전역 변수'
title: ATL 전역 변수
ms.date: 12/06/2017
f1_keywords:
- ATLBASE/_pAtlModule
helpviewer_keywords:
- global variables, ATL
- _pAtlModule
ms.assetid: e881a319-99ca-4f5d-8a0b-34b3dcd0f37f
ms.openlocfilehash: 8d0544651e32f5e569973466af8ce04af1433766
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158779"
---
# <a name="atl-global-variables"></a>ATL 전역 변수

## <a name="_patlmodule"></a>_pAtlModule

현재 모듈에 대 한 포인터를 저장 하는 전역 변수입니다.

```cpp
__declspec(selectany) CAtlModule * _pAtlModule
```

### <a name="remarks"></a>설명

이 전역 변수의 메서드는 Visual C++ 6.0에 제공 된 (현재 사용 되지 않음) 클래스 CComModule 기능을 제공 하는 데 사용할 수 있습니다.

### <a name="example"></a>예제

```cpp
LONG lLocks = _pAtlModule->GetLockCount();
```

### <a name="requirements"></a>요구 사항

**헤더:** 서 기. h
