---
description: '자세한 정보: 장치 컨텍스트'
title: 디바이스 컨텍스트
ms.date: 11/04/2016
helpviewer_keywords:
- OnPrepareDC method [MFC]
- windows [MFC], and device context
- drawing [MFC], device context
- CClientDC class [MFC], and GetDC method [MFC]
- drawing [MFC], in mouse and device contexts
- CDC class [MFC], objects
- device contexts [MFC]
- client areas
- CMetaFileDC class [MFC], and OnPrepareDC method [MFC]
- GDI objects [MFC], device contexts
- graphic objects [MFC], device contexts
- frame windows [MFC], device contexts
- metafiles and device contexts
- EndPaint method [MFC]
- printers [MFC], device contexts
- mouse [MFC], drawing and device contexts
- BeginPaint method, CPaintDC
- CPaintDC class [MFC], device context for painting
- windows [MFC], drawing directly into
- client areas, and device context
- device contexts [MFC], CDC class [MFC]
- user interface [MFC], device contexts
- device-independent drawing
- GetDC method and CClientDC class [MFC]
- CClientDC class [MFC], and ReleaseDC method [MFC]
- ReleaseDC method [MFC]
- device contexts [MFC], about device contexts
- drawing [MFC], directly into windows
- painting and device context
ms.assetid: d0cd51f1-f778-4c7e-bf50-d738d10433c7
ms.openlocfilehash: 725387ad3aa3f099c72c82aecd14d89bad7168bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261595"
---
# <a name="device-contexts"></a>디바이스 컨텍스트

장치 컨텍스트는 디스플레이 또는 프린터와 같은 장치의 그리기 특성에 대 한 정보를 포함 하는 Windows 데이터 구조입니다. 모든 그리기 호출은 선, 도형 및 텍스트를 그리기 위한 Windows Api를 캡슐화 하는 장치 컨텍스트 개체를 통해 수행 됩니다. 장치 컨텍스트는 Windows에서 장치 독립적인 드로잉을 허용 합니다. 장치 컨텍스트를 사용 하 여 화면, 프린터 또는 메타 파일에 그릴 수 있습니다.

[CPaintDC](reference/cpaintdc-class.md) 개체는 함수를 호출 하 고, `BeginPaint` 장치 컨텍스트에서 그린 다음 함수를 호출 하 여 Windows의 일반적인 방법을 캡슐화 합니다 `EndPaint` . 생성자는를 `CPaintDC` 호출 하 `BeginPaint` 고 소멸자는를 호출 합니다 `EndPaint` . 간소화 된 프로세스는 [CDC](reference/cdc-class.md) 개체를 만들고 개체를 그린 다음 삭제 하는 것입니다 `CDC` . 프레임 워크에서는이 프로세스의 대부분이 자동화 됩니다. 특히 `OnDraw` 함수에는 `CPaintDC` 이미 준비한 (via)가 전달 되 `OnPrepareDC` 고 간단히 그립니다. 이는 프레임 워크에 의해 소멸 되며 함수 호출에서 반환 될 때 기본 장치 컨텍스트가 Windows로 릴리스됩니다 `OnDraw` .

[Cclientdc](reference/cclientdc-class.md) 개체는 창의 클라이언트 영역만 나타내는 장치 컨텍스트를 사용 하 여 작업을 캡슐화 합니다. `CClientDC`생성자는 `GetDC` 함수를 호출 하 고 소멸자는 함수를 호출 합니다 `ReleaseDC` . [Cwindowdc](reference/cwindowdc-class.md) 개체는 프레임을 포함 하 여 전체 창을 나타내는 장치 컨텍스트를 캡슐화 합니다.

[CMetaFileDC](reference/cmetafiledc-class.md) 개체는 Windows 메타 파일로 그리기를 캡슐화 합니다. 에 전달 된와는 달리 `CPaintDC` `OnDraw` 이 경우에는 직접 [onpreparedc](reference/cview-class.md#onpreparedc) 를 호출 해야 합니다.

## <a name="mouse-drawing"></a>마우스 그리기

대부분의 장치 컨텍스트 작업은 프레임 워크 프로그램에서 대부분의 그리기를 수행 하며 대부분의 장치 컨텍스트 작업은 뷰의 멤버 함수에서 수행 됩니다 `OnDraw` . 그러나 다른 용도로 장치 컨텍스트 개체를 계속 사용할 수 있습니다. 예를 들어 보기에서 마우스를 이동할 때 추적 피드백을 제공 하려면가 호출 될 때까지 기다리지 않고 뷰에 직접 그려야 `OnDraw` 합니다.

이러한 경우 [Cclientdc](reference/cclientdc-class.md) 장치 컨텍스트 개체를 사용 하 여 뷰에 직접 그릴 수 있습니다.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [장치 컨텍스트 (정의)](/windows/win32/gdi/device-contexts)

- [뷰에 그리기](drawing-in-a-view.md)

- [뷰를 통해 사용자 입력 해석](interpreting-user-input-through-a-view.md)

- [선 및 곡선](/windows/win32/gdi/lines-and-curves)

- [채워진 도형](/windows/win32/gdi/filled-shapes)

- [글꼴 및 텍스트](/windows/win32/gdi/fonts-and-text)

- [색](/windows/win32/gdi/colors)

- [좌표 공간 및 변형](/windows/win32/gdi/coordinate-spaces-and-transformations)

## <a name="see-also"></a>참고 항목

[창 개체](window-objects.md)
