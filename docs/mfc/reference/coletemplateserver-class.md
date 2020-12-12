---
description: '자세히 알아보기: COleTemplateServer 클래스'
title: COleTemplateServer 클래스
ms.date: 11/04/2016
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
helpviewer_keywords:
- COleTemplateServer [MFC], COleTemplateServer
- COleTemplateServer [MFC], ConnectTemplate
- COleTemplateServer [MFC], Unregister
- COleTemplateServer [MFC], UpdateRegistry
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
ms.openlocfilehash: da4351730fe548c83e073d3f6eaa02bc0c88cd0d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226625"
---
# <a name="coletemplateserver-class"></a>COleTemplateServer 클래스

OLE 비주얼 편집 서버, 자동화 서버 및 링크 컨테이너(포함에 대한 링크를 지원하는 애플리케이션)에 사용합니다.

## <a name="syntax"></a>구문

```
class COleTemplateServer : public COleObjectFactory
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleTemplateServer:: COleTemplateServer](#coletemplateserver)|`COleTemplateServer` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleTemplateServer:: ConnectTemplate](#connecttemplate)|문서 템플릿을 기본 개체에 연결 `COleObjectFactory` 합니다.|
|[COleTemplateServer:: 등록 취소](#unregister)|연결 된 문서 템플릿의 등록을 취소 합니다.|
|[COleTemplateServer:: UpdateRegistry](#updateregistry)|문서 유형을 OLE 시스템 레지스트리에 등록 합니다.|

## <a name="remarks"></a>설명

이 클래스는 [Coleobjectfactory](../../mfc/reference/coleobjectfactory-class.md)클래스에서 파생 됩니다. 일반적으로 `COleTemplateServer` 고유한 클래스를 파생 하지 않고 직접를 사용할 수 있습니다. `COleTemplateServer`[Cdoctemplate](../../mfc/reference/cdoctemplate-class.md) 개체를 사용 하 여 서버 문서를 관리 합니다. `COleTemplateServer`전체 서버, 즉 독립 실행형 응용 프로그램으로 실행할 수 있는 서버를 구현할 때 사용 합니다. 전체 서버는 일반적으로 SDI (단일 문서 인터페이스) 응용 프로그램이 지원 되기는 하지만 MDI (다중 문서 인터페이스) 응용 프로그램입니다. `COleTemplateServer`응용 프로그램에서 지 원하는 각 서버 문서 유형에 하나의 개체가 필요 합니다. 즉, 서버 응용 프로그램이 워크시트와 차트를 모두 지 원하는 경우에는 두 개의 `COleTemplateServer` 개체가 있어야 합니다.

`COleTemplateServer``OnCreateInstance`로 정의 된 멤버 함수를 재정의 `COleObjectFactory` 합니다. 이 멤버 함수는 적절 한 형식의 c + + 개체를 만들기 위해 프레임 워크에서 호출 됩니다.

서버에 대 한 자세한 내용은 서버 [: 서버 구현](../../mfc/servers-implementing-a-server.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="coletemplateservercoletemplateserver"></a><a name="coletemplateserver"></a> COleTemplateServer:: COleTemplateServer

`COleTemplateServer` 개체를 생성합니다.

```
COleTemplateServer();
```

### <a name="remarks"></a>설명

클래스 사용에 대 한 간략 한 설명은 `COleTemplateServer` [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md) 클래스 개요를 참조 하세요.

## <a name="coletemplateserverconnecttemplate"></a><a name="connecttemplate"></a> COleTemplateServer:: ConnectTemplate

*Pdoctemplate* 이 가리키는 문서 템플릿을 기본 [Coleobjectfactory](../../mfc/reference/coleobjectfactory-class.md) 개체에 연결 합니다.

```cpp
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>매개 변수

*가*<br/>
템플릿이 요청 하는 OLE 클래스 ID에 대 한 참조입니다.

*pDocTemplate*<br/>
문서 템플릿에 대 한 포인터입니다.

*bMultiInstance*<br/>
응용 프로그램의 단일 인스턴스에서 여러 인스턴스화를 지원할 수 있는지 여부를 나타냅니다. TRUE 이면 각 요청에 대해 개체를 만들기 위해 응용 프로그램의 여러 인스턴스가 시작 됩니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK의 [CLSID 키](/windows/win32/com/clsid-key-hklm) 를 참조 하세요.

## <a name="coletemplateserverunregister"></a><a name="unregister"></a> COleTemplateServer:: 등록 취소

연결 된 문서 템플릿의 등록을 취소 합니다.

```
BOOL Unregister();
```

### <a name="return-value"></a>반환 값

성공하면 TRUE이고, 실패하면 FALSE입니다.

### <a name="remarks"></a>설명

설명

## <a name="coletemplateserverupdateregistry"></a><a name="updateregistry"></a> COleTemplateServer:: UpdateRegistry

문서 템플릿 문자열에서 파일 형식 정보를 로드 하 고 해당 정보를 OLE 시스템 레지스트리에 저장 합니다.

```cpp
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>매개 변수

*nAppType*<br/>
AFXDISP.H에 정의 된 OLE_APPTYPE 열거형의 값입니다. 다음 값 중 하나를 사용할 수 있습니다.

- OAT_INPLACE_SERVER 서버에는 전체 서버 사용자 인터페이스가 있습니다.

- OAT_SERVER 서버는 포함만 지원 합니다.

- OAT_CONTAINER 컨테이너는 포함 된 개체에 대 한 링크를 지원 합니다.

- OAT_DISPATCH_OBJECT 개체를 사용할 `IDispatch` 수 있습니다.

- OAT_DOC_OBJECT_SERVER Server는 포함 및 문서 개체 구성 요소 모델을 모두 지원 합니다.

*rglpszRegister*<br/>
항목이 없는 경우에만 레지스트리에 기록 되는 항목 목록입니다.

*rglpszOverwrite*<br/>
이전 항목이 존재 하는지 여부에 관계 없이 레지스트리에 기록 되는 항목의 목록입니다.

*bRegister*<br/>
클래스가 등록 되는지 여부를 결정 합니다. *BRegister* 가 TRUE 이면 클래스가 시스템 레지스트리에 등록 됩니다. 그렇지 않으면 클래스의 등록을 취소 합니다.

### <a name="remarks"></a>설명

등록 정보는 [Cdoctemplate:: GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)에 대 한 호출을 통해 로드 됩니다. 검색 된 부분 문자열은 `regFileTypeId` `regFileTypeName` 참조 페이지에 설명 된 대로 인덱스, 및로 식별 되는 부분 문자열 `fileNewName` `GetDocString` 입니다.

`regFileTypeId`부분 문자열이 비어 있거나에 `GetDocString` 대 한 호출이 다른 이유로 인해 실패 하는 경우이 함수는 실패 하 고 파일 정보가 레지스트리에 입력 되지 않습니다.

*RglpszRegister* 및 *rglpszOverwrite* 인수의 정보는 [AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass)에 대 한 호출을 통해 레지스트리에 기록 됩니다. 두 인수가 NULL 일 때 등록 되는 기본 정보는 대부분의 응용 프로그램에 적합 합니다. 이러한 인수의 정보 구조에 대 한 자세한 내용은을 참조 하십시오 `AfxOleRegisterServerClass` .

자세한 내용은 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)을 참조하십시오.

## <a name="see-also"></a>참고 항목

[MFC 샘플 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleObjectFactory 클래스](../../mfc/reference/coleobjectfactory-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc 클래스](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleServerItem 클래스](../../mfc/reference/coleserveritem-class.md)
