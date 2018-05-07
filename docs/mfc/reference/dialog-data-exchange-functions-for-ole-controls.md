---
title: OLE 컨트롤에 대 한 대화 상자 데이터 교환 함수 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXDISP/DDX_OCBool
- AFXDISP/DDX_OCBoolRO
- AFXDISP/DDX_OCColor
- AFXDISP/DDX_OCColorRO
- AFXDISP/DDX_OCFloat
- AFXDISP/DDX_OCFloatRO
- AFXDISP/DDX_OCInt
- AFXDISP/DDX_OCIntRO
- AFXDISP/DDX_OCShort
- AFXDISP/DDX_OCShortRO
- AFXDISP/DDX_OCText
- AFXDISP/DDX_OCTextRO
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5dd7e1b9b18e8478cfa4e61a22806cf067cb3699
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>OLE 컨트롤에 대한 대화 상자 데이터 교환 함수
이 항목 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체 내 OLE 컨트롤의 속성 및 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버 간에 데이터를 교환 하는 데 사용 하 여 DDX_OC 함수를 나열 합니다.  
  
### <a name="ddxoc-functions"></a>DDX_OC 함수  
  
|||  
|-|-|  
|[DDX_OCBool](#ddx_ocbool)|전송을 관리 **BOOL** OLE 컨트롤의 속성 간에 데이터 및 **BOOL** 데이터 멤버입니다.|  
|[DDX_OCBoolRO](#ddx_ocboolro)|전송을 관리 **BOOL** OLE 컨트롤의 읽기 전용 속성 간에 데이터 및 **BOOL** 데이터 멤버입니다.|  
|[DDX_OCColor](#ddx_occolor)|전송을 관리 **OLE_COLOR** OLE 컨트롤의 속성 간에 데이터 및 **OLE_COLOR** 데이터 멤버입니다.|  
|[DDX_OCColorRO](#ddx_occolorro)|전송을 관리 **OLE_COLOR** OLE 컨트롤의 읽기 전용 속성 간에 데이터 및 **OLE_COLOR** 데이터 멤버입니다.|  
|[DDX_OCFloat](#ddx_ocfloat)|전송을 관리 **float** (또는 **double**) OLE 컨트롤의 속성 간에 데이터 및 **float** (또는 **double**) 데이터 멤버입니다.|  
|[DDX_OCFloatRO](#ddx_ocfloatro)|전송을 관리 **float** (또는 **double**) OLE 컨트롤의 읽기 전용 속성 간에 데이터 및 **float** (또는 **double**) 데이터 멤버입니다.|  
|[DDX_OCInt](#ddx_ocint)|전송을 관리 `int` (또는 **긴**) OLE 컨트롤의 속성 간에 데이터 및 `int` (또는 **긴**) 데이터 멤버입니다.|  
|[DDX_OCIntRO](#ddx_ocintro)|전송을 관리 `int` (또는 **긴**) OLE 컨트롤의 읽기 전용 속성 간에 데이터 및 `int` (또는 **긴**) 데이터 멤버입니다.|  
|[DDX_OCShort](#ddx_ocshort)|전송을 관리 **짧은** OLE 컨트롤의 속성 간에 데이터 및 **짧은** 데이터 멤버입니다.|  
|[DDX_OCShortRO](#ddx_ocshortro)|전송을 관리 **짧은** OLE 컨트롤의 읽기 전용 속성 간에 데이터 및 **짧은** 데이터 멤버입니다.|  
|[DDX_OCText](#ddx_octext)|전송을 관리 **CString** OLE 컨트롤의 속성 간에 데이터 및 **CString** 데이터 멤버입니다.|  
|[DDX_OCTextRO](#ddx_octextro)|전송을 관리 **CString** OLE 컨트롤의 읽기 전용 속성 간에 데이터 및 **CString** 데이터 멤버입니다.|  
  
##  <a name="ddx_ocbool"></a>  DDX_OCBool  
 `DDX_OCBool` 함수의 전송을 관리 **BOOL** 대화 상자에서 OLE 컨트롤의 속성 간에 데이터 폼 뷰 또는 컨트롤 뷰 개체 및 **BOOL** 대화 상자에서 폼 보기의 데이터 멤버 또는 컨트롤 뷰 개체입니다.  
  
```   
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    BOOL& value);
```  
  
### <a name="parameters"></a>매개 변수  
 `pDX`  
 `CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.  
  
 `nIDC`  
 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.  
  
 `dispid`  
 컨트롤의 속성에 대한 디스패치 ID입니다.  
  
 *값*  
 데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.  
  
### <a name="remarks"></a>설명  
 DDX에 대 한 자세한 내용은 참조 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)합니다.  
  
### <a name="requirements"></a>요구 사항  
  **헤더:** afxdisp.h  
  
##  <a name="ddx_ocboolro"></a>  DDX_OCBoolRO  
 `DDX_OCBoolRO` 함수의 전송을 관리 **BOOL** 대화 상자에서 OLE 컨트롤의 읽기 전용 속성 간의 데이터 폼 뷰 또는 컨트롤 뷰 개체 및 **BOOL** 대화 상자의 데이터 멤버 폼 뷰 또는 컨트롤 뷰 개체입니다.  
  
```   
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    BOOL& value);
```  
  
### <a name="parameters"></a>매개 변수  
 `pDX`  
 `CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.  
  
 `nIDC`  
 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.  
  
 `dispid`  
 컨트롤의 속성에 대한 디스패치 ID입니다.  
  
 *값*  
 데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.  
  
### <a name="remarks"></a>설명  
 DDX에 대 한 자세한 내용은 참조 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)합니다.  
  
### <a name="requirements"></a>요구 사항  
  **헤더** afxdisp.h  
  
##  <a name="ddx_occolor"></a>  DDX_OCColor  
 `DDX_OCColor` 함수의 전송을 관리 **OLE_COLOR** 대화 상자에서 OLE 컨트롤의 속성 간에 데이터 폼 뷰 또는 컨트롤 뷰 개체 및 **OLE_COLOR** 대화 상자의 데이터 멤버 폼 뷰 또는 컨트롤 뷰 개체입니다.  
  
```   
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    OLE_COLOR& value);
```  
  
### <a name="parameters"></a>매개 변수  
 `pDX`  
 `CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.  
  
 `nIDC`  
 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.  
  
 `dispid`  
 컨트롤의 속성에 대한 디스패치 ID입니다.  
  
 *값*  
 데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.  
  
### <a name="remarks"></a>설명  
 DDX에 대 한 자세한 내용은 참조 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)합니다.  
  
### <a name="requirements"></a>요구 사항  
  **헤더** afxdisp.h  
  
##  <a name="ddx_occolorro"></a>  DDX_OCColorRO  
 `DDX_OCColorRO` 함수의 전송을 관리 **OLE_COLOR** 대화 상자에서 OLE 컨트롤의 읽기 전용 속성 간의 데이터 폼 뷰 또는 컨트롤 뷰 개체 및 **OLE_COLOR** 데이터 멤버에는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체입니다.  
  
```   
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    OLE_COLOR& value);
```  
  
### <a name="parameters"></a>매개 변수  
 `pDX`  
 `CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.  
  
 `nIDC`  
 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.  
  
 `dispid`  
 컨트롤의 속성에 대한 디스패치 ID입니다.  
  
 *값*  
 데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.  
  
### <a name="remarks"></a>설명  
 DDX에 대 한 자세한 내용은 참조 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)합니다.  
  
### <a name="requirements"></a>요구 사항  
  **헤더** afxdisp.h  
  
##  <a name="ddx_ocfloat"></a>  DDX_OCFloat  
 `DDX_OCFloat` 함수의 전송을 관리 **float** (또는 **double**) 대화 상자에서 OLE 컨트롤의 속성 간에 데이터 폼 뷰 또는 컨트롤 뷰 개체 및 **float** (또는 **double**) 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버입니다.  
  
```   
void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    float& value);

void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    double& value);
```  
  
### <a name="parameters"></a>매개 변수  
 `pDX`  
 `CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.  
  
 `nIDC`  
 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.  
  
 `dispid`  
 컨트롤의 속성에 대한 디스패치 ID입니다.  
  
 *값*  
 데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.  
  
### <a name="remarks"></a>설명  
 DDX에 대 한 자세한 내용은 참조 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)합니다.  
  
### <a name="requirements"></a>요구 사항  
  **헤더** afxdisp.h  
  
##  <a name="ddx_ocfloatro"></a>  DDX_OCFloatRO  
 `DDX_OCFloatRO` 함수의 전송을 관리 **float** (또는 **double**) 대화 상자에서 OLE 컨트롤의 읽기 전용 속성 간의 데이터 폼 뷰 또는 컨트롤 뷰 개체 및  **float** (또는 **double**) 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버입니다.  
  
```   
void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    float& value);

void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    double& value);
```  
  
### <a name="parameters"></a>매개 변수  
 `pDX`  
 `CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.  
  
 `nIDC`  
 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.  
  
 `dispid`  
 컨트롤의 속성에 대한 디스패치 ID입니다.  
  
 *값*  
 데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.  
  
### <a name="remarks"></a>설명  
 DDX에 대 한 자세한 내용은 참조 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)합니다.  
  
### <a name="requirements"></a>요구 사항  
  **헤더** afxdisp.h  
  
##  <a name="ddx_ocint"></a>  DDX_OCInt  
 `DDX_OCInt` 함수의 전송을 관리 `int` (또는 **긴**) 대화 상자에서 OLE 컨트롤의 속성 간에 데이터 폼 뷰 또는 컨트롤 뷰 개체 및 `int` (또는 **장기**) 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버입니다.  
  
```   
void AFXAPI DDX_OCInt(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    int& value);

void AFXAPI DDX_OCInt(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    long& value);
```  
  
### <a name="parameters"></a>매개 변수  
 `pDX`  
 `CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.  
  
 `nIDC`  
 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.  
  
 `dispid`  
 컨트롤의 속성에 대한 디스패치 ID입니다.  
  
 *값*  
 데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.  
  
### <a name="remarks"></a>설명  
 DDX에 대 한 자세한 내용은 참조 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)합니다.  
  
### <a name="requirements"></a>요구 사항  
  **헤더** afxdisp.h  
  
##  <a name="ddx_ocintro"></a>  DDX_OCIntRO  
 `DDX_OCIntRO` 함수의 전송을 관리 `int` (또는 **긴**) 대화 상자에서 OLE 컨트롤의 읽기 전용 속성 간의 데이터 폼 뷰 또는 컨트롤 뷰 개체 및 `int` (또는 **긴** ) 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 데이터 멤버입니다.  
  
```   
void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    int& value);

void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    long& value);
```  
  
### <a name="parameters"></a>매개 변수  
 `pDX`  
 `CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.  
  
 `nIDC`  
 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.  
  
 `dispid`  
 컨트롤의 속성에 대한 디스패치 ID입니다.  
  
 *값*  
 데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.  
  
### <a name="remarks"></a>설명  
 DDX에 대 한 자세한 내용은 참조 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)합니다.  
  
### <a name="requirements"></a>요구 사항  
  **헤더** afxdisp.h  
  
##  <a name="ddx_ocshort"></a>  DDX_OCShort  
 `DDX_OCShort` 폼 보기를 컨트롤 뷰 개체와 짧은 데이터 멤버의 대화 상자 또는 컨트롤 뷰 개체 또는 함수 폼 보기 대화 상자에서 OLE 컨트롤의 속성 간에 간단한 데이터의 전송을 관리 합니다.  
  
```   
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    short& value);
```  
  
### <a name="parameters"></a>매개 변수  
 `pDX`  
 `CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.  
  
 `nIDC`  
 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.  
  
 `dispid`  
 컨트롤의 속성에 대한 디스패치 ID입니다.  
  
 *값*  
 데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.  
  
### <a name="remarks"></a>설명  
 DDX에 대 한 자세한 내용은 참조 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)합니다.  
  
### <a name="requirements"></a>요구 사항  
  **헤더** afxdisp.h  
  
##  <a name="ddx_ocshortro"></a>  DDX_OCShortRO  
 `DDX_OCShortRO` 폼 보기를 컨트롤 뷰 개체와 짧은 데이터 멤버의 대화 상자 또는 컨트롤 뷰 개체 또는 함수에는 폼 보기 대화 상자에서 OLE 컨트롤의 읽기 전용 속성 간의 짧은 데이터의 전송을 관리 합니다.  
  
```   
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    short& value);
```  
  
### <a name="parameters"></a>매개 변수  
 `pDX`  
 `CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.  
  
 `nIDC`  
 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.  
  
 `dispid`  
 컨트롤의 속성에 대한 디스패치 ID입니다.  
  
 *값*  
 데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.  
  
### <a name="remarks"></a>설명  
 DDX에 대 한 자세한 내용은 참조 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)합니다.  
  
