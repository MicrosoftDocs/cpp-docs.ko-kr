---
description: '자세히 알아보기: 테스트 컨테이너로 속성 및 이벤트 테스트'
title: 테스트 컨테이너로 속성 및 이벤트 테스트
ms.date: 11/04/2016
helpviewer_keywords:
- testing, test containers
- tstcon32.exe
- debugging ActiveX controls
- test container
- ActiveX Control Test Container
- ActiveX controls [MFC], testing
- properties [MFC], testing
ms.assetid: 626867cf-fe53-4c30-8973-55bb93ef3917
ms.openlocfilehash: 61cccbda723fb1cfac0ca3fc696639849bde9dd1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216225"
---
# <a name="testing-properties-and-events-with-test-container"></a>테스트 컨테이너로 속성 및 이벤트 테스트

Visual C++에서 제공 되는 테스트 컨테이너 응용 프로그램은 ActiveX 컨트롤을 테스트 하 고 디버깅 하기 위한 ActiveX 컨트롤 컨테이너입니다. 컨트롤 개발자는 테스트 컨테이너를 사용 하 여 해당 속성을 변경 하 고 해당 메서드를 호출 하 고 이벤트를 발생 시켜 컨트롤의 기능을 테스트할 수 있습니다. 테스트 컨테이너는 데이터 바인딩 알림의 로그를 표시할 수 있으며, ActiveX 컨트롤의 지 속성 기능을 테스트 하는 기능을 제공 합니다. 또한 속성을 스트림 또는 하위 저장소에 저장 하 고, 다시 로드 하 고, 저장 된 스트림 데이터를 검사할 수 있습니다. 이 섹션에서는 테스트 컨테이너의 기본 기능을 사용 하는 방법을 설명 합니다. 추가 정보를 보려면 테스트 컨테이너를 실행 하는 동안 **도움말** 메뉴를 선택 합니다.

### <a name="to-access-the-activex-control-test-container"></a>ActiveX 컨트롤 테스트 컨테이너에 액세스 하려면

1. [TSTCON 샘플: ActiveX 컨트롤 테스트 컨테이너](../overview/visual-cpp-samples.md)를 빌드합니다.

### <a name="to-test-your-activex-control"></a>ActiveX 컨트롤을 테스트 하려면

1. 테스트 컨테이너의 **편집** 메뉴에서 **새 컨트롤 삽입** 을 클릭 합니다.

1. **컨트롤 삽입** 상자에서 원하는 컨트롤을 선택 하 고 **확인** 을 클릭 합니다. 컨트롤이 컨트롤 컨테이너에 표시 됩니다.

    > [!NOTE]
    >  컨트롤 **삽입** 대화 상자에 컨트롤이 나열 되어 있지 않으면 테스트 컨테이너의 **파일** 메뉴에서 컨트롤 **등록** 명령으로 등록 했는지 확인 합니다.

이 시점에서 컨트롤의 속성 또는 이벤트를 테스트할 수 있습니다.

#### <a name="to-test-properties"></a>속성을 테스트 하려면

1. **컨트롤** 메뉴에서 **메서드 호출** 을 클릭 합니다.

1. **메서드 이름** 드롭다운 목록에서 테스트 하려는 속성에 대해 PropPut 메서드를 선택 합니다.

1. **매개 변수 값** 또는 **매개 변수 유형을** 수정 하 고 **값 설정** 단추를 클릭 합니다.

1. **호출** 을 클릭 하 여 개체에 새 값을 적용 합니다.

   속성에는 이제 새 값이 포함 됩니다.

#### <a name="to-test-events-and-specify-the-destination-of-event-information"></a>이벤트를 테스트 하 고 이벤트 정보의 대상을 지정 합니다.

1. **옵션** 메뉴에서 **로깅** 을 클릭 합니다.

1. 이벤트 정보의 대상을 지정 합니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](../mfc/mfc-activex-controls.md)<br/>
[방법: ActiveX 컨트롤 디버그](/visualstudio/debugger/how-to-debug-an-activex-control)
