---
description: 'TN071: MFC IOleCommandTarget 구현에 대해 자세히 알아보세요.'
title: 'TN071: MFC IOleCommandTarget 구현'
ms.date: 06/28/2018
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
ms.openlocfilehash: 190dd64f6fd14d6231a6870bf6697a9a85182166
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214509"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071: MFC IOleCommandTarget 구현

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

`IOleCommandTarget`인터페이스를 사용 하면 개체와 해당 컨테이너가 서로 명령을 디스패치할 수 있습니다. 예를 들어, 개체의 도구 모음에는,,, 및와 같은 명령에 대 한 단추가 포함 될 수 있습니다 `Print` `Print Preview` `Save` `New` `Zoom` . 이러한 개체가를 지 원하는 컨테이너에 포함 된 경우 `IOleCommandTarget` 개체는 해당 단추를 사용 하도록 설정 하 고 사용자가이를 클릭 했을 때 처리할 명령을 컨테이너에 전달할 수 있습니다. 컨테이너에서 포함 된 개체를 자체 인쇄 하려는 경우 `IOleCommandTarget` 포함 된 개체의 인터페이스를 통해 명령을 전송 하 여이 요청을 수행할 수 있습니다.

`IOleCommandTarget` 는 클라이언트가 서버에서 메서드를 호출 하는 데 사용 되는 자동화와 유사한 인터페이스입니다. 그러나를 사용 하면 `IOleCommandTarget` 프로그래머가 일반적으로 비용이 많이 드는 메서드를 사용할 필요가 없기 때문에 자동화 인터페이스를 통해 호출 하는 오버 헤드를 줄일 수 `Invoke` `IDispatch` 있습니다.

MFC에서 액티브 문서 서버는 액티브 문서 `IOleCommandTarget` 서버에서 서버에 명령을 디스패치할 수 있도록 하는 인터페이스를 사용 합니다. 액티브 문서 서버 클래스는 `CDocObjectServerItem` mfc 인터페이스 맵 ( [TN038: MFC/OLE IUnknown 구현](../mfc/tn038-mfc-ole-iunknown-implementation.md)참조)을 사용 하 여 인터페이스를 구현 합니다 `IOleCommandTarget` .

`IOleCommandTarget` 도 클래스에서 구현 됩니다 `COleFrameHook` . `COleFrameHook` 는 내부 편집 컨테이너의 프레임 창 기능을 구현 하는 문서화 되지 않은 MFC 클래스입니다. `COleFrameHook` 또한는 MFC 인터페이스 맵을 사용 하 여 `IOleCommandTarget` 인터페이스를 구현 합니다. `COleFrameHook`는의 구현에서 `IOleCommandTarget` `COleDocObjectItem` 파생 된 액티브 문서 컨테이너에 OLE 명령을 전달 합니다. 이렇게 하면 모든 MFC 활성 문서 컨테이너가 포함 된 활성 문서 서버에서 메시지를 받을 수 있습니다.

## <a name="mfc-ole-command-maps"></a>MFC OLE 명령 맵

MFC 개발자는 `IOleCommandTarget` MFC OLE 명령 맵을 사용 하 여를 활용할 수 있습니다. OLE 명령 맵은 메시지 맵과 비슷하며, 명령 맵을 포함 하는 클래스의 멤버 함수에 OLE 명령을 매핑하는 데 사용할 수 있습니다. 이 작업을 수행 하려면 명령 맵에 매크로를 추가 하 여 처리할 명령의 OLE 명령 그룹, OLE 명령 및 OLE 명령이 수신 될 때 전송 되는 [WM_COMMAND](/windows/win32/menurc/wm-command) 메시지의 명령 ID를 지정 합니다. 또한 MFC에서는 표준 OLE 명령에 대해 미리 정의 된 많은 매크로를 제공 합니다. 원래 Microsoft Office 응용 프로그램과 함께 사용 하도록 디자인 된 표준 OLE 명령의 목록은 docobj. h에 정의 된 OLECMDID 열거형을 참조 하세요.

Ole 명령 맵이 포함 된 MFC 응용 프로그램에서 OLE 명령이 수신 되 면 MFC는 응용 프로그램의 OLE 명령 맵에서 요청 된 명령에 대 한 명령 ID 및 명령 그룹을 찾으려고 시도 합니다. 일치 항목이 발견 되 면 요청 된 명령의 ID를 사용 하 여 명령 맵을 포함 하는 응용 프로그램에 WM_COMMAND 메시지가 발송 됩니다. 아래 설명을 참조 하십시오 `ON_OLECMD` . 이러한 방식으로 응용 프로그램에 디스패치 된 OLE 명령은 MFC에 의해 WM_COMMAND 메시지로 설정 됩니다. 그런 다음 WM_COMMAND 메시지는 MFC 표준 [명령 라우팅](../mfc/command-routing.md) 아키텍처를 사용 하 여 응용 프로그램의 메시지 맵을 통해 라우팅됩니다.

메시지 맵과 달리 MFC OLE 명령 맵은 클래스 마법사에서 지원 되지 않습니다. MFC 개발자는 OLE 명령 맵 지원 및 OLE 명령 맵 항목을 직접 추가 해야 합니다. OLE 명령 맵은 컨테이너에서 활성 문서가 활성 상태일 때 WM_COMMAND 메시지 라우팅 체인에 있는 모든 클래스의 MFC 활성 문서 서버에 추가할 수 있습니다. 이러한 클래스에는 [CWinApp](../mfc/reference/cwinapp-class.md), [CView](../mfc/reference/cview-class.md), [CDocument](../mfc/reference/cdocument-class.md)및 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)에서 파생 된 응용 프로그램 클래스가 포함 됩니다. 액티브 문서 컨테이너에서 OLE 명령 맵은 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)파생 클래스에만 추가할 수 있습니다. 또한 액티브 문서 컨테이너에서 WM_COMMAND 메시지는 파생 클래스의 메시지 맵으로만 디스패치 됩니다 `COleDocObjectItem` .

