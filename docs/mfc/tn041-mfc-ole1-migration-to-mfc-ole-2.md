---
description: 'TN041: mfc/OLE 2로 MFC/OLE1 마이그레이션에 대해 자세히 알아보세요.'
title: 'TN041: mfc로의 MFC-OLE1 마이그레이션-OLE 2'
ms.date: 10/18/2018
helpviewer_keywords:
- OLE1 [MFC]
- migrating OLE1 to OLE2
- migration [MFC], OLE1 to OLE2
- OLE2 [MFC]
- porting OLE1 to OLE2
- converting OLE1 to OLE2
- upgrading Visual C++ applications [MFC], OLE1 to OLE2
- TN041
ms.assetid: 67f55552-4b04-4ddf-af0b-4d9eaf5da957
ms.openlocfilehash: 83bb9869d61ca9d2c92780fc6bed55ce3c3ff798
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215380"
---
# <a name="tn041-mfcole1-migration-to-mfcole-2"></a>TN041: MFC/OLE 2로 MFC/OLE1 마이그레이션

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

## <a name="general-issues-relating-to-migration"></a>마이그레이션과 관련 된 일반적인 문제

MFC 2.5의 OLE 2 클래스에 대 한 디자인 목표 중 하나는 OLE 1.0 지원을 위해 MFC 2.0에 배치 되는 것과 동일한 아키텍처를 거의 유지 하는 것 이었습니다. 따라서 MFC 2.0의 동일한 OLE 클래스 대부분이이 버전의 MFC ( `COleDocument` , `COleServerDoc` ,,)에 여전히 존재 `COleClientItem` `COleServerItem` 합니다. 또한 이러한 클래스의 많은 Api는 정확히 동일 합니다. 그러나 OLE 2는 OLE 1.0와 크게 다르므로 일부 세부 정보가 변경 된 것으로 예측할 수 있습니다. MFC 2.0의 OLE1 지원에 대해 잘 알고 있는 경우에는 MFC의 2.0 지원에 대해 가정 합니다.

기존 MFC/OLE1 응용 프로그램을 만들고이 응용 프로그램에 OLE 2 기능을 추가 하는 경우 먼저이 노트를 읽어야 합니다. 이 참고는 OLE1 기능을 MFC/OLE 2로 이식 하는 동안 발생할 수 있는 몇 가지 일반적인 문제를 설명 하 고 mfc 2.0에 포함 된 두 가지 응용 프로그램 (MFC OLE 샘플 [OCLIENT](../overview/visual-cpp-samples.md) 및 [HIERSVR](../overview/visual-cpp-samples.md))을 이식 하는 동안 발생 하는 문제를 설명 합니다

## <a name="mfc-documentview-architecture-is-important"></a>MFC 문서/뷰 아키텍처는 중요 합니다.

응용 프로그램에서 MFC의 문서/뷰 아키텍처를 사용 하지 않는 경우 응용 프로그램에 OLE 2 지원 기능을 추가 하려는 경우 이제 문서/뷰로 이동 하는 데 시간이 소요 됩니다. MFC의 OLE 2 클래스의 많은 이점은 응용 프로그램이 MFC의 기본 제공 아키텍처 및 구성 요소를 사용 하는 경우에만 실현 됩니다.

MFC 아키텍처를 사용 하지 않고 서버 또는 컨테이너를 구현 하는 것은 가능 하지만 권장 되지는 않습니다.

## <a name="use-mfc-implementation-instead-of-your-own"></a>사용자 고유의 대신 MFC 구현을 사용 합니다.

, 및와 같은 MFC "고정 구현" 클래스 `CToolBar` `CStatusBar` `CScrollView` 는 OLE 2 지원에 대 한 특수 한 케이스 코드를 기본적으로 제공 합니다. 따라서 응용 프로그램에서 이러한 클래스를 사용할 수 있는 경우 이러한 클래스에 추가 하 여 OLE를 인식 하도록 하는 것이 좋습니다. 이러한 목적을 위해 여기에서 "사용자 소유의" 클래스를 사용할 수 있지만이는 권장 되지 않습니다. 비슷한 기능을 구현 해야 하는 경우에는 MFC 소스 코드를 사용 하 여 OLE의 세부적인 요소 중 일부를 처리 하는 것이 좋습니다 (특히 내부 활성화로 제공 되는 경우).

## <a name="examine-the-mfc-sample-code"></a>MFC 샘플 코드를 검사 합니다.

OLE 기능을 포함 하는 다양 한 MFC 샘플이 있습니다. 이러한 각 응용 프로그램은 서로 다른 각도에서 OLE를 구현 합니다.

- [HIERSVR](../overview/visual-cpp-samples.md) 주로 서버 응용 프로그램으로 사용 합니다. Mfc/OLE1 응용 프로그램으로 mfc 2.0에 포함 되었으며, MFC/OLE 2로 이식 된 후 OLE 2에서 사용할 수 있는 많은 OLE 기능을 구현 하도록 확장 되었습니다.

- [OCLIENT](../overview/visual-cpp-samples.md) 이는 컨테이너 관점에서 많은 OLE 기능을 보여 주기 위해 독립 실행형 컨테이너 응용 프로그램입니다. MFC 2.0에서 이식 된 후 사용자 지정 클립보드 형식 및 포함 된 항목에 대 한 링크와 같은 많은 고급 OLE 기능을 지원 하도록 확장 되었습니다.

- [DRAWCLI](../overview/visual-cpp-samples.md) 이 응용 프로그램은 기존 개체 지향 그리기 프로그램의 프레임 워크 내에서 수행 하는 경우를 제외 하 고, OCLIENT와 매우 비슷한 OLE 컨테이너 지원을 구현 합니다. OLE 컨테이너 지원을 구현 하 고 기존 응용 프로그램에 통합 하는 방법을 보여 줍니다.

- [SUPERPAD](../overview/visual-cpp-samples.md) 이 응용 프로그램은 물론 적절 한 독립 실행형 응용 프로그램 이기도 한 OLE 서버 이기도 합니다. 구현 하는 서버 지원에는 상당한 전적 있습니다. 여기서는 OLE 클립보드 서비스를 사용 하 여 데이터를 클립보드에 복사 하지만 Windows "편집" 컨트롤에 기본 제공 되는 기능을 사용 하 여 클립보드 붙여넣기 기능을 구현 하는 방법을 다룹니다. 이는 새로운 OLE Api와의 통합 뿐만 아니라 기존 Windows API 사용의 흥미로운 조합을 보여 줍니다.

