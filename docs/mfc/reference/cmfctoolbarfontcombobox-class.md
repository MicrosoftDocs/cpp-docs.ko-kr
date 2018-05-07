---
title: CMFCToolBarFontComboBox 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea8f05c20c3a3276f51b4267b6763831dc23eacf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox 클래스
사용자가 시스템 글꼴 목록에서 글꼴을 선택할 수 있도록 콤보 상자 컨트롤을 포함 하는 도구 모음 단추입니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton  
```  
  
## <a name="members"></a>멤버  
  
### <a name="protected-constructors"></a>Protected 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|`CMFCToolBarFontComboBox` 개체를 생성합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|에 대 한 포인터를 반환 합니다.는 `CMFCFontInfo` 콤보 상자에서 지정한 인덱스에 대 한 개체입니다.|  
|[CMFCToolBarFontComboBox::SetFont](#setfont)|글꼴의 이름 또는 글꼴의 접두사와 문자 집합 중 하나에 따라 글꼴 콤보 상자에는 글꼴을 선택합니다.|  
  
### <a name="data-members"></a>데이터 멤버  
 [CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)  
 글꼴 콤보 상자에 있는 문자의 높이입니다.  
  
## <a name="remarks"></a>설명  
 글꼴 콤보 상자 단추를 도구 모음을 추가 하려면 다음이 단계를 수행 합니다.  
  
1.  부모 도구 모음 리소스의 단추에 대한 더미 리소스 ID를 예약합니다.  
  
2.  생성 된 `CMFCToolBarFontComboBox` 개체입니다.  
  
3.  처리 하는 메시지 처리기에는 `AFX_WM_RESETTOOLBAR` 메시지에서 원래 단추를 사용 하 여 새 콤보 상자 단추와 대체 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)합니다.  
  
4.  동기화를 사용 하 여 문서에 글꼴이 포함 된 콤보 상자에서 선택 된 글꼴의 [CMFCToolBarFontComboBox::SetFont](#setfont) 메서드.  
  
 사용 하 여 문서의 글꼴 콤보 상자에서 선택한 글꼴을 동기화 하려면는 [CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc) 선택한 글꼴의 특성을 검색 한 만들려면 이러한 특성을 사용 하는 메서드는 [ CFont 클래스](../../mfc/reference/cfont-class.md) 개체입니다.  
  
 Win32 함수를 호출 하는 글꼴 콤보 상자 단추 [EnumFontFamiliesEx](http://msdn.microsoft.com/library/windows/desktop/dd162620) 시스템에 사용할 수 있는 화면과 프린터 글꼴을 확인 하려면.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
 [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxtoolbarfontcombobox.h  
  
##  <a name="cmfctoolbarfontcombobox"></a>  CMFCToolBarFontComboBox::CMFCToolBarFontComboBox  
 생성 된 [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) 개체입니다.  
  
```  
public:  
CMFCToolBarFontComboBox(
    UINT uiID,  
    int iImage,  
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,  
    BYTE nCharSet = DEFAULT_CHARSET,  
    DWORD dwStyle = CBS_DROPDOWN,  
    int iWidth = 0,  
    BYTE nPitchAndFamily = DEFAULT_PITCH);

 
protected:  
CMFCToolBarFontComboBox(
    CObList* pLstFontsExternal,  
    int nFontType,  
    BYTE nCharSet,  
    BYTE nPitchAndFamily);  
  
CMFCToolBarFontComboBox();
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `uiID`  
 콤보 상자의 명령 ID입니다.  
  
 [in] `iImage`  
 도구 모음 이미지의 0부터 시작 하는 인덱스입니다. 이미지에는 [CMFCToolBarImages 클래스](../../mfc/reference/cmfctoolbarimages-class.md) 개체를 [CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md) 클래스를 유지 관리 합니다.  
  
 [in] `nFontType`  
 콤보 상자에 포함 된 글꼴의 형식입니다. 이 매개 변수는 다음 값의 조합 (OR 부울) 일 수 있습니다.  
  
 DEVICE_FONTTYPE  
  
 RASTER_FONTTYPE  
  
 또는 이러한 옵션의  
  
 [in] `nCharSet`  
 집합 DEFAULT_CHARSET, 콤보 상자에 포함 된 경우 모든 문자 집합의 모든 고유 하 게 이름이 지정 된 글꼴. (있는 경우 이름이 같은 두 가지 글꼴, 콤보 상자 포함 되어 그 중 하나입니다.) 콤보 상자 유효한 문자 집합 값으로 설정 포함 된 경우 지정된 된 문자 집합의 글꼴만. 참조 [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) 가능한 문자에 대 한 목록을 설정 합니다.  
  
 [in] `dwStyle`  
 콤보 상자의 스타일입니다. (참조 [콤보 상자 스타일](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))  
  
 [in] `iWidth`  
 편집 컨트롤의 픽셀 너비입니다.  
  
 [in] `nPitchAndFamily`  
 집합 DEFAULT_PITCH, 콤보 상자에 포함 된 경우 글꼴 피치에 관계 없이. FIXED_PITCH 또는 VARIABLE_PITCH로 설정, 콤보 상자 포함 해당 피치 형식과 글꼴만 합니다. 글꼴 패밀리를 기반으로 필터링 현재 지원 되지 않습니다.  
  
 [out] `pLstFontsExternal`  
 에 대 한 포인터는 [CObList 클래스](../../mfc/reference/coblist-class.md) 사용 가능한 글꼴을 저장 하는 개체입니다.  
  
