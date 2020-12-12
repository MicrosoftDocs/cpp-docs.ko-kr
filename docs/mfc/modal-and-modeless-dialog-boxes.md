---
description: '자세히 알아보기: 모달 및 모덜리스 대화 상자'
title: 모달 및 모덜리스 대화 상자
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: 11320c2efcb323fe839afecb6165409285f442aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251143"
---
# <a name="modal-and-modeless-dialog-boxes"></a>모달 및 모덜리스 대화 상자

[CDialog](reference/cdialog-class.md) 클래스를 사용 하 여 두 가지 종류의 대화 상자를 관리할 수 있습니다.

- 프로그램을 계속 하기 전에 사용자가 응답 해야 하는 *모달 대화 상자*

- 화면에 유지 되 고 언제 든 지 사용할 수 있지만 다른 사용자 작업을 허용 하는 *모덜리스 대화 상자*

대화 상자 템플릿을 만들기 위한 리소스 편집 및 절차는 모달 및 모덜리스 대화 상자에서 동일 합니다.

프로그램에 대 한 대화 상자를 만들려면 다음 단계를 수행 해야 합니다.

1. 대화 상자 [편집기](../windows/dialog-editor.md) 를 사용 하 여 대화 상자를 디자인 하 고 대화 상자 템플릿 리소스를 만듭니다.

1. 대화 상자 클래스를 만듭니다.

1. 대화 상자 클래스의 [메시지 처리기에 대화 상자 리소스의 컨트롤을](../windows/adding-editing-or-deleting-controls.md) 연결 합니다.

1. 대화 상자 컨트롤과 연결 된 데이터 멤버를 추가 하 고 컨트롤에 대 한 대화 상자 [데이터 교환](dialog-data-exchange.md) 및 [대화 상자 데이터 유효성 검사](dialog-data-validation.md) 를 지정 합니다.

## <a name="see-also"></a>참고 항목

[대화 상자](dialog-boxes.md)<br/>
[MFC에서 대화 상자를 통해 작업](life-cycle-of-a-dialog-box.md)
