---
description: '자세한 정보: OLE 응용 프로그램을 만드는 작업 시퀀스'
title: OLE 애플리케이션을 만드는 작업 시퀀스
ms.date: 11/04/2016
helpviewer_keywords:
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
ms.openlocfilehash: 2bce49d569c6d3def536cbe9386cafbe08ccdbfb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217564"
---
# <a name="sequence-of-operations-for-creating-ole-applications"></a>OLE 애플리케이션을 만드는 작업 시퀀스

다음 표에서는 OLE 연결 및 포함 응용 프로그램을 만들 때의 역할 및 프레임 워크의 역할을 보여 줍니다. 이는 수행할 일련의 단계 대신 사용할 수 있는 옵션을 나타냅니다.

### <a name="creating-ole-applications"></a>OLE 응용 프로그램 만들기

|작업|너 해|프레임 워크는|
|----------|------------|------------------------|
|COM 구성 요소를 만듭니다.|MFC 응용 프로그램 마법사를 실행 합니다. **복합 문서 지원** 탭에서 **전체 서버** 또는 **미니 서버** 를 선택 합니다.|프레임 워크는 COM 구성 요소 기능을 사용 하는 기본 응용 프로그램을 생성 합니다. 약간의 수정 만으로 모든 COM 기능을 기존 응용 프로그램으로 전송할 수 있습니다.|
|컨테이너 응용 프로그램을 처음부터 새로 만듭니다.|MFC 응용 프로그램 마법사를 실행 합니다. **복합 문서 지원** 탭에서 **컨테이너** 를 선택 합니다. 클래스 뷰를 사용 하 여 소스 코드 편집기로 이동 합니다. COM 처리기 함수에 대 한 코드를 채웁니다.|프레임 워크는 COM 구성 요소 (서버) 응용 프로그램에서 만든 COM 개체를 삽입할 수 있는 기본 응용 프로그램을 생성 합니다.|
|처음부터 자동화를 지 원하는 응용 프로그램을 만듭니다.|MFC 응용 프로그램 마법사를 실행 합니다. **고급 기능** 탭에서 **자동화** 를 선택 합니다. 자동화를 위해 클래스 뷰를 사용 하 여 응용 프로그램에서 메서드와 속성을 노출 합니다.|프레임 워크는 다른 응용 프로그램에서 활성화 및 자동화할 수 있는 기본 응용 프로그램을 생성 합니다.|

## <a name="see-also"></a>참고 항목

[프레임 워크를 기반으로 빌드](../mfc/building-on-the-framework.md)<br/>
[MFC 응용 프로그램을 빌드하기 위한 작업 시퀀스](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[ActiveX 컨트롤을 만드는 작업 시퀀스](../mfc/sequence-of-operations-for-creating-activex-controls.md)<br/>
[데이터베이스 응용 프로그램을 만들기 위한 작업 시퀀스](../mfc/sequence-of-operations-for-creating-database-applications.md)
