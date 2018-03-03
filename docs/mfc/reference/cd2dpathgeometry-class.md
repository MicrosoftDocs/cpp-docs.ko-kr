---
title: "CD2DPathGeometry 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::Attach
- AFXRENDERTARGET/CD2DPathGeometry::Create
- AFXRENDERTARGET/CD2DPathGeometry::Destroy
- AFXRENDERTARGET/CD2DPathGeometry::Detach
- AFXRENDERTARGET/CD2DPathGeometry::GetFigureCount
- AFXRENDERTARGET/CD2DPathGeometry::GetSegmentCount
- AFXRENDERTARGET/CD2DPathGeometry::Open
- AFXRENDERTARGET/CD2DPathGeometry::Stream
- AFXRENDERTARGET/CD2DPathGeometry::m_pPathGeometry
dev_langs:
- C++
helpviewer_keywords:
- CD2DPathGeometry [MFC], CD2DPathGeometry
- CD2DPathGeometry [MFC], Attach
- CD2DPathGeometry [MFC], Create
- CD2DPathGeometry [MFC], Destroy
- CD2DPathGeometry [MFC], Detach
- CD2DPathGeometry [MFC], GetFigureCount
- CD2DPathGeometry [MFC], GetSegmentCount
- CD2DPathGeometry [MFC], Open
- CD2DPathGeometry [MFC], Stream
- CD2DPathGeometry [MFC], m_pPathGeometry
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9142b268c5f09a88883d048c35287966d9ef8aab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dpathgeometry-class"></a>CD2DPathGeometry 클래스
ID2D1PathGeometry에 대 한 래퍼입니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CD2DPathGeometry : public CD2DGeometry;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CD2DPathGeometry::CD2DPathGeometry](#cd2dpathgeometry)|CD2DPathGeometry 개체를 만듭니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CD2DPathGeometry::Attach](#attach)|기존 개체에 대 한 리소스 인터페이스를 연결.|  
|[CD2DPathGeometry::Create](#create)|CD2DPathGeometry를 만듭니다. (재정의 [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DPathGeometry::Destroy](#destroy)|CD2DPathGeometry 개체를 소멸 시킵니다. (재정의 [CD2DGeometry::Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy).)|  
|[CD2DPathGeometry::Detach](#detach)|개체에서 리소스 인터페이스를 분리합니다.|  
|[CD2DPathGeometry::GetFigureCount](#getfigurecount)|Pathgeometry에 숫자 값의 수를 검색 합니다.|  
|[CD2DPathGeometry::GetSegmentCount](#getsegmentcount)|Pathgeometry에 세그먼트의 수를 검색합니다.|  
|[CD2DPathGeometry::Open](#open)|숫자 값 및 세그먼트 pathgeometry를 채우는 데 사용 되는 기 하 도형 싱크를 검색 합니다.|  
|[CD2DPathGeometry::Stream](#stream)|지정 된 ID2D1GeometrySink pathgeometry의 내용을 복사합니다.|  
  
### <a name="protected-data-members"></a>보호된 데이터 멤버  
  
|name|설명|  
|----------|-----------------|  
|[CD2DPathGeometry::m_pPathGeometry](#m_ppathgeometry)|ID2D1PathGeometry에 대 한 포인터입니다.|  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)  
  
 `CD2DPathGeometry`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxrendertarget.h  
  
##  <a name="attach"></a>CD2DPathGeometry::Attach  
 기존 개체에 대 한 리소스 인터페이스를 연결.  
  
```  
void Attach(ID2D1PathGeometry* pResource);
```  
  
### <a name="parameters"></a>매개 변수  
 `pResource`  
 기존 리소스 인터페이스입니다. NULL 일 수 없습니다.  
  
##  <a name="cd2dpathgeometry"></a>CD2DPathGeometry::CD2DPathGeometry  
 CD2DPathGeometry 개체를 만듭니다.  
  
```  
CD2DPathGeometry(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>매개 변수  
 `pParentTarget`  
 렌더링 대상에 대 한 포인터입니다.  
  
 `bAutoDestroy`  
 개체를 소유자 (pParentTarget)에 의해 폐기 수를 나타냅니다.  
  
##  <a name="create"></a>CD2DPathGeometry::Create  
 CD2DPathGeometry를 만듭니다.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>매개 변수  
 `pRenderTarget`  
 렌더링 대상에 대 한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 메서드가 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 HRESULT 오류 코드를 반환합니다.  
  
##  <a name="destroy"></a>CD2DPathGeometry::Destroy  
 CD2DPathGeometry 개체를 소멸 시킵니다.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DPathGeometry::Detach  
 개체에서 리소스 인터페이스를 분리합니다.  
  
```  
ID2D1PathGeometry* Detach();
```  
  
### <a name="return-value"></a>반환 값  
 분리 된 리소스 인터페이스 포인터입니다.  
  
##  <a name="getfigurecount"></a>CD2DPathGeometry::GetFigureCount  
 Pathgeometry에 숫자 값의 수를 검색 합니다.  
  
```  
int GetFigureCount() const;  
```  
  
### <a name="return-value"></a>반환 값  
 Pathgeometry에 숫자 값의 수를 반환합니다.  
  
##  <a name="getsegmentcount"></a>CD2DPathGeometry::GetSegmentCount  
 Pathgeometry에 세그먼트의 수를 검색합니다.  
  
```  
int GetSegmentCount() const;  
```  
  
### <a name="return-value"></a>반환 값  
 Pathgeometry에 세그먼트의 수를 반환합니다.  
  
##  <a name="m_ppathgeometry"></a>CD2DPathGeometry::m_pPathGeometry  
 ID2D1PathGeometry에 대 한 포인터입니다.  
  
```  
ID2D1PathGeometry* m_pPathGeometry;  
```  
  
##  <a name="open"></a>CD2DPathGeometry::Open  
 숫자 값 및 세그먼트 pathgeometry를 채우는 데 사용 되는 기 하 도형 싱크를 검색 합니다.  
  
```  
ID2D1GeometrySink* Open();
```  
  
### <a name="return-value"></a>반환 값  
 숫자 값 및 세그먼트 pathgeometry를 채우는 데 사용 되는 ID2D1GeometrySink에 대 한 포인터입니다.  
  
##  <a name="stream"></a>CD2DPathGeometry::Stream  
 지정 된 ID2D1GeometrySink pathgeometry의 내용을 복사합니다.  
  
```  
BOOL Stream(ID2D1GeometrySink* geometrySink);
```  
  
### <a name="parameters"></a>매개 변수  
 `geometrySink`  
 싱크 pathgeometry의 내용이 복사 됩니다. 이 싱크를 수정 하는 경우에이 경로 geometry의 내용을 변경 하지 않습니다.  
  
### <a name="return-value"></a>반환 값  
 메서드가 성공 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE를 반환합니다.  
  
## <a name="see-also"></a>참고 항목  
 [클래스](../../mfc/reference/mfc-classes.md)
