---
title: CNotSupportedException 클래스
ms.date: 11/04/2016
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
ms.openlocfilehash: 0eb3bf0de51345ed4316d2a1c5c29b8ecb3e8bba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456565"
---
# <a name="cnotsupportedexception-class"></a>CNotSupportedException 클래스

지원되지 않는 기능을 요청한 결과인 예외를 나타냅니다.

## <a name="syntax"></a>구문

```
class CNotSupportedException : public CSimpleException
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CNotSupportedException::CNotSupportedException](#cnotsupportedexception)|`CNotSupportedException` 개체를 생성합니다.|

## <a name="remarks"></a>설명

추가 자격 없음은 불필요 하거나 수입니다.

사용 하 여 대 한 자세한 내용은 `CNotSupportedException`, 문서를 참조 하세요 [예외 처리 (MFC)](../../mfc/exception-handling-in-mfc.md)합니다.

## <a name="inheritance-hierarchy"></a>상속 계층

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CNotSupportedException`

## <a name="requirements"></a>요구 사항

**헤더:** afx.h

##  <a name="cnotsupportedexception"></a>  CNotSupportedException::CNotSupportedException

`CNotSupportedException` 개체를 생성합니다.

```
CNotSupportedException();
```

### <a name="remarks"></a>설명

이 생성자를 직접 사용 하지 않고 대신 전역 함수를 호출 [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception)합니다. 예외 처리에 대 한 자세한 내용은 문서 참조 [MFC의 예외 처리](../exception-handling-in-mfc.md)합니다.

## <a name="see-also"></a>참고 항목

[CException 클래스](cexception-class.md)<br/>
[계층 구조 차트](../hierarchy-chart.md)