### <a name="remarks"></a>설명  
 일반적으로 `CMFCToolBarFontComboBox` 개체 목록을 사용할 수 있는 글꼴 공유 되는 하나의 저장 `CObList` 개체입니다. 생성자의 두 번째 오버 로드를 사용 하 고에 대 한 유효한 포인터를 제공 하는 경우 `pLstFontsExternal`, 해당 `CMFCToolBarFontComboBox` 개체를 채울 대신는 `CObList` 있는 `pLstFontsExternal` 있는 사용 가능한 글꼴을 가리킵니다.  
  
### <a name="example"></a>예제  
 다음 예제에서는 생성 하는 방법을 `CMFCToolBarFontComboBox` 개체입니다. 이 코드 조각은 [워드 패드 샘플](../../visual-cpp-samples.md)의 일부입니다.  
  
 [!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]  
  
##  <a name="getfontdesc"></a>  CMFCToolBarFontComboBox::GetFontDesc  
 에 대 한 포인터를 반환 합니다.는 `CMFCFontInfo` 콤보 상자에서 지정한 인덱스에 대 한 개체입니다.  
  
```  
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `iIndex`  
 콤보 상자 항목의 0부터 시작 하는 인덱스를 지정합니다.  
  
### <a name="return-value"></a>반환 값  
 에 대 한 포인터는 `CMFCFontInfo` 개체입니다. 경우 `iIndex` 유효한 항목 인덱스를 지정 하지 않는 경우 반환 값은 `NULL`합니다.  
  
##  <a name="m_nfontheight"></a>  CMFCToolBarFontComboBox::m_nFontHeight  
 콤보 상자에 소유자 그리기 스타일은 글꼴 콤보 상자에 있는 문자의 픽셀 단위 높이 지정 합니다.  
  
```  
static int m_nFontHeight  
```  
  
### <a name="remarks"></a>설명  
 경우는 `m_nFontHeight` 변수는 0, 높이 콤보 상자의 기본 글꼴에 따라 자동으로 계산 됩니다. 높이 상승 된 기준선을 초과 하는 문자 및 문자 기준선 아래 디센더 모두 포함 되어 있습니다.  
  
##  <a name="setfont"></a>  CMFCToolBarFontComboBox::SetFont  
 글꼴의 글꼴 이름 및 문자에 따라 글꼴 콤보 상자에서 집합을 선택 합니다. 매개 변수에서 지정 됩니다.  
  
```  
BOOL SetFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BOOL bExact=FALSE);
```  
  
### <a name="parameters"></a>매개 변수  
 [in] `lpszName`  
 글꼴 이름 또는 접두사를 지정합니다.  
  
 [in] `nCharSet`  
 문자 집합을 지정 합니다.  
  
 [in] `bExact`  
 지정 하는지 여부를 `lpszName` 글꼴 이름 또는 글꼴 접두사를 포함 합니다.  
  
### <a name="return-value"></a>반환 값  
 글꼴을 성공적으로 선택한 경우에 0이 아닌 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 경우 `bExact` 은 `TRUE`,으로 지정한 이름과 정확히 일치 하는 글꼴을 선택 하는이 메서드 `lpszName`합니다. 경우 `bExact` 은 `FALSE`로 지정 된 텍스트로 시작 하는 글꼴을 선택 하는이 메서드 `lpszName` 로 지정 하는 문자 집합을 사용 하 여 `nCharSet`합니다. 경우 `nCharSet` 설정 DEFAULT_CHARSET, 문자 집합 됩니다 무시 되는 항목과 `lpszName` 글꼴을 선택 하는 데 사용 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [클래스](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton 클래스](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBarComboBoxButton 클래스](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCFontInfo 클래스](../../mfc/reference/cmfcfontinfo-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [연습: 도구 모음에 컨트롤 배치](../../mfc/walkthrough-putting-controls-on-toolbars.md)



