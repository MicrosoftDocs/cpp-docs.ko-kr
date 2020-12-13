---
description: '자세한 정보: OLE 배경'
title: OLE 백그라운드
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
ms.openlocfilehash: 89d8e3b6e1a84082fabdf954971e75ab86366622
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150230"
---
# <a name="ole-background"></a>OLE 백그라운드

OLE는 여러 응용 프로그램에서 만든 항목 또는 "개체"가 포함 된 문서를 만들고 편집할 수 있도록 하는 메커니즘입니다.

> [!NOTE]
> OLE는 원래 개체 연결 및 포함에 대 한 머리글자어 였습니다. 그러나 이제 OLE 라고 합니다. OLE의 일부는 연결 및 포함과 관련이 없습니다. 이제 활성 기술의 일부입니다.

지금까지 복합 문서 라고 하는 OLE 문서를 통해 다양 한 유형의 데이터 또는 구성 요소를 원활 하 게 통합할 있습니다. 사운드 클립, 스프레드시트 및 비트맵은 OLE 문서에 있는 구성 요소의 일반적인 예입니다. 응용 프로그램에서 OLE를 지원 하면 사용자가 다른 응용 프로그램 간의 전환에 대해 걱정 하지 않고 OLE 문서를 사용할 수 있습니다. OLE에서 사용자의 전환을 수행 합니다.

컨테이너 응용 프로그램을 사용 하 여 컨테이너 문서 내에 항목을 만드는 복합 문서와 서버 응용 프로그램 또는 구성 요소 응용 프로그램을 만듭니다. 작성 하는 모든 응용 프로그램은 컨테이너, 서버 또는 둘 다 일 수 있습니다.

OLE는 응용 프로그램 간의 원활한 상호 작용 목표를 달성 하기 위해 모든 개념을 포함 하는 다양 한 개념을 통합 합니다. 이러한 영역에는 다음이 포함 됩니다.

- 연결 및 포함

   링크 및 포함은 다른 응용 프로그램에서 만든 OLE 문서 내에 생성 된 항목을 저장 하는 두 가지 방법입니다. 두 방법 간의 차이점에 대 한 일반적인 정보는 [OLE 배경: 연결 및 포함](ole-background-linking-and-embedding.md)문서를 참조 하세요. 자세한 내용은 [컨테이너](containers.md) 및 [서버](servers.md)문서를 참조 하세요.

- 활성화 In-Place (비주얼 편집)

   컨테이너 문서의 컨텍스트에서 포함 된 항목을 활성화 하는 것을 내부 활성화 또는 시각적 편집 이라고 합니다. 컨테이너 응용 프로그램의 인터페이스는 포함 된 항목을 만든 구성 요소 응용 프로그램의 기능을 통합 하도록 변경 됩니다. 연결 된 항목은 링크를 포함 하는 응용 프로그램의 컨텍스트에서 항목의 실제 데이터가 별도의 파일에 포함 되어 있으므로 내부에서 활성화 되지 않습니다. 내부 활성화에 대 한 자세한 내용은 [활성화](activation-cpp.md)문서를 참조 하세요.

   > [!NOTE]
   > 연결 및 포함 및 내부 활성화는 OLE 비주얼 편집의 주요 기능을 제공 합니다.

- Automation 자동화를 사용 하면 한 응용 프로그램에서 다른 응용 프로그램을 구동 합니다. 구동 응용 프로그램을 자동화 클라이언트 라고 하며, 구동 되는 응용 프로그램을 자동화 서버 또는 자동화 구성 요소 라고 합니다. 자동화에 대 한 자세한 내용은 [자동화 클라이언트](automation-clients.md) 및 [자동화 서버](automation-servers.md)문서를 참조 하세요.

   > [!NOTE]
   > Automation은 OLE 및 활성 기술 컨텍스트 모두에서 작동 합니다. COM을 기반으로 개체를 자동화할 수 있습니다.

- 복합 파일

   복합 파일은 OLE 응용 프로그램에 대 한 복합 문서의 구조화 된 저장을 간소화 하는 표준 파일 형식을 제공 합니다. 복합 파일 내에서 저장소는 디렉터리와 스트림의 많은 기능을 포함 하며 파일의 많은 기능을 제공 합니다. 이 기술은 구조화 된 저장소 라고도 합니다. 복합 파일에 대 한 자세한 내용은 [컨테이너: 복합 파일](containers-compound-files.md)문서를 참조 하세요.

- Uniform Data Transfer

   UDT (Uniform Data Transfer)는 데이터를 전송 하기 위해 선택한 실제 메서드에 관계 없이 데이터를 표준 방식으로 보내고 받을 수 있도록 하는 인터페이스 집합입니다. UDT는 끌어서 놓기를 통해 데이터 전송의 기본을 형성 합니다. UDT는 이제 클립보드 및 DDE (동적 데이터 교환)와 같은 기존 Windows 데이터 전송의 기반으로 사용 됩니다. UDT에 대 한 자세한 내용은 [데이터 개체 및 데이터 소스 (OLE)](data-objects-and-data-sources-ole.md)문서를 참조 하세요.

- 끌어서 놓기

   끌어서 놓기는 응용 프로그램 간에 데이터를 전송 하는 사용 하기 쉬운 직접 조작 기술로, 응용 프로그램 내의 창 간에 또는 응용 프로그램의 단일 창 내 에서도 데이터를 전송 합니다. 전송할 데이터를 선택 하 여 원하는 대상으로 끌어옵니다. 끌어서 놓기는 균일 한 데이터 전송을 기반으로 합니다. 끌어서 놓기에 대 한 자세한 내용은 [끌어서 놓기](drag-and-drop-ole.md)문서를 참조 하세요.

- 구성 요소 개체 모델(Component Object Model)

   COM (구성 요소 개체 모델)은 OLE 개체가 서로 통신할 때 사용 되는 인프라를 제공 합니다. MFC OLE 클래스는 프로그래머를 위한 COM을 단순화 합니다. Com 개체는 OLE와 활성 기술의 기반이 되기 때문에 COM은 활성 기술의 일부입니다. COM에 대 한 자세한 내용은 [ATL (액티브 템플릿 라이브러리)](../atl/active-template-library-atl-concepts.md) 항목을 참조 하십시오.

다음 문서에서는 몇 가지 중요 한 OLE 항목에 대해 설명 합니다.

- [OLE 백그라운드: 연결 및 포함](ole-background-linking-and-embedding.md)

- [OLE 백그라운드: 컨테이너 및 서버](ole-background-containers-and-servers.md)

- [OLE 배경: 구현 전략](ole-background-implementation-strategies.md)

- [OLE 백그라운드: MFC 구현](ole-background-mfc-implementation.md)

위의 문서에서 찾을 수 없는 일반적인 OLE 정보는 Microsoft Docs에서 [OLE를 검색](/search/?terms=ole) 합니다.

## <a name="see-also"></a>참고 항목

[OLE](ole-in-mfc.md)
