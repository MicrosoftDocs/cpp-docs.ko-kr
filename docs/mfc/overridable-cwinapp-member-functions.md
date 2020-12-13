---
description: '자세한 정보: 재정의 가능 CWinApp 멤버 함수'
title: 재정의 가능 CWinApp 멤버 함수
ms.date: 11/04/2016
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
ms.openlocfilehash: 3958ad0edc1fbdb77e1f6ce3252fd03d7595344a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330100"
---
# <a name="overridable-cwinapp-member-functions"></a>재정의 가능 CWinApp 멤버 함수

[CWinApp](reference/cwinapp-class.md) 는 다음과 같은 몇 가지 키 재정의 가능 멤버 함수를 제공 합니다 ( `CWinApp` 가 파생 되는 [CWinThread](reference/cwinthread-class.md)클래스에서이 멤버 재정의 `CWinApp` ).

- [InitInstance](initinstance-member-function.md)

- [Run](run-member-function.md)

- [ExitInstance](exitinstance-member-function.md)

- [OnIdle](onidle-member-function.md)

재정의해야 하는 유일한 `CWinApp` 멤버 함수는 `InitInstance`입니다.

## <a name="see-also"></a>참고 항목

[CWinApp: 응용 프로그램 클래스](cwinapp-the-application-class.md)
