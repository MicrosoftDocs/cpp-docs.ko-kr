---
description: '자세히 알아보기: MFC의 OLE'
title: MFC의 OLE
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, OLE and
- OLE items
- OLE applications [MFC], about OLE
- OLE [MFC]
- OLE containers [MFC], about OLE
- applications [OLE], about OLE
- OLE component object model (COM)
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
ms.openlocfilehash: 125a2ad8e900747d859c03b57df33f2e7e5f1c28
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244097"
---
# <a name="ole-in-mfc"></a>MFC의 OLE

이러한 문서에서는 MFC를 사용 하는 OLE 프로그래밍의 기본 사항을 설명 합니다. MFC는 OLE를 사용 하는 프로그램을 작성 하는 가장 쉬운 방법을 제공 합니다.

- OLE 비주얼 편집 (내부 활성화)을 사용 하려면입니다.

- OLE 컨테이너 또는 서버로 작업 하는 경우

- 끌어서 놓기 기능을 구현 합니다.

- 날짜 및 시간 데이터를 사용 하 여 작업 합니다.

- 내보낸 DLL 함수 진입점, OLE/COM 인터페이스 진입점 및 창 프로시저 진입점을 포함 하 여 MFC 모듈의 상태 데이터를 관리 합니다.

[자동화](automation.md)를 사용할 수도 있습니다.

> [!NOTE]
> OLE 라는 용어는 OLE 컨테이너, OLE 서버, OLE 항목, 내부 활성화 (또는 시각적 편집), 추적기, 끌어서 놓기 및 메뉴 병합을 비롯 하 여 연결과 관련 된 기술을 나타냅니다. 활성화 된 용어는 COM (구성 요소 개체 모델) 및 ActiveX 컨트롤과 같은 COM 기반 개체에 적용 됩니다. 이제 OLE 자동화를 Automation 이라고 합니다.

## <a name="in-this-section"></a>섹션 내용

[OLE 배경](ole-background.md)<br/>
OLE에 대해 설명 하 고 작동 방법에 대 한 개념 정보를 제공 합니다.

[활성화](activation-cpp.md)<br/>
OLE 항목을 편집할 때 활성화의 역할에 대해 설명 합니다.

[컨테이너](containers.md)<br/>
OLE에서 컨테이너를 사용 하기 위한 링크를 제공 합니다.

[데이터 개체 및 데이터 원본](data-objects-and-data-sources-ole.md)<br/>
및 클래스 사용에 대해 설명 하는 항목에 대 한 링크를 제공 합니다 `COleDataObject` `COleDataSource` .

[끌어서 놓기](drag-and-drop-ole.md)<br/>
OLE로 복사 및 붙여넣기를 사용 하는 방법을 설명 합니다.

[OLE 메뉴 및 리소스](menus-and-resources-ole.md)<br/>
MFC OLE 문서 응용 프로그램에서 메뉴 및 리소스를 사용 하는 방법을 설명 합니다.

[등록](registration.md)<br/>
서버 설치 및 초기화에 대해 설명 합니다.

[서버](servers.md)<br/>
컨테이너 응용 프로그램에서 사용 하기 위해 OLE 항목 (또는 구성 요소)을 만드는 방법을 설명 합니다.

[Trackers](trackers.md)<br/>
`CRectTracker`사용자가 OLE 클라이언트 항목을 조작할 수 있도록 그래픽 인터페이스를 제공 하는 클래스에 대 한 정보를 제공 합니다.

## <a name="related-sections"></a>관련 단원

[연결 요소](connection-points.md)<br/>
MFC 클래스 및를 사용 하 여 연결 요소 (이전의 OLE 연결점)를 구현 하는 방법에 대해 설명 합니다 `CCmdTarget` `CConnectionPoint` .

[컨테이너/서버 COM 구성 요소](containers-advanced-features.md)<br/>
선택적인 고급 기능을 기존 컨테이너 응용 프로그램에 통합 하는 데 필요한 단계에 대해 설명 합니다.

[구성 요소 개체 모델](/windows/win32/com/the-component-object-model)<br/>
MFC를 사용 하지 않고 OLE를 사용 하는 방법을 설명 합니다.

## <a name="see-also"></a>참고 항목

[개념](mfc-concepts.md)
