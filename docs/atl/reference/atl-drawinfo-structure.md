---
description: '다음에 대 한 자세한 정보: ATL_DRAWINFO 구조체'
title: ATL_DRAWINFO 구조체
ms.date: 11/04/2016
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
ms.openlocfilehash: 726a5b86f5621eba51d84054c80553b5c2f1f928
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165396"
---
# <a name="atl_drawinfo-structure"></a>ATL_DRAWINFO 구조체

프린터, 메타 파일 또는 ActiveX 컨트롤과 같은 다양 한 대상으로 렌더링 하는 데 사용 되는 정보를 포함 합니다.

## <a name="syntax"></a>구문

```cpp
struct ATL_DRAWINFO {
    UINT cbSize;
    DWORD dwDrawAspect;
    LONG lindex;
    DVTARGETDEVICE* ptd;
    HDC hicTargetDev;
    HDC hdcDraw;
    LPCRECTL prcBounds;
    LPCRECTL prcWBounds;
    BOOL bOptimize;
    BOOL bZoomed;
    BOOL bRectInHimetric;
    SIZEL ZoomNum;
    SIZEL ZoomDen;
};
```

## <a name="members"></a>멤버

`cbSize`<br/>
구조체의 크기 (바이트)입니다.

`dwDrawAspect`<br/>
대상이 표시 되는 방법을 지정 합니다. 표현에는 콘텐츠, 아이콘, 축소판 그림 또는 인쇄 된 문서가 포함 될 수 있습니다. 가능한 값 목록은 [Dvaspect](/windows/win32/api/wtypes/ne-wtypes-dvaspect) 및 [DVASPECT2](/windows/win32/api/ocidl/ne-ocidl-dvaspect2)를 참조 하세요.

`lindex`<br/>
그리기 작업에 관심이 있는 대상의 부분입니다. 멤버의 값에 따라 해석이 달라 집니다 `dwDrawAspect` .

`ptd`<br/>
지정 된 측면에 따라 그리기 최적화를 사용 하도록 설정 하는 [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) 구조체에 대 한 포인터입니다. 최적화 된 그리기 인터페이스를 지 원하는 최신 개체 및 컨테이너도이 멤버를 지원 합니다. 최적화 된 그리기 인터페이스를 지원 하지 않는 오래 된 개체와 컨테이너는이 멤버에 대해 항상 NULL을 지정 합니다.

`hicTargetDev`<br/>
`ptd`개체가 장치 메트릭을 추출 하 고 장치 기능을 테스트할 수 있는가 가리키는 대상 장치에 대 한 정보 컨텍스트입니다. `ptd`가 NULL 인 경우 개체는 멤버의 값을 무시 해야 합니다 `hicTargetDev` .

`hdcDraw`<br/>
를 그릴 장치 컨텍스트입니다. 창 없는 개체의 경우 `hdcDraw` 멤버는 `MM_TEXT` 포함 하는 창의 클라이언트 좌표와 일치 하는 논리적 좌표를 사용 하 여 매핑 모드에 있습니다. 또한 장치 컨텍스트는 일반적으로 메시지에서 전달 하는 것과 동일한 상태 여야 합니다 `WM_PAINT` .

`prcBounds`<br/>
개체를 그릴 `hdcDraw`및 사각형을 지정하는 [RECTL](/windows/win32/api/windef/ns-windef-rectl) 구조체에 대한 포인터입니다. 이 멤버는 개체의 위치 지정 및 늘이기를 제어 합니다. 창 없는 내부 활성 개체를 그리려면이 멤버가 NULL 이어야 합니다. 다른 모든 상황에서 NULL은 올바른 값이 아니므로 `E_INVALIDARG` 오류 코드가 생성 됩니다. 컨테이너가 NULL이 아닌 값을 창 없는 개체에 전달 하는 경우 개체는 요청한 측면을 지정 된 장치 컨텍스트와 사각형에 렌더링 해야 합니다. 컨테이너는 창 없는 개체에서이를 요청 하 여 개체의 두 번째 비활성 뷰를 렌더링 하거나 개체를 인쇄할 수 있습니다.

`prcWBounds`<br/>
이 `hdcDraw` 메타 파일 장치 컨텍스트 (Windows SDK의 [GetDeviceCaps](/windows/win32/api/wingdi/nf-wingdi-getdevicecaps) 참조) 이면 `RECTL` 기본 메타 파일의 경계 사각형을 지정 하는 구조체에 대 한 포인터입니다. 사각형 구조에는 창 범위와 창 원점이 포함 됩니다. 이러한 값은 메타 파일을 그리는 데 유용 합니다. 에 의해 표시 된 사각형은 `prcBounds` 이 사각형 안에 중첩 되며 `prcWBounds` 동일한 좌표 공간에 있습니다.

`bOptimize`<br/>
컨트롤의 그리기를 최적화 하는 경우 0이 아니고, 그렇지 않으면 0입니다. 그리기가 최적화 된 경우 렌더링을 마치면 장치 컨텍스트의 상태가 자동으로 복원 됩니다.

`bZoomed`<br/>
대상에 확대/축소 비율이 있으면 0이 아니고, 그렇지 않으면 0입니다. 확대/축소 비율은에 저장 됩니다 `ZoomNum` .

`bRectInHimetric`<br/>
의 차원이 HIMETRIC에 있으면 0이 아닌 값이 고 `prcBounds` , 그렇지 않으면 0입니다.

`ZoomNum`<br/>
개체가 렌더링 되는 사각형의 너비와 높이입니다. 대상의 x 축 (개체의 기본 크기에 대 한 비율)을 따른 확대/축소 비율은의 값 `ZoomNum.cx` 으로 나눈 값입니다 `ZoomDen.cx` . Y 축을 따라 확대/축소 비율은 비슷한 방식으로 달성 됩니다.

`ZoomDen`<br/>
대상의 실제 너비와 높이입니다.

## <a name="remarks"></a>설명

이 구조의 일반적인 사용법은 대상 개체를 렌더링 하는 동안 정보를 검색 하는 것입니다. 예를 들어 [CComControlBase:: OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced)의 오버 로드 내에서 ATL_DRAWINFO의 값을 검색할 수 있습니다.

이 구조는 대상 장치에 대 한 개체의 모양을 렌더링 하는 데 사용 되는 관련 정보를 저장 합니다. 제공 된 정보는 화면, 프린터 또는 메타 파일에 그리는 데 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="see-also"></a>참고 항목

[클래스 및 구조체](../../atl/reference/atl-classes.md)<br/>
[IViewObject::Draw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase:: OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
