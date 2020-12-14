---
description: '자세한 정보: CUserException 클래스'
title: CUserException 클래스
ms.date: 11/04/2016
f1_keywords:
- CUserException
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
ms.openlocfilehash: 6104aa2883a80f88aed03634f09ad1947e9c6794
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344967"
---
# <a name="cuserexception-class"></a>CUserException 클래스

최종 사용자 작업을 중지하도록 throw됩니다.

## <a name="syntax"></a>구문

```
class CUserException : public CSimpleException
```

## <a name="remarks"></a>설명

`CUserException`응용 프로그램별 예외에 throw/catch 예외 메커니즘을 사용 하려는 경우를 사용 합니다. 클래스 이름에서 "사용자"는 "사용자가 처리 해야 하는 예외가 발생 했습니다."로 해석 될 수 있습니다.

는 `CUserException` 일반적으로 `AfxMessageBox` 사용자에 게 작업이 실패 했음을 알리기 위해 전역 함수를 호출한 후에 throw 됩니다. 예외 처리기를 작성 하는 경우 일반적으로 사용자에 게 오류에 대 한 알림이 이미 있으므로 예외를 특별히 처리 합니다. 일부 경우 프레임 워크에서이 예외를 throw 합니다. 사용자를 직접 throw 하려면 `CUserException` 사용자에 게 경고 한 다음 전역 함수를 호출 `AfxThrowUserException` 합니다.

아래 예제에서는 실패할 수 있는 작업을 포함 하는 함수가 사용자에 게 경고 하 고을 throw `CUserException` 합니다. 호출 하는 함수는 예외를 catch 하 고 특수 하 게 처리 합니다.

[!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]

사용에 대 한 자세한 내용은 `CUserException` [예외 처리 (MFC)](../../mfc/exception-handling-in-mfc.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CUserException`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CException 클래스](../../mfc/reference/cexception-class.md)