예제 응용 프로그램에 대 한 자세한 내용은 "MFC 샘플 도움말"을 참조 하십시오.

## <a name="case-study-oclient-from-mfc-20"></a>사례 연구: MFC 2.0의 OCLIENT

위에서 설명한 것 처럼 [OCLIENT](../overview/visual-cpp-samples.md) 는 mfc 2.0에 포함 되었으며 MFC/OLE1을 사용 하 여 OLE를 구현 했습니다. 이 응용 프로그램을 처음으로 MFC/OLE 2 클래스를 사용 하도록 변환 하는 단계는 아래에 설명 되어 있습니다. MFC/OLE 클래스를 보다 잘 보여 주기 위해 초기 포트가 완료 된 후 많은 기능이 추가 되었습니다. 이러한 기능은 여기에서 다루지 않습니다. 이러한 고급 기능에 대 한 자세한 내용은 샘플 자체를 참조 하세요.

> [!NOTE]
> Visual C++ 2.0를 사용 하 여 컴파일러 오류 및 단계별 프로세스를 만들었습니다. Visual C++ 4.0를 사용 하 여 특정 오류 메시지 및 위치를 변경 했을 수 있지만 개념적 정보는 유효한 상태로 유지 됩니다.

### <a name="getting-it-up-and-running"></a>가져오기 및 실행

OCLIENT 샘플을 MFC/OLE로 이식 하는 방식은 시작 하 고 결과를 얻을 수 있는 명확한 컴파일러 오류를 수정 하는 것입니다. MFC 2.0에서 OCLIENT 샘플을 사용 하 여이 버전의 MFC에서 컴파일하는 경우 해결 해야 할 오류가 많지 않은 것을 알 수 있습니다. 발생 한 순서 대로 발생 한 오류는 아래에 설명 되어 있습니다.

### <a name="compile-and-fix-errors"></a>컴파일 및 오류 수정

```Output
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters
```

첫 번째 오류 문제 `COleClientItem::Draw` . MFC/OLE1에서 MFC/OLE 버전에 사용 되는 것 보다 많은 매개 변수를 사용 했습니다. 추가 매개 변수는 일반적으로 필요 하지 않으며 일반적으로 NULL입니다 (이 예에서는). 이 버전의 MFC는 그릴 CDC가 메타 파일 DC 인 경우 lpWBounds의 값을 자동으로 결정할 수 있습니다. 또한 프레임 워크는 전달 된 pDC의 "특성 DC"에서 하나를 빌드하기 때문에 pFormatDC 매개 변수는 더 이상 필요 하지 않습니다. 따라서이 문제를 해결 하려면 두 개의 추가 NULL 매개 변수를 그리기 호출로 제거 하면 됩니다.

```Output
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier
\oclient\mainview.cpp(273) : error C2057: expected constant expression
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
```

위의 오류는 `COleClientItem::CreateXXXX` MFC/OLE1의 모든 함수에서 항목을 나타내기 위해 고유 이름이 전달 되어야 한다는 사실 때문에 발생 합니다. 이는 기본 OLE API에 대 한 요구 사항 이었습니다. OLE 2는 DDE를 기본 통신 메커니즘으로 사용 하지 않습니다 (DDE 대화에서 이름이 사용 됨) .이는 MFC/OLE 2에서는 필요 하지 않습니다. 이 문제를 해결 하려면 함수 뿐만 아니라 `CreateNewName` 함수에 대 한 모든 참조를 제거 하면 됩니다. 단순히 커서를 호출에 배치 하 고 F1 키를 눌러이 버전에서 각 MFC/OLE 함수가 무엇을 기대 하는지 쉽게 확인할 수 있습니다.

다른 영역은 OLE 2 클립보드 처리와 매우 다릅니다. OLE1을 사용 하면 Windows 클립보드 Api를 사용 하 여 클립보드와 상호 작용 합니다. OLE 2에서는 다른 메커니즘을 사용 하 여이 작업을 수행 합니다. MFC/OLE1 Api는 클립보드에 개체를 복사 하기 전에 클립보드를 연 것으로 가정 합니다 `COleClientItem` . 이렇게 하면 더 이상 필요 하지 않으며 모든 MFC/OLE 클립보드 작업이 실패 합니다. 에서 종속성을 제거 하는 코드를 편집 하는 동안 `CreateNewName` Windows 클립보드를 열고 닫는 코드도 제거 해야 합니다.

```Output
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function
\oclient\mainview.cpp(344) : error C2057: expected constant expression
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'
```

이러한 오류는 처리기에서 발생 `CMainView::OnInsertObject` 합니다. "새 개체 삽입" 명령을 처리 하는 것이 매우 약간 변경 된 다른 영역입니다. 이 경우 원래 구현을 새 OLE 컨테이너 응용 프로그램에 대해 응용 프로그램 마법사에서 제공 하는 것과 병합 하는 것이 가장 쉽습니다. 실제로이 기술은 다른 응용 프로그램을 이식 하는 데 적용할 수 있는 기술입니다. MFC/OLE1에서 함수를 호출 하 여 "개체 삽입" 대화 상자를 표시 `AfxOleInsertDialog` 했습니다. 이 버전에서는 `COleInsertObject` 대화 상자 개체를 생성 하 고를 호출 `DoModal` 합니다. 또한 새 OLE 항목은 classname 문자열 대신 **CLSID** 를 사용 하 여 생성 됩니다. 최종 결과는 다음과 같을 것입니다.

```cpp
COleInsertDialog dlg;
if (dlg.DoModal() != IDOK)
    return;

BeginWaitCursor();

CRectItem* pItem = NULL;
TRY
{
    // First create the C++ object
    pItem = GetDocument()->CreateItem();
    ASSERT_VALID(pItem);

    // Initialize the item from the dialog data.
    if (!dlg.CreateItem(pItem))
        AfxThrowMemoryException();
            // any exception will do
    ASSERT_VALID(pItem);

    // run the object if appropriate
    if (dlg.GetSelectionType() == COleInsertDialog::createNewItem)
        pItem->DoVerb(OLEIVERB_SHOW, this);

    // update right away
    pItem->UpdateLink();
    pItem->UpdateItemRectFromServer();

    // set selection to newly inserted item
    SetSelection(pItem);
    pItem->Invalidate();
}
CATCH (CException, e)
{
    // clean up item
    if (pItem != NULL)
        GetDocument()->DeleteItem(pItem);

    AfxMessageBox(IDP_FAILED_TO_CREATE);
}
END_CATCH

EndWaitCursor();
```

