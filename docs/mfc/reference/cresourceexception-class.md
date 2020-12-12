---
description: '자세한 정보: CResourceException 클래스'
title: CResourceException 클래스
ms.date: 11/04/2016
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
ms.openlocfilehash: c76635ae2cfa6c55bf54da7e73f6afbb44506fee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264871"
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
|[CResourceException:: CResourceException](#cresourceexception)|`CResourceException` 개체를 생성합니다.|

## <a name="remarks"></a>설명

더 이상 정규화를 수행할 필요가 없습니다.

사용에 대 한 자세한 내용은 `CResourceException` [예외 처리 (MFC)](../../mfc/exception-handling-in-mfc.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cresourceexceptioncresourceexception"></a><a name="cresourceexception"></a> CResourceException:: CResourceException

`CResourceException` 개체를 생성합니다.

```
CResourceException();
```

### <a name="remarks"></a>설명

이 생성자는 직접 사용 하지 말고 [AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)전역 함수를 호출 합니다. 예외에 대 한 자세한 내용은 [MFC의 예외 처리](../exception-handling-in-mfc.md)문서를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CException 클래스](cexception-class.md)<br/>
[계층 구조 차트](../hierarchy-chart.md)
