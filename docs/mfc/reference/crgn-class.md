---
title: CRgn 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRgn
- AFXWIN/CRgn
- AFXWIN/CRgn::CRgn
- AFXWIN/CRgn::CombineRgn
- AFXWIN/CRgn::CopyRgn
- AFXWIN/CRgn::CreateEllipticRgn
- AFXWIN/CRgn::CreateEllipticRgnIndirect
- AFXWIN/CRgn::CreateFromData
- AFXWIN/CRgn::CreateFromPath
- AFXWIN/CRgn::CreatePolygonRgn
- AFXWIN/CRgn::CreatePolyPolygonRgn
- AFXWIN/CRgn::CreateRectRgn
- AFXWIN/CRgn::CreateRectRgnIndirect
- AFXWIN/CRgn::CreateRoundRectRgn
- AFXWIN/CRgn::EqualRgn
- AFXWIN/CRgn::FromHandle
- AFXWIN/CRgn::GetRegionData
- AFXWIN/CRgn::GetRgnBox
- AFXWIN/CRgn::OffsetRgn
- AFXWIN/CRgn::PtInRegion
- AFXWIN/CRgn::RectInRegion
- AFXWIN/CRgn::SetRectRgn
dev_langs:
- C++
helpviewer_keywords:
- CRgn [MFC], CRgn
- CRgn [MFC], CombineRgn
- CRgn [MFC], CopyRgn
- CRgn [MFC], CreateEllipticRgn
- CRgn [MFC], CreateEllipticRgnIndirect
- CRgn [MFC], CreateFromData
- CRgn [MFC], CreateFromPath
- CRgn [MFC], CreatePolygonRgn
- CRgn [MFC], CreatePolyPolygonRgn
- CRgn [MFC], CreateRectRgn
- CRgn [MFC], CreateRectRgnIndirect
- CRgn [MFC], CreateRoundRectRgn
- CRgn [MFC], EqualRgn
- CRgn [MFC], FromHandle
- CRgn [MFC], GetRegionData
- CRgn [MFC], GetRgnBox
- CRgn [MFC], OffsetRgn
- CRgn [MFC], PtInRegion
- CRgn [MFC], RectInRegion
- CRgn [MFC], SetRectRgn
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b569efb201f95ade8987aaa89bb6cea1bc0c15c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376771"
---
# <a name="crgn-class"></a>CRgn 클래스
Windows GDI(그래픽 장치 인터페이스) 영역을 캡슐화합니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CRgn : public CGdiObject  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CRgn::CRgn](#crgn)|`CRgn` 개체를 생성합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CRgn::CombineRgn](#combinergn)|집합은 `CRgn` 개체의 지정 된 두 합집합 동일 있도록 `CRgn` 개체입니다.|  
|[CRgn::CopyRgn](#copyrgn)|설정 된 `CRgn` 개체는 지정 된 복사본 수 있도록 `CRgn` 개체입니다.|  
|[CRgn::CreateEllipticRgn](#createellipticrgn)|초기화 한 `CRgn` 타원형 영역이 있는 개체입니다.|  
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|초기화 한 `CRgn` 정의한 타원형 영역이 있는 개체는 [RECT](../../mfc/reference/rect-structure1.md) 구조입니다.|  
|[CRgn::CreateFromData](#createfromdata)|지정된 된 지역 및 변환 데이터를 영역을 만듭니다.|  
|[CRgn::CreateFromPath](#createfrompath)|지정 된 장치 컨텍스트로 선택 된 경로에서 영역을 만듭니다.|  
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|초기화 한 `CRgn` 다각형 영역이 있는 개체입니다. 시스템의 다각형 자동으로 닫힙니다, 필요한 경우 첫 번째와 마지막 꼭지점에서 선을 그려.|  
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|초기화 한 `CRgn` 개체는 일련의 닫힌된 다각형으로 구성 된 지역에 있습니다. 다각형이 이거나 겹칠 수 있습니다.|  
|[CRgn::CreateRectRgn](#createrectrgn)|초기화 한 `CRgn` 사각형 영역 개체입니다.|  
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|초기화 한 `CRgn` 개체에 정의 된 사각형 영역이 [RECT](../../mfc/reference/rect-structure1.md) 구조입니다.|  
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|초기화 한 `CRgn` 모퉁이가 둥근 사각형 영역이 있는 개체입니다.|  
|[CRgn::EqualRgn](#equalrgn)|에서는 두 `CRgn` 동일한 지 여부를 결정 하는 개체입니다.|  
|[CRgn::FromHandle](#fromhandle)|에 대 한 포인터를 반환 합니다.는 `CRgn` Windows 영역에 대 한 핸들을 지정 되 면 개체입니다.|  
|[CRgn::GetRegionData](#getregiondata)|지정된 된 영역을 설명 하는 데이터는 지정 된 버퍼를 채웁니다.|  
|[CRgn::GetRgnBox](#getrgnbox)|경계 사각형의 좌표를 검색 한 `CRgn` 개체입니다.|  
|[CRgn::OffsetRgn](#offsetrgn)|이동 된 `CRgn` 개체에서 지정 된 오프셋 합니다.|  
|[CRgn::PtInRegion](#ptinregion)|지정된 된 지점 값이 영역에 있는지 여부를 결정 합니다.|  
|[CRgn::RectInRegion](#rectinregion)|영역의 경계 내에서 지정된 된 사각형의 일부 인지 확인 합니다.|  
|[CRgn::SetRectRgn](#setrectrgn)|설정의 `CRgn` 개체 지정된 된 사각형 영역입니다.|  
  
### <a name="public-operators"></a>Public 연산자  
  
|이름|설명|  
|----------|-----------------|  
|[HRGN CRgn::operator](#operator_hrgn)|에 포함 된 Windows 핸들을 반환 된 `CRgn` 개체입니다.|  
  
## <a name="remarks"></a>설명  
 영역은 원형 또는 다각형 영역 창 내에서. 클래스의 멤버 함수를 사용 하면 영역을 사용 하려면 `CRgn` 클래스의 멤버로 정의 된 클리핑 함수로 `CDC`합니다.  
  
 멤버 함수 `CRgn` 을 생성, 변경 및 영역 개체를 호출 하는 방법에 대 한 정보를 검색 합니다.  
  
 사용 하 여 대 한 자세한 내용은 `CRgn`, 참조 [그래픽 개체](../../mfc/graphic-objects.md)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CRgn`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxwin.h  
  
##  <a name="combinergn"></a>  CRgn::CombineRgn  
 두 개의 기존 영역을 결합 하 여 새 GDI 영역을 만듭니다.  
  
```  
int CombineRgn(
    CRgn* pRgn1,  
    CRgn* pRgn2,  
    int nCombineMode);
```  
  
### <a name="parameters"></a>매개 변수  
 `pRgn1`  
 기존 영역을 식별합니다.  
  
 `pRgn2`  
 기존 영역을 식별합니다.  
  
 `nCombineMode`  
 두 소스 영역을 결합 하는 경우 수행할 작업을 지정 합니다. 다음 값 중 하나일 수 있습니다.  
  
- **RGN_AND** 두 영역 (겹치는 부분)에 대해 겹치는 영역을 사용 합니다.  
  
- **RGN_COPY** 지역 1의 복사본을 만듭니다 (으로 식별 `pRgn1`).  
  
- **RGN_DIFF** 1 영역의 영역으로 구성 된 영역을 만듭니다 (으로 식별 `pRgn1`) 2 영역에 속하지 않는 (으로 식별 `pRgn2`).  
  
- **RGN_OR** (union) 전체에 있는 두 영역을 결합 합니다.  
  
- **RGN_XOR** 두 영역 결합 되지만 겹치는 영역을 제거 합니다.  
  
### <a name="return-value"></a>반환 값  
 결과 영역의 형식을 지정합니다. 다음 값 중 하나일 수 있습니다.  
  
- **COMPLEXREGION** 새 영역에 테두리를 겹치는 합니다.  
  
- **오류** 만든 새 지역 없습니다.  
  
- **NULLREGION** 새 영역 비어 있습니다.  
  
- **SIMPLEREGION** 새 영역에 겹치는 테두리가 없습니다.  
  
### <a name="remarks"></a>설명  
 영역을 결합 하 여 지정 된 대로 `nCombineMode`합니다.  
  
 영역을 결합 하 고 결과 영역 핸들에 저장 된 지정한 두는 `CRgn` 개체입니다. 모든 지역에 저장 되는 따라서는 `CRgn` 개체 결합 된 지역으로 대체 됩니다.  
  
 영역의 크기는 32, 767 32, 767 하 여 논리 단위 또는 64k의 메모리 제한, 중 더 작은 값입니다.  
  
 사용 하 여 [CopyRgn](#copyrgn) 한 지역의 다른 영역에 복사 하 합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]  
  
##  <a name="copyrgn"></a>  CRgn::CopyRgn  
 에 정의 된 영역 복사 `pRgnSrc` 에 `CRgn` 개체입니다.  
  
```  
int CopyRgn(CRgn* pRgnSrc);
```  
  
### <a name="parameters"></a>매개 변수  
 `pRgnSrc`  
 기존 영역을 식별합니다.  
  
### <a name="return-value"></a>반환 값  
 결과 영역의 형식을 지정합니다. 다음 값 중 하나일 수 있습니다.  
  
- **COMPLEXREGION** 새 영역에 테두리를 겹치는 합니다.  
  
- **오류** 만든 새 지역 없습니다.  
  
- **NULLREGION** 새 영역 비어 있습니다.  
  
- **SIMPLEREGION** 새 영역에 겹치는 테두리가 없습니다.  
  
### <a name="remarks"></a>설명  
 이전에 저장 된 영역을 대체 하는 새 영역은 `CRgn` 개체입니다. 이 함수는 특별 한 경우는 [CombineRgn](#combinergn) 멤버 함수입니다.  
  
### <a name="example"></a>예제  
  예를 참조 [CRgn::CreateEllipticRgn](#createellipticrgn)합니다.  
  
##  <a name="createellipticrgn"></a>  CRgn::CreateEllipticRgn  
 타원형 영역을 만듭니다.  
  
```  
BOOL CreateEllipticRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);
```  
  
### <a name="parameters"></a>매개 변수  
 `x1`  
 타원의 경계 사각형의 왼쪽 위 모퉁이의 논리적 x 좌표를 지정합니다.  
  
 `y1`  
 타원의 경계 사각형의 왼쪽 위 모퉁이의 논리적 y 좌표를 지정합니다.  
  
 `x2`  
 타원의 경계 사각형의 오른쪽 아래 모퉁이의 논리적 x 좌표를 지정합니다.  
  
 `y2`  
 타원의 경계 사각형의 오른쪽 아래 모퉁이의 논리적 y 좌표를 지정합니다.  
  
### <a name="return-value"></a>반환 값  
 작업이 성공 하면 0이 아니고 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 지역으로 지정 된 경계 사각형에 의해 정의 된 `x1`, `y1`, `x2`, 및 `y2`합니다. 지역에 저장 되는 `CRgn` 개체입니다.  
  
 영역의 크기는 32, 767 32, 767 하 여 논리 단위 또는 64k의 메모리 제한, 중 더 작은 값입니다.  
  
 마친 다음 사용 하 여 만든 영역을 사용 하는 `CreateEllipticRgn` 함수, 응용 프로그램을 사용 하 여 장치 컨텍스트의 아웃 지역 선택 해야는 `DeleteObject` 함수를 제거 합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]  
  
##  <a name="createellipticrgnindirect"></a>  CRgn::CreateEllipticRgnIndirect  
 타원형 영역을 만듭니다.  
  
```  
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpRect`  
 가리키는 `RECT` 구조 또는 `CRect` 타원의 경계 사각형의 왼쪽 및 오른쪽 아래 모퉁이의 논리적 좌표가 포함 된 개체입니다.  
  
### <a name="return-value"></a>반환 값  
 작업이 성공 하면 0이 아니고 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 지역 구조 또는가 가리키는 개체가 정의 `lpRect` 에 저장 됩니다는 `CRgn` 개체입니다.  
  
 영역의 크기는 32, 767 32, 767 하 여 논리 단위 또는 64k의 메모리 제한, 중 더 작은 값입니다.  
  
 마친 다음 사용 하 여 만든 영역을 사용 하는 `CreateEllipticRgnIndirect` 함수, 응용 프로그램을 사용 하 여 장치 컨텍스트의 아웃 지역 선택 해야는 `DeleteObject` 함수를 제거 합니다.  
  
### <a name="example"></a>예제  
  예를 참조 [CRgn::CreateRectRgnIndirect](#createrectrgnindirect)합니다.  
  
##  <a name="createfromdata"></a>  CRgn::CreateFromData  
 지정된 된 지역 및 변환 데이터를 영역을 만듭니다.  
  
```  
BOOL CreateFromData(
    const XFORM* lpXForm,  
    int nCount,  
    const RGNDATA* pRgnData);
```  
  
### <a name="parameters"></a>매개 변수  
 *lpXForm*  
 가리키는 [XFORM](../../mfc/reference/xform-structure.md) 영역에서 수행할 변환을 정의 하는 데이터 구조입니다. 이 포인터 이면 **NULL**, identity 변환을 사용 합니다.  
  
 `nCount`  
 가 가리키는 바이트 수가 지정 `pRgnData`합니다.  
  
 `pRgnData`  
 가리키는 [RGNDATA](../../mfc/reference/rgndata-structure.md) 지역 데이터를 포함 하는 데이터 구조입니다.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공하면 0이 아니고 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 응용 프로그램 호출 하 여 영역에 대 한 데이터를 검색할 수는 `CRgn::GetRegionData` 함수입니다.  
  
##  <a name="createfrompath"></a>  CRgn::CreateFromPath  
 지정 된 장치 컨텍스트로 선택 된 경로에서 영역을 만듭니다.  
  
```  
BOOL CreateFromPath(CDC* pDC);
```  
  
### <a name="parameters"></a>매개 변수  
 `pDC`  
 닫힌된 경로가 포함 된 장치 컨텍스트를 식별 합니다.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공하면 0이 아니고 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 지정 된 디바이스 컨텍스트는 `pDC` 매개 변수는 닫힌된 경로가 포함 되어야 합니다. 후 `CreateFromPath` Windows 영역 경로 장치 컨텍스트에서 닫힌된 경로 삭제 합니다.  
  
##  <a name="createpolygonrgn"></a>  CRgn::CreatePolygonRgn  
 다각형 영역을 만듭니다.  
  
```  
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,  
    int nCount,  
    int nMode);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpPoints`  
 배열을 가리키는 **지점** 구조 또는 배열을 `CPoint` 개체입니다. X-좌표와 y 좌표는 다각형의 한 꼭 짓 점에 각 구조를 지정합니다. **지점** 구조 형식은 다음과 같습니다.  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 `nCount`  
 개수를 지정 **지점** 구조 또는 `CPoint` 가 가리키는 배열의 개체에에서 `lpPoints`합니다.  
  
 `nMode`  
 지역에 대 한 채우기 모드를 지정합니다. 이 매개 변수 중 하나일 수 있습니다 **대체** 또는 **굴곡**합니다.  
  
### <a name="return-value"></a>반환 값  
 작업이 성공 하면 0이 아니고 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 시스템의 다각형 자동으로 닫힙니다, 필요한 경우 첫 번째와 마지막 꼭지점에서 선을 그려. 결과 영역에 저장 되는 `CRgn` 개체입니다.  
  
 영역의 크기는 32, 767 32, 767 하 여 논리 단위 또는 64k의 메모리 제한, 중 더 작은 값입니다.  
  
 다각형 채우기 모드가 인 경우 **대체**, 시스템 간에 검색 한 줄에 홀수 번호와 짝수 다각형 면 영역을 채웁니다. 즉, 시스템 등 세 번째와 네 번째 쪽 사이, 첫 번째 및 두 번째 쪽 사이 영역을 채웁니다.  
  
 다각형 채우기 모드가 인 경우 **굴곡**, 도형 그린 영역을 채우는 여부를 결정 하는 방향을 사용 됩니다. Polygon에 있는 각 선 세그먼트는 시계 방향으로 또는 시계 반대 방향에 그려집니다. 그림의 외부로 둘러싸인된 영역에서 가져온 가상 선 시계 반대 방향으로 선 세그먼트를 통과할 때마다 수는 증가 합니다. 줄 시계 반대 방향으로 선 세그먼트를 통과할 때의 개수가 감소 됩니다. 줄이 그림의 바깥쪽에 도달할 때 수가 0이 아닌 경우는 영역을 채웁니다.  
  
 응용 프로그램이를 완료할 때 사용 하 여 만든 영역을 사용 하 여 `CreatePolygonRgn` 함수를 사용 하 여 장치 컨텍스트의 아웃 지역 선택 해야는 `DeleteObject` 함수를 제거 합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]  
  
##  <a name="createpolypolygonrgn"></a>  CRgn::CreatePolyPolygonRgn  
 일련의 닫힌된 다각형으로 구성 된 영역을 만듭니다.  
  
```  
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,  
    LPINT lpPolyCounts,  
    int nCount,  
    int nPolyFillMode);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpPoints`  
 배열을 가리키는 **지점** 구조 또는 배열을 `CPoint` 다각형의 꼭 짓 점을 정의 하는 개체입니다. 시스템에 자동으로 닫히지 않습니다 때문에 각 다각형 명시적으로 닫아야 합니다. 다각형은 연속으로 지정 됩니다. **지점** 구조 형식은 다음과 같습니다.  
  
 `typedef struct tagPOINT {`  
  
 `int x;`  
  
 `int y;`  
  
 `} POINT;`  
  
 `lpPolyCounts`  
 정수 배열 가리킵니다. 에 있는 첫 번째 다각형의 꼭 짓 점 수를 지정 하는 첫 번째 정수는 `lpPoints` 배열에 두 번째 정수 두 번째 다각형의 꼭 짓 점 수를 지정 합니다.  
  
 `nCount`  
 정수 총 수를 지정 된 `lpPolyCounts` 배열입니다.  
  
 `nPolyFillMode`  
 다각형 채우기 모드를 지정합니다. 이 값 중 하나일 수 있습니다 **대체** 또는 **굴곡**합니다.  
  
### <a name="return-value"></a>반환 값  
 작업이 성공 하면 0이 아니고 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 결과 영역에 저장 되는 `CRgn` 개체입니다.  
  
 다각형이 이거나 겹칠 수 있습니다.  
  
 영역의 크기는 32, 767 32, 767 하 여 논리 단위 또는 64k의 메모리 제한, 중 더 작은 값입니다.  
  
 다각형 채우기 모드가 인 경우 **대체**, 시스템 간에 검색 한 줄에 홀수 번호와 짝수 다각형 면 영역을 채웁니다. 즉, 시스템 등 세 번째와 네 번째 쪽 사이, 첫 번째 및 두 번째 쪽 사이 영역을 채웁니다.  
  
 다각형 채우기 모드가 인 경우 **굴곡**, 도형 그린 영역을 채우는 여부를 결정 하는 방향을 사용 됩니다. Polygon에 있는 각 선 세그먼트는 시계 방향으로 또는 시계 반대 방향에 그려집니다. 그림의 외부로 둘러싸인된 영역에서 가져온 가상 선 시계 반대 방향으로 선 세그먼트를 통과할 때마다 수는 증가 합니다. 줄 시계 반대 방향으로 선 세그먼트를 통과할 때의 개수가 감소 됩니다. 줄이 그림의 바깥쪽에 도달할 때 수가 0이 아닌 경우는 영역을 채웁니다.  
  
 응용 프로그램이를 완료할 때 사용 하 여 만든 영역을 사용 하 여 `CreatePolyPolygonRgn` 함수를 사용 하 여 장치 컨텍스트의 아웃 지역 선택 해야는 [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) 멤버 함수를 제거 합니다.  
  
##  <a name="createrectrgn"></a>  CRgn::CreateRectRgn  
 에 저장 되어 있는 사각형 영역을 만드는 데는 `CRgn` 개체입니다.  
  
```  
BOOL CreateRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);
```  
  
### <a name="parameters"></a>매개 변수  
 `x1`  
 영역의 왼쪽 위 모퉁이의 논리적 x 좌표를 지정합니다.  
  
 `y1`  
 영역의 왼쪽 위 모퉁이의 논리적 y 좌표를 지정합니다.  
  
 `x2`  
 영역의 오른쪽 아래 모퉁이의 논리적 x 좌표를 지정합니다.  
  
 `y2`  
 영역의 오른쪽 아래 모퉁이의 논리적 y 좌표를 지정합니다.  
  
### <a name="return-value"></a>반환 값  
 작업이 성공 하면 0이 아니고 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 영역의 크기는 32, 767 32, 767 하 여 논리 단위 또는 64k의 메모리 제한, 중 더 작은 값입니다.  
  
 마친 의해 만들어진 영역을 사용 하 여 `CreateRectRgn`, 응용 프로그램을 사용할지는 [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) 영역을 제거 하는 멤버 함수입니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]  
  
 추가 예제를 참조 하십시오. [CRgn::CombineRgn](#combinergn)합니다.  
  
##  <a name="createrectrgnindirect"></a>  CRgn::CreateRectRgnIndirect  
 에 저장 되어 있는 사각형 영역을 만드는 데는 `CRgn` 개체입니다.  
  
```  
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>매개 변수  
 `lpRect`  
 가리키는 `RECT` 구조 또는 `CRect` 영역의 왼쪽 및 오른쪽 아래 모퉁이의 논리적 좌표가 포함 된 개체입니다. `RECT` 구조체 형식은 다음과 같습니다.  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>반환 값  
 작업이 성공 하면 0이 아니고 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 영역의 크기는 32, 767 32, 767 하 여 논리 단위 또는 64k의 메모리 제한, 중 더 작은 값입니다.  
  
 마친 의해 만들어진 영역을 사용 하 여 `CreateRectRgnIndirect`, 응용 프로그램을 사용할지는 [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) 영역을 제거 하는 멤버 함수입니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]  
  
##  <a name="createroundrectrgn"></a>  CRgn::CreateRoundRectRgn  
 에 저장 된 모퉁이가 둥근 사각형 영역을 만드는 데는 `CRgn` 개체입니다.  
  
```  
BOOL CreateRoundRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    int x3,  
    int y3);
```  
  
### <a name="parameters"></a>매개 변수  
 `x1`  
 영역의 왼쪽 위 모퉁이의 논리적 x 좌표를 지정합니다.  
  
 `y1`  
 영역의 왼쪽 위 모퉁이의 논리적 y 좌표를 지정합니다.  
  
 `x2`  
 영역의 오른쪽 아래 모퉁이의 논리적 x 좌표를 지정합니다.  
  
 `y2`  
 영역의 오른쪽 아래 모퉁이의 논리적 y 좌표를 지정합니다.  
  
 *x3*  
 둥근된 모퉁이 만드는 데는 타원의 너비를 지정 합니다.  
  
 `y3`  
 둥근된 모퉁이 만드는 데는 타원의 높이 지정 합니다.  
  
### <a name="return-value"></a>반환 값  
 작업이 성공 하면 0이 아니고 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 영역의 크기는 32, 767 32, 767 하 여 논리 단위 또는 64k의 메모리 제한, 중 더 작은 값입니다.  
  
 응용 프로그램이를 완료할 때 사용 하 여 만든 영역을 사용 하 여 `CreateRoundRectRgn` 함수를 사용 하 여 장치 컨텍스트의 아웃 지역 선택 해야는 [CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) 멤버 함수를 제거 합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]  
  
##  <a name="crgn"></a>  CRgn::CRgn  
 `CRgn` 개체를 생성합니다.  
  
```  
CRgn();
```  
  
### <a name="remarks"></a>설명  
 `m_hObject` 데이터 멤버에 없는 Windows GDI 영역이 다른의 하나 이상의 개체가 인스턴스화될 때까지 `CRgn` 멤버 함수입니다.  
  
### <a name="example"></a>예제  
  예를 참조 [CRgn::CreateRoundRectRgn](#createroundrectrgn)합니다.  
  
##  <a name="equalrgn"></a>  CRgn::EqualRgn  
 지정된 된 영역에 저장 된 영역에 동일한 여부를 확인는 `CRgn` 개체입니다.  
  
```  
BOOL EqualRgn(CRgn* pRgn) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 `pRgn`  
 영역을 식별 합니다.  
  
### <a name="return-value"></a>반환 값  
 두 영역 동일 하면 0이 아닌 그렇지 않으면 0입니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]  
  
##  <a name="fromhandle"></a>  CRgn::FromHandle  
 에 대 한 포인터를 반환 합니다.는 `CRgn` Windows 영역에 대 한 핸들을 지정 되 면 개체입니다.  
  
```  
static CRgn* PASCAL FromHandle(HRGN hRgn);
```  
  
### <a name="parameters"></a>매개 변수  
 `hRgn`  
 Windows 영역에 대 한 핸들을 지정합니다.  
  
### <a name="return-value"></a>반환 값  
 에 대 한 포인터는 `CRgn` 개체입니다. 함수가 성공 하지 못한 경우 반환 값은 **NULL**합니다.  
  
### <a name="remarks"></a>설명  
 경우는 `CRgn` 개체가 이미 임시 핸들에 연결 되지 않은 `CRgn` 개체가 생성 되 고 연결 합니다. 이 임시 `CRgn` 개체는 다음에 응용 프로그램의 경우 이벤트 루프 유휴 시간에 인 될 때까지 모든 임시 그래픽 대답 하에서 개체를 삭제만 유효 합니다. 임시 개체가 올바른지만 한 창 메시지를 처리 하는 동안는 하는 또 다른 방법은 말하면 합니다.  
  
##  <a name="getregiondata"></a>  CRgn::GetRegionData  
 데이터 영역을 설명 하는 지정된 된 버퍼를 채웁니다.  
  
```  
int GetRegionData(
    LPRGNDATA lpRgnData,  
    int nCount) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 `lpRgnData`  
 가리키는 [RGNDATA](../../mfc/reference/rgndata-structure.md) 정보를 받는 데이터 구조입니다. 이 매개 변수가 **NULL**, 반환 값 영역 데이터에 필요한 바이트 수를 포함 합니다.  
  
 `nCount`  
 크기를 바이트 단위로 지정 된 `lpRgnData` 버퍼입니다.  
  
### <a name="return-value"></a>반환 값  
 함수가 성공 하면 및 `nCount` 적절 한 수를 지정, 바이트의 반환 값은 항상 `nCount`합니다. 함수가 실패 하거나 경우 `nCount` 작은 지정 보다 적절 한 바이트 수를 반환 값은 0 (오류).  
  
### <a name="remarks"></a>설명  
 이 데이터 영역을 구성 하는 사각형의 크기를 포함 합니다. 이 함수는와 함께에서 사용 되는 `CRgn::CreateFromData` 함수입니다.  
  
##  <a name="getrgnbox"></a>  CRgn::GetRgnBox  
 경계 사각형의 좌표를 검색 된 `CRgn` 개체입니다.  
  
```  
int GetRgnBox(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 `lpRect`  
 가리키는 `RECT` 구조 또는 `CRect` 경계 사각형의 좌표를 받을 개체입니다. `RECT` 구조체 형식은 다음과 같습니다.  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>반환 값  
 영역의 형식을 지정합니다. 다음 값 중 하나일 수 있습니다.  
  
- **COMPLEXREGION** 테두리가 겹치는 영역에 있습니다.  
  
- **NULLREGION** 영역이 비어 있습니다.  
  
- **오류** `CRgn` 개체 유효한 영역을 지정 하지 않습니다.  
  
- **SIMPLEREGION** 지역에 겹치는 테두리가 없습니다.  
  
### <a name="example"></a>예제  
  예를 참조 [CRgn::CreatePolygonRgn](#createpolygonrgn)합니다.  
  
##  <a name="offsetrgn"></a>  CRgn::OffsetRgn  
 에 저장 된 영역으로 이동 된 `CRgn` 개체에서 지정 된 오프셋 합니다.  
  
```  
int OffsetRgn(
    int x,  
    int y);  
  
int OffsetRgn(POINT point);
```  
  
### <a name="parameters"></a>매개 변수  
 *x*  
 오른쪽 또는 왼쪽으로 이동 하는 단위 수를 지정 합니다.  
  
 *y*  
 위로 또는 아래로 이동할 단위 수를 지정 합니다.  
  
 `point`  
 x 좌표 `point` 오른쪽 또는 왼쪽으로 이동 하는 단위 수를 지정 합니다. y-좌표 `point` 위로 또는 아래로 이동할 단위 수를 지정 합니다. `point` 매개 변수 중 하나일 수 있습니다는 **지점** 구조 또는 `CPoint` 개체입니다.  
  
### <a name="return-value"></a>반환 값  
 새 영역의 유형입니다. 다음 값 중 하나일 수 있습니다.  
  
- **COMPLEXREGION** 테두리가 겹치는 영역에 있습니다.  
  
- **오류** 지역 핸들이 잘못 되었습니다.  
  
- **NULLREGION** 영역이 비어 있습니다.  
  
- **SIMPLEREGION** 지역에 겹치는 테두리가 없습니다.  
  
### <a name="remarks"></a>설명  
 함수는 영역을 이동 *x* x 축 단위 및 *y* y 축의 단위입니다.  
  
 영역의 좌표 값은 32, 767 및 보다 크거나-32, 768 보다 작아야 합니다. *x* 및 *y* 잘못 된 지역 좌표를 방지 하기 위해 매개 변수를 신중 하 게 선택 해야 합니다.  
  
### <a name="example"></a>예제  
  예를 참조 [CRgn::CreateEllipticRgn](#createellipticrgn)합니다.  
  
##  <a name="operator_hrgn"></a>  HRGN CRgn::operator  
 이 연산자를 사용 하 여의 연결 된 Windows GDI 핸들을 가져올 수는 `CRgn` 개체입니다.  
  
```  
operator HRGN() const;  
```  
  
### <a name="return-value"></a>반환 값  
 경우 성공 Windows GDI 개체에 대 한 핸들 나타내는 `CRgn` 개체; 그렇지 않으면 **NULL**합니다.  
  
### <a name="remarks"></a>설명  
 이 연산자는의 직접 사용을 지원 하려면 캐스팅 연산자는 **HRGN** 개체입니다.  
  
 그래픽 개체를 사용 하는 방법에 대 한 자세한 내용은 문서 참조 [그래픽 개체](http://msdn.microsoft.com/library/windows/desktop/dd144962) Windows sdk에서입니다.  
  
##  <a name="ptinregion"></a>  CRgn::PtInRegion  
 확인 여부로 지정한 점을 *x* 및 *y* 에 저장 된 영역에는 `CRgn` 개체입니다.  
  
```  
BOOL PtInRegion(
    int x,  
    int y) const;  
  
BOOL PtInRegion(POINT point) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 *x*  
 테스트할 점의의 논리적 x 좌표를 지정 합니다.  
  
 *y*  
 테스트할 점의의 논리적 y 좌표를 지정 합니다.  
  
 `point`  
 x 및 y 좌표 `point` 의 값을 테스트할 점의 x 및 y 좌표를 지정 합니다. `point` 매개 변수 수는 **지점** 구조 또는 `CPoint` 개체입니다.  
  
### <a name="return-value"></a>반환 값  
 지점이; 지역에 있으면 0이 아닌 그렇지 않으면 0입니다.  
  
##  <a name="rectinregion"></a>  CRgn::RectInRegion  
 사각형의 모든 부분에서 지정한 `lpRect` 내에 저장 된 영역의 경계는 `CRgn` 개체입니다.  
  
```  
BOOL RectInRegion(LPCRECT lpRect) const;  
```  
  
### <a name="parameters"></a>매개 변수  
 `lpRect`  
 가리키는 `RECT` 구조 또는 `CRect` 개체입니다. `RECT` 구조체 형식은 다음과 같습니다.  
  
 `typedef struct tagRECT {`  
  
 `int left;`  
  
 `int top;`  
  
 `int right;`  
  
 `int bottom;`  
  
 `} RECT;`  
  
### <a name="return-value"></a>반환 값  
 지정된 된 사각형의 일부 영역;의 경계 내에 있는 경우 0이 아닌 그렇지 않으면 0입니다.  
  
##  <a name="setrectrgn"></a>  CRgn::SetRectRgn  
 사각형 영역을 만듭니다.  
  
```  
void SetRectRgn(
    int x1,  
    int y1,  
    int x2,  
    int y2);  
  
void SetRectRgn(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>매개 변수  
 `x1`  
 사각형 영역의 왼쪽 위 모서리의 x 좌표를 지정합니다.  
  
 `y1`  
 사각형 영역의 왼쪽 위 모퉁이의 y 좌표를 지정합니다.  
  
 `x2`  
 사각형 영역의 오른쪽 아래 모서리의 x 좌표를 지정합니다.  
  
 `y2`  
 사각형 영역의 오른쪽 아래 모서리의 y 좌표를 지정합니다.  
  
 `lpRect`  
 사각형 영역을 지정 합니다. 에 대 한 일 수 있습니다는 `RECT` 구조 또는 `CRect` 개체입니다.  
  
### <a name="remarks"></a>설명  
 그러나와 달리 [CreateRectRgn](#createrectrgn),는 추가 메모리를 로컬 Windows 응용 프로그램 힙에서 할당 하지 않습니다. 대신,에 저장 된 영역에 대해 할당 된 공간을 사용 하 여 `CRgn` 개체입니다. 즉는 `CRgn` 개체 해야 이미 초기화 된 호출 하기 전에 유효한 Windows 영역과 `SetRectRgn`합니다. 제공한 포인트 `x1`, `y1`, `x2`, 및 `y2` 할당 된 공간의 최소 크기를 지정 합니다.  
  
 대신이 함수를 사용 하 여는 `CreateRectRgn` 로컬 메모리 관리자에 대 한 호출을 방지 하려면 멤버 함수입니다.  
  
## <a name="see-also"></a>참고 항목  
 [CWnd 클래스](../../mfc/reference/cwnd-class.md)   
 [계층 구조 차트](../../mfc/hierarchy-chart.md)



