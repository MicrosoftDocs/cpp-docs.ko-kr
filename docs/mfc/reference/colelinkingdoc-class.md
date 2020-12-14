---
description: '자세히 알아보기: COleLinkingDoc 클래스'
title: COleLinkingDoc 클래스
ms.date: 11/04/2016
f1_keywords:
- COleLinkingDoc
- AFXOLE/COleLinkingDoc
- AFXOLE/COleLinkingDoc::COleLinkingDoc
- AFXOLE/COleLinkingDoc::Register
- AFXOLE/COleLinkingDoc::Revoke
- AFXOLE/COleLinkingDoc::OnFindEmbeddedItem
- AFXOLE/COleLinkingDoc::OnGetLinkedItem
helpviewer_keywords:
- COleLinkingDoc [MFC], COleLinkingDoc
- COleLinkingDoc [MFC], Register
- COleLinkingDoc [MFC], Revoke
- COleLinkingDoc [MFC], OnFindEmbeddedItem
- COleLinkingDoc [MFC], OnGetLinkedItem
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
ms.openlocfilehash: 10cf9bb81c4cbbd324b95a13dc2fa44548266583
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226911"
---
# <a name="colelinkingdoc-class"></a>COleLinkingDoc 클래스

포함된 항목에 대한 연결을 지원하는 OLE 컨테이너 문서의 기본 클래스입니다.

## <a name="syntax"></a>구문

```
class COleLinkingDoc : public COleDocument
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleLinkingDoc::COleLinkingDoc](#colelinkingdoc)|`COleLinkingDoc` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleLinkingDoc:: Register](#register)|OLE 시스템 Dll을 사용 하 여 문서를 등록 합니다.|
|[COleLinkingDoc:: Revoke](#revoke)|문서의 등록을 취소 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|지정 된 포함 항목을 찾습니다.|
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|지정 된 연결 된 항목을 찾습니다.|

## <a name="remarks"></a>설명

포함 된 항목에 대 한 링크를 지 원하는 컨테이너 응용 프로그램을 "링크 컨테이너" 라고 합니다. [OCLIENT](../../overview/visual-cpp-samples.md) 샘플 응용 프로그램은 링크 컨테이너의 한 예입니다.

연결 된 항목의 소스가 다른 문서에 포함 된 항목인 경우 포함 된 항목을 편집 하려면 문서를 포함 하는 문서를 로드 해야 합니다. 따라서 사용자가 연결 된 항목의 소스를 편집 하려는 경우 다른 컨테이너 응용 프로그램에서 링크 컨테이너를 시작할 수 있어야 합니다. 응용 프로그램은 프로그래밍 방식으로 시작 될 때 문서를 만들 수 있도록 [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) 클래스도 사용 해야 합니다.

컨테이너를 링크 컨테이너로 설정 하려면 `COleLinkingDoc` [coledocument](../../mfc/reference/coledocument-class.md)대신에서 문서 클래스를 파생 시킵니다. 다른 OLE 컨테이너와 마찬가지로 응용 프로그램의 네이티브 데이터 및 포함 되거나 연결 된 항목을 저장 하는 클래스를 디자인 해야 합니다. 또한 네이티브 데이터를 저장 하기 위한 데이터 구조를 디자인 해야 합니다. `CDocItem`응용 프로그램의 네이티브 데이터에 대해 파생 클래스를 정의 하는 경우에 정의 된 인터페이스를 사용 `COleDocument` 하 여 기본 데이터 및 OLE 데이터를 저장할 수 있습니다.

응용 프로그램을 다른 컨테이너에서 프로그래밍 방식으로 시작할 수 있도록 하려면 `COleTemplateServer` 개체를 응용 프로그램 파생 클래스의 멤버로 선언 합니다 `CWinApp` .

[!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]

`InitInstance`파생 클래스의 멤버 함수에서 `CWinApp` 문서 템플릿을 만들고 `COleLinkingDoc` 파생 클래스를 document 클래스로 지정 합니다.

[!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]

`COleTemplateServer`개체의 멤버 함수를 호출 하 여 개체를 문서 템플릿에 연결 `ConnectTemplate` 하 고 다음을 호출 하 여 모든 클래스 개체를 OLE 시스템에 등록 합니다 `COleTemplateServer::RegisterAll` .

[!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]

샘플 `CWinApp` 파생 클래스 정의 및 `InitInstance` 함수는 OCLIENT를 참조 하세요. H 및 OCLIENT. MFC 샘플 [OCLIENT](../../overview/visual-cpp-samples.md)의 CPP

사용에 대 한 자세한 내용은 컨테이너 `COleLinkingDoc` [: 컨테이너](../../mfc/containers-implementing-a-container.md) 및 컨테이너 구현 [: 고급 기능](../../mfc/containers-advanced-features.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

`COleLinkingDoc`

## <a name="requirements"></a>요구 사항

**헤더:** afxole

## <a name="colelinkingdoccolelinkingdoc"></a><a name="colelinkingdoc"></a> COleLinkingDoc::COleLinkingDoc

`COleLinkingDoc`OLE 시스템 dll과의 통신을 시작 하지 않고 개체를 생성 합니다.

```
COleLinkingDoc();
```

### <a name="remarks"></a>설명

멤버 함수를 호출 `Register` 하 여 문서가 열려 있음을 OLE에 알려야 합니다.

## <a name="colelinkingdoconfindembeddeditem"></a><a name="onfindembeddeditem"></a> COleLinkingDoc::OnFindEmbeddedItem

지정 된 이름을 가진 포함 된 OLE 항목이 문서에 포함 되어 있는지 여부를 확인 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>매개 변수

*lpszItemName*<br/>
요청 된 포함 된 OLE 항목의 이름에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

지정 된 항목에 대 한 포인터입니다. 항목을 찾을 수 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

기본 구현에서는 포함 된 항목 목록을 검색 하 여 지정 된 이름의 항목을 검색 합니다. 이름 비교는 대/소문자를 구분 합니다. 포함 된 OLE 항목을 저장 하거나 이름을 지정 하는 고유한 메서드가 있는 경우이 함수를 재정의 합니다.

## <a name="colelinkingdocongetlinkeditem"></a><a name="ongetlinkeditem"></a> COleLinkingDoc::OnGetLinkedItem

문서에 지정 된 이름을 가진 연결 된 서버 항목이 포함 되어 있는지 여부를 확인 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>매개 변수

*lpszItemName*<br/>
요청 된 OLE 항목의 이름에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

지정 된 항목에 대 한 포인터입니다. 항목을 찾을 수 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

기본 `COleLinkingDoc` 구현에서는 항상 NULL을 반환 합니다. 이 함수는 파생 클래스에서 재정의 되어 `COleServerDoc` 지정 된 이름의 연결 된 항목에 대 한 OLE 서버 항목 목록을 검색 합니다. 이름 비교는 대/소문자를 구분 합니다. 연결 된 서버 항목을 저장 하거나 검색 하는 사용자 고유의 메서드를 구현한 경우이 함수를 재정의 합니다.

## <a name="colelinkingdocregister"></a><a name="register"></a> COleLinkingDoc:: Register

OLE 시스템 Dll에 문서가 열려 있음을 알립니다.

```
BOOL Register(
    COleObjectFactory* pFactory,
    LPCTSTR lpszPathName);
