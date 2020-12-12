---
description: '자세한 정보: 인터넷의 비동기 모니커'
title: 인터넷의 비동기 모니커
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX controls [MFC], asynchronous
- MFC, asynchronous monikers
- asynchronous monikers [MFC]
- Web applications [MFC], asynchronous
- downloading Internet resources and asynchronous monikers
- optimization [MFC], asynchronous downloading across Internet
- Internet [MFC], asynchronous downloading
ms.assetid: 418b0c64-0046-4dae-8118-c9c762b5822e
ms.openlocfilehash: f937c2c1189dcb44bf49b4b386bca68a61f925fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274023"
---
# <a name="asynchronous-monikers-on-the-internet"></a>인터넷의 비동기 모니커

네트워크 액세스 속도가 느리기 때문에 인터넷에 응용 프로그램 디자인에 대 한 새로운 접근 방식이 필요 합니다. 응용 프로그램은 사용자 인터페이스의 상태일를 방지 하기 위해 비동기적으로 네트워크 액세스를 수행 해야 합니다. MFC 클래스 [CAsyncMonikerFile](reference/casyncmonikerfile-class.md) 는 파일 다운로드에 대 한 비동기 지원을 제공 합니다.

비동기 모니커를 사용 하면 인터넷을 통해 비동기적으로 다운로드 하 고 비트맵 및 VRML 개체와 같은 커다란 개체의 점진적 렌더링을 제공 하도록 COM 응용 프로그램을 확장할 수 있습니다. 비동기 모니커를 사용 하면 사용자 인터페이스의 응답을 차단 하지 않고 인터넷에서 ActiveX 컨트롤 속성 또는 파일을 다운로드할 수 있습니다.

## <a name="advantages-of-asynchronous-monikers"></a>비동기 모니커의 이점

비동기 모니커를 사용 하 여 다음을 수행할 수 있습니다.

- 차단 하지 않고 코드 및 파일을 다운로드 합니다.

- 차단 하지 않고 ActiveX 컨트롤에서 속성을 다운로드 합니다.

- 다운로드 진행률에 대 한 알림을 받습니다.

- 진행률 및 준비 상태 정보를 추적 합니다.

- 진행률에 대 한 상태 정보를 사용자에 게 제공 합니다.

- 사용자가 언제 든 지 다운로드를 취소할 수 있도록 허용 합니다.

## <a name="mfc-classes-for-asynchronous-monikers"></a>비동기 모니커의 MFC 클래스

[CAsyncMonikerFile](reference/casyncmonikerfile-class.md) 는 [CMonikerFile](reference/cmonikerfile-class.md)에서 파생 되며,이는 차례로 [colestreamfile](reference/colestreamfile-class.md)에서 파생 됩니다. `COleStreamFile`개체는 데이터 스트림을 나타내며, 개체는를 `CMonikerFile` 사용 하 여 `IMoniker` 데이터를 가져오고, `CAsyncMonikerFile` 개체는 비동기적으로 수행 합니다.

비동기 모니커는 주로 인터넷 사용 응용 프로그램 및 ActiveX 컨트롤에서 파일을 전송 하는 동안 응답성이 뛰어난 사용자 인터페이스를 제공 하는 데 사용 됩니다. 이에 대 한 가장 대표적인 예는 ActiveX 컨트롤에 대 한 비동기 속성을 제공 하는 데 [CDataPathProperty](reference/cdatapathproperty-class.md) 를 사용 하는 것입니다.

## <a name="mfc-classes-for-data-paths-in-activex-controls"></a>ActiveX 컨트롤의 데이터 경로에 대 한 MFC 클래스

MFC 클래스 `CDataPathProperty` 및 [CCachedDataPathProperty](reference/ccacheddatapathproperty-class.md) 는 비동기적으로 로드할 수 있는 ActiveX 컨트롤 속성을 구현 합니다. 비동기 속성은 동기 시작 후에 로드 됩니다. 비동기 ActiveX 컨트롤은 긴 속성 교환 프로세스 중에 새 데이터의 가용성을 나타내기 위해 콜백을 반복적으로 호출 합니다.

`CDataPathProperty`는 `CAsyncMonikerFile`에서 파생됩니다. `CCachedDataPathProperty`는 `CDataPathProperty`에서 파생됩니다. ActiveX 컨트롤에서 비동기 속성을 구현 하려면 또는에서 클래스를 파생 `CDataPathProperty` 시키고 `CCachedDataPathProperty` 수신 하려는 [ondataavailable](reference/casyncmonikerfile-class.md#ondataavailable) 및 기타 알림을 재정의 합니다.

#### <a name="to-download-a-file-using-asynchronous-monikers"></a>비동기 모니커를 사용 하 여 파일을 다운로드 하려면

1. [CAsyncMonikerFile](reference/casyncmonikerfile-class.md)에서 파생 된 클래스를 선언 합니다.

1. 데이터를 표시 하는 데 [사용할 수 있는 Ondataavailable](reference/casyncmonikerfile-class.md#ondataavailable) 재정의 합니다.

1. [OnProgress](reference/casyncmonikerfile-class.md#onprogress), [Onstartbinding](reference/casyncmonikerfile-class.md#onstartbinding)및 [onstartbinding](reference/casyncmonikerfile-class.md#onstopbinding)을 비롯 한 다른 멤버 함수를 재정의 합니다.

1. 이 클래스의 인스턴스를 선언 하 고이를 사용 하 여 Url을 엽니다.

ActiveX 컨트롤에서 비동기로 다운로드 하는 방법에 대 한 자세한 내용은 [인터넷의 Activex 컨트롤](activex-controls-on-the-internet.md)을 참조 하십시오.

## <a name="see-also"></a>참고 항목

[MFC 인터넷 프로그래밍 작업](mfc-internet-programming-tasks.md)<br/>
[MFC 인터넷 프로그래밍 기본 사항](mfc-internet-programming-basics.md)
