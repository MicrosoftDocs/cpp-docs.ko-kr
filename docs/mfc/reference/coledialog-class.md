---
title: COleDialog 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDialog
- AFXODLGS/COleDialog
- AFXODLGS/COleDialog::GetLastError
dev_langs:
- C++
helpviewer_keywords:
- COleDialog [MFC], GetLastError
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a41aa479fd87c76dbf167d728ad2dbb830f6a24b
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853623"
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
|[COleDialog::GetLastError](#getlasterror)|대화 상자에서 반환 된 오류 코드를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 파생 된 여러 클래스를 제공 하는 Microsoft Foundation Class 라이브러리를 `COleDialog`:  
  
- [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)  
  
- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)  
  
- [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)  
  
- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
- [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)  
  
- [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)  
  
- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)  
  
- [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)  
  
- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)  
  
 OLE 관련 대화 상자에 대 한 자세한 내용은 문서 참조 [OLE의 대화 상자](../../mfc/dialog-boxes-in-ole.md)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `COleDialog`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxodlgs.h  
  
##  <a name="getlasterror"></a>  COleDialog::GetLastError  
 호출을 `GetLastError` 멤버 함수 추가 오류 정보를 가져올 때 `DoModal` IDABORT를 반환 합니다.  
  
```  
UINT GetLastError() const;  
```  
  
### <a name="return-value"></a>반환 값  
 반환 된 오류 코드 `GetLastError` 표시 되는 특정 대화 상자에 따라 달라 집니다.  
  
### <a name="remarks"></a>설명  
 참조 된 `DoModal` 특정 오류 메시지에 대 한 정보에 대 한 파생된 클래스에서 멤버 함수입니다.  
  
## <a name="see-also"></a>참고 항목  
 [CCommonDialog 클래스](../../mfc/reference/ccommondialog-class.md)   
 [계층 구조 차트](../../mfc/hierarchy-chart.md)



