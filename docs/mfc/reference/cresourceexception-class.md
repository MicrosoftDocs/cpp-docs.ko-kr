---
title: CResourceException 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
dev_langs:
- C++
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 993b484c40386a60dd2da04d7198d692f5e16f97
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445076"
---
# <a name="cresourceexception-class"></a>CResourceException 클래스

Windows에서 요청된 리소스를 찾거나 할당할 수 없을 경우 발생합니다.

## <a name="syntax"></a>구문

```
class CResourceException : public CSimpleException
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CResourceException::CResourceException](#cresourceexception)|`CResourceException` 개체를 생성합니다.|

## <a name="remarks"></a>설명

추가 자격 없음은 불필요 하거나 수입니다.

사용 하 여 대 한 자세한 내용은 `CResourceException`, 문서를 참조 하세요 [예외 처리 (MFC)](../../mfc/exception-handling-in-mfc.md)합니다.

## <a name="inheritance-hierarchy"></a>상속 계층

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

##  <a name="cresourceexception"></a>  CResourceException::CResourceException

`CResourceException` 개체를 생성합니다.

```
CResourceException();
```

### <a name="remarks"></a>설명

이 생성자를 직접 사용 하지 않고 대신 전역 함수를 호출 [AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)합니다. 예외에 대 한 자세한 내용은 문서 참조 [MFC의 예외 처리](../exception-handling-in-mfc.md)합니다.

## <a name="see-also"></a>참고 항목

[CException 클래스](cexception-class.md)<br/>
[계층 구조 차트](../hierarchy-chart.md)


