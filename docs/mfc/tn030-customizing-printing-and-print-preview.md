---
description: '자세히 알아보기: TN030: 인쇄 및 인쇄 미리 보기 사용자 지정'
title: 'TN030: 인쇄 및 인쇄 미리 보기 사용자 지정'
ms.date: 06/28/2018
f1_keywords:
- vc.print
helpviewer_keywords:
- TN030
- customizing printing and print preview
- printing [MFC], views
- printing views [MFC]
- print preview [MFC], customizing
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
ms.openlocfilehash: 6fc0571b908f85b24b8a0752a00842077d537dce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215614"
---
# <a name="tn030-customizing-printing-and-print-preview"></a>TN030: 인쇄 및 인쇄 미리 보기 사용자 지정

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 참고에서는 인쇄 및 인쇄 미리 보기를 사용자 지정 하는 프로세스를 설명 하 고 `CView` ,의 콜백 루틴 및의 멤버 함수에 사용 되는 콜백 루틴의 용도에 대해 설명 합니다 `CPreviewView` .

## <a name="the-problem"></a>문제

MFC는 대부분의 인쇄 및 인쇄 미리 보기 요구 사항에 대 한 완전 한 솔루션을 제공 합니다. 대부분의 경우에는 보기를 인쇄 하 고 미리 볼 수 있는 추가 코드가 필요 하지 않습니다. 그러나 개발자의 일부에 대해 상당한 노력이 필요 하 고 일부 응용 프로그램은 인쇄 미리 보기 모드에 특정 사용자 인터페이스 요소를 추가 해야 하는 인쇄를 최적화 하는 방법이 있습니다.

## <a name="efficient-printing"></a>효율적인 인쇄

MFC 응용 프로그램이 표준 메서드를 사용 하 여 인쇄 하면 Windows는 모든 GDI (그래픽 장치 인터페이스) 출력 호출을 메모리 내 메타 파일로 보냅니다. `EndPage`가 호출 되 면 Windows는 프린터에서 한 페이지를 인쇄 하는 데 필요한 각 실제 밴드에 대해 메타 파일을 한 번씩 재생 합니다. 이 렌더링 중에 GDI는 중단 프로시저를 자주 쿼리하여 계속 해야 하는지 확인 합니다. 일반적으로 abort 프로시저를 사용 하면 사용자가 인쇄 대화 상자를 사용 하 여 인쇄 작업을 중단할 수 있도록 메시지를 처리할 수 있습니다.

그러나 이렇게 하면 인쇄 프로세스가 느려질 수 있습니다. 응용 프로그램의 인쇄가 표준 기술을 사용 하 여 달성할 수 있는 속도 보다 빠른 경우 수동 개요를 구현 해야 합니다.

## <a name="print-banding"></a>인쇄 줄무늬

수동으로 밴드를 조정 하려면 페이지당 `OnPrint` 한 번씩 여러 번 호출 되는 인쇄 루프를 다시 구현 해야 합니다. 인쇄 루프가 `OnFilePrint` viewprnt의 함수에서 구현 됩니다. `CView`파생 클래스에서 인쇄 명령을 처리 하기 위한 메시지 맵 항목이 인쇄 함수를 호출 하도록이 함수를 오버 로드 합니다. 루틴을 복사 하 `OnFilePrint` 고 인쇄 루프를 변경 하 여 밴딩을 구현 합니다. 인쇄 중인 페이지의 섹션을 기준으로 그리기를 최적화할 수 있도록 줄무늬 사각형을 인쇄 함수에 전달 하는 것도 좋습니다.

두 번째로, `QueryAbort` 밴드를 그리는 동안를 자주 호출 해야 합니다. 그렇지 않으면 Abort 프로시저가 호출 되지 않고 사용자가 인쇄 작업을 취소할 수 없게 됩니다.

