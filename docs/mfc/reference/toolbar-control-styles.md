---
description: '자세한 정보: ToolBar 컨트롤 스타일'
title: ToolBar 컨트롤 스타일
ms.date: 11/04/2016
helpviewer_keywords:
- ToolBar control styles [MFC]
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
ms.openlocfilehash: b044f353ddbdc4ccc9d5050ea14307386b7c2a15
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218721"
---
# <a name="toolbar-control-styles"></a>ToolBar 컨트롤 스타일

[CMFCToolBarButton 클래스](../../mfc/reference/cmfctoolbarbutton-class.md) 에는 단추의 모양과 동작을 결정 하는 스타일 플래그 집합이 있습니다. [CMFCToolBarButton:: system.windows.forms.control.setstyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)를 호출 하 여 이러한 플래그를 조합 하 여 설정할 수 있습니다. 이 항목에는 스타일 플래그 값 및 해당 의미가 나열됩니다.

## <a name="property-values"></a>속성 값

다음 값에 따라 컨트롤에서 제공되는 단추 형식이 결정됩니다.

|Name|설명|
|-|-|
|TBBS_BUTTON|표준 누름 단추입니다(기본값).  |
|TBBS_CHECKBOX|확인란입니다.  |
|TBBS_CHECKGROUP|확인란 그룹의 시작 부분입니다.  |
|TBBS_GROUP|여러 단추 그룹의 시작 부분입니다.  |
|TBBS_SEPARATOR|구분선입니다.  |

다음 값은 컨트롤의 현재 상태를 나타냅니다.

|Name|설명|
|-|-|
|TBBS_CHECKED|확인란이 선택되었습니다.  |
|TBBS_DISABLED|컨트롤이 비활성화되었습니다.  |
|TBBS_INDETERMINATE|확인란이 결정되지 않은 상태입니다.  |
|TBBS_PRESSED|단추를 눌렀습니다.  |

다음 값은 도구 모음에 있는 단추의 레이아웃을 변경합니다.

|Name|설명|
|-|-|
|TBBS_BREAK|새 줄에 항목을 배치하거나 열을 구분하지 않기 새 열에 배치합니다.  |

## <a name="remarks"></a>설명

현재 스타일은 [CMFCToolBarButton:: m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle)에 저장 됩니다. 를                 `m_nStyle` 호출할 때 일부 파생 클래스에서 추가 처리를 수행 하기 때문에 새 값을 직접 설정 하지 마십시오 `SetStyles` .

시각화 관리자는 각 상태에서 단추의 모양을 결정합니다. 자세한 내용은 [시각화 관리자](../../mfc/visualization-manager.md) 를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** afxtoolbarbutton

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CMFCToolBarButton 클래스](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[시각화 관리자](../../mfc/visualization-manager.md)
