---
description: '자세한 정보: 그래픽 개체'
title: 그래픽 개체
ms.date: 11/04/2016
f1_keywords:
- HRGN
- HFONT
- HBITMAP
helpviewer_keywords:
- CRgn class [MFC], HRGN handle type
- HPEN [MFC]
- objects [MFC], graphic
- palettes [MFC], creating in device context
- pens [MFC], creating in device context
- bitmaps [MFC], creating in device contexts
- palette objects [MFC]
- memory [MFC], display contexts
- MFC, graphic objects
- regions [MFC], creating in device context
- CPen class [MFC], HPEN handle type
- GDI objects [MFC]
- HRGN [MFC]
- graphic objects [MFC]
- GDI objects [MFC], graphic-object classes
- CFont class [MFC], HFONT handle type
- HFONT and class CFont [MFC]
- HBITMAP and class CBitmap [MFC]
- fonts [MFC], creating in device context
- images [MFC], graphic objects [MFC]
- CBitmap class [MFC], HBITMAP handle type
- HPALETTE and class CPalette [MFC]
- CBrush class [MFC], HBRUSH handle type
- objects [MFC], graphic objects
- drawing [MFC], in device contexts
- device contexts [MFC], graphic objects [MFC]
- brushes [MFC], creating in device context
- region objects [MFC]
- pen objects [MFC]
- GDI [MFC], graphic-object classes
- graphic objects [MFC], creating in device context
- HBRUSH and class CBrush [MFC]
- painting and device context [MFC]
- CPalette class [MFC], HPALETTE handle type
ms.assetid: 41963b25-34b7-4343-8446-34ba516b83ca
ms.openlocfilehash: 7fbb4b6a4eb7586773eff309daddf60d98c7ec3b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189251"
---
# <a name="graphic-objects"></a>그래픽 개체

Windows는 디바이스 컨텍스트에서 사용할 수 있는 다양한 그리기 도구를 제공합니다. 선을 그리는 펜, 내부를 채우는 브러시 및 텍스트를 그리는 글꼴을 제공합니다. MFC는 Windows의 그리기 도구에 해당하는 그래픽 개체 클래스를 제공합니다. 아래 표에서는 사용 가능한 클래스와 그에 해당하는 Windows GDI(그래픽 디바이스 인터페이스) 핸들 형식을 보여 줍니다.

> [!NOTE]
> 자세한 내용은 [Gdi + SDK 설명서](/windows/win32/gdiplus/-gdiplus-gdi-start)를 참조 하세요.

이 문서에서는 이러한 그래픽 개체 클래스의 사용에 대해 설명합니다.

### <a name="classes-for-windows-gdi-objects"></a>Windows GDI 개체에 대한 클래스

|클래스|Windows 핸들 형식|
|-----------|-------------------------|
|[CPen](reference/cpen-class.md)|`HPEN`|
|[CBrush](reference/cbrush-class.md)|`HBRUSH`|
|[CFont](reference/cfont-class.md)|**HFONT**|
|[CBitmap](reference/cbitmap-class.md)|`HBITMAP`|
|[CPalette](reference/cpalette-class.md)|`HPALETTE`|
|[CRgn](reference/crgn-class.md)|**HRGN**|

> [!NOTE]
> [CImage](../atl-mfc-shared/reference/cimage-class.md) 클래스는 향상 된 비트맵 지원을 제공 합니다.

클래스 라이브러리의 각 그래픽 개체 클래스에는 해당 클래스의 그래픽 개체를 만들 수 있는 생성자가 있으며, `CreatePen`과 같은 적절한 만들기 함수를 사용하여 초기화해야 합니다.

클래스 라이브러리의 각 그래픽 개체 클래스에는 MFC 개체를 연결된 Windows 핸들에 캐스트하는 캐스트 연산자가 있습니다. 결과 핸들은 연결된 개체가 분리될 때까지 유효합니다. 개체의 `Detach` 멤버 함수를 사용 하 여 핸들을 분리 합니다.

다음 코드에서는 `CPen` 개체를 Windows 핸들에 캐스트합니다.

[!code-cpp[NVC_MFCDocViewSDI#5](codesnippet/cpp/graphic-objects_1.cpp)]

#### <a name="to-create-a-graphic-object-in-a-device-context"></a>디바이스 컨텍스트에서 그래픽 개체를 만들려면

1. 스택 프레임에 그래픽 개체를 정의합니다. `CreatePen`과 같은 형식별 만들기 함수를 사용하여 개체를 초기화합니다. 또는 생성자에서 개체를 초기화합니다. 예제 코드를 제공 하는 [1 단계 및 2 단계 만들기](one-stage-and-two-stage-construction-of-objects.md)에 대 한 설명을 참조 하세요.

1. [현재 장치 컨텍스트에서 개체를 선택](selecting-a-graphic-object-into-a-device-context.md)하 여 이전에 선택한 이전 그래픽 개체를 저장 합니다.

1. 현재 그래픽 개체 작업이 완료되면 이전 그래픽 개체를 선택하여 디바이스 컨텍스트로 다시 넣고 해당 상태를 복원합니다.

1. 범위가 종료되면 프레임 할당 그래픽 개체가 자동으로 삭제되도록 합니다.

> [!NOTE]
> 그래픽 개체를 반복해서 사용하려는 경우 한 번 할당한 다음 필요할 때마다 선택하여 디바이스 컨텍스트로 넣을 수 있습니다. 더 이상 필요 없는 경우에는 이러한 개체를 삭제해야 합니다.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [1단계 및 2단계 그래픽 개체 생성](one-stage-and-two-stage-construction-of-objects.md)

- [1단계 및 2단계의 펜 생성 예제](one-stage-and-two-stage-construction-of-objects.md)

- [장치 컨텍스트에 그래픽 개체 선택](selecting-a-graphic-object-into-a-device-context.md)

- [디바이스 컨텍스트](device-contexts.md)

## <a name="see-also"></a>참고 항목

[창 개체](window-objects.md)
