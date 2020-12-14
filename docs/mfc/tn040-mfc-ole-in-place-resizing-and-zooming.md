---
description: 'TN040: MFC/OLE In-Place 크기 조정 및 확대/축소에 대해 자세히 알아보세요.'
title: 'TN040: MFC-OLE In-Place 크기 조정 및 확대/축소'
ms.date: 11/04/2016
helpviewer_keywords:
- resizing in-place
- TN040
- zooming and in-place activation
- in-place activation, zooming and resizing
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
ms.openlocfilehash: e21b70dc10ee467f94386880255287218a3b6e99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215393"
---
# <a name="tn040-mfcole-in-place-resizing-and-zooming"></a>TN040: MFC/OLE 내부 크기 조정 및 확대/축소

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 메모는 내부 편집과 관련 된 문제에 대해 설명 하 고 서버에서 확대/축소 및 전체 크기 조정을 수행 하는 방법에 대해 설명 합니다. 내부 활성화를 사용 하는 경우, WYSIWYG 개념은 컨테이너와 서버가 서로 상호 작용 하 고 특히 거의 동일한 방법으로 OLE 사양을 해석 하는 한 단계로 이루어집니다.

내부 활성화를 지 원하는 컨테이너와 서버 간의 상호 작용으로 인해 최종 사용자가 유지 관리 해야 하는 여러 가지 기대 사항이 있습니다.

- 프레젠테이션 표시 (재정의에 그려진 메타 파일 `COleServerItem::OnDraw` )는 편집을 위해 그릴 때와 정확히 동일 하 게 표시 되어야 합니다. 단, 편집 도구는 표시 되지 않습니다.

- 컨테이너를 확대 하면 서버 창도 그렇지 않습니다.

- 컨테이너와 서버 모두 동일한 메트릭을 사용 하 여 편집할 개체를 표시 해야 합니다. 즉, 디스플레이 장치에서 렌더링할 때 인치당 *논리적* 픽셀 수 (인치당 픽셀 수)를 기반으로 하는 매핑 모드를 사용 합니다.

> [!NOTE]
> 내부 활성화는 포함 된 (연결 되지 않음) 항목에만 적용 되므로 확대/축소는 포함 된 개체에만 적용 됩니다. 및에는 `COleServerDoc` `COleServerItem` 확대/축소에 사용 되는 api가 모두 표시 됩니다. 이 dichotomy에 대 한 이유는 연결 된 항목 및 포함 된 항목 모두에 유효한 함수만에 있고 `COleServerItem` (이로 인해 공통 구현을 사용할 수 있음) 포함 된 개체에 대해서만 유효한 함수는 `COleServerDoc` 클래스 (서버의 관점에서 포함 된 **문서** )에 있습니다.

서버는 컨테이너의 확대/축소 비율을 인식 하 고 해당 편집 인터페이스를 적절 하 게 수정 해야 한다는 사실을 고려 하 여 대부분의 부담이 서버 구현에 배치 됩니다. 그러나 서버가 컨테이너에서 사용 하는 확대/축소 비율을 결정 하는 방법은 무엇 인가요?

## <a name="mfc-support-for-zooming"></a>확대/축소를 위한 MFC 지원

현재 확대/축소 비율은를 호출 하 여 확인할 수 있습니다 `COleServerDoc::GetZoomFactor` . 문서가 현재 위치가 아닐 때이를 호출 하면 항상 100% 확대/축소 비율 (또는 1:1 비율)이 발생 합니다. 내부 활성 상태에서이를 호출 하면 100% 이외의 항목을 반환할 수 있습니다.

확대/축소의 예제를 보려면 MFC OLE 샘플 [HIERSVR](../overview/visual-cpp-samples.md)을 참조 하십시오. HIERSVR는 텍스트를 표시 하 고 일반 텍스트는 선형 방식으로 확장 되지 않습니다 (힌트, 입력 체계, 디자인 너비 및 높이가 모두 복잡 하 게 됨). 여전히 HIERSVR는 확대/축소를 올바르게 구현 하기 위한 적절 한 참조 이므로 MFC 자습서 [SCRIBBLE](../overview/visual-cpp-samples.md) (7 단계)입니다.

