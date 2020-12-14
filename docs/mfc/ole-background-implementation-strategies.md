---
description: '자세한 정보: OLE 백그라운드: 구현 전략'
title: OLE 백그라운드 구현 전략
ms.date: 11/04/2016
helpviewer_keywords:
- OLE [MFC], development strategy
- OLE applications [MFC], implementing OLE
- applications [OLE], implementing OLE
ms.assetid: 0875ddae-99df-488c-82c6-164074a81058
ms.openlocfilehash: fe492adf755f9163586832f5c7aa7dfc5470349f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275479"
---
# <a name="ole-background-implementation-strategies"></a>OLE 백그라운드 구현 전략

애플리케이션에 따라 OLE 지원 추가를 위해서는 다음 네 가지 구현 전략을 사용할 수 있습니다.

- 새 애플리케이션을 작성합니다.

   이 경우에는 일반적으로 필요한 작업이 가장 적습니다. MFC 애플리케이션 마법사를 실행하고 고급 기능 또는 복합 문서 지원을 선택해서 기초 애플리케이션을 만듭니다. 이러한 옵션과 해당 옵션에 대 한 자세한 내용은 [MFC EXE 프로그램 만들기](reference/mfc-application-wizard.md)문서를 참조 하세요.

- 프로그램이 Microsoft Foundation Class 라이브러리 버전 2.0 이상으로 작성되어 OLE를 지원하지 않습니다.

   앞에서 설명한 것처럼 MFC 애플리케이션 마법사를 사용해서 새 애플리케이션을 만든 후 새 애플리케이션에서 기존 애플리케이션으로 코드를 복사하고 붙여넣습니다. 이 방식은 서버, 컨테이너 또는 자동화된 애플리케이션에서 작동합니다. 이 전략의 예제는 MFC [SCRIBBLE](../overview/visual-cpp-samples.md) 샘플을 참조 하세요.

- OLE 버전 1.0 지원을 구현하는 Microsoft Foundation Class 라이브러리 프로그램이 있습니다.

   이 변환 전략은 [MFC 기술 정보 41](tn041-mfc-ole1-migration-to-mfc-ole-2.md) 을 참조 하세요.

- 애플리케이션이 Microsoft Foundation Classes를 사용하여 작성되지 않았고 OLE 지원이 구현되거나 구현되지 않았을 수 있습니다.

   이 경우에는 가장 많은 작업이 필요합니다. 한 가지 방법은 첫 번째 전략에서와 같이 새 애플리케이션을 만들고 기존 코드를 여기에 복사해서 붙여넣는 방법입니다. 기존 코드가 C로 작성된 경우 C++ 코드로 컴파일될 수 있도록 수정해야 할 수 있습니다. C 코드가 Windows API를 호출하는 경우 Microsoft Foundation Class를 사용하도록 변경할 필요가 없습니다. 이 접근 방법에서는 Microsoft Foundation Class 버전 2.0 이상에서 사용되는 문서/뷰 아키텍처를 지원하기 위해 프로그램을 일부 재구성해야 합니다. 이 아키텍처에 대 한 자세한 내용은 [Technical Note 25](tn025-document-view-and-frame-creation.md)를 참조 하십시오.

전략을 결정 한 후에는 작성 중인 응용 프로그램의 형식에 따라 [컨테이너](containers.md) 또는 [서버](servers.md) 문서를 읽거나 샘플 프로그램 또는 둘 다를 검사 해야 합니다. MFC OLE 샘플 [OCLIENT](../overview/visual-cpp-samples.md) 및 [HIERSVR](../overview/visual-cpp-samples.md) 는 각각 컨테이너와 서버의 다양 한 측면을 구현 하는 방법을 보여 줍니다. 이러한 문서 전체의 여러 지점에서는 설명 중인 기술의 예제로 이러한 샘플에 포함된 일부 함수가 참조될 수 있습니다.

## <a name="see-also"></a>참고 항목

[OLE 배경](ole-background.md)<br/>
[컨테이너: 컨테이너 구현](containers-implementing-a-container.md)<br/>
[서버: 서버 구현](servers-implementing-a-server.md)<br/>
[MFC 응용 프로그램 마법사](reference/mfc-application-wizard.md)
