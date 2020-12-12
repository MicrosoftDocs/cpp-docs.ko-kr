---
description: '자세한 정보: MFC에서 대화 상자 작업'
title: MFC에서 대화 상자를 통해 작업
ms.date: 09/27/2019
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
ms.openlocfilehash: 5e88d34ab26f8abd24923aacafa02c3c62ec7f06
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327795"
---
# <a name="working-with-dialog-boxes-in-mfc"></a>MFC에서 대화 상자를 통해 작업

대화 상자의 수명 주기 동안 사용자가 대화 상자를 호출 합니다 .이 대화 상자는 일반적으로 대화 상자 개체를 만들고 초기화 하는 명령 처리기 내에서 사용자가 대화 상자와 상호 작용 한 다음 대화 상자를 닫습니다.

모달 대화 상자의 경우 처리기는 대화 상자를 닫을 때 사용자가 입력 한 데이터를 수집 합니다. Dialog 개체는 대화 상자 창이 닫힌 후에도 존재 하므로 대화 상자 클래스의 멤버 변수를 사용 하 여 데이터를 추출할 수 있습니다.

모덜리스 대화 상자의 경우 대화 상자를 계속 표시 하는 동안 대화 상자 개체에서 데이터를 추출 하는 경우가 종종 있습니다. 특정 시점에 대화 상자 개체가 제거 됩니다. 이러한 상황이 발생 하는 경우에는 코드에 따라 달라 집니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [대화 상자 만들기 및 표시](creating-and-displaying-dialog-boxes.md)

- [모달 대화 상자 만들기](creating-modal-dialog-boxes.md)

- [모덜리스 대화 상자 만들기](creating-modeless-dialog-boxes.md)

- [메모리의 대화 상자 템플릿 사용](using-a-dialog-template-in-memory.md)

- [대화 상자의 배경색 설정](setting-the-dialog-boxs-background-color.md)

- [대화 상자 초기화](initializing-the-dialog-box.md)

- [대화 상자에서 Windows 메시지 처리](handling-windows-messages-in-your-dialog-box.md)

- [대화 상자 개체에서 데이터 검색](retrieving-data-from-the-dialog-object.md)

- [대화 상자 닫기](closing-the-dialog-box.md)

- [대화 상자 소멸시키기](destroying-the-dialog-box.md)

- [DDX (대화 상자 데이터 교환) 및 유효성 검사 (DDV)](dialog-data-exchange-and-validation.md)

- [속성 시트 대화 상자](property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>참고 항목

[대화 상자](dialog-boxes.md)
