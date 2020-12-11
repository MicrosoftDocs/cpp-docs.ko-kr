---
description: '자세한 정보: MFC 인터넷 프로그래밍 작업'
title: MFC 인터넷 프로그래밍 작업
ms.date: 09/12/2018
helpviewer_keywords:
- Internet applications [MFC], getting started
- Internet applications [MFC], first steps
ms.assetid: 6377e9b8-07c4-4380-b63b-05f5a9061313
ms.openlocfilehash: 26823dbd85222998ebf20947ac2af30a6b11e987
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159936"
---
# <a name="mfc-internet-programming-tasks"></a>MFC 인터넷 프로그래밍 작업

이 섹션에서는 응용 프로그램에 인터넷 지원을 추가 하는 단계를 자세히 설명 합니다. MFC 클래스를 사용 하 여 기존 응용 프로그램을 인터넷에서 사용할 수 있도록 하는 방법 및 기존 COM 구성 요소에 활성 문서 지원을 추가 하는 방법을 다룹니다. 최신 주식 시세 (Pittsburgh의 축구 점수)와 남극 Microsoft의 최신 온도를 사용 하는 문서를 만들어 인터넷을 통해이 작업을 수행 하는 데 도움이 되는 다양 한 기술을 제공 합니다.

활성 기술에는 ActiveX 컨트롤 (이전의 OLE 컨트롤) 및 활성 문서가 포함 됩니다. 인터넷을 통해 파일을 쉽게 검색 하 고 저장 하기 위한 WinInet 효율적인 데이터 다운로드를 위한 비동기 모니커. Visual C++는 시작 응용 프로그램을 빠르게 시작 하는 데 도움이 되는 마법사를 제공 합니다. 이러한 기술에 대 한 소개는 [Mfc 인터넷 프로그래밍 기본 사항](mfc-internet-programming-basics.md) 및 [mfc COM](mfc-com.md)을 참조 하세요.

항상 파일에 FTP를 사용 하 고 있지만 WinSock 및 네트워크 프로그래밍 프로토콜을 확인 하지는 않습니다. WinInet 클래스는 이러한 프로토콜을 캡슐화 하 여 HTTP, FTP 및 gopher를 사용 하 여 파일을 다운로드 하기 위해 인터넷에 클라이언트 응용 프로그램을 작성 하는 데 사용할 수 있는 간단한 함수 집합을 제공 합니다. WinInet을 사용 하 여 하드 드라이브나 전 세계의 디렉터리를 검색할 수 있습니다. 여러 다른 유형의 데이터를 투명 하 게 수집 하 여 통합 된 인터페이스에서 사용자에 게 제공할 수 있습니다.

비동기 모니커를 다운로드 하는 데 많은 양의 데이터가 있으므로 대규모 개체의 점진적 렌더링을 위한 COM (구성 요소 개체 모델) 솔루션을 제공 합니다. WinInet을 비동기식으로 사용할 수도 있습니다.

다음 표에서는 이러한 기술을 사용 하 여 수행할 수 있는 몇 가지 작업에 대해 설명 합니다.

|당신이 가지고 있어요|다음 사항 필요|사용자가|
|--------------|-----------------|----------------|
|웹 서버입니다.|URL 요청에 대 한 로그온 및 자세한 정보를 추적 합니다.|필터를 작성 하 고 로그온 이벤트 및 URL 매핑에 대 한 알림을 요청 합니다.|
|웹 브라우저.|동적 콘텐츠를 제공 합니다.|ActiveX 컨트롤 및 활성 문서를 만듭니다.|
|문서 기반 응용 프로그램입니다.|FTP a 파일에 지원을 추가 합니다.|WinInet 또는 비동기 모니커를 사용 합니다.|

시작 하는 방법에 대 한 자세한 내용은 다음 항목을 참조 하십시오.

- [응용 프로그램 디자인 선택](application-design-choices.md)

- [MFC 응용 프로그램 작성](writing-mfc-applications.md)

- [인터넷의 ActiveX 컨트롤](activex-controls-on-the-internet.md)

- [기존 ActiveX 컨트롤 업그레이드](upgrading-an-existing-activex-control.md)

- [인터넷의 비동기 모니커](asynchronous-monikers-on-the-internet.md)

- [인터넷 응용 프로그램 테스트](testing-internet-applications.md)

- [인터넷 보안](internet-security-cpp.md)

## <a name="see-also"></a>참고 항목

[MFC 인터넷 프로그래밍 기본 사항](mfc-internet-programming-basics.md)<br/>
[작업별 인터넷 정보](internet-information-by-task.md)
