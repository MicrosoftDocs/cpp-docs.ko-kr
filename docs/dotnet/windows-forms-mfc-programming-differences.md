---
description: Windows Forms/MFC 프로그래밍 차이점에 대해 자세히 알아보세요.
title: Windows Forms-MFC 프로그래밍 차이점
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
ms.openlocfilehash: abb41a64a894eed682c26b2460259fc6bbc43b56
ms.sourcegitcommit: 3987d9c39f5a5b4824303a48a6215984ce8949e8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/02/2021
ms.locfileid: "99478021"
---
# <a name="windows-formsmfc-programming-differences"></a>Windows Forms/MFC 프로그래밍의 차이점

[Mfc에서 Windows Form 사용자 정의 컨트롤 사용](../dotnet/using-a-windows-form-user-control-in-mfc.md) 의 항목에서는 Windows Forms에 대 한 mfc 지원을 설명 합니다. .NET Framework 또는 MFC 프로그래밍에 익숙하지 않은 경우이 항목에서는 두 가지 사이의 프로그래밍 차이점에 대 한 배경 정보를 제공 합니다.

Windows Forms은 .NET Framework에서 Microsoft Windows 응용 프로그램을 만들기 위한 것입니다. 이 프레임 워크는 풍부한 Windows 기반 응용 프로그램을 개발 하는 데 사용할 수 있는 최신의 개체 지향적 확장 가능 클래스 집합을 제공 합니다. Windows Forms를 사용 하면 다양 한 데이터 소스에 액세스 하 고 Windows Forms 컨트롤을 사용 하 여 데이터 표시 및 데이터 편집 기능을 제공할 수 있는 다양 한 클라이언트 응용 프로그램을 만들 수 있습니다.

그러나 MFC에 익숙한 경우에는 Windows Forms에서 아직 명시적으로 지원 되지 않는 특정 유형의 응용 프로그램을 만드는 데 사용할 수 있습니다. Windows Forms 응용 프로그램은 MFC 대화 상자 응용 프로그램에 해당 합니다. 그러나 이러한 응용 프로그램은 OLE 문서 서버/컨테이너, ActiveX 문서, SDI (단일 문서 인터페이스)에 대 한 문서/뷰 지원, MDI (다중 문서 인터페이스) 및 여러 개의 MTI (최상위 인터페이스)와 같은 다른 MFC 응용 프로그램 유형을 직접 지원 하기 위한 인프라를 제공 하지 않습니다. 사용자 고유의 논리를 작성 하 여 이러한 응용 프로그램을 만들 수 있습니다.

Windows Forms 응용 프로그램에 대 한 자세한 내용은 [Windows Forms 소개](/dotnet/framework/winforms/windows-forms-overview)를 참조 하세요.

MFC와 함께 사용 Windows Forms을 보여 주는 예제 응용 프로그램은 [mfc 및 Windows Forms 통합](https://download.cnet.com/MFC-and-WinForms-Integration/3000-2383_4-75453644.html)을 참조 하세요.

다음 MFC 뷰나 문서 및 명령 라우팅 기능은 Windows Forms에 해당 하지 않습니다.

- 셸 통합

   MFC는 문서를 마우스 오른쪽 단추로 클릭 하 고 열기, 편집 또는 인쇄와 같은 동사를 선택할 때 셸에서 사용 하는 DDE (동적 데이터 교환) 명령과 명령줄 인수를 처리 합니다. Windows Forms에는 셸 통합이 없으며 셸 동사에 응답 하지 않습니다.

- 문서 템플릿

   MFC에서 문서 템플릿은 프레임 창에 포함 된 뷰 (MDI, SDI 또는 MTI 모드)를 연 문서와 연결 합니다. Windows Forms에는 문서 템플릿과 동일한 기능이 없습니다.

- 문서

   MFC는 문서 파일 형식을 등록 하 고 셸에서 문서를 열 때 문서 형식을 처리 합니다. Windows Forms는 문서를 지원 하지 않습니다.

- 문서 상태

   MFC는 문서의 더티 상태를 유지 합니다. 따라서 응용 프로그램을 닫거나 응용 프로그램을 포함 하는 마지막 보기를 닫거나 Windows에서 종료 하는 경우 MFC는 문서를 저장 하 라는 메시지를 표시 합니다. Windows Forms에는 해당 하는 지원 기능이 없습니다.

- 명령

   MFC에는 명령의 개념이 있습니다. 메뉴 모음, 도구 모음 및 상황에 맞는 메뉴는 모두 동일한 명령 (예: 잘라내기 및 복사)을 호출할 수 있습니다. Windows Forms에서 명령은 특정 UI 요소 (예: 메뉴 항목)의 긴밀 하 게 바인딩된 이벤트입니다. 따라서 모든 명령 이벤트를 명시적으로 후크 해야 합니다. Windows Forms에서 단일 처리기를 사용 하 여 여러 이벤트를 처리할 수도 있습니다. 자세한 내용은 [Windows Forms에서 단일 이벤트 처리기에 여러 이벤트 연결](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms)을 참조 하세요.

- 명령 라우팅

   MFC 명령 라우팅은 활성 뷰나 문서에서 명령을 처리할 수 있도록 합니다. 동일한 명령의 경우에 따라 보기 마다 다른 의미가 있기 때문에 (예를 들어, 복사는 그래픽 편집기 에서보다 텍스트 편집 뷰에서 다르게 동작) 활성 뷰에서 처리 해야 합니다. Windows Forms 메뉴와 도구 모음은 활성 뷰를 고유 하 게 이해 하지 못하기 때문에 MenuItem의 각 보기 형식에 대해 다른 처리기를 사용할 수 없습니다. 추가 내부 코드를 작성 하지 않고 이벤트를 **클릭** 합니다.

- 명령 업데이트 메커니즘

   MFC에는 명령 업데이트 메커니즘이 있습니다. 따라서 활성 뷰나 문서는 UI 요소의 상태를 담당 합니다 (예: 메뉴 항목 또는 도구 단추를 사용 하거나 사용 하지 않도록 설정, 선택 된 상태). Windows Forms에는 명령 업데이트 메커니즘과 동일한 기능이 없습니다.

## <a name="see-also"></a>참고 항목

[MFC에서 Windows Form 사용자 정의 컨트롤 사용](../dotnet/using-a-windows-form-user-control-in-mfc.md)