## <a name="print-preview-electronic-paper-with-user-interface"></a>인쇄 미리 보기: 사용자 인터페이스가 포함 된 전자 용지

인쇄 미리 보기는 기본적으로 디스플레이를 프린터 에뮬레이션으로 전환 하려고 시도 합니다. 기본적으로 주 창의 클라이언트 영역은 창에 하나 또는 두 개의 페이지를 완전히 표시 하는 데 사용 됩니다. 사용자는 페이지의 영역을 확대 하 여 더 자세히 볼 수 있습니다. 추가 지원을 통해 사용자가 미리 보기 모드에서 문서를 편집 하도록 허용할 수도 있습니다.

## <a name="customizing-print-preview"></a>인쇄 미리 보기 사용자 지정

이 메모는 인쇄 미리 보기를 수정 하는 한 가지 측면을 다룹니다. 미리 보기 모드에 UI를 추가 합니다. 다른 수정 작업을 수행할 수 있지만 이러한 변경 내용은이 논의의 범위를 벗어나는 것입니다.

## <a name="to-add-ui-to-the-preview-mode"></a>미리 보기 모드에 UI를 추가 하려면

1. 에서 뷰 클래스를 파생 시킵니다 `CPreviewView` .

2. 원하는 UI 요소에 대 한 명령 처리기를 추가 합니다.

3. 시각적 요소를 표시에 추가 하는 경우를 `OnDraw` 호출한 후에 그리기를 재정의 하 고 수행 `CPreviewView::OnDraw` 합니다.

## <a name="onfileprintpreview"></a>OnFilePrintPreview

인쇄 미리 보기에 대 한 명령 처리기입니다. 기본 구현은 다음과 같습니다.

```cpp
void CView::OnFilePrintPreview()
{
    // In derived classes, implement special window handling here
    // Be sure to Unhook Frame Window close if hooked.

    // must not create this on the frame. Must outlive this function
    CPrintPreviewState* pState = new CPrintPreviewState;

    if (!DoPrintPreview(AFX_IDD_PREVIEW_TOOLBAR, this,
        RUNTIME_CLASS(CPreviewView), pState))
    {
        // In derived classes, reverse special window handling
        // here for Preview failure case

        TRACE0("Error: DoPrintPreview failed");
        AfxMessageBox(AFX_IDP_COMMAND_FAILURE);
        delete pState;  // preview failed to initialize, delete State now
    }
}
```

`DoPrintPreview` 응용 프로그램의 주 창을 숨깁니다. 상태 표시줄과 같은 컨트롤 막대는 pState->*Dwstates* 멤버에 지정 하 여 유지할 수 있습니다 .이는 비트 마스크 이며 개별 컨트롤 막대의 비트는 AFX_CONTROLBAR_MASK (AFX_IDW_MYBAR)에 의해 정의 됩니다. *NIDMainPane* >창에는 자동으로 숨겨지거나 reshown 창이 표시 됩니다. `DoPrintPreview` 그런 다음 표준 미리 보기 UI에 대 한 단추 모음을 만듭니다. 다른 창을 숨기 거 나 표시 하는 등의 특수 창 처리가 필요한 경우를 호출 하기 전에 수행 해야 합니다 `DoPrintPreview` .

기본적으로 인쇄 미리 보기가 완료 되 면 컨트롤 막대를 원래 상태와 표시 되는 주 창으로 되돌립니다. 특수 처리가 필요한 경우의 재정의에서 수행 해야 합니다 `EndPrintPreview` . `DoPrintPreview`가 실패 하면 특별 한 처리도 제공 합니다.

DoPrintPreview는 다음을 사용 하 여 호출 됩니다.

- 미리 보기 도구 모음에 대 한 대화 상자 템플릿의 리소스 ID입니다.

- 인쇄 미리 보기 인쇄를 수행 하는 뷰에 대 한 포인터입니다.

- Preview 뷰 클래스의 런타임 클래스입니다. 이는 DoPrintPreview에서 동적으로 만들어집니다.

