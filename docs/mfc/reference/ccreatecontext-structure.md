---
description: '자세한 정보: CCreateContext 구조체'
title: CCreateContext 구조체
ms.date: 11/04/2016
f1_keywords:
- CCreateContext
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
ms.openlocfilehash: b0d8c3a38d4d6ce9ee6130092ea6b27a50ed15e3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220463"
---
# <a name="ccreatecontext-structure"></a>CCreateContext 구조체

프레임 워크는 `CCreateContext` 문서와 연결 된 프레임 창과 뷰를 만들 때 구조체를 사용 합니다.

## <a name="syntax"></a>구문

```
struct CCreateContext
```

## <a name="remarks"></a>설명

`CCreateContext` 는 구조체 이며 기본 클래스를 포함 하지 않습니다.

창을 만들 때이 구조의 값은 문서의 구성 요소를 데이터 보기에 연결 하는 데 사용 되는 정보를 제공 합니다. `CCreateContext`만들기 프로세스의 일부를 재정의 하는 경우에만를 사용 해야 합니다.

`CCreateContext`구조는 문서, 프레임 창, 뷰 및 문서 템플릿에 대 한 포인터를 포함 합니다. 또한 `CRuntimeClass` 만들 뷰의 유형을 식별 하는에 대 한 포인터를 포함 합니다. 런타임 클래스 정보 및 현재 문서 포인터를 사용 하 여 새 뷰를 동적으로 만들 수 있습니다. 다음 표에서는 각 멤버를 사용 하는 방법과 시기를 제안 합니다 `CCreateContext` .

|멤버|형식|대상|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass` 새 뷰를 만듭니다.|
|`m_pCurrentDoc`|`CDocument*`|새 뷰와 연결 될 기존 문서입니다.|
|`m_pNewDocTemplate`|`CDocTemplate*`|새 MDI 프레임 창의 생성과 관련 된 문서 템플릿입니다.|
|`m_pLastView`|`CView*`|분할 창 보기를 만들거나 문서에 대 한 두 번째 뷰를 만들 때와 같이 추가 뷰가 모델링 되는 원래 뷰입니다.|
|`m_pCurrentFrame`|`CFrameWnd*`|문서에 두 번째 프레임 창을 만들 때와 같이 추가 프레임 창이 모델링 되는 프레임 창입니다.|

문서 템플릿은 문서와 관련 구성 요소를 만들 때 구조에 저장 된 정보의 유효성을 검사 합니다 `CCreateContext` . 예를 들어 존재 하지 않는 문서에 대 한 뷰를 만들지 않아야 합니다.

> [!NOTE]
> 의 모든 포인터는 `CCreateContext` 선택 사항이 며 `NULL` 지정 되지 않거나 알 수 없는 경우 일 수 있습니다.

`CCreateContext` 는 "참고 항목"에 나열 된 멤버 함수에서 사용 됩니다. 이러한 함수를 재정의 하려는 경우 특정 정보에 대해서는 이러한 함수에 대 한 설명을 참조 하세요.

다음은 몇 가지 일반적인 지침입니다.

- , 및에서와 같이 창 만들기에 대 한 인수로 전달 되 `CWnd::Create` `CFrameWnd::Create` 는 경우 `CFrameWnd::LoadFrame` 만들기 컨텍스트는 새 창이 연결 되는 대상을 지정 합니다. 대부분의 windows에서 전체 구조는 선택 사항이 며 `NULL` 포인터를 전달할 수 있습니다.

- 와 같은 재정의 가능한 멤버 함수의 경우 `CFrameWnd::OnCreateClient` 인수는 `CCreateContext` 선택 사항입니다.

- 뷰 생성에 관련 된 멤버 함수의 경우 뷰를 만드는 데 충분 한 정보를 제공 해야 합니다. 예를 들어 분할자 창의 첫 번째 뷰에 대해 뷰 클래스 정보와 현재 문서를 제공 해야 합니다.

일반적으로 프레임 워크 기본값을 사용 하는 경우 무시 해도 `CCreateContext` 됩니다. 더 많은 고급 수정을 시도 하는 경우 MFC 라이브러리 소스 코드 또는 샘플 프로그램 (예: VIEWEX)이 안내 합니다. 필수 매개 변수를 잊은 경우 프레임 워크 어설션이 사용자의 잊어버린 사항을 알려 줍니다.

에 대 한 자세한 내용은 `CCreateContext` MFC 샘플 [VIEWEX](../../overview/visual-cpp-samples.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** afxext.h

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterWnd:: Create](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterWnd:: CreateView](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[CWnd::Create](../../mfc/reference/cwnd-class.md#create)
