---
description: '자세히 알아보기: 뷰를 통해 사용자 입력 해석'
title: 뷰를 통해 사용자 입력 해석
ms.date: 11/04/2016
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
ms.openlocfilehash: f3442a13bc60b7424840e23673806c1e5120c4ad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335835"
---
# <a name="interpreting-user-input-through-a-view"></a>뷰를 통해 사용자 입력 해석

뷰의 다른 멤버 함수는 모든 사용자 입력을 처리 하 고 해석 합니다. 일반적으로 다음과 같이 처리 하기 위해 뷰 클래스에서 메시지 처리기 멤버 함수를 정의 합니다.

- 마우스 및 키보드 작업을 통해 생성 되는 Windows [메시지](messages.md) 입니다.

- 메뉴, 도구 모음 단추 및 액셀러레이터 키의 [명령](user-interface-objects-and-command-ids.md) 입니다.

이러한 메시지 처리기 멤버 함수는 데이터를 클립보드로 이동 하거나 클립보드에서 데이터를 이동 하는 작업을 포함 하 여 다음 작업을 데이터 입력, 선택 또는 편집으로 해석 합니다.

- 마우스 이동 및 클릭, 끌기 및 두 번 클릭

- 누르는

- 메뉴 명령

뷰가 처리 하는 Windows 메시지는 응용 프로그램의 요구 사항에 따라 달라 집니다.

[메시지 처리 및 매핑 항목](message-handling-and-mapping.md) 에서는 메뉴 항목과 기타 사용자 인터페이스 개체를 명령에 할당 하는 방법과 명령을 처리기 함수에 바인딩하는 방법에 대해 설명 합니다. [메시지 처리 및 매핑 항목](message-handling-and-mapping.md) 에서는 MFC가 명령을 라우팅하고 표준 Windows 메시지를 해당 개체에 대 한 처리기를 포함 하는 개체로 보내는 방법에 대해서도 설명 합니다.

예를 들어 응용 프로그램은 뷰에서 직접 마우스 그리기를 구현 해야 할 수 있습니다. Scribble 샘플은 각각 WM_LBUTTONDOWN, WM_MOUSEMOVE 및 WM_LBUTTONUP 메시지를 처리 하 여 줄 세그먼트의 그리기를 시작, 계속 및 종료 하는 방법을 보여 줍니다. 반면, 보기에서 마우스를 클릭 하 여 선택 항목으로 해석 해야 하는 경우도 있습니다. 뷰의 `OnLButtonDown` 처리기 함수는 사용자가 그리거나 선택 했는지 여부를 확인 합니다. 선택 하는 경우 처리기는 클릭이 뷰에 있는 일부 개체의 범위 내에 있는지 여부를 확인 하 고, 그럴 경우 표시를 변경 하 여 개체를 선택 된 상태로 표시 합니다.

뷰는 편집 메뉴에서 클립보드를 사용 하 여 선택한 데이터를 잘라내거나 복사 하거나 붙여넣거나 삭제 하는 것과 같은 특정 메뉴 명령을 처리할 수도 있습니다. 이러한 처리기는 클래스의 클립보드 관련 멤버 함수 중 일부를 호출 `CWnd` 하 여 선택한 데이터 항목을 클립보드에서 또는 클립보드에서 전송 합니다.

## <a name="see-also"></a>참고 항목

[뷰 사용](using-views.md)
