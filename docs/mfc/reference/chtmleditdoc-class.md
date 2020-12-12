---
description: '자세히 알아보기: CHtmlEditDoc 클래스'
title: CHtmlEditDoc 클래스
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditDoc
- AFXHTML/CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::GetView
- AFXHTML/CHtmlEditDoc::IsModified
- AFXHTML/CHtmlEditDoc::OpenURL
helpviewer_keywords:
- CHtmlEditDoc [MFC], CHtmlEditDoc
- CHtmlEditDoc [MFC], GetView
- CHtmlEditDoc [MFC], IsModified
- CHtmlEditDoc [MFC], OpenURL
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
ms.openlocfilehash: 5fb8187ff7925efc5bdfa6a0079a8ec4b186ae63
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115315"
---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc 클래스

[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)를 사용 하면 MFC 문서 뷰 아키텍처 컨텍스트 내에서 WebBrowser 편집 플랫폼의 기능을 제공 합니다.

## <a name="syntax"></a>구문

```
class AFX_NOVTABLE CHtmlEditDoc : public CDocument
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CHtmlEditDoc::CHtmlEditDoc](#chtmleditdoc)|`CHtmlEditDoc` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CHtmlEditDoc:: GetView](#getview)|`CHtmlEditView`이 문서에 연결 된 개체를 검색 합니다.|
|[CHtmlEditDoc:: IsModified](#ismodified)|연결 된 뷰의 WebBrowser 컨트롤이 사용자에 의해 수정 된 문서를 포함 하는지 여부를 반환 합니다.|
|[CHtmlEditDoc:: OpenURL](#openurl)|URL을 엽니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>요구 사항

**헤더:** afxhtml.h

## <a name="chtmleditdocchtmleditdoc"></a><a name="chtmleditdoc"></a> CHtmlEditDoc::CHtmlEditDoc

`CHtmlEditDoc` 개체를 생성합니다.

```
CHtmlEditDoc();
```

## <a name="chtmleditdocgetview"></a><a name="getview"></a> CHtmlEditDoc:: GetView

이 문서에 연결 된 [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) 개체를 검색 합니다.

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>반환 값

문서 개체에 대 한 포인터를 반환 합니다 `CHtmlEditView` .

## <a name="chtmleditdocismodified"></a><a name="ismodified"></a> CHtmlEditDoc:: IsModified

연결 된 뷰의 WebBrowser 컨트롤이 사용자에 의해 수정 된 문서를 포함 하는지 여부를 반환 합니다.

```
virtual BOOL IsModified();
```

## <a name="chtmleditdocopenurl"></a><a name="openurl"></a> CHtmlEditDoc:: OpenURL

URL을 엽니다.

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>매개 변수

*lpszURL*<br/>
열려는 URL입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

## <a name="see-also"></a>참고 항목

[HTMLEdit 샘플](../../overview/visual-cpp-samples.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