> [!NOTE]
> 새 개체 삽입은 응용 프로그램에 따라 다를 수 있습니다.

또한 \<afxodlgs.h> 대화 상자 클래스에 대 한 선언과 `COleInsertObject` MFC에서 제공 하는 다른 표준 대화 상자를 포함 하는를 포함 해야 합니다.

```Output
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters
```

이러한 오류는 일부 OLE1 상수가 OLE 2에서 변경 되었기 때문에 발생 합니다. 개념적으로는 동일 합니다. 이 경우 `OLEVERB_PRIMARY` 는로 변경 되었습니다 `OLEIVERB_PRIMARY` . 사용자가 항목을 두 번 클릭 하는 경우에는 일반적으로 컨테이너에서 기본 동사를 실행 합니다.

또한 이제는 `DoVerb` 추가 매개 변수 ( `CView` *)를 사용 합니다. 이 매개 변수는 "비주얼 편집" (또는 내부 활성화)을 구현 하는 데만 사용 됩니다. 지금은이 기능을 구현 하지 않으므로이 매개 변수를 NULL로 설정 합니다.

프레임 워크가 내부 활성화를 시도 하지 않도록 하려면 다음과 같이를 재정의 해야 합니다 `COleClientItem::CanActivate` .

```cpp
BOOL CRectItem::CanActivate()
{
    return FALSE;
}
```

```Output
\oclient\rectitem.cpp(53) : error C2065: 'GetBounds' : undeclared identifier
\oclient\rectitem.cpp(53) : error C2064: term does not evaluate to a function
\oclient\rectitem.cpp(84) : error C2065: 'SetBounds' : undeclared identifier
\oclient\rectitem.cpp(84) : error C2064: term does not evaluate to a function
```

MFC/OLE1에서 `COleClientItem::GetBounds` 및는 `SetBounds` 항목의 범위를 쿼리하고 조작 하는 데 사용 되었습니다 `left` `top` . 및 멤버는 항상 0입니다. MFC/OLE 2에서이는 `COleClientItem::GetExtent` `SetExtent` **크기** 를 처리 하는 및에서 직접 지원 됩니다 `CSize` .

새 SetItemRectToServer 및 UpdateItemRectFromServer 호출에 대 한 코드는 다음과 같습니다.

```cpp
BOOL CRectItem::UpdateItemRectFromServer()
{
    ASSERT(m_bTrackServerSize);
    CSize size;
    if (!GetExtent(&size))
        return FALSE;    // blank

    // map from HIMETRIC to screen coordinates
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.LPtoDP(&size);
    }
    // just set the item size
    if (m_rect.Size() != size)
    {
        // invalidate the old size/position
        Invalidate();
        m_rect.right = m_rect.left + size.cx;
        m_rect.bottom = m_rect.top + size.cy;
        // as well as the new size/position
        Invalidate();
    }
    return TRUE;
}

BOOL CRectItem::SetItemRectToServer()
{
    // set the official bounds for the embedded item
    CSize size = m_rect.Size();
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.DPtoLP(&size);
    }
    TRY
    {
        SetExtent(size);    // may do a wait
    }
    CATCH(CException, e)
    {
        return FALSE;  // links will not allow SetBounds
    }
    END_CATCH
    return TRUE;
}
```

```Output
\oclient\frame.cpp(50) : error C2039: 'InWaitForRelease' : is not a member of 'COleClientItem'
\oclient\frame.cpp(50) : error C2065: 'InWaitForRelease' : undeclared identifier
\oclient\frame.cpp(50) : error C2064: term does not evaluate to a function
```

대부분의 경우에는 OLE1이 기본적으로 비동기 이기 때문에, MFC/OLE1 동기 API는 컨테이너에서 서버로 호출을 *시뮬레이션* 했습니다. 사용자의 명령을 처리 하기 전에 진행 중인 비동기 호출을 확인 해야 했습니다. MFC/OLE1에서이 `COleClientItem::InWaitForRelease` 작업을 수행 하는 함수를 제공 했습니다. MFC/OLE 2에서는이 작업이 필요 하지 않으므로 CMainFrame에서 OnCommand의 재정의를 함께 제거할 수 있습니다.

이 시점에서 OCLIENT는를 컴파일하고 연결 합니다.

### <a name="other-necessary-changes"></a>기타 필요한 변경 내용

그러나 실행이 실행 되지 않도록 하기 위해 수행 되지 않는 몇 가지 작업이 있습니다. 나중에 이러한 문제를 해결 하는 것이 좋습니다.

먼저 OLE 라이브러리를 초기화 해야 합니다. 이 작업은 다음에서를 호출 하 여 수행 됩니다 `AfxOleInit` `InitInstance` .

```cpp
if (!AfxOleInit())
{
    AfxMessageBox("Failed to initialize OLE libraries");
    return FALSE;
}
```

매개 변수 목록 변경에 대 한 가상 함수를 확인 하는 것도 좋습니다. 이러한 함수 중 하나는 `COleClientItem::OnChange` 모든 MFC/OLE 컨테이너 응용 프로그램에서 재정의 되는입니다. 온라인 도움말을 살펴보면 추가 ' DWORD dwParam '이 추가 된 것을 볼 수 있습니다. 새 CRectItem:: OnChange는 다음과 같습니다.

```cpp
void
CRectItem::OnChange(OLE_NOTIFICATION wNotification, DWORD dwParam)
{
    if (m_bTrackServerSize && !UpdateItemRectFromServer())
    {
        // Blank object
        if (wNotification == OLE_CLOSED)
        {
            // no data received for the object - destroy it
            ASSERT(!IsVisible());
            GetDocument()->DeleteItem(this);
            return; // no update (item is gone now)
        }
    }
    if (wNotification != OLE_CLOSED)
        Dirty();
    Invalidate();
    // any change will cause a redraw
}
```

