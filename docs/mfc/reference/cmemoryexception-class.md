---
description: '자세한 정보: CMemoryException 클래스'
title: CMemoryException 클래스
ms.date: 11/04/2016
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
ms.openlocfilehash: 694629d65c8b4cffc351873d5da3d8ed3c34cf8e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336655"
---
# <a name="cmemoryexception-class"></a>CMemoryException 클래스

메모리 부족 예외 상태를 나타냅니다.

## <a name="syntax"></a>구문

```
class CMemoryException : public CSimpleException
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMemoryException:: CMemoryException](#cmemoryexception)|`CMemoryException` 개체를 생성합니다.|

## <a name="remarks"></a>설명

더 이상 정규화를 수행할 필요가 없습니다. 메모리 예외는에 의해 자동으로 throw 됩니다 **`new`** . 예를 들어를 사용 하 여 사용자 고유의 메모리 함수를 작성 하 `malloc` 는 경우 메모리 예외를 throw 해야 합니다.

에 대 한 자세한 내용은 `CMemoryException` [예외 처리 (MFC)](../../mfc/exception-handling-in-mfc.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="cmemoryexceptioncmemoryexception"></a><a name="cmemoryexception"></a> CMemoryException:: CMemoryException

`CMemoryException` 개체를 생성합니다.

```
CMemoryException();
```

### <a name="remarks"></a>설명

이 생성자는 직접 사용 하지 말고 [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)전역 함수를 호출 합니다. 이 전역 함수는 이전에 할당 된 메모리에서 예외 개체를 생성 하기 때문에 메모리 부족 상황에서 성공할 수 있습니다. 예외 처리에 대 한 자세한 내용은 [예외](../exception-handling-in-mfc.md)문서를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CException 클래스](cexception-class.md)<br/>
[계층 구조 차트](../hierarchy-chart.md)
