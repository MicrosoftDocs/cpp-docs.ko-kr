---
title: CWinFormsDialog 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1fe7c8518366065e93360187247cbd07df42d79f
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122499"
---
# <a name="cwinformsdialog-class"></a>CWinFormsDialog 클래스
Windows Forms 사용자 정의 컨트롤을 호스팅하는 MFC 대화 상자 클래스의 래퍼입니다.  
  
## <a name="syntax"></a>구문  
  
```  
template <typename TManagedControl>  
class CWinFormsDialog :   
    public CDialog  
```  
  
#### <a name="parameters"></a>매개 변수  
 `TManagedControl`  
 MFC 응용 프로그램에 표시 되는.NET Framework 사용자 정의 컨트롤  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|`CWinFormsDialog` 개체를 생성합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CWinFormsDialog::GetControl](#getcontrol)|Windows Forms 사용자 정의 컨트롤에 대 한 참조를 검색합니다.|  
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|Windows Forms 사용자 정의 컨트롤에 대 한 창 핸들을 검색합니다.|  
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|MFC 대화 상자를 만들고에 Windows Forms 사용자 정의 컨트롤 호스팅 하 여 초기화 합니다.|  
  
### <a name="public-operators"></a>Public 연산자  
  
|name||  
|----------|-|  
|[CWinFormsDialog::operator-&gt;](#operator_-_gt)|대체 [CWinFormsDialog::GetControl](#getcontrol) 식에 있습니다.|  
|[CWinFormsDialog::operator TManagedControl ^](#operator_tmanagedcontrol)|Windows Forms 사용자 정의 컨트롤에 대 한 참조로 형식을 캐스팅합니다.|  
  
## <a name="remarks"></a>설명  
 `CWinFormsDialog` MFC 대화 상자 클래스에 대 한 래퍼 인지 ( [CDialog](../../mfc/reference/cdialog-class.md))를 호스팅하는 Windows Forms 사용자 정의 컨트롤입니다. 이.NET Framework는 모달 또는 모덜리스 MFC 대화 상자 컨트롤에 표시할 수 있습니다.  
  
 Windows Forms를 사용 하 여에 대 한 자세한 내용은 참조 하십시오. [MFC의 Windows Form 사용자 정의 컨트롤을 사용 하 여](../../dotnet/using-a-windows-form-user-control-in-mfc.md) 및 [는 Windows Form 사용자 정의 컨트롤을 MFC 대화 상자로 호스팅](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxwinforms.h  
  
##  <a name="cwinformsdialog"></a>  CWinFormsDialog::CWinFormsDialog  
 `CWinFormsDialog` 개체를 생성합니다.  
  
```  
CWinFormsDialog(UINT nIDTemplate = IDD);
```  
  
### <a name="parameters"></a>매개 변수  
 *nIDTemplate*  
 대화 상자 템플릿 리소스의 ID를 포함 합니다. 대화 상자 편집기를 사용 하 여 대화 상자 템플릿을 만들고 응용 프로그램의 리소스 스크립트 파일에 저장 합니다. 대화 상자 템플릿에 대 한 자세한 내용은 참조 하십시오. [CDialog 클래스](../../mfc/reference/cdialog-class.md)합니다.  
  
##  <a name="getcontrol"></a>  CWinFormsDialog::GetControl  
 Windows Forms 사용자 정의 컨트롤에 대 한 참조를 검색합니다.  
  
```  
inline TManagedControl^ GetControl() const;  
```  
  
### <a name="return-value"></a>반환 값  
 MFC 대화 상자에서 Windows Forms 컨트롤에 대 한 참조를 반환합니다.  
  
##  <a name="getcontrolhandle"></a>  CWinFormsDialog::GetControlHandle  
 Windows Forms 사용자 정의 컨트롤에 대 한 창 핸들을 검색합니다.  
  
```  
inline HWND GetControlHandle() const throw();
```  
  
### <a name="return-value"></a>반환 값  
 Windows Forms 사용자 정의 컨트롤에 대 한 창 핸들을 반환합니다.  
  
##  <a name="oninitdialog"></a>  CWinFormsDialog::OnInitDialog  
 MFC 대화 상자를 만들고에 Windows Forms 사용자 정의 컨트롤 호스팅 하 여 초기화 합니다.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>반환 값  
 설정 여부를 응용 프로그램에 입력된 포커스가 컨트롤 중 하나를 대화 상자에서 지정 하는 부울 값입니다. 경우 `OnInitDialog` 반환 0이 아닌 Windows 입력된 포커스를 첫 번째 컨트롤로 설정 대화 상자에서 합니다. 이 메서드는 응용 프로그램에 명시적으로 설정 입력된 포커스가 컨트롤 중 하나를 대화 상자에서 경우에 0을 반환할 수 있습니다.  
  
### <a name="remarks"></a>설명  
 MFC 대화 상자를 만들 때 (사용 하는 [만들기](../../mfc/reference/cdialog-class.md#create), [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect), 또는 [DoModal](../../mfc/reference/cdialog-class.md#domodal) 에서 상속 된 [CDialog](../../mfc/reference/cdialog-class.md))는 WM_ INITDIALOG 메시지 보내고이 메서드를 호출 합니다. 대화 상자에 있는 Windows Forms 컨트롤의 인스턴스를 만들고 하 고 사용자 정의 컨트롤의 크기에 맞게 대화 상자의 크기를 조정 합니다. 그런 다음 MFC 대화 상자에서 새 컨트롤을 호스트 합니다.  
  
 대화 상자 초기화 될 때 특수 한 처리를 수행 해야 할 경우이 멤버 함수를 재정의 합니다. 이 메서드를 사용 하 여에 대 한 자세한 내용은 참조 하십시오. [CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)합니다.  
  
##  <a name="operator_-_gt"></a>  CWinFormsDialog::operator-&gt;  
 대체 [CWinFormsDialog::GetControl](#getcontrol) 식에 있습니다.  
  
```  
inline TManagedControl^  operator->() const throw();
```  
  
### <a name="remarks"></a>설명  
 이 연산자를 대체 하는 편리한 구문 제공 `GetControl` 식에 있습니다.  
  
 Windows Forms를 사용 하는 방법은 참조 하십시오. [MFC의 Windows Form 사용자 정의 컨트롤을 사용 하 여](../../dotnet/using-a-windows-form-user-control-in-mfc.md)합니다.  
  
##  <a name="operator_tmanagedcontrol_xor"></a>  CWinFormsDialog::operator TManagedControl ^  
 Windows Forms 사용자 정의 컨트롤에 대 한 참조로 형식을 캐스팅합니다.  
  
```  
inline operator TManagedControl^() const throw();
```  
  
### <a name="remarks"></a>설명  
 이 연산자는 Windows Forms 컨트롤에 대 한 참조로 형식을 캐스팅합니다. 전달 하는 데 사용 되는 `CWinFormsDialog<TManagedControl>` 대화 상자에 Windows Forms 사용자 컨트롤 개체에 대 한 포인터를 허용 하는 함수입니다.  
  
## <a name="see-also"></a>참고 항목  
 [CWnd 클래스](../../mfc/reference/cwnd-class.md)   
 [CWinFormsView 클래스](../../mfc/reference/cwinformsview-class.md)   
 [CDialog 클래스](../../mfc/reference/cdialog-class.md)