MFC/OLE1의 컨테이너 응용 프로그램은에서 문서 클래스를 파생 합니다 `COleClientDoc` . MFC/OLE 2에서이 클래스는 제거 되 고로 대체 되었습니다 `COleDocument` .이 새로운 조직은 컨테이너/서버 응용 프로그램을 쉽게 빌드할 수 있습니다. 에 매핑되는 **#define** 을 통해 `COleClientDoc` `COleDocument` mfc/OLE1 응용 프로그램의 포팅을 mfc/OLE 2 (예: OCLIENT)로 간소화할 수 있습니다. 에서 제공 하지 않는 기능 중 하나 `COleDocument` `COleClientDoc` 는 표준 명령 메시지 맵 항목입니다. 이 작업은 (간접적으로)를 사용 하는 서버 응용 프로그램이 `COleDocument` 컨테이너/서버 응용 프로그램이 아닌 경우 이러한 명령 처리기의 오버 헤드를 전달 하지 않도록 하기 위해 수행 됩니다. CMainDoc 메시지 맵에 다음 항목을 추가 해야 합니다.

```cpp
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE, OnUpdatePasteMenu)
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK, OnUpdatePasteLinkMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS, OnUpdateEditLinksMenu)
ON_COMMAND(ID_OLE_EDIT_LINKS, COleDocument::OnEditLinks)
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST, OnUpdateObjectVerbMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT, OnUpdateObjectVerbMenu)
ON_COMMAND(ID_OLE_EDIT_CONVERT, OnEditConvert)
```

이러한 모든 명령의 구현은 `COleDocument` 문서에 대 한 기본 클래스인에 있습니다.

이 시점에서 OCLIENT는 함수형 OLE 컨테이너 응용 프로그램입니다. 모든 형식의 항목 (OLE1 또는 OLE 2)을 삽입할 수 있습니다. 내부 활성화를 사용 하도록 설정 하는 데 필요한 코드는 구현 되지 않으므로 OLE1과 마찬가지로 항목이 별도의 창에서 편집 됩니다. 다음 섹션에서는 내부 편집을 사용 하도록 설정 하는 데 필요한 변경 사항에 대해 설명 합니다 ("시각적 편집"이 라고도 함).

### <a name="adding-visual-editing"></a>"비주얼 편집" 추가

OLE의 가장 흥미로운 기능 중 하나는 내부 활성화 (또는 "시각적 편집")입니다. 이 기능을 통해 서버 응용 프로그램은 컨테이너의 사용자 인터페이스의 일부를 통해 사용자에 게 보다 원활한 편집 인터페이스를 제공할 수 있습니다. OCLIENT에 대 한 내부 활성화를 구현 하려면 일부 특수 리소스 뿐만 아니라 몇 가지 추가 코드도 추가 해야 합니다. 이러한 리소스 및 코드는 일반적으로 응용 프로그램 마법사에서 제공 됩니다. 실제로 여기에서 대부분의 코드는 "컨테이너"를 지 원하는 새로운 응용 프로그램 마법사 응용 프로그램에서 직접 빌려 온 것입니다.

