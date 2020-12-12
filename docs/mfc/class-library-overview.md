---
description: '자세히 알아보기: 클래스 라이브러리 개요'
title: 클래스 라이브러리 개요
ms.date: 09/17/2019
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- grouping MFC classes
- MFC, class library
- classes [MFC], MFC
- class libraries, MFC
- class libraries
ms.assetid: 9b0e3152-ac39-4f52-91b4-f20aa3a674aa
ms.openlocfilehash: 458fc06aa8e13a2f2f7024c11a822496bccefbea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176693"
---
# <a name="class-library-overview"></a>클래스 라이브러리 개요

이 개요에서는 MFC (MFC 라이브러리) 버전 9.0의 클래스를 분류 하 고 설명 합니다. 응용 프로그램 프레임 워크를 구성 하는 MFC의 클래스는 Windows API 용으로 작성 된 응용 프로그램의 프레임 워크입니다. 응용 프로그램에 관련 된 코드를 작성 하는 것이 프로그래밍 작업입니다.

라이브러리의 클래스는 다음 범주에 표시 됩니다.

- [루트 클래스: CObject](root-class-cobject.md)

- [MFC 응용 프로그램 아키텍처 클래스](mfc-application-architecture-classes.md)

  - [응용 프로그램 및 스레드 지원 클래스](application-and-thread-support-classes.md)

  - [명령 라우팅 클래스](command-routing-classes.md)

  - [문서 클래스](document-classes.md)

  - [뷰 클래스 (아키텍처)](view-classes-architecture.md)

  - [프레임 창 클래스 (아키텍처)](frame-window-classes-architecture.md)

  - [문서 템플릿 클래스](document-template-classes.md)

- [창, 대화 상자 및 컨트롤 클래스](window-dialog-and-control-classes.md)

  - [프레임 창 클래스 (Windows)](frame-window-classes-windows.md)

  - [뷰 클래스 (Windows)](view-classes-windows.md)

  - [대화 상자 클래스](dialog-box-classes.md)

  - [컨트롤 클래스](control-classes.md)

  - [컨트롤 막대 클래스](control-bar-classes.md)

- [클래스 그리기 및 인쇄](drawing-and-printing-classes.md)

  - [출력 (장치 컨텍스트) 클래스](output-device-context-classes.md)

  - [그리기 도구 클래스](drawing-tool-classes.md)

- [단순 데이터 형식 클래스](simple-data-type-classes.md)

- [배열, 목록 및 맵 클래스](array-list-and-map-classes.md)

  - [배열, 목록 및 맵에 대 한 템플릿 클래스](template-classes-for-arrays-lists-and-maps.md)

  - [바로 사용할 수 있는 배열 클래스](ready-to-use-array-classes.md)

  - [바로 사용할 수 있는 목록 클래스](ready-to-use-list-classes.md)

  - [바로 사용할 수 있는 맵 클래스](ready-to-use-map-classes.md)

- [파일 및 데이터베이스 클래스](file-and-database-classes.md)

  - [파일 i/o 클래스](file-i-o-classes.md)

  - [DAO 클래스](dao-classes.md)

  - [ODBC 클래스](odbc-classes.md)

  - [OLE DB 클래스](ole-db-classes.md)

- [인터넷 및 네트워킹 클래스](internet-and-networking-classes.md)

  - [Windows 소켓 클래스](windows-sockets-classes.md)

  - [Win32 인터넷 클래스](win32-internet-classes.md)

- [OLE 클래스](ole-classes.md)

  - [OLE 컨테이너 클래스](ole-container-classes.md)

  - [OLE 서버 클래스](ole-server-classes.md)

  - [OLE 끌어서 놓기 및 데이터 전송 클래스](ole-drag-and-drop-and-data-transfer-classes.md)

  - [OLE 일반 대화 상자 클래스](ole-common-dialog-classes.md)

  - [OLE 자동화 클래스](ole-automation-classes.md)

  - [OLE 컨트롤 클래스](ole-control-classes.md)

  - [액티브 문서 클래스](active-document-classes.md)

  - [OLE 관련 클래스](ole-related-classes.md)

- [디버깅 및 예외 클래스](debugging-and-exception-classes.md)

  - [디버깅 지원 클래스](debugging-support-classes.md)

  - [예외 클래스](exception-classes.md)

[일반 클래스 디자인 원칙](general-class-design-philosophy.md) 섹션에서는 MFC 라이브러리가 디자인 된 방식을 설명 합니다.

프레임 워크에 대 한 개요는 [클래스를 사용 하 여 Windows 용 응용 프로그램 작성](using-the-classes-to-write-applications-for-windows.md)을 참조 하세요. 위에 나열 된 클래스 중 일부는 프레임 워크 외부에서 사용할 수 있고 컬렉션, 예외, 파일 및 문자열과 같은 유용한 추상화를 제공 하는 범용 클래스입니다.

클래스의 상속을 확인 하려면 [클래스 계층 구조 차트](hierarchy-chart.md)를 사용 합니다.

이 개요에 나열 된 클래스 외에도 MFC 라이브러리에는 여러 전역 함수, 전역 변수 및 매크로가 포함 되어 있습니다. Mfc 클래스에 대 한 사전순 참조를 따르는 [Mfc 매크로 및 전역](reference/mfc-macros-and-globals.md)항목에는이에 대 한 개요와 자세한 목록이 나와 있습니다.

## <a name="see-also"></a>참고 항목

[MFC 데스크톱 응용 프로그램](mfc-desktop-applications.md)
