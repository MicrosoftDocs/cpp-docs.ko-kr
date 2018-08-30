---
title: CMFCAcceleratorKeyAssignCtrl 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::GetAccel
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsFocused
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::ResetKey
dev_langs:
- C++
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl [MFC], CMFCAcceleratorKeyAssignCtrl
- CMFCAcceleratorKeyAssignCtrl [MFC], GetAccel
- CMFCAcceleratorKeyAssignCtrl [MFC], IsFocused
- CMFCAcceleratorKeyAssignCtrl [MFC], IsKeyDefined
- CMFCAcceleratorKeyAssignCtrl [MFC], PreTranslateMessage
- CMFCAcceleratorKeyAssignCtrl [MFC], ResetKey
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f42be291628a1d301309adbb48dd13211cd7857
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210325"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>CMFCAcceleratorKeyAssignCtrl 클래스
합니다 `CMFCAcceleratorKeyAssignCtrl` 클래스를 확장 합니다 [CEdit 클래스](../../mfc/reference/cedit-class.md) ALT, CONTROL, SHIFT 등의 추가 시스템 단추를 지원 하도록 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CMFCAcceleratorKeyAssignCtrl : public CEdit  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|`CMFCAcceleratorKeyAssignCtrl` 개체를 생성합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|`CMFCAcceleratorKeyAssignCtrl` 개체에서 누른 바로 가기 키에 대한 `ACCEL` 구조체를 검색합니다.|  
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||  
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|바로 가기 키가 정의되었는지 여부를 확인합니다.|  
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|클래스에서 사용 하는 [CWinApp](../../mfc/reference/cwinapp-class.md) 디스패치 되기 전에 창 메시지를 변환 하는 [TranslateMessage](https://msdn.microsoft.com/library/windows/desktop/ms644955) 하 고 [DispatchMessage](https://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 함수입니다. ( [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)를 재정의합니다.)|  
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|바로 가기 키를 다시 설정합니다.|  
  
## <a name="remarks"></a>설명  
 이 클래스는 액셀러레이터 키라고도 하는 바로 가기 키를 지원하여 `CEdit` 클래스의 기능을 확장합니다. 합니다 `CMFCAcceleratorKeyAssignCtrl` 함수를 클래스를 [CEdit 클래스](../../mfc/reference/cedit-class.md) 및 시스템 단추를 인식할 수도 있습니다.  
  
 이 클래스는 실제 바로 가기 키 조합을 문자열 값에 매핑합니다. 예를 들어 키 조합 ALT + B가 문자열 "Alt + B"에 매핑된다고 가정하겠습니다. 사용자가 `CMFCAcceleratorKeyAssignCtrl` 개체에서 이 키를 조합을 누르면 "Alt + B"가 사용자에게 표시됩니다. 바로 가기 키와 문자열 형식 간 매핑에 대 한 자세한 내용은 참조 하십시오 [CMFCAcceleratorKey 클래스](../../mfc/reference/cmfcacceleratorkey-class.md)합니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 `CMFCAcceleratorKeyAssignCtrl` 개체를 생성하고 해당 `ResetKey` 메서드를 사용하여 바로 가기 키를 다시 설정하는 방법을 보여 줍니다.  
  
 [!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 `CMFCAcceleratorKeyAssignCtrl`   
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxacceleratorkeyassignctrl.h  
  
##  <a name="cmfcacceleratorkeyassignctrl"></a>  CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl  
 생성 된 [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) 개체입니다.  
  
```  
CMFCAcceleratorKeyAssignCtrl();
```  
  
##  <a name="getaccel"></a>  CMFCAcceleratorKeyAssignCtrl::GetAccel  
 검색 된 `ACCEL` 구조체의 바로 가기 키 누름에 대 한는 [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) 개체입니다.  
  
```  
ACCEL const* GetAccel() const;  
```  
  
### <a name="return-value"></a>반환 값  
 `ACCEL` 바로 가기 키를 설명 하는 구조입니다.  
  
### <a name="remarks"></a>설명  
 이 함수를 사용 하 여 검색 하는 `ACCEL` 사용자가 입력 하는 바로 가기 키에 대 한 구조에 `CMFCAcceleratorKeyAssignCtrl` 개체입니다.  
  
##  <a name="isfocused"></a>  CMFCAcceleratorKeyAssignCtrl::IsFocused  
 자세한 세부 정보에 대 한 참조에 있는 소스 코드를 **VC\\atlmfc\\src\\mfc** Visual Studio 설치의 폴더입니다.  
  
```  
BOOL IsFocused() const;  
```  
  
### <a name="return-value"></a>반환 값  
  
### <a name="remarks"></a>설명  
  
##  <a name="iskeydefined"></a>  CMFCAcceleratorKeyAssignCtrl::IsKeyDefined  
 바로 가기 키에 정의 되었는지 여부를 결정 합니다 [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) 개체입니다.  
  
```  
BOOL IsKeyDefined() const;  
```  
  
### <a name="return-value"></a>반환 값  
 이미 눌렀음을 바로 가기 키를 정의 하는 키의 유효한 조합이 아닌 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 이 함수를 사용 하 여 사용자의 유효한 바로 가기 키를 입력 하는지 여부를 확인 하려면 프로그램 `CMFCAcceleratorKeyAssignCtrl` 개체입니다. 바로 가기 키가 있는 경우 사용할 수 있습니다 [CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel) 메서드를 `ACCEL` 이 바로 가기 키와 연결 된 구조입니다.  
  
##  <a name="pretranslatemessage"></a>  CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage  
 자세한 세부 정보에 대 한 참조에 있는 소스 코드를 **VC\\atlmfc\\src\\mfc** Visual Studio 설치의 폴더입니다.  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] *pMsg*  
  
### <a name="return-value"></a>반환 값  
  
### <a name="remarks"></a>설명  
  
##  <a name="resetkey"></a>  CMFCAcceleratorKeyAssignCtrl::ResetKey  
 바로 가기 키를 다시 설정합니다.  
  
```  
void ResetKey();
```  
  
### <a name="remarks"></a>설명  
 함수 편집 컨트롤 텍스트를 지웁니다. 이 사용자가 누른 바로 가기 키를 포함 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [클래스](../../mfc/reference/mfc-classes.md)   
 [CMFCAcceleratorKey 클래스](../../mfc/reference/cmfcacceleratorkey-class.md)