### <a name="requirements"></a>요구 사항  
  **헤더** afxdisp.h  
  
##  <a name="ddx_octext"></a>  DDX_OCText  
 **DDX_OCText** 함수의 전송을 관리 **CString** 대화 상자에서 OLE 컨트롤의 속성 간에 데이터 폼 뷰 또는 컨트롤 뷰 개체 및 **CString** 데이터 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버입니다.  
  
```   
void AFXAPI DDX_OCText(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    CString& value); 
```  
  
### <a name="parameters"></a>매개 변수  
 `pDX`  
 에 대 한 포인터는 **CDataExchange** 개체입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.  
  
 `nIDC`  
 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.  
  
 `dispid`  
 컨트롤의 속성에 대한 디스패치 ID입니다.  
  
 *값*  
 데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.  
  
### <a name="remarks"></a>설명  
 DDX에 대 한 자세한 내용은 참조 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)합니다.  
  
### <a name="requirements"></a>요구 사항  
  **헤더** afxdisp.h  
  
##  <a name="ddx_octextro"></a>  DDX_OCTextRO  
 `DDX_OCTextRO` 함수는 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체 내 OLE 컨트롤의 읽기 전용 속성과 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 `CString` 데이터 멤버 간 `CString` 데이터 전송을 관리합니다.  
  
```  
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    CString& value); 
```  
  
### <a name="parameters"></a>매개 변수  
 `pDX`  
 `CDataExchange` 개체에 대한 포인터입니다. 프레임워크는 해당 방향을 포함해서 데이터 교환의 컨텍스트를 설정하기 위해 이 개체를 제공합니다.  
  
 `nIDC`  
 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 OLE 컨트롤 ID입니다.  
  
 `dispid`  
 컨트롤의 속성에 대한 디스패치 ID입니다.  
  
 *값*  
 데이터를 교환할 대화 상자, 폼 뷰 또는 컨트롤 뷰 개체의 멤버 변수에 대한 참조입니다.  
  
### <a name="remarks"></a>설명  
 DDX에 대 한 자세한 내용은 참조 [대화 상자 데이터 교환 및 유효성 검사](../../mfc/dialog-data-exchange-and-validation.md)합니다.  

### <a name="requirements"></a>요구 사항  
  **헤더** afxdisp.h
    
## <a name="see-also"></a>참고 항목  
 [매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
