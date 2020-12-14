---
description: '자세한 정보: 프레임 워크 (MFC)'
title: 프레임워크(MFC)
ms.date: 09/17/2019
helpviewer_keywords:
- encapsulation [MFC], Win32 API
- MFC, application framework
- wrapper classes [MFC], explained
- Win32 [MFC], API encapsulation by MFC
- application framework [MFC], about MFC application framework
- APIs [MFC], encapsulation by MFC Win32
- encapsulation [MFC]
- Windows API [MFC], encapsulation by MFC
- encapsulated Win32 API [MFC]
ms.assetid: 3be0fec8-9843-4119-ae42-ece993ef500b
ms.openlocfilehash: 12e5a28e231dfadec867213ebf1cea6fd6ae7300
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193489"
---
# <a name="framework-mfc"></a>프레임워크(MFC)

MFC (Microsoft Foundation Class) 라이브러리 프레임 워크를 사용 하는 작업은 주로 몇 가지 주요 클래스와 몇 가지 Visual C++ 도구를 기반으로 합니다. 일부 클래스는 Win32 API (응용 프로그래밍 인터페이스)의 많은 부분을 캡슐화 합니다. 다른 클래스는 문서, 뷰 및 응용 프로그램 자체와 같은 응용 프로그램 개념을 캡슐화 합니다. OLE 기능과 ODBC 및 DAO 데이터 액세스 기능을 캡슐화 하는 경우도 있습니다.  (DAO는 Office 2013을 통해 지원 됩니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다.)

예를 들어 Win32's 창의 개념은 MFC 클래스에 의해 캡슐화 됩니다 `CWnd` . 즉, 호출 되는 c + + 클래스는 `CWnd` Windows 창을 나타내는 핸들을 캡슐화 하거나 "래핑" `HWND` 합니다. 마찬가지로 클래스는 `CDialog` Win32 대화 상자를 캡슐화 합니다.

캡슐화는 예를 들어 c + + 클래스에 `CWnd` 형식의 멤버 변수를 포함 하 `HWND` 고 클래스의 멤버 함수는를 매개 변수로 사용 하는 Win32 함수에 대 한 호출을 캡슐화 하는 것을 의미 합니다 `HWND` . 클래스 멤버 함수는 일반적으로 캡슐화 하는 Win32 함수와 동일한 이름을 갖습니다.

## <a name="in-this-section"></a>섹션 내용

[SDI 및 MDI](sdi-and-mdi.md)

[문서, 뷰 및 프레임 워크](documents-views-and-the-framework.md)

[마법사 및 리소스 편집기](wizards-and-the-resource-editors.md)

## <a name="in-related-sections"></a>관련 섹션

[프레임 워크를 기반으로 빌드](building-on-the-framework.md)

[프레임 워크가 코드를 호출 하는 방법](how-the-framework-calls-your-code.md)

[CWinApp: 응용 프로그램 클래스](cwinapp-the-application-class.md)

[문서 템플릿 및 문서/뷰 만들기 프로세스](document-templates-and-the-document-view-creation-process.md)

[메시지 처리 및 매핑](message-handling-and-mapping.md)

[창 개체](window-objects.md)

## <a name="see-also"></a>참고 항목

[클래스를 사용 하 여 Windows 용 응용 프로그램 작성](using-the-classes-to-write-applications-for-windows.md)
