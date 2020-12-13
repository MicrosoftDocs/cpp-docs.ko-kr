---
description: '자세한 정보: 액티브 문서'
title: 액티브 문서
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC]
- active documents [MFC], requirements
- view objects [MFC], requirements
- OLE [MFC], active documents
- views [MFC], active documents
- active documents [MFC], views
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
ms.openlocfilehash: cae0eda775670867d5e36b4f2b9ec895a5dc3eb7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150308"
---
# <a name="active-documents"></a>액티브 문서

액티브 문서는 OLE의 복합 문서 기술을 확장합니다. 이러한 확장은 보기를 관리하는 추가 인터페이스의 형태로 제공되므로, 개체가 컨테이너 내에서 작동하면서 해당 표시 및 인쇄 기능에 대한 제어를 계속 유지할 수 있습니다. 이 프로세스는 외부 프레임(예: Microsoft Office Binder 또는 Microsoft Internet Explorer) 및 고유 프레임(예: 제품의 고유 보기 포트)에서 문서를 표시할 수 있게 해줍니다.

이 섹션에서는 [액티브 문서의 기능 요구 사항](#requirements_for_active_documents)에 대해 설명 합니다. 액티브 문서는 데이터 세트을 소유하고 데이터를 저장 및 검색할 수 있는 스토리지에 대한 액세스 권한을 갖습니다. 액티브 문서는 해당 데이터에 대해 하나 이상의 보기를 만들고 관리할 수 있습니다. OLE 문서에 대해 일반적인 포함 및 현재 위치 활성화 인터페이스를 지원하는 것 외에도, 액티브 문서는 해당 기능을 통신하여 `IOleDocument`를 통해 보기를 만듭니다. 이 인터페이스를 통해 컨테이너는 액티브 문서가 표시할 수 있는 보기를 만들도록(그리고 가능한 경우 열거하도록) 요청할 수 있습니다. 이 인터페이스를 통해 액티브 문서는 다중 뷰 또는 복합 사각형 지원 여부와 같은 자체에 대한 여러 정보도 제공할 수 있습니다.

인터페이스는 다음과 같습니다 `IOleDocument` . `IEnumOleDocumentViews`인터페이스는 형식에 대 한 표준 OLE 열거자입니다 `IOleDocumentView*` .

```
interface IOleDocument : IUnknown
    {
    HRESULT CreateView(
        [in] IOleInPlaceSite *pIPSite,
        [in] IStream *pstm,
        [in] DWORD dwReserved,
        [out] IOleDocumentView **ppView);

    HRESULT GetDocMiscStatus([out] DWORD *pdwStatus);

    HRESULT EnumViews(
        [out] IEnumOleDocumentViews **ppEnum,
        [out] IOleDocumentView **ppView);
    }
```

모든 액티브 문서는 이 인터페이스를 지원하는 보기 프레임 공급자가 있어야 합니다. 문서가 컨테이너 내에 포함되어 있지 않으면 액티브 문서 서버 자체에서 보기 프레임을 제공해야 합니다. 하지만 액티브 문서가 액티브 문서 컨테이너에 포함되어 있으면 컨테이너가 보기 프레임을 제공합니다.

활성 문서에서는 표준, 개요, 페이지 레이아웃 등의 데이터 [보기](#requirements_for_view_objects) 유형을 하나 이상 만들 수 있습니다. 보기는 데이터를 볼 수 있는 필터처럼 작동합니다. 문서에 뷰 형식이 하나만 있는 경우에도 새 창 기능 (예: Office 응용 프로그램의 **창** 메뉴에 있는 **새 창** 항목)을 지원 하기 위해 여러 뷰를 지원할 수 있습니다.

## <a name="requirements-for-active-documents"></a><a name="requirements_for_active_documents"></a> 활성 문서에 대 한 요구 사항

액티브 문서 컨테이너에 표시할 수 있는 액티브 문서의 요구 사항은 다음과 같습니다.

- `IPersistStorage`를 구현하여 OLE의 복합 파일을 스토리지 메커니즘으로 사용해야 합니다.

- **파일에서 만들기** 를 포함 하 여 OLE 문서의 기본 포함 기능을 지원 합니다. 이를 위해서는 `IPersistFile`, `IOleObject` 및 `IDataObject` 인터페이스가 필요합니다.

- 현재 위치 활성화가 가능한 하나 이상의 보기를 지원해야 합니다. 즉, 뷰는 인터페이스 뿐만 아니라 인터페이스 `IOleDocumentView` `IOleInPlaceObject` 및 `IOleInPlaceActiveObject` (컨테이너의 및 인터페이스를 사용 하 여 `IOleInPlaceSite` `IOleInPlaceFrame` )를 지원 해야 합니다.

- 표준 액티브 문서 인터페이스 `IOleDocument`, `IOleCommandTarget` 및 `IPrint`를 지원해야 합니다.

컨테이너 쪽 인터페이스를 사용하는 경우 및 방법에 대한 지식은 이러한 요구 사항에 암시적으로 포함됩니다.

## <a name="requirements-for-view-objects"></a><a name="requirements_for_view_objects"></a> 뷰 개체에 대 한 요구 사항

액티브 문서는 해당 데이터에 대해 하나 이상의 보기를 만들 수 있습니다. 기능적으로 이러한 보기는 데이터를 표시하기 위해 특정 메서드로 가는 포트와 비슷합니다. 액티브 문서가 단일 보기만 지원하는 경우 액티브 문서 및 해당 단일 보기는 단일 클래스를 사용해서 구현할 수 있습니다. `IOleDocument::CreateView` 동일한 개체의 인터페이스 포인터를 반환 합니다 `IOleDocumentView` .

액티브 문서 컨테이너 내에 표시 되려면 뷰 구성 요소는 다음을 지원 해야 합니다 `IOleInPlaceObject` `IOleInPlaceActiveObject` `IOleDocumentView` .

```
interface IOleDocumentView : IUnknown
    {
    HRESULT SetInPlaceSite([in] IOleInPlaceSite *pIPSite);
    HRESULT GetInPlaceSite([out] IOleInPlaceSite **ppIPSite);
    HRESULT GetDocument([out] IUnknown **ppunk);
    [input_sync] HRESULT SetRect([in] LPRECT prcView);
    HRESULT GetRect([in] LPRECT prcView);
    [input_sync] HRESULT SetRectComplex(
        [in] LPRECT prcView,
        [in] LPRECT prcHScroll,
        [in] LPRECT prcVScroll,
        [in] LPRECT prcSizeBox);
    HRESULT Show([in] BOOL fShow);
    HRESULT UIActivate([in] BOOL fUIActivate);
    HRESULT Open(void);
    HRESULT CloseView([in] DWORD dwReserved);
    HRESULT SaveViewState([in] IStream *pstm);
    HRESULT ApplyViewState([in] IStream *pstm);
    HRESULT Clone(
        [in] IOleInPlaceSite *pIPSiteNew,
        [out] IOleDocumentView **ppViewNew);
    }
```

모든 보기에는 보기 프레임 및 보기 포트(HWND 및 해당 창의 사각형 영역)를 캡슐화하는 연관된 보기 사이트가 포함됩니다. 사이트는 표준 인터페이스를 통해이 기능을 노출 합니다 `IOleInPlaceSite` . 단일 HWND에서는 두 개 이상의 보기 포트를 가질 수 있습니다.

일반적을 각 보기 유형에는 서로 다른 인쇄된 표현이 포함됩니다. 따라서 보기 및 해당 보기 사이트는 인쇄 인터페이스 `IPrint` 및 `IContinueCallback`을 각각 구현해야 합니다. 뷰 프레임은 인쇄를 시작할 때를 통해 뷰 공급자와 협상 해야 `IPrint` 하므로 머리글, 바닥글, 여백 및 관련 요소가 올바르게 인쇄 됩니다. 보기 공급자는 프레임에 `IContinueCallback`을 통해 인쇄 관련 이벤트를 알립니다. 이러한 인터페이스를 사용 하는 방법에 대 한 자세한 내용은 [프로그래밍 방식 인쇄](programmatic-printing.md)를 참조 하세요.

액티브 문서에서 단일 보기만 지원될 경우에는 하나의 구체적 클래스를 사용해서 액티브 문서 및 해당 단일 보기를 구현할 수 있습니다. `IOleDocument::CreateView` 는 동일한 개체의 인터페이스 포인터를 반환 하기만 합니다 `IOleDocumentView` . 간단히 말해서, 보기가 하나만 필요할 때는 별도의 개체 인스턴스가 두 개 있을 필요가 없습니다.

또한 보기 개체는 명령 대상일 수 있습니다. `IOleCommandTarget`뷰를 구현 하면 컨테이너의 사용자 인터페이스에서 시작 하는 명령 (예: **새로 만들기**, **열기**, 다른 **이름으로 저장**, **인쇄** , **파일** 메뉴의 **복사**, **붙여넣기**, **실행 취소** )을  받을 수 있습니다. 자세한 내용은 [메시지 처리 및 명령 대상](message-handling-and-command-targets.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[액티브 문서 포함](active-document-containment.md)
