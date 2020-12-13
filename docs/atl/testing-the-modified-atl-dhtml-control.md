---
description: '자세히 알아보기: 수정 된 ATL DHTML 컨트롤 테스트'
title: 수정 된 ATL DHTML 컨트롤 테스트
ms.date: 11/06/2018
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls, testing
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
ms.openlocfilehash: a797eab308ad7fb8c5c7b72566ec3d57a169370b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138335"
---
# <a name="testing-the-modified-atl-dhtml-control"></a>수정 된 ATL DHTML 컨트롤 테스트

새 컨트롤을 사용해 보고 지금 어떻게 작동 하는지 알아보세요.

## <a name="to-build-and-test-the-modified-control"></a>수정 된 컨트롤을 빌드하고 테스트 하려면

1. 프로젝트를 다시 빌드하고 **테스트 컨테이너** 에서 엽니다. **테스트 컨테이너** 에 액세스 하는 방법에 대 한 자세한 내용은 [테스트 컨테이너로 속성 및 이벤트](../mfc/testing-properties-and-events-with-test-container.md) 테스트를 참조 하세요.

   추가한 모든 단추를 표시 하도록 컨트롤의 크기를 조정 합니다.

1. HTML을 변경 하 여 삽입 한 두 단추를 검사 합니다. 각 단추에는 [ATL DHTML 컨트롤을 수정할](../atl/modifying-the-atl-dhtml-control.md)때 확인 한 레이블 ( **Refresh** 및 **HelloHTML**)이 있습니다.

1. 두 개의 새 단추를 테스트 하 여 작동 방식을 확인 합니다.

이제 UI의 일부가 아닌 메서드를 테스트 합니다.

1. 테두리를 활성화 하도록 컨트롤을 강조 표시 합니다.

1. **컨트롤** 메뉴에서 **메서드 호출** 을 선택 합니다.

   **메서드 이름** 목록에서 메서드는 컨테이너에서 호출할 수 있는 메서드 (및)입니다. `MethodInvoked` `GoToURL` 다른 모든 메서드는 UI에 의해 제어 됩니다.

1. 호출할 메서드를 선택 하 고 **호출** 을 선택 하 여 메서드의 메시지 상자를 표시 하거나로 이동 `www.microsoft.com` 합니다.

1. **메서드 호출** 대화 상자에서 **닫기** 를 선택 합니다.

ATL DHTML 컨트롤을 구성 하는 다양 한 요소 및 파일에 대해 자세히 알아보려면 [DHTML 컨트롤 프로젝트의 요소 식별](../atl/identifying-the-elements-of-the-dhtml-control-project.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[DHTML 컨트롤에 대한 지원](../atl/atl-support-for-dhtml-controls.md)