`COleServerDoc::GetZoomFactor` 컨테이너 또는 및 클래스의 구현에서 사용할 수 있는 여러 가지 메트릭을 기반으로 확대/축소 비율을 결정 합니다 `COleServerItem` `COleServerDoc` . 간단히 말해서 현재 확대/축소 비율은 다음 수식에 따라 결정 됩니다.

```
Position Rectangle (PR) / Container Extent (CE)
```

위치 사각형은 컨테이너에 의해 결정 됩니다. 가 호출 되 면 내부 활성화 중에 서버에 반환 되 `COleClientItem::OnGetItemPosition` 고,를 호출 하 여 컨테이너에서 서버를 호출할 때이를 업데이트 `COleServerDoc::OnSetItemRects` `COleClientItem::SetItemRects` 합니다.

컨테이너 범위를 계산 하는 것은 약간 더 복잡 합니다. 를 호출 하 여 컨테이너를 호출한 경우 `COleServerItem::OnSetExtent` 에는 `COleClientItem::SetExtent` 논리 인치당 픽셀 수를 기준으로이 값이 픽셀 수로 변환 됩니다. 컨테이너가 SetExtent (일반적으로)을 호출 하지 않은 경우 컨테이너 익스텐트는에서 반환 된 크기입니다 `COleServerItem::OnGetExtent` . 따라서 컨테이너가 SetExtent를 호출 하지 않은 경우 프레임 워크는 컨테이너에서 자연 익스텐트의 100% (에서 반환 된 값)를 사용 하 여이를 호출한 것으로 가정 합니다 `COleServerItem::GetExtent` . 다른 방법으로 설명 된 것 처럼 프레임 워크에서는 컨테이너가 항목의 100% (더 작은 값 없음)를 표시 한다고 가정 합니다.

`COleServerItem::OnSetExtent`및에 `COleServerItem::OnGetExtent` 비슷한 이름이 있지만 항목의 동일한 특성을 조작 하지는 않는다는 점에 유의 해야 합니다. `OnSetExtent` 는 확대/축소 비율에 관계 없이 컨테이너에 표시 되는 개체의 양을 서버에서 알 수 있도록 호출 되며, `OnGetExtent` 컨테이너에 의해 호출 되어 개체의 이상적인 크기를 결정 합니다.

관련 된 각 Api를 살펴보면 보다 명확한 그림을 얻을 수 있습니다.

## <a name="coleserveritemongetextent"></a>COleServerItem::OnGetExtent

이 함수는 항목의 HIMETRIC unit에서 "기본 크기"를 반환 해야 합니다. "자연 크기"를 생각 하는 가장 좋은 방법은 인쇄 시 표시 될 수 있는 크기로 정의 하는 것입니다. 여기에서 반환 되는 크기는 특정 항목 내용에 대해 상수입니다 (특정 항목에 대 한 상수인 메타 파일의 경우와 매우 유사). 확대/축소를 항목에 적용 하는 경우에는이 크기가 변경 되지 않습니다. 일반적으로 컨테이너는를 호출 하 여 항목을 더 또는 더 작은 공간에 제공 하는 경우 변경 되지 않습니다 `OnSetExtent` . 예를 들어 컨테이너에서 보낸 마지막 익스텐트를 기준으로 텍스트를 래핑하는 "margin" 기능이 없는 간단한 텍스트 편집기의 경우 이러한 변경이 발생할 수 있습니다. 서버가 변경 되는 경우 서버는 시스템 레지스트리에서 OLEMISC_RECOMPOSEONRESIZE 비트를 설정 해야 합니다 .이 옵션에 대 한 자세한 내용은 OLE SDK 설명서를 참조 하십시오.

## <a name="coleserveritemonsetextent"></a>COleServerItem::OnSetExtent

이 함수는 컨테이너가 개체의 "자세히"를 표시 하는 경우 호출 됩니다. 대부분의 컨테이너는이를 전혀 호출 하지 않습니다. 기본 구현은 `COleServerDoc::GetZoomFactor` 위에 설명 된 컨테이너 범위 값을 계산할 때에서 사용 되는 ' m_sizeExtent '의 컨테이너에서 받은 마지막 값을 저장 합니다.

## <a name="coleserverdoconsetitemrects"></a>COleServerDoc:: OnSetItemRects