- CPrintPreviewState 포인터입니다. CPrintPreviewState 구조 (또는 응용 프로그램에 더 많은 상태를 유지 해야 하는 경우 파생 된 구조)는 프레임에 생성 *되지* 않아야 합니다. DoPrintPreview는 모덜리스이 고 EndPrintPreview가 호출 될 때까지이 구조가 존속 되어야 합니다.

  > [!NOTE]
  > 인쇄 지원에 별도의 뷰나 뷰 클래스가 필요한 경우 해당 개체에 대 한 포인터를 두 번째 매개 변수로 전달 해야 합니다.

## <a name="endprintpreview"></a>EndPrintPreview

이를 호출 하 여 인쇄 미리 보기 모드를 종료 합니다. 인쇄 미리 보기에 마지막으로 표시 된 문서의 페이지로 이동 하는 것이 바람직한 경우가 종종 있습니다. `EndPrintPreview` 응용 프로그램에서이 작업을 수행할 수 있는 기회입니다. PInfo->*m_nCurPage* 멤버는 마지막으로 표시 된 페이지 (두 페이지가 표시 된 경우 맨 왼쪽)이 고 포인터는 사용자가 관심을 가진 페이지의 위치에 대 한 힌트입니다. 응용 프로그램의 뷰 구조는 프레임 워크에서 알 수 없기 때문에 선택한 지점으로 이동 하는 코드를 제공 해야 합니다.

를 호출 하기 전에 대부분의 작업을 수행 해야 `CView::EndPrintPreview` 합니다. 이 호출은 `DoPrintPreview` pView, pDC 및 pInfo의 영향을 취소 하 고 삭제 합니다.

```cpp
// Any further cleanup should be done here.
CView::EndPrintPreview(pDC, pInfo, point, pView);
```

## <a name="cwinapponfileprintsetup"></a>CWinApp:: OnFilePrintSetup

이 항목은 인쇄 설정 메뉴 항목에 대해 매핑되어야 합니다. 대부분의 경우에는 구현을 재정의할 필요가 없습니다.

## <a name="page-nomenclature"></a>페이지 명명법

또 다른 문제는 페이지 번호 매기기 및 주문입니다. 간단한 워드 프로세서 유형 응용 프로그램의 경우이는 간단한 문제입니다. 대부분의 인쇄 미리 보기 시스템에서는 인쇄 된 각 페이지가 문서의 한 페이지에 해당 하는 것으로 가정 합니다.

일반화 된 솔루션을 제공 하려는 경우 몇 가지 사항을 고려해 야 합니다. CAD 시스템을 가정 합니다. 사용자에 게 여러 E 크기 시트를 포함 하는 그리기가 있습니다. 전자 크기 (또는 더 작은 크기의 크기의 플로터)에서 페이지 번호 매기기는 간단한 경우와 같습니다. 그러나 레이저 프린터에서 용지당 16 개의 페이지 인쇄, 인쇄 미리 보기에서 "페이지"를 고려 하는 내용

소개 단락 상태로 인쇄 미리 보기는 프린터 처럼 작동 합니다. 따라서 사용자는 선택한 특정 프린터에서 제공 되는 항목을 확인할 수 있습니다. 각 페이지에 인쇄 되는 이미지를 결정 하는 것은 보기에 있습니다.

구조에 있는 페이지 설명 문자열은 `CPrintInfo` "페이지 1" 또는 "페이지 1-2"와 같이 페이지당 하나의 숫자로 표시할 수 있는 경우 사용자에 게 페이지 번호를 표시 하는 방법을 제공 합니다. 이 문자열은의 기본 구현에서 사용 됩니다 `CPreviewView::OnDisplayPageNumber` . 다른 표시를 수행 해야 하는 경우이 가상 함수를 재정의 하 여 "Sheet1, 섹션 A, B"를 제공할 수 있습니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
