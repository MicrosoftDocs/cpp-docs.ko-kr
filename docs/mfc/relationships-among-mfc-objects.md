---
description: '자세한 정보: MFC 개체 간 관계'
title: MFC 개체 간 관계
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
ms.openlocfilehash: 0646d487d1d60293461316edddcb97fde30905a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218058"
---
# <a name="relationships-among-mfc-objects"></a>MFC 개체 간 관계

문서/뷰 만들기 프로세스를 큐브 뷰에 추가 하는 데 도움이 되도록 문서, 뷰를 포함 하는 데 사용 되는 프레임 창 및 문서와 연결 된 뷰를 실행 하는 프로그램을 고려해 보세요.

- 문서는 해당 문서의 뷰 목록과 문서를 만든 문서 템플릿에 대 한 포인터를 유지 합니다.

- 뷰는 해당 문서에 대 한 포인터를 유지 하 고 부모 프레임 창의 자식입니다.

- 문서 프레임 창은 현재 활성 뷰에 대 한 포인터를 유지 합니다.

- 문서 템플릿은 열려 있는 문서의 목록을 보관 합니다.

- 응용 프로그램은 해당 문서 템플릿 목록을 보관 합니다.

- Windows는 메시지를 보낼 수 있도록 열려 있는 모든 창을 추적 합니다.

이러한 관계는 문서/뷰를 만드는 동안 설정 됩니다. 다음 표에서는 실행 중인 프로그램의 개체가 다른 개체에 액세스할 수 있는 방법을 보여 줍니다. 모든 개체는 [AfxGetApp](../mfc/reference/application-information-and-management.md#afxgetapp)전역 함수를 호출 하 여 응용 프로그램 개체에 대 한 포인터를 가져올 수 있습니다.

### <a name="gaining-access-to-other-objects-in-your-application"></a>응용 프로그램의 다른 개체에 대 한 액세스 권한 얻기

|From 개체|다른 개체에 액세스 하는 방법|
|-----------------|---------------------------------|
|문서|[Getfirstviewposition](../mfc/reference/cdocument-class.md#getfirstviewposition) 및 [GetNextView](../mfc/reference/cdocument-class.md#getnextview) 를 사용 하 여 문서의 뷰 목록에 액세스 합니다.<br /><br /> [Getdoctemplate](../mfc/reference/cdocument-class.md#getdoctemplate) 을 호출 하 여 문서 템플릿을 가져옵니다.|
|보기|[Getdocument](../mfc/reference/cview-class.md#getdocument) 를 호출 하 여 문서를 가져옵니다.<br /><br /> [GetParentFrame](../mfc/reference/cwnd-class.md#getparentframe) 를 호출 하 여 프레임 창을 가져옵니다.|
|문서 프레임 창|[Getactiveview](../mfc/reference/cframewnd-class.md#getactiveview) 를 호출 하 여 현재 뷰를 가져옵니다.<br /><br /> [GetActiveDocument](../mfc/reference/cframewnd-class.md#getactivedocument) 를 호출 하 여 현재 뷰에 첨부 된 문서를 가져옵니다.|
|MDI 프레임 창|[Mdigetactive](../mfc/reference/cmdiframewnd-class.md#mdigetactive) 를 호출 하 여 현재 활성 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)를 가져옵니다.|

일반적으로 프레임 창에는 하나의 뷰가 있지만 때때로 분할자 창에는 동일한 프레임 창에 여러 뷰가 포함 되어 있습니다. 프레임 창은 현재 활성 뷰에 대 한 포인터를 유지 합니다. 포인터는 다른 뷰가 활성화 될 때마다 업데이트 됩니다.

> [!NOTE]
> 주 프레임 창에 대 한 포인터는 응용 프로그램 개체의 [m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd) 멤버 변수에 저장 됩니다. `OnFileNew`집합의 멤버 함수 재정의에서를 호출 하면 `InitInstance` `CWinApp` *m_pMainWnd* . 를 호출 하지 않으면 `OnFileNew` 직접 변수의 값을 설정 해야 합니다 `InitInstance` . 프로그램이/embedding가 명령줄에 있으면 SDI COM 구성 요소 (서버) 응용 프로그램에서 변수를 설정 하지 않을 수 있습니다. *M_pMainWnd* 은 이제이 아닌 클래스의 멤버입니다 `CWinThread` `CWinApp` .

## <a name="see-also"></a>참고 항목

[문서 템플릿 및 문서/뷰 만들기 프로세스](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[문서 템플릿 만들기](../mfc/document-template-creation.md)<br/>
[문서/뷰 만들기](../mfc/document-view-creation.md)<br/>
[새 문서, 창 및 뷰 만들기](../mfc/creating-new-documents-windows-and-views.md)
