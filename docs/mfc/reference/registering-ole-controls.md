---
description: '자세한 정보: OLE 컨트롤 등록'
title: OLE 컨트롤 등록
ms.date: 11/04/2016
helpviewer_keywords:
- registering OLE controls
- OLE controls [MFC], registering
ms.assetid: 73c45b7f-7dbc-43f5-bd17-dd77c6acec72
ms.openlocfilehash: 2556d67e509f7c4217a726ed097bbb69788af7fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218929"
---
# <a name="registering-ole-controls"></a>OLE 컨트롤 등록

다른 ole 서버 개체와 같은 OLE 컨트롤은 다른 OLE 인식 응용 프로그램에서 액세스할 수 있습니다. 이렇게 하려면 컨트롤의 형식 라이브러리와 클래스를 등록 합니다.

다음 함수를 사용 하면 Windows 등록 데이터베이스에서 컨트롤의 클래스, 속성 페이지 및 형식 라이브러리를 추가 하 고 제거할 수 있습니다.

### <a name="registering-ole-controls"></a>OLE 컨트롤 등록

|Name|설명|
|-|-|
|[AfxOleRegisterControlClass](#afxoleregistercontrolclass)|등록 데이터베이스에 컨트롤의 클래스를 추가 합니다.|
|[AfxOleRegisterPropertyPageClass](#afxoleregisterpropertypageclass)|등록 데이터베이스에 컨트롤 속성 페이지를 추가 합니다.|
|[AfxOleRegisterTypeLib](#afxoleregistertypelib)|컨트롤의 형식 라이브러리를 등록 데이터베이스에 추가 합니다.|
|[AfxOleUnregisterClass](#afxoleunregisterclass)|등록 데이터베이스에서 컨트롤 클래스 또는 속성 페이지 클래스를 제거 합니다.|
|[AfxOleUnregisterTypeLib](#afxoleunregistertypelib)|등록 데이터베이스에서 컨트롤의 형식 라이브러리를 제거 합니다.|

`AfxOleRegisterTypeLib` 는 일반적으로 컨트롤 DLL의 구현에서 호출 됩니다 `DllRegisterServer` . 마찬가지로 `AfxOleUnregisterTypeLib` 는에 의해 호출 됩니다 `DllUnregisterServer` . `AfxOleRegisterControlClass`, `AfxOleRegisterPropertyPageClass` 및 `AfxOleUnregisterClass` 는 일반적으로 `UpdateRegistry` 컨트롤의 클래스 팩터리 또는 속성 페이지의 멤버 함수에 의해 호출 됩니다.

## <a name="afxoleregistercontrolclass"></a><a name="afxoleregistercontrolclass"></a> AfxOleRegisterControlClass

Windows 등록 데이터베이스에 컨트롤 클래스를 등록 합니다.

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

*hInstance*<br/>
컨트롤 클래스와 연결 된 모듈의 인스턴스 핸들입니다.

*가*<br/>
컨트롤의 고유 클래스 ID입니다.

*pszProgID*<br/>
컨트롤의 고유 프로그램 ID입니다.

*idTypeName*<br/>
컨트롤에 대해 사용자가 읽을 수 있는 형식 이름을 포함 하는 문자열의 리소스 ID입니다.

*idBitmap*<br/>
도구 모음이 나 색상표에서 OLE 컨트롤을 나타내는 데 사용 되는 비트맵의 리소스 ID입니다.

*nRegFlags*<br/>
다음 플래그 중 하나 이상을 포함 합니다.

- `afxRegInsertable` OLE 개체에 대 한 개체 삽입 대화 상자에 컨트롤을 표시할 수 있습니다.

- `afxRegApartmentThreading` 레지스트리의 스레딩 모델을 ThreadingModel = 아파트로 설정 합니다.

- `afxRegFreeThreading` 레지스트리의 스레딩 모델을 ThreadingModel = Free로 설정 합니다.

   두 플래그를 결합 하 `afxRegApartmentThreading` 고 `afxRegFreeThreading` ThreadingModel =를 설정할 수 있습니다. 스레딩 모델 등록에 대 한 자세한 내용은 Windows SDK의 [InprocServer32](/windows/win32/com/inprocserver32) 를 참조 하세요.

> [!NOTE]
> MFC 4.2 이전 MFC 버전에서 **`int`** *nregflags* 매개 변수는 개체 삽입 대화 상자에서 삽입할 컨트롤을 허용 하거나 허용 하지 않는 부울 매개 변수 *binsertable* 입니다.

*dwMiscStatus*<br/>
다음 상태 플래그 중 하나 이상을 포함 합니다. 플래그에 대 한 설명은 Windows SDK에서 OLEMISC 열거를 참조 하세요.

- OLEMISC_RECOMPOSEONRESIZE

- OLEMISC_ONLYICONIC

- OLEMISC_INSERTNOTREPLACE

- OLEMISC_STATIC

- OLEMISC_CANTLINKINSIDE

- OLEMISC_CANLINKBYOLE1

- OLEMISC_ISLINKOBJECT

- OLEMISC_INSIDEOUT

- OLEMISC_ACTIVATEWHENVISIBLE

- OLEMISC_RENDERINGISDEVICEINDEPENDENT

- OLEMISC_INVISIBLEATRUNTIME

- OLEMISC_ALWAYSRUN

- OLEMISC_ACTSLIKEBUTTON

- OLEMISC_ACTSLIKELABEL

- OLEMISC_NOUIACTIVATE

- OLEMISC_ALIGNABLE

- OLEMISC_IMEMODE

- OLEMISC_SIMPLEFRAME

- OLEMISC_SETCLIENTSITEFIRST

*tlid*<br/>
컨트롤 클래스의 고유 ID입니다.

*wVerMajor*<br/>
컨트롤 클래스의 주 버전 번호입니다.

*wVerMinor*<br/>
컨트롤 클래스의 부 버전 번호입니다.

### <a name="return-value"></a>반환 값

컨트롤 클래스가 등록 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이렇게 하면 OLE 컨트롤을 인식 하는 컨테이너에서 컨트롤을 사용할 수 있습니다. `AfxOleRegisterControlClass` 시스템의 컨트롤 이름과 위치를 사용 하 여 레지스트리를 업데이트 하 고 레지스트리에서 컨트롤에서 지 원하는 스레딩 모델도 설정 합니다. 자세한 내용은 [기술 참고 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "OLE 컨트롤의 아파트 모델 스레딩" 및 Windows SDK의 [프로세스 및 스레드 정보](/windows/win32/ProcThread/about-processes-and-threads) 를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCAxCtl#11](../../mfc/reference/codesnippet/cpp/registering-ole-controls_1.cpp)]

위의 예제에서는를 사용 하 여를 호출 하는 방법을 보여 줍니다 .이 플래그를 사용 하 여 ORed의 플래그를 사용 하 여 `AfxOleRegisterControlClass` 여섯 번째 매개 변수를 만듭니다.

[!code-cpp[NVC_MFCAxCtl#12](../../mfc/reference/codesnippet/cpp/registering-ole-controls_2.cpp)]

컨트롤은 활성화 된 컨테이너에 대 한 개체 삽입 대화 상자에 표시 되 고, 아파트 모델을 인식 합니다. 아파트 모델 인식 컨트롤은 정적 클래스 데이터를 잠금으로 보호 해야 하므로 한 아파트의 컨트롤이 정적 데이터에 액세스 하는 동안에는 스케줄러가 활성화 되지 않고, 동일한 클래스의 다른 인스턴스가 동일한 정적 데이터를 사용 하 여 시작 되도록 해야 합니다. 정적 데이터에 대 한 모든 액세스는 임계 영역 코드로 둘러싸여 있습니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl

## <a name="afxoleregisterpropertypageclass"></a><a name="afxoleregisterpropertypageclass"></a> AfxOleRegisterPropertyPageClass

Windows 등록 데이터베이스에 속성 페이지 클래스를 등록 합니다.

```
BOOL AFXAPI AfxOleRegisterPropertyPageClass(
   HINSTANCE hInstance,
   REFCLSID  clsid,
   UINT idTypeName,
   int nRegFlags);
```

### <a name="parameters"></a>매개 변수

*hInstance*<br/>
속성 페이지 클래스와 연결 된 모듈의 인스턴스 핸들입니다.

*가*<br/>
속성 페이지의 고유 클래스 ID입니다.

*idTypeName*<br/>
속성 페이지에 대해 사용자가 읽을 수 있는 이름을 포함 하는 문자열의 리소스 ID입니다.

*nRegFlags*<br/>
플래그를 포함할 수 있습니다.

- `afxRegApartmentThreading` 레지스트리의 스레딩 모델을 ThreadingModel = 아파트로 설정 합니다.

> [!NOTE]
> MFC 4.2 이전 MFC 버전에서 **`int`** *nregflags* 매개 변수를 사용할 수 없습니다. 또한 `afxRegInsertable` 플래그는 속성 페이지에 대 한 올바른 옵션이 아니므로 MFC에서 어설션이 설정 된 경우이를 발생 시킵니다.

### <a name="return-value"></a>반환 값

컨트롤 클래스가 등록 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이렇게 하면 OLE 컨트롤을 인식 하는 컨테이너에서 속성 페이지를 사용할 수 있습니다. `AfxOleRegisterPropertyPageClass` 레지스트리를 시스템의 속성 페이지 이름 및 해당 위치로 업데이트 하 고, 레지스트리에서 컨트롤에서 지 원하는 스레딩 모델도 설정 합니다. 자세한 내용은 [기술 참고 64](../../mfc/tn064-apartment-model-threading-in-activex-controls.md), "OLE 컨트롤의 아파트 모델 스레딩" 및 Windows SDK의 [프로세스 및 스레드 정보](/windows/win32/ProcThread/about-processes-and-threads) 를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl

## <a name="afxoleregistertypelib"></a><a name="afxoleregistertypelib"></a> AfxOleRegisterTypeLib

Windows 등록 데이터베이스에 형식 라이브러리를 등록하고 OLE 컨트롤을 인식하는 다른 컨테이너에서 형식 라이브러리를 사용할 수 있도록 허용합니다.

```
BOOL AfxOleRegisterTypeLib(
    HINSTANCE hInstance,
    REFGUID tlid,
    LPCTSTR pszFileName = NULL,
    LPCTSTR pszHelpDir  = NULL);
```

### <a name="parameters"></a>매개 변수

*hInstance*<br/>
형식 라이브러리와 연결된 애플리케이션의 인스턴스 핸들입니다.

*tlid*<br/>
형식 라이브러리의 고유 ID입니다.

*pszFileName*<br/>
컨트롤에 대해 지역화된 형식 라이브러리(.TLB) 파일의 선택적인 파일 이름을 가리킵니다.

*pszHelpDir*<br/>
형식 라이브러리에 대한 도움말 파일을 찾을 수 있는 디렉터리의 이름입니다. NULL인 경우, 도움말 파일은 해당 형식 라이브러리 자체와 동일한 디렉터리에 있는 것으로 간주됩니다.

### <a name="return-value"></a>반환 값

형식 라이브러리가 등록된 경우 0이 아닌 값이고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 시스템에서 레지스트리를 형식 라이브러리 이름 및 해당 위치로 업데이트합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCAutomation#7](../../mfc/codesnippet/cpp/registering-ole-controls_3.cpp)]

[!code-cpp[NVC_MFCAutomation#8](../../mfc/codesnippet/cpp/registering-ole-controls_4.cpp)]

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="afxoleunregisterclass"></a><a name="afxoleunregisterclass"></a> AfxOleUnregisterClass

Windows 등록 데이터베이스에서 컨트롤 또는 속성 페이지 클래스 항목을 제거 합니다.

```
BOOL AFXAPI AfxOleUnregisterClass(REFCLSID clsID, LPCSTR pszProgID);
```

### <a name="parameters"></a>매개 변수

*가*<br/>
컨트롤 또는 속성 페이지의 고유 클래스 ID입니다.

*pszProgID*<br/>
컨트롤 또는 속성 페이지의 고유한 프로그램 ID입니다.

### <a name="return-value"></a>반환 값

컨트롤 또는 속성 페이지 클래스가 성공적으로 등록 취소 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl

## <a name="afxoleunregistertypelib"></a><a name="afxoleunregistertypelib"></a> AfxOleUnregisterTypeLib

Windows 등록 데이터베이스에서 형식 라이브러리 항목을 제거 하려면이 함수를 호출 합니다.

```
BOOL AFXAPI AfxOleUnregisterTypeLib(REFGUID tlID);
```

### <a name="parameters"></a>매개 변수

*tlID*<br/>
형식 라이브러리의 고유 ID입니다.

### <a name="return-value"></a>반환 값

형식 라이브러리가 성공적으로 등록 취소 된 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCAxCtl#13](../../mfc/reference/codesnippet/cpp/registering-ole-controls_5.cpp)]

### <a name="requirements"></a>요구 사항

  **헤더** afxdisp.h

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
