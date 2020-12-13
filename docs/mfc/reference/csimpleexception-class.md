---
description: '자세히 알아보기: CSimpleException 클래스'
title: CSimpleException 클래스
ms.date: 11/04/2016
f1_keywords:
- CSimpleException
- AFX/CSimpleException
- AFX/CSimpleException::CSimpleException
- AFX/CSimpleException::GetErrorMessage
helpviewer_keywords:
- CSimpleException [MFC], CSimpleException
- CSimpleException [MFC], GetErrorMessage
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
ms.openlocfilehash: 8070604e05fa59f7fcdfef6dcaad12ab0497da9f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342820"
---
# <a name="csimpleexception-class"></a>CSimpleException 클래스

이 클래스는 리소스에 중요한 MFC 예외의 기본 클래스입니다.

## <a name="syntax"></a>구문

```
class AFX_NOVTABLE CSimpleException : public CException
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSimpleException::CSimpleException](#csimpleexception)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSimpleException:: GetErrorMessage](#geterrormessage)|발생 한 오류에 대 한 텍스트를 제공 합니다.|

## <a name="remarks"></a>설명

`CSimpleException` 는 리소스에 중요 한 MFC 예외의 기본 클래스 이며 오류 메시지의 소유권 및 초기화를 처리 합니다. 다음 클래스는를 `CSimpleException` 기본 클래스로 사용 합니다.

|Name|설명|
|-|-|
|[CMemoryException 클래스](../../mfc/reference/cmemoryexception-class.md)|메모리 부족 예외|
|[CNotSupportedException 클래스](../../mfc/reference/cnotsupportedexception-class.md)|지원 되지 않는 작업에 대 한 요청|
|[CResourceException 클래스](../../mfc/reference/cresourceexception-class.md)|Windows 리소스를 찾을 수 없거나 만들 수 없습니다.|
|[CUserException 클래스](../../mfc/reference/cuserexception-class.md)|리소스를 찾을 수 없음을 나타내는 예외입니다.|
|[CInvalidArgException 클래스](../../mfc/reference/cinvalidargexception-class.md)|잘못 된 인수를 나타내는 예외입니다.|

`CSimpleException`는 추상 기본 클래스 이므로 개체를 직접 선언할 수 없습니다 `CSimpleException` . 대신, 이전 표에 나와 있는 것과 같은 파생 개체를 선언 해야 합니다. 사용자 고유의 파생 클래스를 선언 하는 경우에는 이전 클래스를 모델로 사용 합니다.

자세한 내용은 [Cexception 클래스](../../mfc/reference/cexception-class.md) 항목 및 [예외 처리 (MFC)](../../mfc/exception-handling-in-mfc.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="csimpleexceptioncsimpleexception"></a><a name="csimpleexception"></a> CSimpleException::CSimpleException

생성자입니다.

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>매개 변수

*bAutoDelete*<br/>
개체에 대 한 메모리가 힙에 할당 된 경우 TRUE를 지정 `CSimpleException` 합니다. 이렇게 하면 `CSimpleException` `Delete` 멤버 함수를 호출 하 여 예외를 삭제할 때 개체가 삭제 됩니다. `CSimpleException`개체가 스택에 있거나 전역 개체 이면 FALSE를 지정 합니다. 이 경우 `CSimpleException` 멤버 함수가 호출 되 면 개체가 삭제 되지 않습니다 `Delete` .

### <a name="remarks"></a>설명

일반적으로이 생성자는 직접 호출할 필요가 없습니다. 예외를 throw 하는 함수는 파생 클래스의 인스턴스를 만들고 `CException` 해당 생성자를 호출 하거나, [AfxThrowFileException](exception-processing.md#afxthrowfileexception)와 같은 MFC throw 함수 중 하나를 사용 하 여 미리 정의 된 형식을 throw 해야 합니다.

## <a name="csimpleexceptiongeterrormessage"></a><a name="geterrormessage"></a> CSimpleException:: GetErrorMessage

발생 한 오류에 대 한 텍스트를 제공 하려면이 멤버 함수를 호출 합니다.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszError*<br/>
오류 메시지를 수신 하는 버퍼에 대 한 포인터입니다.

*nMaxError*<br/>
NULL 종결자를 포함 하 여 버퍼에서 보유할 수 있는 최대 문자 수입니다.

*pnHelpContext*<br/>
도움말 컨텍스트 ID를 받을 UINT의 주소입니다. NULL 인 경우 ID가 반환 되지 않습니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아닌 값입니다. 오류 메시지 텍스트를 사용할 수 없는 경우에는 0이 고,

### <a name="remarks"></a>설명

자세한 내용은 [Cexception:: GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CException 클래스](../../mfc/reference/cexception-class.md)<br/>
[예외 처리](../../mfc/exception-handling-in-mfc.md)