```

### <a name="parameters"></a>매개 변수

*pFactory*<br/>
OLE 팩터리 개체에 대 한 포인터입니다 (NULL 일 수 있음).

*lpszPathName*<br/>
컨테이너 문서의 정규화 된 경로에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

문서가 성공적으로 등록 되 면 0이 아닌 것입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

OLE 시스템 Dll을 사용 하 여 문서를 등록 하기 위해 명명 된 파일을 만들거나 열 때이 함수를 호출 합니다. 문서가 포함 된 항목을 나타내는 경우에는이 함수를 호출할 필요가 없습니다.

응용 프로그램에서를 사용 하는 경우, `COleTemplateServer` `Register` `COleLinkingDoc` 및의 구현을 통해가 호출 됩니다 `OnNewDocument` `OnOpenDocument` `OnSaveDocument` .

## <a name="colelinkingdocrevoke"></a><a name="revoke"></a> COleLinkingDoc:: Revoke

OLE 시스템 Dll에 문서가 더 이상 열려 있지 않음을 알립니다.

```cpp
void Revoke();
```

### <a name="remarks"></a>설명

OLE 시스템 Dll을 사용 하 여 문서의 등록을 취소 하려면이 함수를 호출 합니다.

명명 된 파일을 닫을 때이 함수를 호출 해야 하지만 일반적으로 직접 호출할 필요는 없습니다. `Revoke` 는 `COleLinkingDoc` ,, 및의 구현에 의해 호출 됩니다 `OnCloseDocument` `OnNewDocument` `OnOpenDocument` `OnSaveDocument` .

## <a name="see-also"></a>참고 항목

[MFC 샘플 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDocument 클래스](../../mfc/reference/coledocument-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate 클래스](../../mfc/reference/cdoctemplate-class.md)
