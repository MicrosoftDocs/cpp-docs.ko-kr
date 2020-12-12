---
description: 'ActiveX 컨트롤 컨테이너: activex 컨트롤을 멤버 변수에 연결에 대 한 자세한 정보'
title: 'ActiveX 컨트롤 컨테이너: ActiveX 컨트롤을 멤버 변수에 연결'
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- ActiveX controls [MFC], member variables of project
- connecting ActiveX controls to container member variables
- ActiveX controls [MFC], accessing
- member variables [MFC], ActiveX controls in project
- ActiveX control containers [MFC], ActiveX controls as member variables
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
ms.openlocfilehash: c3b890b5705624a18ec42583b143fbd33e4f0608
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271904"
---
# <a name="activex-control-containers-connecting-an-activex-control-to-a-member-variable"></a>ActiveX 컨트롤 컨테이너: ActiveX 컨트롤을 멤버 변수에 연결

컨트롤 컨테이너 응용 프로그램 내에서 ActiveX 컨트롤에 액세스 하는 가장 쉬운 방법은 ActiveX 컨트롤을 컨트롤을 포함 하는 대화 상자 클래스의 멤버 변수와 연결 하는 것입니다.

> [!NOTE]
> 이는 컨테이너 클래스 내에서 포함 된 컨트롤에 액세스 하는 유일한 방법은 아니지만이 문서의 목적을 위해 충분 합니다.

### <a name="adding-a-member-variable-to-the-dialog-class"></a>대화 상자 클래스에 멤버 변수 추가

1. 클래스 뷰에서 주 대화 상자 클래스를 마우스 오른쪽 단추로 클릭 하 여 바로 가기 메뉴를 엽니다. 예: `CContainerDlg`.

1. 바로 가기 메뉴에서 **추가** 를 클릭 하 고 **변수 추가** 를 클릭 합니다.

1. 멤버 변수 추가 마법사에서 **제어 변수** 를 클릭 합니다.

1. **컨트롤 id** 목록 상자에서 포함 된 ActiveX 컨트롤의 컨트롤 id를 선택 합니다. 예: `IDC_CIRCCTRL1`.

1. **변수 이름** 상자에 이름을 입력 합니다.

   예를 들어 *m_circctl* 합니다.

1. **마침** 을 클릭 하 여 선택 사항을 적용 하 고 멤버 변수 추가 마법사를 종료 합니다.

## <a name="see-also"></a>참고 항목

[ActiveX 컨트롤 컨테이너](activex-control-containers.md)
