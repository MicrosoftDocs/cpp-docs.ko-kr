---
description: '자세히 알아보기: InvokeModeOptions Structure'
title: InvokeModeOptions 구조체
ms.date: 03/22/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
ms.openlocfilehash: 1e1382242c95c47355239c220c43c278280dd451
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298983"
---
# <a name="invokemodeoptions-structure"></a>InvokeModeOptions 구조체

대리자 큐의 모든 이벤트를 시작할지, 아니면 오류가 발생 한 후 발생을 중지할지를 지정 합니다. 허용 되는 값은 열거형에 지정 됩니다 `InvokeMode` .

## <a name="syntax"></a>Syntax

```cpp
enum InvokeMode
{
   StopOnFirstError = 1,
   FireAll = 2,
};

struct InvokeModeOptions
{
   static const InvokeMode invokeMode = invokeModeValue;
};
```

## <a name="requirements"></a>요구 사항

**헤더:** 이벤트. h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL 네임 스페이스](microsoft-wrl-namespace.md)<br/>
[Microsoft:: WRL:: AgileEventSource 클래스](agileeventsource-class.md)
