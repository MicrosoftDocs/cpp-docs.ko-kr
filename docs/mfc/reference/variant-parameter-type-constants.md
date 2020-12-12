---
description: '자세한 정보: Variant 매개 변수 형식 상수'
title: 가변 매개 변수 형식 상수
ms.date: 11/04/2016
f1_keywords:
- VTS_YPOS_HIMETRIC
- VTS_PICTURE
- VTS_FONT
- VTS_XPOS_HIMETRIC
- VTS_XPOS_PIXELS
- VTS_XSIZE_HIMETRIC
- VTS_YPOS_PIXELS
- VTS_TRISTATE
- VTS_HANDLE
- VTS_YSIZE_HIMETRIC
- VTS_COLOR
- VTS_OPTEXCLUSIVE
- VTS_YSIZE_PIXELS
- VTS_XSIZE_PIXELS
helpviewer_keywords:
- VTS_XPOS_HIMETRIC constant [MFC]
- VTS_FONT constant [MFC]
- VTS_XPOS_PIXELS constant [MFC]
- VTS_COLOR constant [MFC]
- Variants [MFC]
- VTS_YPOS_PIXELS constant [MFC]
- VTS_YSIZE_HIMETRIC constant [MFC]
- VTS_YPOS_HIMETRIC constant [MFC]
- Variants, parameter type constants
- Variant data constants [MFC]
- VTS_PICTURE constant [MFC]
- VTS_TRISTATE constant [MFC]
- VTS_XSIZE_HIMETRIC constant [MFC]
- VTS_HANDLE constant [MFC]
- VTS_XSIZE_PIXELS constant [MFC]
- VTS_OPTEXCLUSIVE constant [MFC]
- VTS_YSIZE_PIXELS constant [MFC]
ms.assetid: de99c7a9-7aae-4dc4-b723-40c6380543ab
ms.openlocfilehash: 5bc3dcc8a0a888b21b88700db99b05c0f12a4c5e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218500"
---
# <a name="variant-parameter-type-constants"></a>가변 매개 변수 형식 상수

이 항목에서는 MFC 라이브러리의 OLE 컨트롤 클래스와 함께 사용 하도록 디자인 된 변형 매개 변수 형식을 나타내는 새 상수를 나열 합니다.

다음은 클래스 상수 목록입니다.

## <a name="variant-data-constants"></a><a name="_mfc_variant_data_constants"></a> Variant 데이터 상수

- RGB 색 값을 나타내는 데 사용 되는 32 비트 정수를 VTS_COLOR 합니다.

- OLE 글꼴 개체의 인터페이스에 대 한 포인터를 VTS_FONT `IFontDisp` 합니다.

- Windows 핸들 값을 VTS_HANDLE 합니다.

- OLE 그림 개체의 인터페이스에 대 한 포인터를 VTS_PICTURE `IPictureDisp` 합니다.

- 라디오 단추와 같은 컨트롤 그룹에서 사용 하기 위해 사용 되는 컨트롤에 사용 되는 16 비트 값을 VTS_OPTEXCLUSIVE 합니다. 이 형식은 그룹의 한 컨트롤에 TRUE 값이 있는 경우 다른 모든 항목은 FALSE가 되도록 컨테이너에 지시 합니다.

- 사용 가능한 세 가지 값 중 하나 (선택, 선택 취소, 사용할 수 없음) 중 하나를 가질 수 있는 속성에 사용 되는 16 비트 부호 있는 정수를 VTS_TRISTATE 합니다 (예: 확인란).

- HIMETRIC unit에서 x 축을 따라 위치를 나타내는 데 사용 되는 32 비트 부호 없는 정수를 VTS_XPOS_HIMETRIC 합니다.

- HIMETRIC unit에서 y 축을 따라 위치를 나타내는 데 사용 되는 32 비트 부호 없는 정수를 VTS_YPOS_HIMETRIC 합니다.

- X 축의 위치를 픽셀 단위로 나타내는 데 사용 되는 32 비트 부호 없는 정수를 VTS_XPOS_PIXELS 합니다.

- Y 축의 위치를 픽셀 단위로 나타내는 데 사용 되는 32 비트 부호 없는 정수를 VTS_YPOS_PIXELS 합니다.

- 화면 개체의 너비를 픽셀 단위로 나타내는 데 사용 되는 32 비트 부호 없는 정수를 VTS_XSIZE_PIXELS 합니다.

- 화면 개체의 높이를 픽셀 단위로 나타내는 데 사용 되는 32 비트 부호 없는 정수를 VTS_YSIZE_PIXELS 합니다.

- HIMETRIC unit에서 화면 개체의 너비를 나타내는 데 사용 되는 32 비트 부호 없는 정수를 VTS_XSIZE_HIMETRIC 합니다.

- HIMETRIC unit에서 화면 개체의 높이를 나타내는 데 사용 되는 32 비트 부호 없는 정수를 VTS_YSIZE_HIMETRIC 합니다.

    > [!NOTE]
    >  Variant 데이터 상수에 대 한 포인터를 제공 하는 VTS_FONT 및 VTS_PICTURE를 제외 하 고 모든 variant 형식에 대해 추가 변형 상수가 정의 되었습니다. 이러한 상수는 VTS_P 규칙을 사용 하 여 명명 됩니다 `constantname` . 예를 들어 VTS_PCOLOR은 VTS_COLOR 상수에 대 한 포인터입니다.

## <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
