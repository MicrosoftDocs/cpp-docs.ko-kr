---
description: '자세히 알아보기: 표준 명령 라우팅 재정의'
title: 표준 명령 라우팅 재정의
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
ms.openlocfilehash: 5241e767beee85f92875128cc5ebccd1a23477f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205995"
---
# <a name="overriding-the-standard-command-routing"></a>표준 명령 라우팅 재정의

드물지만 표준 프레임 워크 라우팅의 일부 변형을 구현 해야 하는 경우에는이를 재정의할 수 있습니다. 이러한 클래스에서를 재정의 하 여 하나 이상의 클래스에서 라우팅을 변경 하는 것이 좋습니다 `OnCmdMsg` . 이렇게 하려면 다음을 수행 합니다.

- 기본이 아닌 개체로 전달 되는 순서를 중단 하는 클래스입니다.

- 기본값이 아닌 새 개체 또는 명령 대상에서 명령을 전달할 수 있습니다.

라우팅에 새 개체를 삽입 하는 경우 해당 클래스는 명령 대상 클래스 여야 합니다. 의 재정의 버전에서는 `OnCmdMsg` 재정의 하는 버전을 호출 해야 합니다. 예제는 [](reference/ccmdtarget-class.md#oncmdmsg) `CCmdTarget` 제공 된 소스 코드에서 *MFC 참조* 의 클래스의 OnCmdMsg 멤버 함수 및 및와 같은 클래스의 버전을 참조 하세요 `CView` `CDocument` .

## <a name="see-also"></a>참고 항목

[프레임 워크가 처리기를 호출 하는 방법](how-the-framework-calls-a-handler.md)
