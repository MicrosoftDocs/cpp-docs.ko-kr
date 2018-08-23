---
title: 'Ftmbase:: Getmarshalsizemax 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
dev_langs:
- C++
helpviewer_keywords:
- GetMarshalSizeMax method
ms.assetid: b416b1bf-c73e-45d5-abb8-04921c1a0c94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: baa1597a3ef0ba7014408e15cacc71bce618cd5d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590587"
---
# <a name="ftmbasegetmarshalsizemax-method"></a>FtmBase::GetMarshalSizeMax 메서드

지정된 된 개체의 지정 된 인터페이스 포인터를 마샬링하는 데 필요한 바이트 수에 상한값을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
STDMETHODIMP GetMarshalSizeMax(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out DWORD *pSize
) override;
```

### <a name="parameters"></a>매개 변수

*riid*  
마샬링될 인터페이스의 식별자에 대 한 참조입니다.

*pv*  
인터페이스 포인터를 마샬링할 수 있습니다. NULL 일 수 있습니다.

*dwDestContext*  
대상 위치 지정된 된 인터페이스를 컨텍스트 마샬링해야 합니다.

하나 이상의 MSHCTX 열거형 값을 지정 합니다.

현재 역마샬링 발생할 수 있습니다 (MSHCTX_INPROC) 현재 프로세스의 다른 아파트 또는 현재 프로세스 (MSHCTX_LOCAL)와 동일한 컴퓨터에서 다른 프로세스에서.

*pvDestContext*  
사용 하도록 예약 됩니다. NULL 이어야 합니다.

*mshlflags*  
클라이언트 프로세스에 다시 전송할 데이터를 마샬링할 수 인지 여부를 나타내는 플래그-일반적인 사례-여러 클라이언트에서 검색할 수 있는 전역 테이블에 기록 합니다. 하나 이상의 MSHLFLAGS 열거형 값을 지정 합니다.

*pSize*  
이 작업이 완료 될 때 마샬링 스트림에 쓸 데이터의 양에 상한을에 대 한 포인터입니다.

## <a name="return-value"></a>반환 값

성공 하면 s_ok이 고 이 고, 그렇지 E_FAIL 또는 E_NOINTERFACE

## <a name="requirements"></a>요구 사항

**헤더:** ftm.h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[FtmBase 클래스](../windows/ftmbase-class.md)