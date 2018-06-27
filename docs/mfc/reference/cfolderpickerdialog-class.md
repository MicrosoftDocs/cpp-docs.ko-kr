---
title: CFolderPickerDialog 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
dev_langs:
- C++
helpviewer_keywords:
- CFolderPickerDialog [MFC], CFolderPickerDialog
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ded586e6d8ad5252d73e0972424915d174b8b1f3
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956527"
---
# <a name="cfolderpickerdialog-class"></a>CFolderPickerDialog 클래스
CFolderPickerDialog 클래스 폴더 선택 모드에서 CFileDialog를 구현 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CFolderPickerDialog : public CFileDialog;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CFolderPickerDialog:: ~ CFolderPickerDialog](#cfolderpickerdialog__~cfolderpickerdialog)|소멸자|  
|[CFolderPickerDialog::CFolderPickerDialog](#cfolderpickerdialog)|생성자입니다.|  
  
## <a name="remarks"></a>설명  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [CFileDialog](../../mfc/reference/cfiledialog-class.md)  
  
 `CFolderPickerDialog`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxdlgs.h  
  
##  <a name="cfolderpickerdialog"></a>  CFolderPickerDialog::CFolderPickerDialog  
 생성자입니다.  
  
```  
explicit CFolderPickerDialog(
    LPCTSTR lpszFolder = NULL,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL,  
    DWORD dwSize = 0);
```  
  
### <a name="parameters"></a>매개 변수  
 *lpszFolder*  
 초기 폴더입니다.  
  
 *dwFlags*  
 대화 상자를 사용자 지정할 수 있도록 하는 하나 이상의 플래그의 조합입니다.  
  
 *pParentWnd*  
 대화 상자 개체의 부모 또는 소유자 창에 대 한 포인터입니다.  
  
 *dwSize*  
 OPENFILENAME 구조체의 크기입니다.  
  
### <a name="remarks"></a>설명  
  
##  <a name="_dtorcfolderpickerdialog"></a>  CFolderPickerDialog:: ~ CFolderPickerDialog  
 소멸자  
  
```  
virtual ~CFolderPickerDialog();
```  
  
### <a name="remarks"></a>설명  
  
## <a name="see-also"></a>참고 항목  
 [클래스](../../mfc/reference/mfc-classes.md)
