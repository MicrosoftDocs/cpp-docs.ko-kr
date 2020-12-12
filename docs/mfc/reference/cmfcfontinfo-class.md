---
description: '자세히 알아보기: CMFCFontInfo 클래스'
title: CMFCFontInfo 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::GetFullName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nCharSet
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nPitchAndFamily
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nType
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strScript
helpviewer_keywords:
- CMFCFontInfo [MFC], GetFullName
- CMFCFontInfo [MFC], m_nCharSet
- CMFCFontInfo [MFC], m_nPitchAndFamily
- CMFCFontInfo [MFC], m_nType
- CMFCFontInfo [MFC], m_strName
- CMFCFontInfo [MFC], m_strScript
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
ms.openlocfilehash: 0922e07f268509cd4b5552a6123d8d3465a426bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265417"
---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo 클래스

`CMFCFontInfo`클래스는 글꼴의 이름 및 기타 특성을 설명 합니다.

## <a name="syntax"></a>구문

```
class CMFCFontInfo : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CMFCFontInfo`|`CMFCFontInfo` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCFontInfo::GetFullName](#getfullname)|글꼴 및 해당 문자 집합 (스크립트)의 연결 된 이름을 검색 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CMFCFontInfo:: m_nCharSet](#m_ncharset)|글꼴과 관련 된 문자 집합 (스크립트)을 지정 하는 값입니다.|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|글꼴의 피치와 패밀리를 지정 하는 값입니다.|
|[CMFCFontInfo::m_nType](#m_ntype)|글꼴의 유형을 지정 하는 값입니다.|
|[CMFCFontInfo::m_strName](#m_strname)|글꼴의 이름입니다. 예를 들면 **Arial** 입니다.|
|[CMFCFontInfo:: m_strScript](#m_strscript)|글꼴과 연결 된 문자 집합 (스크립트)의 이름입니다.|

## <a name="remarks"></a>설명

`CMFCFontInfo`개체를 [Cmfc; 콤보 상자 클래스](../../mfc/reference/cmfctoolbarfontcombobox-class.md) 클래스의 항목에 연결할 수 있습니다. [Cmfc의 글꼴 combobox:: Get글꼴 desc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) 메서드를 호출 하 여 개체에 대 한 포인터를 검색 `CMFCFontInfo` 합니다.

## <a name="example"></a>예제

다음 예제에서는 클래스의 여러 멤버를 사용 하는 방법을 보여 줍니다 `CMFCFontInfo` . 이 예제에서는에서 개체를 가져오는 방법과 `CMFCFontInfo` `CMFCRibbonFontComboBox` 해당 지역 변수에 액세스 하는 방법을 보여 줍니다. 이 예제는 [MSOffice 2007 Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>요구 사항

**헤더:** afxtoolbarfontcombobox

## <a name="cmfcfontinfocmfcfontinfo"></a><a name="cmfcfontinfo"></a> CMFCFontInfo::CMFCFontInfo

`CMFCFontInfo` 개체를 생성합니다.

```
CMFCFontInfo(
    LPCTSTR lpszName,
    LPCTSTR lpszScript,
    BYTE nCharSet,
    BYTE nPitchAndFamily,
    int nType);

CMFCFontInfo(const CMFCFontInfo& src);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
진행 글꼴의 이름입니다. 자세한 내용은 `lfFaceName` [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 구조체의 멤버를 참조 하십시오.

*lpszScript*<br/>
진행 글꼴의 스크립트 (문자 집합) 이름입니다.

*nCharSet*<br/>
진행 글꼴의 문자 집합 (스크립트)을 지정 하는 값입니다. 자세한 내용은 `lfCharSet` [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 구조체의 멤버를 참조 하십시오.

*nPitchAndFamily*<br/>
진행 글꼴의 피치와 패밀리를 지정 하는 값입니다. 자세한 내용은 `lfPitchAndFamily` [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 구조체의 멤버를 참조 하십시오.

*nType*<br/>
진행 글꼴 유형을 지정 하는 값입니다. 이 매개 변수는 DEVICE_FONTTYPE, RASTER_FONTTYPE 및 TRUETYPE_FONTTYPE의 비트 조합 (OR) 일 수 있습니다.

*src*<br/>
진행 `CMFCFontInfo` 이 개체를 생성 하는 데 사용 되는 멤버를 포함 하는 기존 개체 `CMFCFontInfo` 입니다.

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

이 설명서에서는 *문자 집합* 및 *스크립트* 를 교대로 사용 합니다. 쓰기 시스템이 라고도 하는 *스크립트* 는 하나 이상의 언어로 문자를 쓰는 데 사용할 수 있는 문자 및 규칙의 모음입니다. 문자 컬렉션에는 해당 스크립트에서 사용 되는 영문자와 문장 부호가 포함 됩니다. 예를 들어 라틴어 스크립트는 미국에서 음성으로 사용되는 영어에 사용되고 알파벳은 A부터 Z 까지의 문자를 포함합니다. [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 구조체의 `lfCharSet`멤버는 문자 집합을 지정합니다. 예를 들어 ANSI_CHARSET 값은 라틴어 스크립트의 영문자를 포함 하는 ANSI 문자 집합을 지정 합니다.

## <a name="cmfcfontinfogetfullname"></a><a name="getfullname"></a> CMFCFontInfo:: GetFullName

글꼴 및 해당 문자 집합 (스크립트)의 연결 된 이름을 검색 합니다.

```
CString GetFullName() const;
```

### <a name="return-value"></a>반환 값

글꼴 이름 및 스크립트를 포함 하는 문자열입니다.

### <a name="remarks"></a>설명

이 메서드를 사용 하 여 글꼴의 전체 이름을 가져옵니다. 예를 들어 글꼴 이름이 **Arial** 이 고 글꼴 스크립트가 **키릴 자모** 인 경우이 메서드는 "arial (키릴 자모)"을 반환 합니다.

## <a name="cmfcfontinfom_ncharset"></a><a name="m_ncharset"></a> CMFCFontInfo:: m_nCharSet

글꼴과 관련 된 문자 집합 (스크립트)을 지정 하는 값입니다.

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>설명

자세한 내용은 [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) 생성자의 *ncharset* 매개 변수를 참조 하세요.

## <a name="cmfcfontinfom_npitchandfamily"></a><a name="m_npitchandfamily"></a> CMFCFontInfo:: m_nPitchAndFamily

글꼴의 피치 (포인트 크기)와 패밀리 (예: serif, sans-serif, 고정 폭)를 지정 하는 값입니다.

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>설명

자세한 내용은 [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) 생성자의 *nPitchAndFamily* 매개 변수를 참조 하세요.

## <a name="cmfcfontinfom_ntype"></a><a name="m_ntype"></a> CMFCFontInfo:: m_nType

글꼴의 유형을 지정 하는 값입니다.

```
const int m_nType;
```

### <a name="remarks"></a>설명

자세한 내용은 [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) 생성자의 *nType* 매개 변수를 참조 하세요.

## <a name="cmfcfontinfom_strname"></a><a name="m_strname"></a> CMFCFontInfo:: m_strName

글꼴 이름입니다 (예: **Arial**).

```
const CString m_strName;
```

### <a name="remarks"></a>설명

자세한 내용은 [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) 생성자의 *lpszName* 매개 변수를 참조 하세요.

## <a name="cmfcfontinfom_strscript"></a><a name="m_strscript"></a> CMFCFontInfo:: m_strScript

글꼴과 연결 된 문자 집합 (스크립트)의 이름입니다.

```
const CString m_strScript;
```

### <a name="remarks"></a>설명

자세한 내용은 [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo) 생성자의 *lpszScript* 매개 변수를 참조 하세요.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc의 글꼴 Combobox 클래스](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCToolBarFontSizeComboBox 클래스](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
