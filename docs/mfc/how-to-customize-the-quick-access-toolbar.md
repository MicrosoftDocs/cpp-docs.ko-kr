---
description: '자세히 알아보기: 방법: 빠른 실행 도구 모음 사용자 지정'
title: '방법: 빠른 실행 도구 모음 사용자 지정'
ms.date: 09/07/2019
helpviewer_keywords:
- quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
ms.openlocfilehash: cb7935f9e340734f8af0e7ec9197e139c30af894
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330233"
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>방법: 빠른 실행 도구 모음 사용자 지정

QAT(빠른 실행 도구 모음)는 애플리케이션 단추 옆 또는 범주 탭 아래에 표시된 명령 집합이 포함된 사용자 지정 가능한 도구 모음입니다. 다음 그림에서는 일반적인 빠른 실행 도구 모음을 보여 줍니다.

![MFC 리본 빠른 실행 도구 모음](../mfc/media/quick_access_toolbar.png "MFC 리본 빠른 실행 도구 모음")

빠른 실행 도구 모음을 사용자 지정 하려면 **속성** 창에서 열고 해당 명령을 수정한 다음 리본 컨트롤을 미리 봅니다.

### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>속성 창에서 빠른 실행 도구 모음을 열려면

1. Visual Studio의 **보기** 메뉴에서 **리소스 뷰** 를 클릭 합니다.

1. **리소스 뷰** 에서 리본 리소스를 두 번 클릭 하 여 디자인 화면에 표시 합니다.

1. 디자인 화면에서 빠른 실행 도구 모음 메뉴를 마우스 오른쪽 단추로 클릭 한 다음 **속성** 을 클릭 합니다.

## <a name="quick-access-toolbar-properties"></a>빠른 실행 도구 모음 속성

다음 표에서는 빠른 실행 도구 모음의 속성을 정의합니다.

|속성|정의|
|--------------|----------------|
|QAT 위치|애플리케이션이 시작될 때 빠른 실행 도구 모음의 위치를 지정합니다. 위치는 리본 컨트롤의 **위** 또는 **아래** 일 수 있습니다.|
|QAT 항목|빠른 실행 도구 모음에 사용할 수 있는 명령을 지정합니다.|

#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>빠른 실행 도구 모음에서 명령을 추가 또는 제거하려면

1. **속성** 창에서 **QAT Items** 를 클릭 한 다음 줄임표 단추 **(...)** 를 클릭 합니다.

1. **QAT Items 편집기** 대화 상자에서 **추가** 및 **제거** 단추를 사용 하 여 빠른 실행 도구 모음의 명령 목록을 수정 합니다.

1. 빠른 실행 도구 모음과 빠른 실행 도구 모음 메뉴 모두에 나타나는 명령을 원하는 경우 명령 옆의 상자를 선택하십시오. 메뉴에만 명령을 표시하려면 상자 선택을 취소합니다.

## <a name="previewing-the-ribbon"></a>리본 미리 보기

디자인 화면에 빠른 실행 도구 모음 명령이 나타나지 않습니다. 해당 명령을 보려면 리본을 미리 보거나 애플리케이션을 실행해야 합니다.

#### <a name="to-preview-the-ribbon-control"></a>리본 컨트롤을 미리 보려면

- **리본 편집기 도구 모음** 에서 **테스트 리본** 을 클릭 합니다.

## <a name="see-also"></a>참고 항목

[리본 디자이너 (MFC)](ribbon-designer-mfc.md)
