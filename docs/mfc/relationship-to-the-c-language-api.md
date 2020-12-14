---
description: '자세히 알아보기: C 언어 API와의 관계'
title: C 언어 API와의 관계
ms.date: 11/04/2016
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
ms.openlocfilehash: fdfc03d9e8379ee4f19452ce81cba9957930bfe4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218071"
---
# <a name="relationship-to-the-c-language-api"></a>C 언어 API와의 관계

Windows 용 다른 클래스 라이브러리와는 별도로 MFC (Microsoft Foundation Class) 라이브러리를 설정 하는 단일 특성은 C 언어로 작성 된 Windows API에 대 한 매우 가깝게 매핑됩니다. 또한 일반적으로 Windows API에 대 한 직접 호출을 통해 클래스 라이브러리에 대 한 호출을 자유롭게 혼합할 수 있습니다. 그러나이 직접 액세스는 클래스가 해당 API에 대 한 완전 한 대체 임을 의미 합니다. 예를 들어, 개발자는 때때로 [Setcursor](/windows/win32/api/winuser/nf-winuser-setcursor) 및 [Getsystemmetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics)같은 일부 Windows 함수를 직접 호출 해야 합니다. Windows 함수는이 작업을 수행 하는 데 명백한 이점이 있는 경우에만 클래스 멤버 함수에 의해 래핑됩니다.

네이티브 Windows 함수 호출을 수행 해야 하는 경우가 있으므로 C 언어 Windows API 설명서에 대 한 액세스 권한이 있어야 합니다. 이 설명서는 Microsoft Visual C++ 포함 되어 있습니다.

> [!NOTE]
> MFC 라이브러리 프레임 워크의 작동 방식에 대 한 개요는 [클래스를 사용 하 여 Windows 용 응용 프로그램 작성](../mfc/using-the-classes-to-write-applications-for-windows.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[일반 클래스 디자인 원칙](../mfc/general-class-design-philosophy.md)
