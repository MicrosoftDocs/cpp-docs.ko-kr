---
description: '자세히 알아보기: MFC 및 ATL에서 공유 하는 클래스'
title: MFC와 ATL에서 공유되는 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: df196f92b7b16742545a7d82320ef4fe8da77fe2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166787"
---
# <a name="classes-shared-by-mfc-and-atl"></a>MFC와 ATL에서 공유되는 클래스

다음 표에서는 MFC와 ATL 간에 공유 되는 클래스를 보여 줍니다.

|클래스|설명|헤더 파일|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|파일과 연결 된 날짜 및 시간 값을 관리 하기 위한 메서드를 제공 합니다.|atltime.h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|파일과 연결 된 상대 날짜 및 시간 값을 관리 하기 위한 메서드를 제공 합니다.|atltime.h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|고정 문자 버퍼를 사용 하는 문자열 개체를 나타냅니다.|cstringt.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|JPEG, GIF, BMP 및 PNG (이동식 네트워크 그래픽) 형식으로 이미지를 로드 하 고 저장 하는 기능을 포함 하 여 향상 된 비트맵 지원 기능을 제공 합니다.|atlimage.h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|OLE 자동화에 사용 되는 날짜 데이터 형식을 캡슐화 합니다.|atlcomtime.h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|시간 범위에 상대적인 시간을 나타냅니다.|atlcomtime.h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|`CPoint` 및 `POINT` 구조체를 조작하는 멤버함수도 포함하는 Windows [POINT](/windows/win32/api/windef/ns-windef-point) 구조체와 유사한 클래스입니다.|atltypes.h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|개체와 Windows 구조를 조작 하는 멤버 함수도 포함 하는 Windows [RECT](/windows/win32/api/windef/ns-windef-rect) 구조와 비슷한 클래스입니다 `CRect` `RECT` .|atltypes.h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|`CSimpleStringT` 개체를 나타냅니다.|atlsimpstr.h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|상대 좌표 또는 위치를 구현 하는 Windows [SIZE](/windows/win32/api/windef/ns-windef-size) 구조체와 유사한 클래스입니다.|atltypes.h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|기존 개체에 대 한 및 호출에 대 한 자동 리소스 정리 기능을 제공 `GetBuffer` `ReleaseBuffer` `CStringT` 합니다.|atlsimpstr.h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|문자열 개체의 데이터를 나타냅니다.|atlsimpstr.h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|`CStringT` 개체를 나타냅니다.|cstringt (MFC 종속). m n. h (MFC 독립적)|
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|절대 시간과 날짜를 나타냅니다.|atltime.h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|시간 범위의 초 수로 내부적으로 저장 되는 시간 간격입니다.|atltime.h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|메모리 관리자에 대 한 인터페이스를 나타냅니다 `CStringT` .|atlsimpstr.h|

## <a name="see-also"></a>참고 항목

[ATL/MFC 공유 클래스](../../atl-mfc-shared/atl-mfc-shared-classes.md)
