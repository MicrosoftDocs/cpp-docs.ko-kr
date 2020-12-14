---
description: '자세히 알아보기: CMFCCustomColorsPropertyPage 클래스'
title: CMFCCustomColorsPropertyPage 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
ms.openlocfilehash: 9a1e5a83f2dcb291b266c3ef8fcd65422d30135a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193346"
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage 클래스

색 대화 상자에서 사용자 지정 색을 선택할 수 있는 속성 페이지를 나타냅니다.

## <a name="syntax"></a>구문

```
class CMFCCustomColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|-|-|
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|기본 생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|-|-|
|`CMFCCustomColorsPropertyPage::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|`CMFCCustomColorsPropertyPage::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[CMFCCustomColorsPropertyPage:: 설치](#setup)|속성 페이지의 색 구성 요소를 설정 합니다.|

### <a name="remarks"></a>설명

`CMFCColorDialog`클래스는이 클래스를 사용 하 여 사용자 지정 색 속성 페이지를 표시 합니다. 에 대 한 자세한 내용은 `CMFCColorDialog` [CMFCColorDialog 클래스](../../mfc/reference/cmfccolordialog-class.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 개체를 생성 하 `CMFCCustomColorsPropertyPage` 고 속성 페이지의 색 구성 요소를 설정 하는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxcustomcolorspropertypage

## <a name="cmfccustomcolorspropertypagesetup"></a><a name="setup"></a> CMFCCustomColorsPropertyPage:: 설치

속성 페이지의 색 구성 요소를 설정 합니다.

```cpp
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>매개 변수

*&*\
진행 RGB 값의 빨강 구성 요소입니다.

*Express-g*\
진행 RGB 값의 녹색 구성 요소입니다.

*B*\
진행 RGB 값의 파랑 구성 요소입니다.

### <a name="remarks"></a>설명

이 메서드는 속성 페이지의 현재 RGB 및 연결 된 HLS (색상, 밝기 및 채도) 색 값을 업데이트 합니다. [CMFCColorDialog:: SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) 메서드는 프레임 워크가 색 대화 상자를 초기화 하거나 사용자가 왼쪽 마우스 단추를 누를 때이 메서드를 호출 합니다. 에 대 한 자세한 내용은 `CMFCColorDialog` [CMFCColorDialog 클래스](../../mfc/reference/cmfccolordialog-class.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog 클래스](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCStandardColorsPropertyPage 클래스](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
