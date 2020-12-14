---
description: '자세히 알아보기: 대화 상자 클래스 만들기'
title: 대화 상자 클래스 만들기
ms.date: 09/06/2019
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
ms.openlocfilehash: d135d6acaefbc73f435e48db8f72add7081fdac2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309448"
---
# <a name="creating-your-dialog-class"></a>대화 상자 클래스 만들기

프로그램의 각 대화 상자에 대해 대화 상자 리소스를 사용 하는 새 대화 상자 클래스를 만듭니다.

[클래스를 추가](../ide/adding-a-class-visual-cpp.md) 하면 새 대화 상자 클래스를 만드는 방법을 설명 합니다. [클래스 마법사](reference/mfc-class-wizard.md)를 사용 하 여 대화 상자 클래스를 만들면 사용자가 지정 하는 .h 및 .cpp 파일에 다음 항목이 작성 됩니다.

.H 파일에서 다음을 수행 합니다.

- 대화 상자 클래스에 대 한 클래스 선언입니다. 클래스는 [CDialog](reference/cdialog-class.md)에서 파생 됩니다.

.Cpp 파일에서 다음을 수행 합니다.

- 클래스에 대 한 메시지 맵입니다.

- 대화 상자에 대 한 표준 생성자입니다.

- [DoDataExchange](reference/cwnd-class.md#dodataexchange) 멤버 함수의 재정의입니다. 이 함수를 편집 합니다. 대화 [상자 데이터 교환 및 유효성 검사](dialog-data-exchange-and-validation.md)의 뒷부분에 설명 된 대로 대화 상자 데이터 교환 및 유효성 검사 기능에 사용 됩니다.

## <a name="see-also"></a>참고 항목

[코드 마법사로 대화 상자 클래스 만들기](creating-a-dialog-class-with-code-wizards.md)<br/>
[MFC에서 대화 상자를 통해 작업](life-cycle-of-a-dialog-box.md)
