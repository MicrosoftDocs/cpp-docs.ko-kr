---
title: "회색 및 디더링된 비트맵 함수 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
dev_langs:
- C++
helpviewer_keywords:
- gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7f895fb22e4f4d2649cdec1e4c9925b69b013e49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="gray-and-dithered-bitmap-functions"></a>회색 및 디더링된 비트맵 함수
**회색 비트맵 함수**  
  
 MFC는 비트맵이 비활성화된 컨트롤의 모양을 갖도록 하기 위한 두 가지 함수를 제공합니다.  
  
 ![회색 및 기존 아이콘 버전 비교](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
|||  
|-|-|  
|[AfxDrawGrayBitmap](#afxdrawgraybitmap)|비트맵의 회색 버전을 그립니다.|  
|[AfxGetGrayBitmap](#afxgetgraybitmap)|비트맵의 회색 버전을 복사합니다.|  
  
 **디더링된 비트맵 함수**  
  
 MFC는 비트맵의 배경을 디더링된 패턴으로 바꾸기 위한 두 가지 함수도 제공합니다.  
  
 ![디더링된 및 기존 아이콘 버전 비교](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
|||  
|-|-|  
|[AfxDrawDitheredBitmap](#afxdrawditheredbitmap)|디더링된 배경을 사용하여 비트맵을 그립니다.|  
|[AfxGetDitheredBitmap](#afxgetditheredbitmap)|디더링된 배경을 사용하여 비트맵을 복사합니다.|  
  
##  <a name="afxdrawgraybitmap"></a>  AfxDrawGrayBitmap  
 비트맵의 회색 버전을 그립니다.  
  
```   
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,  
    int x,  
    int y,  
    const CBitmap& rSrc,  
    COLORREF crBackground); 
```  
  
### <a name="parameters"></a>매개 변수  
 `pDC`  
 대상 DC를 가리킵니다.  
  
 *x*  
 대상 x 좌표입니다.  
  
 *y*  
 대상 y 좌표입니다.  
  
 `rSrc`  
 소스 비트맵입니다.  
  
 `crBackground`  
 새 배경색(일반적으로 회색, 예: COLOR_MENU)입니다.  
  
### <a name="remarks"></a>설명  
 `AfxDrawGrayBitmap` 으로 그린 비트맵은 비활성화된 컨트롤의 모양을 갖습니다.  
  
 ![회색 및 기존 아이콘 버전 비교](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
### <a name="example"></a>예  
 [!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]  

### <a name="requirements"></a>요구 사항  
 **헤더:** afxwin.h  

##  <a name="afxgetgraybitmap"></a>  AfxGetGrayBitmap  
 비트맵의 회색 버전을 복사합니다.  
  
```   
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,  
    CBitmap* pDest,  
    COLORREF crBackground); 
```  
  
### <a name="parameters"></a>매개 변수  
 `rSrc`  
 소스 비트맵입니다.  
  
 `pDest`  
 대상 비트맵입니다.  
  
 `crBackground`  
 새 배경색(일반적으로 회색, 예: COLOR_MENU)입니다.  
  
### <a name="remarks"></a>설명  
 `AfxGetGrayBitmap` 로 복사한 비트맵은 비활성화된 컨트롤의 모양을 갖습니다.  
  
 ![회색 및 기존 아이콘 버전 비교](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
### <a name="example"></a>예  
 [!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]  

### <a name="requirements"></a>요구 사항  
 **헤더:** afxwin.h  
  
##  <a name="afxdrawditheredbitmap"></a>  AfxDrawDitheredBitmap  
 배경이 디더링된 (checker) 패턴으로 바꾸기 비트맵을 그립니다.  
  
```   
void AFXAPI AfxDrawDitheredBitmap(
    CDC* pDC,  
    int x,  
    int y,  
    const CBitmap& rSrc,  
    COLORREF cr1  ,  
    COLORREF cr2); 
```  
  
### <a name="parameters"></a>매개 변수  
 `pDC`  
 대상 DC를 가리킵니다.  
  
 *x*  
 대상 x 좌표입니다.  
  
 *y*  
 대상 y 좌표입니다.  
  
 `rSrc`  
 소스 비트맵입니다.  
  
 `cr1`  
 두 개의 디더링 색상 중 하나로 일반적으로 흰색 개입니다.  
  
 `cr2`  
 다른 디더링 색, 일반적으로 밝은 회색 (: COLOR_MENU)입니다.  
  
### <a name="remarks"></a>설명  
 두 가지 색을 사용 하 여 대상 DC에서 소스 비트맵을 그릴 ( `cr1` 및 `cr2`) 바둑판된 패턴 비트맵의 배경을 대체 합니다. 소스 비트맵의 배경은 흰색 픽셀 및 모든 픽셀 비트맵의 왼쪽 위 모서리에 있는 픽셀의 색으로 정의 됩니다.  
  
 ![디더링된 및 기존 아이콘 버전 비교](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
### <a name="example"></a>예  
 [!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]  

### <a name="requirements"></a>요구 사항  
 **헤더:** afxwin.h  


##  <a name="afxgetditheredbitmap"></a>  AfxGetDitheredBitmap  
 배경이 디더링된 (checker) 패턴으로 바꾸기 비트맵에 복사 합니다.  
  
```   
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,  
    CBitmap* pDest,  
    COLORREF cr1  ,  
    COLORREF cr2); 
```  
  
### <a name="parameters"></a>매개 변수  
 `rSrc`  
 소스 비트맵입니다.  
  
 `pDest`  
 대상 비트맵입니다.  
  
 `cr1`  
 두 개의 디더링 색상 중 하나로 일반적으로 흰색 개입니다.  
  
 `cr2`  
 다른 디더링 색, 일반적으로 밝은 회색 (: COLOR_MENU)입니다.  
  
### <a name="remarks"></a>설명  
 소스 비트맵을 두 색으로 대상 비트맵에 복사 됩니다 ( `cr1` 및 `cr2`) 소스 비트맵의 배경을 바꾸기 바둑판된 패턴입니다. 소스 비트맵의 배경은 흰색 픽셀 및 모든 픽셀 비트맵의 왼쪽 위 모서리에 있는 픽셀의 색으로 정의 됩니다.  
  
 ![디더링된 및 기존 아이콘 버전 비교](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
### <a name="example"></a>예  
 [!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]  

### <a name="requirements"></a>요구 사항  
 **헤더:** afxwin.h  
  
## <a name="see-also"></a>참고 항목  
 [매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
