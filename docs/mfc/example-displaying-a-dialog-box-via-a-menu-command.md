---
description: '자세한 정보: 예제: 메뉴 명령을 통해 대화 상자 표시'
title: '예: 메뉴 명령을 통해 대화 상자 표시'
ms.date: 09/07/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
ms.openlocfilehash: dcfa34eb05733d2f27176795a447e15949d6e274
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290858"
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>예: 메뉴 명령을 통해 대화 상자 표시

이 항목에는 다음 절차가 포함 되어 있습니다.

- 메뉴 명령을 통해 모달 대화 상자를 표시 합니다.

- 메뉴 명령을 통해 모덜리스 대화 상자를 표시 합니다.

두 샘플 프로시저는 모두 MFC 응용 프로그램을 위한 것 이며 [Mfc 응용 프로그램 마법사](reference/mfc-application-wizard.md)를 사용 하 여 만든 응용 프로그램에서 작동 합니다.

프로시저는 다음 이름 및 값을 사용 합니다.

|항목|이름 또는 값|
|----------|-------------------|
|애플리케이션|DisplayDialog|
|메뉴 명령입니다.|보기 메뉴의 테스트 명령 명령 ID = ID_VIEW_TEST|
|대화 상자|테스트 대화 상자 Class = CTestDialog; 헤더 파일 = TestDialog .h; Variable = testdlg, ptestdlg|
|명령 처리기|OnViewTest|

### <a name="to-display-a-modal-dialog-box"></a>모달 대화 상자를 표시 하려면

1. 메뉴 명령을 만듭니다. [메뉴 또는 메뉴 항목 만들기](../windows/menu-editor.md)를 참조 하세요.

1. 대화 상자를 만듭니다. [대화 상자 편집기 시작을](../windows/creating-a-new-dialog-box.md)참조 하세요.

1. 대화 상자에 대 한 클래스를 추가 합니다. 자세한 내용은 [클래스 추가를](../ide/adding-a-class-visual-cpp.md) 참조 하세요.

1. **클래스 뷰** 에서 문서 클래스 (CDisplayDialogDoc)를 선택 합니다. **속성** 창에서 **이벤트** 단추를 클릭합니다. 메뉴 명령의 ID (ID_VIEW_TEST)를 두 번 클릭 합니다. 그런 다음 아래쪽 화살표를 클릭 하 고 **\<Add> onviewtest** 를 선택 합니다.

   MDI 응용 프로그램의 메인프레임에 메뉴 명령을 추가한 경우 응용 프로그램 클래스 (CDisplayDialogApp)를 대신 선택 합니다.

1. 기존 include 문 뒤에 CDisplayDialogDoc (또는 Cdisplaydialogdoc)에 다음 include 문을 추가 합니다.

   ```cpp
   #include "TestDialog.h"
   ```

1. 다음 코드를에 추가 하 여 `OnViewTest` 함수를 구현 합니다.

   ```cpp
   CTestDialog testdlg;
   testdlg.DoModal();
   ```

### <a name="to-display-a-modeless-dialog-box"></a>모덜리스 대화 상자를 표시 하려면

1. 4 단계에서 뷰 클래스 (CDisplayDialogView)를 선택 하는 것을 제외 하 고 처음 네 단계를 수행 하 여 모달 대화 상자를 표시 합니다.

1. DisplayDialogView .h를 편집 합니다.

   - 첫 번째 클래스 선언 앞에 대화 상자 클래스를 선언 합니다.

   ```cpp
   class CTestDialog;
   ```

   - 특성 public 섹션 뒤의 대화 상자에 대 한 포인터를 선언 합니다.

   ```cpp
   CTestDialog* m_pTestDlg;
   ```

1. DisplayDialogView .cpp를 편집 합니다.

   - 기존 include 문 뒤에 다음 include 문을 추가 합니다.

   ```cpp
   #include "TestDialog.h"
   ```

   - 생성자에 다음 코드를 추가 합니다.

   ```cpp
   m_pTestDlg = NULL;
   ```

   - 소멸자에 다음 코드를 추가 합니다.

   ```cpp
   delete m_pTestDlg;
   ```

   - 다음 코드를에 추가 하 여 `OnViewTest` 함수를 구현 합니다.

   ```cpp
   if (NULL == m_pTestDlg)
   {
      m_pTestDlg = new CTestDialog(this);
      m_pTestDlg->Create(CTestDialog::IDD, this);
   }
   m_pTestDlg->ShowWindow(SW_SHOW);
   ```

## <a name="see-also"></a>참고 항목

[대화 상자](dialog-boxes.md)<br/>
[모달 및 모덜리스 대화 상자](modal-and-modeless-dialog-boxes.md)
