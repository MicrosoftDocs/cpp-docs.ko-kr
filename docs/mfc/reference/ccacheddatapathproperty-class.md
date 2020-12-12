---
description: '자세히 알아보기: CCachedDataPathProperty 클래스'
title: CCachedDataPathProperty 클래스
ms.date: 11/04/2016
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
ms.openlocfilehash: a61d2553afc4415da29399293843deb1be5f113d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122501"
---
# <a name="ccacheddatapathproperty-class"></a>CCachedDataPathProperty 클래스

비동기적으로 전송되고 메모리 파일에 캐싱되는 OLE 컨트롤 속성을 구현합니다.

## <a name="syntax"></a>구문

```
class CCachedDataPathProperty : public CDataPathProperty
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|`CCachedDataPathProperty` 개체를 생성합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CCachedDataPathProperty:: m_Cache](#m_cache)|`CMemFile` 데이터를 캐시할 개체입니다.|

## <a name="remarks"></a>설명

메모리 파일은 디스크가 아닌 RAM에 저장 되며 빠른 임시 전송에 유용 합니다.

및와 `CAysncMonikerFile` 함께 `CDataPathProperty` 에서는 `CCachedDataPathProperty` OLE 컨트롤에서 비동기 모니커를 사용 하는 기능을 제공 합니다. `CCachedDataPathProperty`개체를 사용 하면 URL 또는 파일 원본에서 데이터를 비동기적으로 전송 하 고 공용 변수를 통해 메모리 파일에 저장할 수 있습니다 `m_Cache` . 모든 데이터는 메모리 파일에 저장 되며, 알림을 감시 하 고 응답 하려는 경우가 아니면 [사용 가능한 Ondataavailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) 재정의할 필요가 없습니다. 예를 들어, 크게를 전송 하는 경우 GIF 파일은 더 많은 데이터가 도착 했음을 컨트롤에 알리고, 자신을 다시 그려야 합니다 .를 재정의 하 여 `OnDataAvailable` 알림을 만듭니다.

클래스는 `CCachedDataPathProperty` 에서 파생 됩니다 `CDataPathProperty` .

인터넷 응용 프로그램에서 비동기 모니커 및 ActiveX 컨트롤을 사용 하는 방법에 대 한 자세한 내용은 다음 항목을 참조 하세요.

- [인터넷 우선 단계: ActiveX 컨트롤](../../mfc/activex-controls-on-the-internet.md)

- [인터넷 우선 단계: 비동기 모니커](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)

`CCachedDataPathProperty`

## <a name="requirements"></a>요구 사항

**헤더:** afxctl

## <a name="ccacheddatapathpropertyccacheddatapathproperty"></a><a name="ccacheddatapathproperty"></a> CCachedDataPathProperty::CCachedDataPathProperty

`CCachedDataPathProperty` 개체를 생성합니다.

```
CCachedDataPathProperty(COleControl* pControl = NULL);

CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>매개 변수

*pControl*<br/>
이 개체와 연결 될 ActiveX 컨트롤 개체에 대 한 포인터 `CCachedDataPathProperty` 입니다.

*lpszPath*<br/>
절대 또는 상대 경로일 수 있는 경로는 속성의 실제 절대 위치를 참조 하는 비동기 모니커를 만드는 데 사용 됩니다. `CCachedDataPathProperty` 파일 이름이 아닌 Url을 사용 합니다. `CCachedDataPathProperty`파일에 대 한 개체를 원하는 경우 file://앞에 경로를 추가 합니다.

### <a name="remarks"></a>설명

`COleControl` *Pcontrol* 에서 가리키는 개체는 파생 클래스에서 파생 [](../../mfc/reference/cdatapathproperty-class.md#open) 되 고 검색에서 사용 됩니다. *Pcontrol* 이 NULL 인 경우에 사용 되는 컨트롤은 `Open` [setcontrol](../../mfc/reference/cdatapathproperty-class.md#setcontrol)을 사용 하 여 설정 해야 합니다. *LpszPath* 가 NULL 인 경우 경로를 통과 `Open` 하거나 [setpath](../../mfc/reference/cdatapathproperty-class.md#setpath)를 사용 하 여 설정할 수 있습니다.

## <a name="ccacheddatapathpropertym_cache"></a><a name="m_cache"></a> CCachedDataPathProperty:: m_Cache

데이터가 캐시 되는 메모리 파일의 클래스 이름을 포함 합니다.

```
CMemFile m_Cache;
```

### <a name="remarks"></a>설명

메모리 파일은 디스크가 아닌 RAM에 저장 됩니다.

## <a name="see-also"></a>참고 항목

[CDataPathProperty 클래스](../../mfc/reference/cdatapathproperty-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDataPathProperty 클래스](../../mfc/reference/cdatapathproperty-class.md)
