---
title: BITMAP 구조체
ms.date: 11/04/2016
f1_keywords:
- BITMAP
helpviewer_keywords:
- BITMAP structure [MFC]
ms.assetid: 05d33b4d-7232-4643-a108-87dda8ff5f22
ms.openlocfilehash: a9ffa7191b5f0e815db9c7e8b8a26b0b6b200f2d
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330244"
---
# <a name="bitmap-structure"></a>BITMAP 구조체

합니다 **비트맵** 높이, 너비, 색상 형식 및 논리적 비트맵의 비트 값 구조체를 정의 합니다.

## <a name="syntax"></a>구문

```
typedef struct tagBITMAP {  /* bm */
    int bmType;
    int bmWidth;
    int bmHeight;
    int bmWidthBytes;
    BYTE bmPlanes;
    BYTE bmBitsPixel;
    LPVOID bmBits;
} BITMAP;
```

#### <a name="parameters"></a>매개 변수

*bmType*<br/>
비트맵 형식을 지정합니다. 논리적 비트맵의 경우 이 멤버는 0이어야 합니다.

*bmWidth*<br/>
비트맵의 너비(픽셀)를 지정합니다. 너비는 0보다 커야 합니다.

*bmHeight*<br/>
비트맵의 높이(래스터 줄)를 지정합니다. 높이는 0보다 커야 합니다.

*bmWidthBytes*<br/>
각 래스터 줄에서 바이트 수를 지정합니다. GDI(그래픽 장치 인터페이스)에서는 비트맵의 비트 값이 정수(2바이트) 값의 배열을 형성한다고 가정하기 때문에 이 값은 짝수여야 합니다. 즉, *bmWidthBytes* \* 8 때 가져온 값 보다 크거나 16의 다음 배수 여야 합니다 *bmWidth* 멤버는 *bmBitsPixel*  멤버입니다.

*bmPlanes*<br/>
비트맵에서 색 평면의 수를 지정합니다.

*bmBitsPixel*<br/>
픽셀을 정의하는 데 필요한 각 평면의 인접 색상 비트 수를 지정합니다.

*bmBits*<br/>
비트맵에 대한 비트 값의 위치를 가리킵니다. 합니다 *bmBits* 멤버 1 바이트 값의 배열에 대 한 긴 포인터 여야 합니다.

## <a name="remarks"></a>설명

현재 사용되는 비트맵 형식은 흑백 및 컬러입니다. 흑백 비트맵에는 1비트, 1평면 형식이 사용됩니다. 각 스캔은 16비트의 배수입니다.

검색 높이의 흑백 비트맵에 대해 다음과 같이 구성 됩니다 *n*:

```
Scan 0
Scan 1
.
.
.
Scan n-2
Scan n-1
```

흑백 장치에서 픽셀은 검정색 또는 흰색입니다. 비트맵에서 해당 비트가 1이면 픽셀이 켜집니다(흰색). 비트맵에서 해당 비트가 0이면 픽셀이 꺼집니다(검정색).

모든 장치 집합 RC_BITBLT 비트의 RASTERCAPS 인덱스에 있는 비트맵을 지원 합니다 [CDC::GetDeviceCaps](../../mfc/reference/cdc-class.md#getdevicecaps) 멤버 함수입니다.

각 장치는 고유한 색상 형식을 가집니다. 다른 장치로 비트맵을 전송 하기 위해 사용 합니다 [GetDIBits](/windows/desktop/api/wingdi/nf-wingdi-getdibits) 하 고 [SetDIBits](/windows/desktop/api/wingdi/nf-wingdi-setdibits) Windows 함수입니다.

## <a name="requirements"></a>요구 사항

**헤더:** wingdi.h

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Cbitmap:: Createbitmapindirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)
