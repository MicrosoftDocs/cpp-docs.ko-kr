---
description: '자세히 알아보기: COleDialog 클래스'
title: COleDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- COleDialog
- AFXODLGS/COleDialog
- AFXODLGS/COleDialog::GetLastError
helpviewer_keywords:
- COleDialog [MFC], GetLastError
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
ms.openlocfilehash: 9bdb532d58136ac2aac622fa88f674e60ec7221e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227301"
---
# <a name="coledialog-class"></a>COleDialog 클래스

OLE 대화 상자에 공통적인 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class COleDialog : public CCommonDialog
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleDialog:: GetLastError](#getlasterror)|대화 상자에서 반환 하는 오류 코드를 가져옵니다.|

## <a name="remarks"></a>설명

MFC 라이브러리는에서 파생 된 여러 클래스를 제공 합니다 `COleDialog` .

- [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)

- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)

- [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)

- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

- [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)

- [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)

- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)

- [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)

- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)

OLE 관련 대화 상자에 대 한 자세한 내용은 [ole의 아티클 대화 상자](../../mfc/dialog-boxes-in-ole.md)를 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`COleDialog`

## <a name="requirements"></a>요구 사항

**헤더:** afxodlgs

## <a name="coledialoggetlasterror"></a><a name="getlasterror"></a> COleDialog:: GetLastError

`GetLastError`에서 IDABORT를 반환 하면 멤버 함수를 호출 하 여 추가 오류 정보를 가져옵니다 `DoModal` .

```
UINT GetLastError() const;
```

### <a name="return-value"></a>반환 값

에서 반환 되는 오류 코드는 `GetLastError` 표시 되는 특정 대화 상자에 따라 다릅니다.

### <a name="remarks"></a>설명

`DoModal`특정 오류 메시지에 대 한 자세한 내용은 파생 클래스의 멤버 함수를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CCommonDialog 클래스](../../mfc/reference/ccommondialog-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
