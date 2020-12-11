---
description: '자세한 정보: 명령 Id'
title: 명령 ID
ms.date: 11/04/2016
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
ms.openlocfilehash: bba3b8b342b4d2e0c9492f9d0f3100a5d8f9e7d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159988"
---
# <a name="command-ids"></a>명령 ID

명령은 명령 ID로만 완전히 설명 됩니다 ( **WM_COMMAND** 메시지에서 인코딩 됨). 이 ID는 명령을 생성 하는 사용자 인터페이스 개체에 할당 됩니다. 일반적으로 Id는 할당 된 사용자 인터페이스 개체의 기능에 대해 이름이 지정 됩니다.

예를 들어 편집 메뉴의 모두 지우기 항목에 **ID_EDIT_CLEAR_ALL** 와 같은 ID가 할당 될 수 있습니다. 클래스 라이브러리는 일부 Id (특히 프레임 워크가 자체를 처리 하는 명령 (예: **ID_EDIT_CLEAR_ALL** 또는 **ID_FILE_OPEN**)을 (를) 자동으로 합니다. 다른 명령 Id를 직접 만듭니다.

Visual C++ 메뉴 편집기에서 사용자 고유의 메뉴를 만들 때 **ID_FILE_OPEN** 에 설명 된 대로 클래스 라이브러리의 명명 규칙을 따르는 것이 좋습니다. [표준 명령은](standard-commands.md) 클래스 라이브러리에서 정의한 표준 명령을 설명 합니다.

## <a name="see-also"></a>참고 항목

[사용자 인터페이스 개체 및 명령 Id](user-interface-objects-and-command-ids.md)