이 함수는 문서가 내부 활성 상태인 경우에만 호출 됩니다. 컨테이너에서 항목의 위치 또는 항목에 적용 된 클리핑을 업데이트할 때 호출 됩니다. 위에서 설명한 것 처럼 POSITION 사각형은 확대/축소 비율 계산에 대 한 분자를 제공 합니다. 서버는를 호출 하 여 항목 위치를 변경 하도록 요청할 수 있습니다 `COleServerDoc::RequestPositionChange` . 컨테이너는를 호출 하 여를 호출 하 여이 요청에 응답할 수도 있고 그렇지 않을 수도 있습니다 `OnSetItemRects` `COleServerItem::SetItemRects` .

## <a name="coleserverdocondraw"></a>COleServerDoc:: OnDraw

을 재정의 하 여 만든 메타 파일은 `COleServerItem::OnDraw` 현재 확대/축소 비율에 관계 없이 정확히 동일한 메타 파일을 생성 합니다. 컨테이너는 메타 파일의 크기를 적절 하 게 조정 합니다. 이는 뷰와 서버 항목의에 대 한 중요 한 차이점입니다 `OnDraw` `OnDraw` . 뷰는 확대/축소를 처리 하 고, 항목은 확대/축소 *가능* 메타 파일을 만들고 컨테이너에 남겨 두고 적절 한 확대/축소를 수행 합니다.

서버가 제대로 작동 하는지 확인할 수 있는 가장 좋은 방법은 `COleServerDoc::GetZoomFactor` 문서가 활성 상태인 경우의 구현을 사용 하는 것입니다.

## <a name="mfc-support-for-in-place-resizing"></a>In-Place 크기 조정에 대 한 MFC 지원

MFC는 OLE 2 사양에 설명 된 대로 내부 크기 조정 인터페이스를 완전히 구현 합니다. 사용자 인터페이스는 `COleResizeBar` 클래스, 사용자 지정 메시지 WM_SIZECHILD 및에서이 메시지의 특수 처리를 통해 지원 됩니다 `COleIPFrameWnd` .

프레임 워크에서 제공 하는 것과 다른 처리를 구현 하는 것이 좋습니다. 위에서 설명한 것 처럼 프레임 워크는 컨테이너에 대 한 내부 크기 조정 결과를 그대로 둡니다. 서버는 확대/축소 비율의 변경에 응답 합니다. 컨테이너에서를 처리 하는 동안 컨테이너 범위와 위치 사각형을 모두 설정 하 여 응답 `COleClientItem::OnChangeItemPosition` 하는 경우 `COleServerDoc::RequestPositionChange` 에는 내부 크기 조정으로 인해 편집 창에 항목이 "더 낮음"으로 표시 됩니다. 을 처리 하는 동안 POSITION 사각형을 설정 하 여 컨테이너가 반응 하는 경우 `COleClientItem::OnChangeItemPosition` 확대/축소 비율이 변경 되 고 항목이 "확대 또는 축소"로 표시 됩니다.

서버는이 협상 중에 발생 하는 작업을 제어할 수 있습니다. 예를 들어 스프레드시트는 현재 위치에서 항목을 편집 하는 동안 사용자가 창의 크기를 조정할 때 더 많거나 더 작은 셀을 표시 하도록 선택할 수 있습니다. 워드 프로세서는 창과 동일 하 고 텍스트를 새 여백으로 래핑하지 "페이지 여백"을 변경 하도록 선택할 수 있습니다. 서버는 크기 조정이 완료 되 면 자연 범위 (에서 반환 되는 크기)를 변경 하 여이를 구현 `COleServerItem::OnGetExtent` 합니다. 이렇게 하면 POSITION 사각형과 컨테이너 범위가 같은 양만큼 변경 되어 확대/축소 비율이 동일 하 게 표시 되 고 확대/축소 영역이 더 커질 수 있습니다. 또한 문서는에 의해 생성 된 메타 파일에 표시 됩니다 `OnDraw` . 이 경우 문서 자체는 보기 영역 뿐만 아니라 사용자가 항목의 크기를 조정할 때 변경 됩니다.

사용자 지정 크기 조정을 구현 하 고 `COleResizeBar` 클래스의 WM_SIZECHILD 메시지를 재정의 하 여에서 제공 하는 사용자 인터페이스를 계속 활용할 수 있습니다 `COleIPFrameWnd` . WM_SIZECHILD의 세부 정보에 대 한 자세한 내용은 [Technical Note 24](../mfc/tn024-mfc-defined-messages-and-resources.md)를 참조 하십시오.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