먼저 활성화 된 항목이 있을 때 사용 되는 메뉴 리소스를 추가 해야 합니다. IDR_OCLITYPE 리소스를 복사 하 고 파일 및 창 팝업을 제외한 모든 파일을 제거 하 여 Visual C++에서이 추가 메뉴 리소스를 만들 수 있습니다. 파일 및 창 팝업 사이에 두 개의 구분선 막대가 삽입 되어 그룹의 분리를 표시 합니다 (예: File &#124;&#124; Window). 이러한 구분 기호에 대 한 자세한 내용과 서버 및 컨테이너 메뉴가 병합 되는 방법에 대 한 자세한 내용은 [메뉴 및 리소스: 메뉴 병합](../mfc/menus-and-resources-menu-merging.md)을 참조 하세요.

이러한 메뉴를 만든 후에는 프레임 워크에서 해당 메뉴를 인식 하도록 해야 합니다. `CDocTemplate::SetContainerInfo`InitInstance의 문서 템플릿 목록에 추가 하기 전에 문서 템플릿에 대해를 호출 하 여이 작업을 수행 합니다. 문서 템플릿을 등록 하는 새 코드는 다음과 같습니다.

```cpp
CDocTemplate* pTemplate = new CMultiDocTemplate(
    IDR_OLECLITYPE,
    RUNTIME_CLASS(CMainDoc),
    RUNTIME_CLASS(CMDIChildWnd), // standard MDI child frame
    RUNTIME_CLASS(CMainView));

pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);

AddDocTemplate(pTemplate);
```

IDR_OLECLITYPE_INPLACE 리소스는 Visual C++에서 만든 특수 한 내부 리소스입니다.

내부 활성화를 사용 하려면 파생 클래스 `CView` (CRectItem) 뿐만 아니라 (cmainview) 파생 클래스에서 변경 해야 하는 몇 가지 사항이 있습니다 `COleClientItem` . 이러한 모든 재정의는 응용 프로그램 마법사에서 제공 되며 대부분의 구현은 기본 응용 프로그램 마법사 응용 프로그램에서 직접 제공 됩니다.

이 포트의 첫 번째 단계에서 전체 활성화는를 재정의 하 여 완전히 사용 하지 않도록 설정 되었습니다 `COleClientItem::CanActivate` . 내부 활성화를 허용 하려면이 재정의를 제거 해야 합니다. 또한 `DoVerb` 뷰를 제공 하는 것은 내부 활성화에만 필요 하기 때문에에 대 한 모든 호출에 NULL이 전달 되었습니다. 내부 활성화를 완전히 구현 하려면 호출에서 올바른 뷰를 전달 해야 `DoVerb` 합니다. 다음 호출 중 하나는에 `CMainView::OnInsertObject` 있습니다.

```cpp
pItem->DoVerb(OLEIVERB_SHOW, this);
```

또 다른 경우는 `CMainView::OnLButtonDblClk` 다음과 같습니다.

```cpp
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);
```

을 재정의 해야 `COleClientItem::OnGetItemPosition` 합니다. 그러면 항목이 활성 상태로 활성화 될 때 컨테이너 창에 상대적인 창을 배치할 위치를 서버에 알려 줍니다. OCLIENT의 경우 구현은 trivial입니다.

```cpp
void CRectItem::OnGetItemPosition(CRect& rPosition)
{
    rPosition = m_rect;
}
```

또한 대부분의 서버는 "현재 위치의 크기 조정" 이라는 것을 구현 합니다. 이렇게 하면 사용자가 항목을 편집 하는 동안 서버 창의 크기를 조정 하 고 이동할 수 있습니다. 창을 이동 하거나 크기를 조정 하는 작업은 일반적으로 컨테이너 문서 자체 내의 위치와 크기에 영향을 주므로 컨테이너는이 작업에 참여 해야 합니다. OCLIENT의 구현은 m_rect에 의해 유지 관리 되는 내부 사각형을 새 위치 및 크기와 동기화 합니다.

```cpp
BOOL CRectItem::OnChangeItemPosition(const CRect& rectPos)
{
    ASSERT_VALID(this);

    if (!COleClientItem::OnChangeItemPosition(rectPos))
        return FALSE;

    Invalidate();
    m_rect = rectPos;
    Invalidate();
    GetDocument()->SetModifiedFlag();

    return TRUE;
}
```

이 시점에서 항목을 활성화 하 고 항목의 크기를 조정 하 고 활성 상태일 때 항목을 이동 하는 데 충분 한 코드를 사용할 수 있지만 사용자가 편집 세션을 종료할 수 있는 코드는 없습니다. 일부 서버는 이스케이프 키를 처리 하 여이 기능을 직접 제공 하지만, 컨테이너는 항목 바깥쪽을 클릭 하 여 (1), (2), ESC 키를 눌러 항목을 비활성화 하는 두 가지 방법을 제공 하는 것이 좋습니다.

이스케이프 키의 경우 VK_ESCAPE 키를 명령에 매핑하는 Visual C++ 있는 액셀러레이터를 추가 ID_CANCEL_EDIT 리소스에 추가 됩니다. 이 명령의 처리기는 다음과 같습니다.

```cpp
// The following command handler provides the standard
// keyboard user interface to cancel an in-place
// editing session.void CMainView::OnCancelEdit()
{
    // Close any in-place active item on this view.
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->Close();
    ASSERT(GetDocument()->GetInPlaceActiveItem(this) == NULL);
}
```

사용자가 항목 바깥쪽을 클릭 하는 경우를 처리 하려면의 시작 부분에 다음 코드를 추가 합니다 `CMainView::SetSelection` .

```cpp
if (pNewSel != m_pSelection || pNewSel == NULL)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL&& pActiveItem != pNewSel)
        pActiveItem->Close();
}
```

항목이 활성화 된 상태 이면 포커스가 있어야 합니다. 뷰가 포커스를 받을 때 포커스가 항상 활성 항목으로 전송 되도록 OnSetFocus를 처리 하는 것을 확인 하려면 다음을 수행 합니다.

```cpp
// Special handling of OnSetFocus and OnSize are required
// when an object is being edited in-place.
void CMainView::OnSetFocus(CWnd* pOldWnd)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);

    if (pActiveItem != NULL &&
        pActiveItem->GetItemState() == COleClientItem::activeUIState)
    {
        // need to set focus to this item if it is same view
        CWnd* pWnd = pActiveItem->GetInPlaceWindow();
        if (pWnd != NULL)
        {
            pWnd->SetFocus();   // don't call the base class
            return;
        }
    }

    CView::OnSetFocus(pOldWnd);
}
```

뷰의 크기를 조정 하는 경우 활성 항목에 클리핑 사각형이 변경 되었음을 알려야 합니다. 이렇게 하려면 다음에 대 한 처리기를 제공 합니다 `OnSize` .

```cpp
void CMainView::OnSize(UINT nType, int cx, int cy)
{
    CView::OnSize(nType, cx, cy);
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->SetItemRects();
}
```

## <a name="case-study-hiersvr-from-mfc-20"></a>사례 연구: MFC 2.0의 HIERSVR

[HIERSVR](../overview/visual-cpp-samples.md) 는 mfc 2.0에도 포함 되었으며 MFC/OLE1을 사용 하 여 OLE를 구현 했습니다. 이 정보는 MFC/OLE 2 클래스를 사용 하도록이 응용 프로그램을 처음으로 변환 하는 단계를 간략하게 설명 합니다. MFC/OLE 2 클래스를 보다 잘 보여 주기 위해 초기 포트가 완료 된 후 많은 기능이 추가 되었습니다. 이러한 기능은 여기에서 다루지 않습니다. 이러한 고급 기능에 대 한 자세한 내용은 샘플 자체를 참조 하세요.

> [!NOTE]
> Visual C++ 2.0를 사용 하 여 컴파일러 오류 및 단계별 프로세스를 만들었습니다. Visual C++ 4.0를 사용 하 여 특정 오류 메시지 및 위치를 변경 했을 수 있지만 개념적 정보는 유효한 상태로 유지 됩니다.

### <a name="getting-it-up-and-running"></a>가져오기 및 실행

HIERSVR 샘플을 MFC/OLE로 이식 하는 방식은 먼저이를 빌드하고 결과를 얻을 수 있는 명확한 컴파일러 오류를 수정 하는 것입니다. MFC 2.0에서 HIERSVR 샘플을 사용 하 여이 버전의 MFC에서 컴파일하는 경우에는 오류를 해결할 수 없습니다 (OCLIENT 샘플이 포함 되어 있지만). 일반적으로 발생 하는 순서 대로 발생 한 오류는 아래에 설명 되어 있습니다.

### <a name="compile-and-fix-errors"></a>컴파일 및 오류 수정

```Output
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'
```

이 첫 번째 오류는 `InitInstance` 서버에 대 한 함수와 훨씬 더 큰 문제를 가리킵니다. OLE 서버에 필요한 초기화는 MFC/OLE1 응용 프로그램을 실행 하기 위해 수행 해야 하는 가장 큰 변경 내용 중 하나일 것입니다. 가장 좋은 방법은 응용 프로그램이 OLE 서버에 대해 만드는 작업을 확인 하 고 코드를 적절 하 게 수정 하는 것입니다. 유의 해야 할 몇 가지 사항은 다음과 같습니다.

을 호출 하 여 OLE 라이브러리를 초기화 해야 합니다. `AfxOleInit`

문서 템플릿 개체에 대해 SetServerInfo를 호출 하 여 생성자를 사용 하 여 설정할 수 없는 서버 리소스 핸들 및 런타임 클래스 정보를 설정 `CDocTemplate` 합니다.

프로그램이/embedding가 명령줄에 있으면 응용 프로그램의 주 창을 표시 하지 않습니다.

문서에 대 한 **GUID** 가 필요 합니다. 문서 형식 (128 비트)의 고유 식별자입니다. 응용 프로그램 마법사는 사용자를 위해 하나를 만듭니다. 따라서 여기서 설명 하는 기술을 사용 하 여 새 코드 마법사에서 생성 된 서버 응용 프로그램에서 새 코드를 복사 하는 경우 해당 응용 프로그램에서 GUID를 "도용" 할 수 있습니다. 그렇지 않은 경우 BIN 디렉터리에서 GUIDGEN.EXE 유틸리티를 사용할 수 있습니다.

을 `COleTemplateServer` 호출 하 여 개체를 문서 템플릿에 "연결" 해야 `COleTemplateServer::ConnectTemplate` 합니다.

응용 프로그램을 독립 실행형으로 실행 하는 경우 시스템 레지스트리를 업데이트 합니다. 사용자가를 이동 하는 경우이 방법을 사용 합니다. 응용 프로그램에 대 한 EXE를 새 위치에서 실행 하면 Windows 시스템 등록 데이터베이스가 새 위치를 가리키도록 업데이트 됩니다.

응용 프로그램에서 생성 하는 항목에 따라 이러한 변경 내용을 모두 적용 한 후에 `InitInstance` 는 `InitInstance` HIERSVR의 및 관련 GUID를 다음과 같이 읽어야 합니다.

```cpp
// this is the GUID for HIERSVR documents
static const GUID BASED_CODE clsid =
{ 0xA0A16360L, 0xC19B, 0x101A, { 0x8C, 0xE5, 0x00, 0xDD, 0x01, 0x11, 0x3F, 0x12 } };

/////////////////////////////////////////////////////////////////////////////
// COLEServerApp initialization

BOOL COLEServerApp::InitInstance()
{
    // OLE 2 initialization
    if (!AfxOleInit())
    {
        AfxMessageBox("Initialization of the OLE failed!");
        return FALSE;
    }

    // Standard initialization
    LoadStdProfileSettings();   // Load standard INI file options

    // Register document templates
    CDocTemplate* pDocTemplate;
    pDocTemplate = new CMultiDocTemplate(IDR_HIERSVRTYPE,
        RUNTIME_CLASS(CServerDoc),
        RUNTIME_CLASS(CMDIChildWnd),
        RUNTIME_CLASS(CServerView));
    pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB);
    AddDocTemplate(pDocTemplate);

    // create main MDI Frame window
    CMainFrame* pMainFrame = new CMainFrame;
    if (!pMainFrame->LoadFrame(IDR_MAINFRAME))
        return FALSE;
    m_pMainWnd = pMainFrame;

    SetDialogBkColor(); // gray look

    // enable file manager drag/drop and DDE Execute open
    m_pMainWnd->DragAcceptFiles();
    EnableShellOpen();

    m_server.ConnectTemplate(clsid, pDocTemplate, FALSE);
    COleTemplateServer::RegisterAll();

    // try to launch as an OLE server
    if (RunEmbedded())
    {
        // "short-circuit" initialization -- run as server!
        return TRUE;
    }
    m_server.UpdateRegistry();
    RegisterShellFileTypes();

    // not run as OLE server, so show the main window
    if (m_lpCmdLine[0] == '\0')
    {
        // create a new (empty) document
        OnFileNew();
    }
    else
    {
        // open an existing document
        OpenDocumentFile(m_lpCmdLine);
    }

    pMainFrame->ShowWindow(m_nCmdShow);
    pMainFrame->UpdateWindow();

    return TRUE;
}
```

위의 코드는 IDR_HIERSVRTYPE_SRVR_EMB 새 리소스 ID를 참조 합니다. 다른 컨테이너에 포함 된 문서를 편집할 때 사용 되는 메뉴 리소스입니다. MFC/OLE1에서 포함 된 항목 편집과 관련 된 메뉴 항목이 즉석에서 수정 되었습니다. 파일 기반 문서를 편집 하는 대신 포함 된 항목을 편집할 때 완전히 다른 메뉴 구조를 사용 하면 이러한 두 가지 별도의 모드에 다른 사용자 인터페이스를 더 쉽게 제공할 수 있습니다. 나중에 볼 수 있듯이 포함 된 개체를 내부에서 편집할 때 완전히 별도의 메뉴 리소스가 사용 됩니다.

이 리소스를 만들려면 리소스 스크립트를 Visual C++ 로드 하 고 기존 IDR_HIERSVRTYPE 메뉴 리소스를 복사 합니다. 새 리소스의 이름을 IDR_HIERSVRTYPE_SRVR_EMB로 바꿉니다 (이는 응용 프로그램에서 사용 하는 것과 동일한 명명 규칙). 다음으로 "파일 저장"을 "파일 업데이트"로 변경 합니다. ID_FILE_UPDATE에 명령 ID를 제공 합니다. 또한 "파일 다른 이름으로 저장"을 "파일을 다른 이름으로 저장";으로 변경 합니다. ID_FILE_SAVE_COPY_AS에 명령 ID를 제공 합니다. 프레임 워크는 두 명령 모두의 구현을 제공 합니다.

```Output
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers
```

`OnSetData` **OLESTATUS** 형식을 참조 하므로의 재정의로 인해 발생 하는 여러 오류가 있습니다. **OLESTATUS** 는 OLE1에서 오류를 반환 하는 방법 이었습니다. 이는 일반적으로 **hresult** 를 오류가 포함 된로 변환 하지만,이는 OLE 2의 **hresult** 로 변경 되었습니다 `COleException` . 이 특정 경우의 재정의는 더 이상 `OnSetData` 필요 하지 않으므로 가장 쉬운 방법은 제거 하는 것입니다.

```Output
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters
```

`COleServerItem`생성자는 추가 ' BOOL ' 매개 변수를 사용 합니다. 이 플래그는 개체에서 메모리 관리를 수행 하는 방법을 결정 합니다 `COleServerItem` . 이를 TRUE로 설정 하면 프레임 워크는 이러한 개체의 메모리 관리를 처리 하 여 더 이상 필요 하지 않은 경우 삭제 합니다. HIERSVR는 `CServerItem` `COleServerItem` 네이티브 데이터의 일부로 (에서 파생 된) 개체를 사용 하므로이 플래그를 FALSE로 설정 합니다. 이렇게 하면 각 서버 항목이 삭제 되는 시기를 HIERSVR에서 확인할 수 있습니다.

```Output
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
```

이러한 오류는 의미 하므로 CServerItem에서 재정의 되지 않은 일부 ' 순수 가상 ' 함수가 있습니다. 이는 OnDraw의 매개 변수 목록이 변경 되었기 때문일 수 있습니다. 이 오류를 해결 하려면 `CServerItem::OnDraw` 다음과 같이 svritem의 선언을 변경 합니다.

```cpp
BOOL CServerItem::OnDraw(CDC* pDC, CSize& rSize)
{
    // request from OLE to draw node
    pDC->SetMapMode(MM_TEXT); // always in pixels
    return DoDraw(pDC, CPoint(0, 0), FALSE);
}
```

새 매개 변수는 ' rSize '입니다. 이렇게 하면 그리기의 크기를 채울 수 있습니다 (편리한 경우). 이 크기는 **HIMETRIC** 에 있어야 합니다. 이 경우에서이 값을 입력 하는 것이 편리 하지 않으므로 프레임 워크가 익스텐트를 `OnGetExtent` 검색 하기 위해를 호출 합니다. 이 작업을 수행 하려면 다음을 구현 해야 합니다 `OnGetExtent` .

```cpp
BOOL CServerItem::OnGetExtent(DVASPECT dwDrawAspect, CSize& rSize)
{
    if (dwDrawAspect != DVASPECT_CONTENT)
        return COleServerItem::OnGetExtent(dwDrawAspect, rSize);

    rSize = CalcNodeSize();
    return TRUE;
}
```

```Output
\hiersvr\svritem.cpp(104) : error C2065: 'm_rectBounds' : undeclared identifier
\hiersvr\svritem.cpp(104) : error C2228: left of '.SetRect' must have class/struct/union type
\hiersvr\svritem.cpp(106) : error C2664: 'void __pascal __far DPtoLP(struct ::tagPOINT __far *,
    int)__far const ' : cannot convert parameter 1 from 'int __far *' to 'struct ::tagPOINT __far *'
```

CServerItem:: CalcNodeSize 함수에서 항목 크기는 **HIMETRIC** 로 변환 되 고 *m_rectBounds* 에 저장 됩니다. 의 문서화 되지 않은 '*m_rectBounds*' 멤버가 없습니다 .이 멤버는 `COleServerItem` *m_sizeExtent* 에 의해 부분적으로 대체 되었지만 OLE 2에서는이 멤버가 *m_rectBounds* 에서 사용 된 것과 약간 다른 방식으로 사용 됩니다. **HIMETRIC** 크기를이 멤버 변수로 설정 하는 대신 반환 합니다. 이 반환 값은 이전에 구현 된에 사용 됩니다 `OnGetExtent` .

```cpp
CSize CServerItem::CalcNodeSize()
{
    CClientDC dcScreen(NULL);

    m_sizeNode = dcScreen.GetTextExtent(m_strDescription,
        m_strDescription.GetLength());
    m_sizeNode += CSize(CX_INSET * 2, CY_INSET * 2);

    // set suggested HIMETRIC size
    CSize size(m_sizeNode.cx, m_sizeNode.cy);
    dcScreen.SetMapMode(MM_HIMETRIC);
    dcScreen.DPtoLP(&size);
    return size;
}
```

CServerItem도 `COleServerItem::OnGetTextData` 를 재정의 합니다. 이 함수는 MFC/OLE에서 사용 되지 않으며 다른 메커니즘으로 대체 되었습니다. Mfc OLE 샘플 [HIERSVR](../overview/visual-cpp-samples.md) 의 mfc 3.0 버전은를 재정의 하 여이 기능을 구현 `COleServerItem::OnRenderFileData` 합니다. 이 기본 포트에서는이 기능이 중요 하지 않으므로 OnGetTextData 재정의를 제거할 수 있습니다.

Svritem에 해결 되지 않은 오류가 더 많이 있습니다. "실제" 오류는 아닙니다. 이전 오류로 인 한 오류만 발생 합니다.

```Output
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters
```

`COleServerItem::CopyToClipboard` 에서 더 이상 플래그를 지원 하지 않습니다 `bIncludeNative` . 원시 데이터 (서버 항목의 직렬화 함수를 통해 작성 된 데이터)는 항상 복사 되므로 첫 번째 매개 변수를 제거 합니다. 또한에서는 FALSE를 반환 하는 대신 오류가 발생 하는 `CopyToClipboard` 경우에서 예외를 throw 합니다. 다음과 같이 CServerView:: OnEditCopy에 대 한 코드를 변경 합니다.

```cpp
void CServerView::OnEditCopy()
{
    if (m_pSelectedNode == NULL)
        AfxThrowNotSupportedException();

    TRY
    {
        m_pSelectedNode->CopyToClipboard(TRUE);
    }
    CATCH_ALL(e)
    {
        AfxMessageBox("Copy to clipboard failed");
    }
    END_CATCH_ALL
}
```

동일한 버전의 OCLIENT에서 얻은 것 보다 MFC 2.0 버전의 HIERSVR를 컴파일하면 오류가 발생 했지만 실제로 변경 된 내용이 거의 없습니다.

이 시점에서 HIERSVR는 다음에 구현 되는 내부 편집 기능 없이 컴파일 및 연결 하 고 OLE 서버로 작동 합니다.

### <a name="adding-visual-editing"></a>"비주얼 편집" 추가

이 서버 응용 프로그램에 "시각적 편집" (또는 전체 활성화)을 추가 하려면 다음과 같은 몇 가지 작업을 수행 해야 합니다.

- 항목이 활성 상태로 있을 때 사용할 특별 한 메뉴 리소스가 필요 합니다.

- 이 응용 프로그램에는 도구 모음이 있으므로 서버에서 사용할 수 있는 메뉴 명령과 일치 하는 도구 모음 (위에서 언급 한 메뉴 리소스와 일치)이 있어야 합니다.

- 내부 사용자 인터페이스를 제공 하는에서 파생 된 새 클래스가 필요 `COleIPFrameWnd` 합니다 (에서 파생 된 CMainFrame과 매우 유사 `CMDIFrameWnd` , MDI 사용자 인터페이스 제공).

- 이러한 특수 리소스와 클래스에 대 한 프레임 워크를 알려 주어 야 합니다.

메뉴 리소스를 쉽게 만들 수 있습니다. Visual C++를 실행 하 고 메뉴 리소스 IDR_HIERSVRTYPE IDR_HIERSVRTYPE_SRVR_IP 라는 메뉴 리소스에 복사 합니다. 편집 및 도움말 메뉴 팝업만 남아 있도록 메뉴를 수정 합니다. 편집 및 도움말 메뉴 사이에 있는 메뉴에 두 개의 구분 기호를 추가 합니다 (예: 편집 &#124;&#124; 도움말). 이러한 구분 기호와 서버 및 컨테이너 메뉴가 병합 되는 방법에 대 한 자세한 내용은 메뉴 [및 리소스: 메뉴 병합](../mfc/menus-and-resources-menu-merging.md)을 참조 하세요.

"Server" 옵션을 선택 하 여 새 응용 프로그램 마법사에서 생성 된 응용 프로그램의 비트맵을 복사 하 여 하위 집합 도구 모음에 대 한 비트맵을 쉽게 만들 수 있습니다. 그런 다음이 비트맵을 Visual C++으로 가져올 수 있습니다. 비트맵에 IDR_HIERSVRTYPE_SRVR_IP ID를 제공 해야 합니다.

에서 파생 된 클래스는 `COleIPFrameWnd` 서버 지원과 함께 응용 프로그램 마법사에서 생성 된 응용 프로그램 에서도 복사할 수 있습니다. 두 파일 IPFRAME을 복사 합니다. CPP 및 IPFRAME. H를 추가 하 고 프로젝트에 추가 합니다. `LoadBitmap`호출에서 이전 단계에서 만든 비트맵 IDR_HIERSVRTYPE_SRVR_IP를 참조 하는지 확인 합니다.

이제 모든 새 리소스 및 클래스가 만들어지므로 프레임 워크에서 이러한 정보를 인식할 수 있도록 필요한 코드를 추가 합니다 .이 응용 프로그램은 현재 내부 편집을 지원 한다는 것을 알고 있습니다. 이 작업은 함수에서 호출에 매개 변수를 더 추가 하 여 수행 됩니다 `SetServerInfo` `InitInstance` .

```cpp
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,
    IDR_HIERSVRTYPE_SRVR_IP,
    RUNTIME_CLASS(CInPlaceFrame));
```

이제 내부 활성화도 지 원하는 모든 컨테이너에서 바로 실행할 수 있습니다. 그러나 코드에는 숨어 한 개의 사소한 버그가 있습니다. HIERSVR는 사용자가 마우스 오른쪽 단추를 누를 때 표시 되는 상황에 맞는 메뉴를 지원 합니다. 이 메뉴는 HIERSVR를 완전히 열 때 작동 하지만 포함을 편집 하는 경우 작동 하지 않습니다. 이 이유는 CServerView:: OnRButtonDown의이 단일 코드 줄에 고정 될 수 있습니다.

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetApp()->m_pMainWnd);
```

에 대 한 참조를 확인 합니다 `AfxGetApp()->m_pMainWnd` . 서버가 활성화 된 후에는 주 창이 있고 m_pMainWnd 설정 되지만 일반적으로 표시 되지 않습니다. 또한이 창은 응용 프로그램의 *주* 창, 서버가 완전히 열리거나 독립 실행형으로 실행 될 때 표시 되는 MDI 프레임 창을 나타냅니다. 활성 프레임 창을 참조 하지 않습니다. 내부 활성화 된 경우에서 파생 되는 프레임 창이 됩니다 `COleIPFrameWnd` . 내부 편집 시에도 올바른 활성 창을 가져오기 위해이 버전의 MFC는 새 함수인를 추가 `AfxGetMainWnd` 합니다. 일반적으로 대신이 함수를 사용 해야 `AfxGetApp()->m_pMainWnd` 합니다. 이 코드는 다음과 같이 변경 해야 합니다.

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetMainWnd());
```

이제 기능 내부 활성화를 위해 OLE 서버를 최소한으로 설정 했습니다. 하지만 mfc/OLE1에서 사용할 수 없었던 MFC/OLE 2에서 사용할 수 있는 많은 기능이 있습니다. 구현 하려는 기능에 대 한 추가 정보는 HIERSVR 샘플을 참조 하세요. HIERSVR에서 구현 하는 기능 중 일부는 아래에 나열 되어 있습니다.

- 확대/축소-컨테이너와 관련 된 진정한 WYSIWYG 동작

- 끌어서 놓기 및 사용자 지정 클립보드 형식입니다.

- 선택 항목이 변경 될 때 컨테이너 창을 스크롤합니다.

MFC 3.0의 HIERSVR 샘플도 서버 항목에 대해 약간 다른 디자인을 사용 합니다. 이렇게 하면 메모리를 절약 하 고 링크를 더욱 유연 하 게 만들 수 있습니다. 2.0 버전의 HIERSVR에서 트리의 각 노드는 *-a* `COleServerItem` 입니다. `COleServerItem` 는 이러한 각 노드에 반드시 필요한 것 보다 더 많은 오버 헤드를 전달 하지만 `COleServerItem` 각 활성 링크에는가 필요 합니다. 그러나 대부분의 경우에는 지정 된 시간에 활성 링크가 거의 없습니다. 이러한 작업을 더 효율적으로 수행 하기 위해이 버전의 MFC에서 HIERSVR는와 노드를 분리 합니다 `COleServerItem` . CServerNode와 클래스가 모두 있습니다 `CServerItem` . 에서 파생 된는 필요한 경우에 `CServerItem` `COleServerItem` 만 생성 됩니다. 컨테이너 (또는 컨테이너)가 특정 노드에 대 한 특정 링크를 사용 하지 않으면 Cserveritem와 연결 된 CServerItem 개체가 삭제 됩니다. 이 디자인은 보다 효율적이 고 유연 합니다. 여러 선택 링크를 처리할 때 유연성이 제공 됩니다. 이러한 두 버전의 HIERSVR는 여러 선택 영역을 지원 하지 않지만 MFC 3.0 버전의 MFC 버전을 사용 하 여 이러한 선택에 대 한 링크를 지원할 수 `COleServerItem` 있습니다 .이 네이티브 데이터와 분리 되기 때문입니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