## <a name="ole-command-map-macros"></a>OLE 명령 맵 매크로

다음 매크로를 사용 하 여 클래스에 명령 맵 기능을 추가 합니다.

```cpp
DECLARE_OLECMD_MAP ()
```

이 매크로는 명령 맵을 포함 하는 클래스의 클래스 선언 (일반적으로 헤더 파일)로 이동 합니다.

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*theClass*<br/>
명령 맵을 포함 하는 클래스의 이름입니다.

*baseClass*<br/>
명령 맵을 포함 하는 클래스의 기본 클래스 이름입니다.

이 매크로는 명령 맵의 시작을 표시 합니다. 명령 맵을 포함 하는 클래스에 대 한 구현 파일에서이 매크로를 사용 합니다.

```
END_OLECMD_MAP()
```

이 매크로는 명령 맵의 끝을 표시 합니다. 명령 맵을 포함 하는 클래스에 대 한 구현 파일에서이 매크로를 사용 합니다. 이 매크로는 항상 BEGIN_OLECMD_MAP 매크로를 따라야 합니다.

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*<br/>
OLE 명령의 명령 그룹 GUID에 대 한 포인터입니다. 표준 OLE 명령 그룹의 경우이 매개 변수는 **NULL** 입니다.

*olecmdid*<br/>
호출할 명령의 OLE 명령 ID입니다.

*id*<br/>
이 OLE 명령이 호출 될 때 명령 맵을 포함 하는 응용 프로그램으로 보낼 WM_COMMAND 메시지의 ID입니다.

명령 맵의 ON_OLECMD 매크로를 사용 하 여 처리 하려는 OLE 명령에 대 한 항목을 추가 합니다. OLE 명령이 수신 되 면 지정 된 WM_COMMAND 메시지로 변환 되 고 표준 MFC 명령 라우팅 아키텍처를 사용 하 여 응용 프로그램의 메시지 맵을 통해 라우팅됩니다.

## <a name="example"></a>예제

다음 예에서는 ole 명령 [OLECMDID_PRINT](/windows/win32/api/docobj/ne-docobj-olecmdid) 를 처리 하는 MFC 활성 문서 서버에 ole 명령 처리 기능을 추가 하는 방법을 보여 줍니다. 이 예에서는 사용자가 응용 프로그램 마법사를 사용 하 여 활성 문서 서버인 MFC 응용 프로그램을 생성 했다고 가정 합니다.

1. `CView`파생 클래스의 헤더 파일에서 DECLARE_OLECMD_MAP 매크로를 클래스 선언에 추가 합니다.

    > [!NOTE]
    > `CView`-Derived 클래스는 WM_COMMAND 메시지 라우팅 체인에 있는 활성 문서 서버의 클래스 중 하나 이기 때문에 사용 합니다.

    ```cpp
    class CMyServerView : public CView
    {
    protected: // create from serialization only
        CMyServerView();
        DECLARE_DYNCREATE(CMyServerView)
        DECLARE_OLECMD_MAP()
        // . . .
    };
    ```

2. 파생 클래스에 대 한 구현 파일에서 `CView` BEGIN_OLECMD_MAP 및 END_OLECMD_MAP 매크로를 추가 합니다.

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. 표준 OLE 인쇄 명령을 처리 하려면 표준 인쇄 명령에 대 한 OLE 명령 ID를 지정 하 고 WM_COMMAND ID에 **ID_FILE_PRINT** 명령 맵에 [ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd) 매크로를 추가 합니다. **ID_FILE_PRINT** 은 응용 프로그램 마법사에서 생성 된 MFC 응용 프로그램에서 사용 하는 표준 인쇄 명령 ID입니다.

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

Afxdocob에 정의 된 표준 OLE 명령 매크로 중 하나는 **OLECMDID_PRINT** 표준 OLE 명령 ID 이므로 ON_OLECMD 매크로 대신 사용할 수 있습니다. ON_OLECMD_PRINT 매크로는 위에 표시 된 ON_OLECMD 매크로와 동일한 작업을 수행 합니다.

컨테이너 응용 프로그램에서이 서버를 서버 인터페이스를 통해 **OLECMDID_PRINT** 명령으로 보내면 서버 `IOleCommandTarget` 에서 MFC 인쇄 명령 처리기가 호출 되어 서버에서 응용 프로그램을 인쇄 합니다. 위의 단계에서 추가 된 인쇄 명령을 호출 하는 액티브 문서 컨테이너의 코드는 다음과 같습니다.

```cpp
void CContainerCntrItem::DoOleCmd()
{
    IOleCommandTarget *pCmd = NULL;
    HRESULT hr = E_FAIL;
    OLECMD ocm={OLECMDID_PRINT, 0};

    hr = m_lpObject->QueryInterface(
        IID_IOleCommandTarget,reinterpret_cast<void**>(&pCmd));

    if (FAILED(hr))
        return;

    hr = pCmd->QueryStatus(NULL, 1, &ocm, NULL);

    if (SUCCEEDED(hr) && (ocm.cmdf& OLECMDF_ENABLED))
    {
        //Command is available and enabled so call it
        COleVariant vIn;
        COleVariant vOut;
        hr = pCmd->Exec(NULL, OLECMDID_PRINT,
            OLECMDEXECOPT_DODEFAULT, &vIn, &vOut);
        ASSERT(SUCCEEDED(hr));
    }
    pCmd->Release();
}
```

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
