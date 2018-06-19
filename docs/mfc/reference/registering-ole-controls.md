---
title: OLE 컨트롤 등록 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e51e4c425d3d16b57a2b1ce0d4fc2f585dc505d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378059"
---
# <a name="registering-ole-controls"></a>OLE 컨트롤 등록
다른 OLE 서버 개체와 같은 OLE 컨트롤은 다른 OLE 인식 응용 프로그램에서 액세스할 수 있습니다. 이 컨트롤의 형식 라이브러리와 클래스를 등록 하 여 이루어집니다.  
  
 다음 함수를 사용 하 여 추가 하 고 Windows 등록 데이터베이스에 컨트롤의 클래스, 속성 페이지 및 형식 라이브러리를 제거 하면:  
  
### <a name="registering-ole-controls"></a>OLE 컨트롤 등록  
  
|||  
|-|-|  
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|등록 데이터베이스에 컨트롤의 클래스를 추가합니다.|  
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|등록 데이터베이스에 컨트롤 속성 페이지를 추가합니다.|  
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|등록 데이터베이스에 컨트롤의 형식 라이브러리를 추가합니다.|  
|[AfxOleUnregisterClass](#afxoleunregisterclass)|등록 데이터베이스에서 컨트롤 클래스 또는 속성 페이지 클래스를 제거합니다.|  
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|컨트롤의 형식 라이브러리 등록 데이터베이스에서 제거합니다.|  
  
 `AfxOleRegisterTypeLib` 일반적으로의 컨트롤 DLL의 구현에서 호출 `DllRegisterServer`합니다. 마찬가지로, `AfxOleUnregisterTypeLib` 호출한 `DllUnregisterServer`합니다. `AfxOleRegisterControlClass``AfxOleRegisterPropertyPageClass`, 및 `AfxOleUnregisterClass` 일반적으로 의해 호출 됩니다는 `UpdateRegistry` 컨트롤의 클래스 팩터리 또는 속성 페이지의 멤버 함수입니다.  
  
##  <a name="afxoleregistercontrolclass"></a>  AfxOleRegisterControlClass  
 컨트롤 클래스는 Windows 등록 데이터베이스에 등록합니다.  
  
```   
BOOL AFXAPI AfxOleRegisterControlClass(
    HINSTANCE hInstance,  
    REFCLSID clsid,  
    LPCTSTR pszProgID,  
    UINT idTypeName,  
    UINT idBitmap,  
    int nRegFlags,  
    DWORD dwMiscStatus,  
    REFGUID tlid,  
    WORD wVerMajor,  
    WORD wVerMinor); 
```  
  
### <a name="parameters"></a>매개 변수  
 `hInstance`  
 컨트롤 클래스와 연관 된 모듈의 인스턴스 핸들입니다.  
  
 `clsid`  
 컨트롤의 고유 클래스 ID입니다.  
  
 `pszProgID`  
 컨트롤의 고유 프로그램 ID입니다.  
  
 `idTypeName`  
 컨트롤에 대 한 사용자가 읽을 수 있는 형식 이름을 포함 하는 문자열의 리소스 ID입니다.  
  
 *idBitmap*  
 도구 모음이 나 색상표에서 OLE 컨트롤을 나타내는 데 사용 되는 비트맵의 리소스 ID입니다.  
  
 `nRegFlags`  
 다음과 같은 플래그 중 하나 이상을 포함 되어 있습니다.  
  
- `afxRegInsertable` OLE 개체에 대 한 개체 삽입 대화 상자에 표시를 제어할 수 있습니다.  
  
- `afxRegApartmentThreading` ThreadingModel 레지스트리에서 설정 하는 스레딩 모델이 아파트 = 합니다.  
  
- `afxRegFreeThreading` ThreadingModel 레지스트리에서 스레딩 모델을 설정 합니다. 무료 = 합니다.  
  
     두 플래그를 결합할 수 있습니다 `afxRegApartmentThreading` 및 `afxRegFreeThreading` ThreadingModel 설정할 = Both입니다. 참조 [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) 스레딩 모델 등록에 대 한 자세한 내용은 Windows sdk입니다.  
  
> [!NOTE]
>  MFC 4.2 이전 버전의 MFC에서는 `int` `nRegFlags` 매개 변수가 한 **BOOL** 매개 변수를 *bInsertable*를 허용 하는 되거나 개체 삽입 대화 상자에서 삽입할 제어를 허용 상자입니다.  
  
 *dwMiscStatus*  
 상태 플래그 중 하나 이상이 포함 됩니다 (플래그에 대 한 참조 **OLEMISC** Windows SDK에서 열거형):  
  
-   OLEMISC_RECOMPOSEONRESIZE  
  
-   OLEMISC_ONLYICONIC  
  
-   OLEMISC_INSERTNOTREPLACE  
  
-   OLEMISC_STATIC  
  
-   OLEMISC_CANTLINKINSIDE  
  
-   OLEMISC_CANLINKBYOLE1  
  
-   OLEMISC_ISLINKOBJECT  
  
-   OLEMISC_INSIDEOUT  
  
-   OLEMISC_ACTIVATEWHENVISIBLE  
  
-   OLEMISC_RENDERINGISDEVICEINDEPENDENT  
  
-   OLEMISC_INVISIBLEATRUNTIME  
  
-   OLEMISC_ALWAYSRUN  
  
-   OLEMISC_ACTSLIKEBUTTON  
  
-   OLEMISC_ACTSLIKELABEL  
  
-   OLEMISC_NOUIACTIVATE  
  
-   OLEMISC_ALIGNABLE  
  
-   OLEMISC_IMEMODE  
  
-   OLEMISC_SIMPLEFRAME  
  
-   OLEMISC_SETCLIENTSITEFIRST  
  
 *tlid*  
 컨트롤 클래스의 고유 ID입니다.  
  
 `wVerMajor`  
 컨트롤 클래스의 주 버전 번호입니다.  
  
 `wVerMinor`  
 컨트롤 클래스의 부 버전 번호입니다.  
  
### <a name="return-value"></a>반환 값  
 컨트롤 클래스 등록 되었습니다. 0이 아닌 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 이렇게 하면 컨트롤을 OLE 컨트롤을 인식 하는 컨테이너에서 사용할 수 있습니다. `AfxOleRegisterControlClass` 컨트롤의 이름 및 시스템의 위치에 레지스트리를 업데이트 하 고 또한 레지스트리에 컨트롤이 지 원하는 스레딩 모델을 설정 합니다. 자세한 내용은 참조 [기술 참고 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "아파트 모델 스레딩에서 OLE 컨트롤," 및 [에 대 한 프로세스 및 스레드](http://msdn.microsoft.com/library/windows/desktop/ms681917) Windows sdk에서입니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]  
  
 위의 예제에서는 어떻게 `AfxOleRegisterControlClass` 없음에 대 한 플래그를 사용 하 여 호출 되 아파트에 대 한 플래그 여섯 번째 매개 변수 조합 하는 ORed 모델 및:  
  
 [!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]  
  
 컨트롤이 활성화 된 컨테이너에 대 한 개체 삽입 대화 상자에 표시 됩니다 및 아파트 모델 인식 됩니다. 아파트 모델 인식 컨트롤 되므로 한 개의 아파트에서 컨트롤 정적 데이터에 액세스를 하는 동안 것 되지 사용 되지 않는 스케줄러에서 작업이 완료 되 고 동일한 클래스의 다른 인스턴스가 사용 하 여 시작 하기 전에 데이터를 보호 하 고 있는 잠금으로, 해당 정적 클래스를 확인 해야 합니다. 동일한 정적 데이터입니다. 정적 데이터에 대 한 모든 액세스는 임계 영역 코드로 묶어 됩니다.  
  
### <a name="requirements"></a>요구 사항  
  **헤더** afxctl.h  
  
##  <a name="afxoleregisterpropertypageclass"></a>  AfxOleRegisterPropertyPageClass  
 Windows 등록 데이터베이스 속성 페이지 클래스에 등록합니다.  
  
```  
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,  
   REFCLSID  clsid,  
   UINT idTypeName,  
   int nRegFlags); 
```  
  
### <a name="parameters"></a>매개 변수  
 `hInstance`  
 속성 페이지 클래스와 연관 된 모듈의 인스턴스 핸들입니다.  
  
 `clsid`  
 속성 페이지의 고유 클래스 ID입니다.  
  
 `idTypeName`  
 속성 페이지에 대 한 사용자가 읽을 수 있는 이름을 포함 하는 문자열의 리소스 ID입니다.  
  
 `nRegFlags`  
 플래그를 포함할 수 있습니다.  
  
- `afxRegApartmentThreading` ThreadingModel 레지스트리에서 설정 하는 스레딩 모델이 아파트 = 합니다.  
  
> [!NOTE]
>  MFC 4.2 이전 MFC 버전에는 `int` `nRegFlags` 매개 변수를 사용할 수 없습니다. 또한는 `afxRegInsertable` 플래그 속성 페이지에 대 한 올바른 옵션이 아닙니다와 설정 된 경우 MFC에서 어설션을 발생 합니다  
  
### <a name="return-value"></a>반환 값  
 컨트롤 클래스 등록 되었습니다. 0이 아닌 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 이렇게 하면 속성 페이지를 OLE 컨트롤을 인식 하는 컨테이너에서 사용할 수 있습니다. `AfxOleRegisterPropertyPageClass` 속성 페이지 이름 및 해당 시스템의 위치에 사용 하 여 레지스트리를 업데이트 하 고 또한 레지스트리에 컨트롤이 지 원하는 스레딩 모델을 설정 합니다. 자세한 내용은 참조 [기술 참고 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "아파트 모델 스레딩에서 OLE 컨트롤," 및 [에 대 한 프로세스 및 스레드](http://msdn.microsoft.com/library/windows/desktop/ms681917) Windows sdk에서입니다.  
  
### <a name="requirements"></a>요구 사항  
  **헤더** afxctl.h  
  
##  <a name="afxoleregistertypelib"></a>  AfxOleRegisterTypeLib  
 Windows 등록 데이터베이스에 형식 라이브러리를 등록하고 OLE 컨트롤을 인식하는 다른 컨테이너에서 형식 라이브러리를 사용할 수 있도록 허용합니다.  
  
```   
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,  
    REFGUID tlid,  
    LPCTSTR pszFileName = NULL,  
    LPCTSTR pszHelpDir  = NULL); 
```  
  
### <a name="parameters"></a>매개 변수  
 `hInstance`  
 형식 라이브러리와 연결된 응용 프로그램의 인스턴스 핸들입니다.  
  
 *tlid*  
 형식 라이브러리의 고유 ID입니다.  
  
 *pszFileName*  
 컨트롤에 대해 지역화된 형식 라이브러리(.TLB) 파일의 선택적인 파일 이름을 가리킵니다.  
  
 *pszHelpDir*  
 형식 라이브러리에 대한 도움말 파일을 찾을 수 있는 디렉터리의 이름입니다. 경우 **NULL**, 도움말 파일은 형식 라이브러리 자체와 동일한 디렉터리에 있는 것으로 간주 됩니다.  
  
### <a name="return-value"></a>반환 값  
 형식 라이브러리가 등록된 경우 0이 아닌 값이고, 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 이 함수는 시스템에서 레지스트리를 형식 라이브러리 이름 및 해당 위치로 업데이트합니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]  
  
 [!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]  
  
### <a name="requirements"></a>요구 사항  
  **헤더** afxdisp.h  
  
##  <a name="afxoleunregisterclass"></a>  AfxOleUnregisterClass  
 Windows 등록 데이터베이스에서 컨트롤이 나 속성 페이지 클래스 항목을 제거합니다.  
  
```   
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID); 
```  
  
### <a name="parameters"></a>매개 변수  
 *clsID*  
 컨트롤 또는 속성 페이지의 고유 클래스 ID입니다.  
  
 `pszProgID`  
 컨트롤 또는 속성 페이지의 고유 프로그램 ID입니다.  
  
### <a name="return-value"></a>반환 값  
 컨트롤이 나 속성 페이지 클래스; 성공적으로 등록 하지 않은 경우 0이 아닌 그렇지 않으면 0입니다.  
  
### <a name="requirements"></a>요구 사항  
  **헤더** afxctl.h  
  
##  <a name="afxoleunregistertypelib"></a>  AfxOleUnregisterTypeLib  
 Windows 등록 데이터베이스에서 형식 라이브러리 항목을 제거 하려면이 함수를 호출 합니다.  
  
```   
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID); 
```  
  
### <a name="parameters"></a>매개 변수  
 `tlID`  
 형식 라이브러리의 고유 ID입니다.  
  
### <a name="return-value"></a>반환 값  
 형식 라이브러리를 성공적으로 등록 된; 하지 않았으면 0이 아닌 그렇지 않으면 0입니다.  
  
### <a name="example"></a>예제  
 [!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]  

### <a name="requirements"></a>요구 사항  
  **헤더** afxdisp.h  

## <a name="see-also"></a>참고 항목  
 [매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
