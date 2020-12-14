---
description: '자세히 알아보기: 대화 상자 만들기 및 표시'
title: 대화 상자 만들기 및 표시
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
ms.openlocfilehash: 9865e43392021cc7ba1349a73bffb8e47f4cca9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309827"
---
# <a name="creating-and-displaying-dialog-boxes"></a>대화 상자 만들기 및 표시

대화 상자 개체 만들기는 2단계 작업입니다. 먼저, 대화 상자 개체를 생성한 다음 대화 상자 창을 만듭니다. 모달 및 모덜리스 대화 상자는 만들고 표시하는 과정에서 차이가 있습니다. 다음 표는 모달 및 모덜리스 대화 상자가 일반적으로 생성되고 표시되는 방법을 보여 줍니다.

### <a name="dialog-creation"></a>대화 상자 만들기

|대화 유형|대화 상자를 만드는 방법|
|-----------------|----------------------|
|[Modeless](creating-modeless-dialog-boxes.md)|`CDialog`를 구성한 다음 `Create` 멤버 함수를 호출합니다.|
|[모달](creating-modal-dialog-boxes.md)|`CDialog`를 구성한 다음 `DoModal` 멤버 함수를 호출합니다.|

원하는 경우 대화 상자 템플릿 리소스 대신 생성 한 [메모리 내 대화 상자 템플릿에서](using-a-dialog-template-in-memory.md) 대화 상자를 만들 수 있습니다. 그러나 이는 고급 항목입니다.

## <a name="see-also"></a>참고 항목

[MFC에서 대화 상자를 통해 작업](life-cycle-of-a-dialog-box.md)
