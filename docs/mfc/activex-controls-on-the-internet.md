---
description: '자세한 정보: 인터넷의 ActiveX 컨트롤'
title: 인터넷의 ActiveX 컨트롤
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX controls [MFC], creating
- ActiveX controls [MFC], Internet
- downloading data with ActiveX controls
- OLE controls [MFC], upgrading to ActiveX
- Internet applications [MFC], ActiveX controls
- networks [MFC], downloading with ActiveX controls
ms.assetid: 7ab943c8-2022-41df-9065-d629b616eeec
ms.openlocfilehash: 5f186d74ff0b448d1cef6a956a6495f6a8890798
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339132"
---
# <a name="activex-controls-on-the-internet"></a>인터넷의 ActiveX 컨트롤

ActiveX 컨트롤은 OLE 컨트롤 사양의 업데이트 된 버전입니다.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. 자세한 내용은 [ActiveX Controls](activex-controls.md)을 참조 하세요.

컨트롤은 인터넷의 COM 인식 웹 브라우저를 비롯 한 다양 한 컨테이너에서 사용할 수 있는 프로그래밍 가능한 소프트웨어 구성 요소를 개발 하기 위한 기본 아키텍처입니다. 모든 ActiveX 컨트롤은 인터넷 컨트롤이 될 수 있으며 해당 기능을 활성 문서에 추가 하거나 웹 페이지의 일부가 될 수 있습니다. 웹 페이지의 컨트롤은 스크립팅을 사용 하 여 서로 통신할 수 있습니다.

ActiveX 컨트롤은 인터넷으로 제한 되지 않습니다. 컨트롤이 해당 컨테이너에 필요한 인터페이스를 지원 하기만 하면 모든 컨테이너에서 ActiveX 컨트롤을 사용할 수도 있습니다.

**ActiveX 컨트롤에는 다음과 같은 여러 가지 이점이 있습니다.**

- 이전 OLE 컨트롤 보다 필요한 인터페이스가 줄어듭니다.

- 창 없는 상태 이며 항상 활성 상태로 있을 수 있습니다.

**ActiveX 컨트롤이 되려면 컨트롤은 다음을 수행 해야 합니다.**

- 인터페이스를 지원 `IUnknown` 합니다.

- COM 개체입니다.

- **DLLRegisterServer** 및 **DLLUnRegisterServer** 를 내보냅니다.

- 기능에 필요한 추가 인터페이스를 지원 합니다.

## <a name="making-your-existing-controls-internet-friendly"></a>기존 컨트롤 Internet-Friendly

인터넷 환경에서 잘 작동 하는 컨트롤을 디자인 하려면 인터넷에서 비교적 낮은 전송 요금을 고려해 야 합니다. 기존 컨트롤을 사용할 수 있습니다. 그러나 코드 크기를 작게 만들고 컨트롤 속성을 비동기식으로 다운로드 하기 위해 수행 해야 하는 단계가 있습니다.

컨트롤의 성능을 향상 시키려면 효율성 고려 사항에 대 한 다음 팁을 따르십시오.

- [ActiveX 컨트롤: 최적화](mfc-activex-controls-optimization.md)문서에 설명 된 기술을 구현 합니다.

- 컨트롤을 인스턴스화하는 방법을 고려 합니다.

- 비동기 여야 합니다. 다른 프로그램을 유지 하지 않습니다.

- 데이터를 작은 블록으로 다운로드 합니다.

   비트맵 또는 비디오 데이터와 같은 대량 스트림을 다운로드 하는 경우 컨테이너와 협력 하 여 컨트롤의 데이터에 비동기적으로 액세스 합니다. 데이터를 검색할 수 있는 다른 컨트롤과 협조적으로 작동 하는 증분 또는 프로그레시브 방식으로 데이터를 검색 합니다. 코드를 비동기적으로 다운로드할 수도 있습니다.

- 백그라운드에서 코드 및 속성을 다운로드 합니다.

- 가능한 한 빨리 사용자 인터페이스가 활성화 됩니다.

- 영구 데이터를 저장 하는 방법, 속성 및 대량 데이터 Blob (예: 비트맵 이미지 또는 비디오 데이터)를 고려 합니다.

   큰 비트맵 또는 AVI 파일과 같이 상당한 양의 영구적인 데이터를 가진 컨트롤은 다운로드 하는 방법에 주의 해야 합니다. 문서 또는 페이지는 가능한 한 빨리 표시 될 수 있으며, 컨트롤이 백그라운드에서 데이터를 검색 하는 동안 사용자가 페이지와 상호 작용할 수 있습니다.

- 코드 크기와 실행 시간을 유지 하기 위해 효율적인 루틴을 작성 합니다.

   몇 바이트의 영구 데이터를 포함 하는 작은 단추 및 레이블 컨트롤은 인터넷 환경에서 사용 하기에 적합 하 고 브라우저 내에서 잘 작동 합니다.

- 진행 상황을 컨테이너에 전달 하는 것이 좋습니다.

   사용자가 페이지와의 상호 작용을 시작 하 고 다운로드가 완료 될 때를 포함 하 여 비동기 다운로드에서 컨테이너에 대 한 진행률을 알립니다. 컨테이너는 사용자에 게 진행률 (예: 완료율)을 표시할 수 있습니다.

- 클라이언트 컴퓨터에 컨트롤을 등록 하는 방법을 고려 합니다.

## <a name="creating-a-new-activex-control"></a>새 ActiveX 컨트롤 만들기

응용 프로그램 마법사를 사용 하 여 새 컨트롤을 만들 때 비동기 모니커 및 기타 최적화에 대 한 지원을 사용 하도록 선택할 수 있습니다. 컨트롤 속성을 비동기적으로 다운로드 하기 위한 지원을 추가 하려면 다음 단계를 수행 합니다.

#### <a name="to-create-your-project-using-the-mfc-activex-control-wizard"></a>MFC ActiveX 컨트롤 마법사를 사용 하 여 프로젝트를 만들려면

1. **파일** 메뉴에서 **새로 만들기** 를 클릭 합니다.

1. Visual Studio c + + 프로젝트에서 **MFC ActiveX 컨트롤 마법사** 를 선택 하 고 프로젝트의 이름을로 합니다.

1. **컨트롤 설정** 페이지에서 **속성을 비동기적으로 로드** 를 선택 합니다. 이 옵션을 선택 하면 준비 상태 속성과 준비 상태 변경 이벤트를 설정 합니다.

   [ActiveX 컨트롤: 최적화](mfc-activex-controls-optimization.md)에 설명 된 창 없는 **활성화** 와 같은 기타 최적화를 선택할 수도 있습니다.

1. **마침** 을 선택하여 프로젝트를 만듭니다.

#### <a name="to-create-a-class-derived-from-cdatapathproperty"></a>CDataPathProperty에서 파생 된 클래스를 만들려면

1. 에서 파생 된 클래스를 만듭니다 `CDataPathProperty` .

1. 컨트롤의 헤더 파일을 포함 하는 각 소스 파일에이 클래스에 대 한 헤더 파일을 추가 합니다.

1. 이 클래스에서를 재정의 `OnDataAvailable` 합니다. 이 함수는 데이터를 표시할 수 있을 때마다 호출 됩니다. 데이터를 사용할 수 있게 되 면, 예를 들어 점진적으로 렌더링 하 여 선택 하는 방법으로 데이터를 처리할 수 있습니다.

   아래 발췌 한 코드는 편집 컨트롤의 데이터를 점진적으로 표시 하는 간단한 예제입니다. **BSCF_FIRSTDATANOTIFICATION** 플래그를 사용 하 여 편집 컨트롤을 지웁니다.

   [!code-cpp[NVC_MFCActiveXControl#1](codesnippet/cpp/activex-controls-on-the-internet_1.cpp)]

   AFXCMN.H를 포함 해야 합니다. H를 사용 하 여 클래스를 사용 `CListCtrl` 합니다.

1. 컨트롤의 전체 상태가 변경 되 면 (예: 로드에서 초기화 또는 사용자 대화형으로)를 호출 `COleControl::InternalSetReadyState` 합니다. 컨트롤에 데이터 경로 속성이 하나만 있는 경우 **BSCF_LASTDATANOTIFICATION** 에 코드를 추가 하 여 다운로드 완료를 컨테이너에 알릴 수 있습니다. 예를 들어:

   [!code-cpp[NVC_MFCActiveXControl#2](codesnippet/cpp/activex-controls-on-the-internet_2.cpp)]

1. `OnProgress`를 재정의합니다. 에는 `OnProgress` 최대 범위를 표시 하는 숫자와 현재 다운로드를 따라 표시 되는 값이 전달 됩니다. 이러한 번호를 사용 하 여 완료율과 같은 상태를 사용자에 게 표시할 수 있습니다.

다음 절차에서는 컨트롤에 속성을 추가 하 여 막 파생 된 클래스를 사용 합니다.

#### <a name="to-add-a-property"></a>속성을 추가 하려면

1. **클래스 뷰** 에서 라이브러리 노드 아래의 인터페이스를 마우스 오른쪽 단추로 클릭 하 고 **추가** 를 선택한 다음 **속성 추가** 를 선택 합니다. 그러면 **속성 추가 마법사** 가 시작 됩니다.

1. **속성 추가 마법사** 에서 **Set/Get 메서드** 라디오 단추를 선택 하 고 **속성 이름**(예: editcontroltext)을 입력 한 다음 **속성 형식** 으로 BSTR을 선택 합니다.

1. **Finish** 를 클릭합니다.

1. 파생 클래스의 멤버 변수를 `CDataPathProperty` ActiveX 컨트롤 클래스로 선언 합니다.

   [!code-cpp[NVC_MFCActiveXControl#3](codesnippet/cpp/activex-controls-on-the-internet_3.h)]

1. `Get/Set` 메서드를 구현합니다. 의 `Get` 경우 문자열을 반환 합니다. 의 경우 `Set` 속성을 로드 하 고를 호출 `SetModifiedFlag` 합니다.

   [!code-cpp[NVC_MFCActiveXControl#4](codesnippet/cpp/activex-controls-on-the-internet_4.cpp)]

1. [Dopropexchange](reference/colecontrol-class.md#dopropexchange)에서 다음 줄을 추가 합니다.

   [!code-cpp[NVC_MFCActiveXControl#5](codesnippet/cpp/activex-controls-on-the-internet_5.cpp)]

1. 다음 줄을 추가 하 여 속성에 컨트롤을 다시 설정 하도록 알리기 위해 [Resetdata](reference/cdatapathproperty-class.md#resetdata) 를 재정의 합니다.

   [!code-cpp[NVC_MFCActiveXControl#6](codesnippet/cpp/activex-controls-on-the-internet_6.cpp)]

## <a name="deciding-whether-to-derive-from-cdatapathproperty-or-ccacheddatapathproperty"></a>CDataPathProperty 또는 CCachedDataPathProperty에서 파생 되는지 결정

이전 예제에서는에서 컨트롤의 속성을 파생 하는 단계를 설명 합니다 `CDataPathProperty` . 자주 변경 되는 실시간 데이터를 다운로드 하 고 모든 데이터를 유지할 필요가 없는 경우에는 현재 값만 선택 하는 것이 좋습니다. 예를 들어 주식 시세 컨트롤이 있습니다.

에서 파생 시킬 수도 있습니다 `CCachedDataPathProperty` . 이 경우 다운로드 된 데이터는 메모리 파일에 캐시 됩니다. 이 옵션은 다운로드 한 모든 데이터를 유지 해야 하는 경우 (예: 비트맵을 점진적으로 렌더링 하는 컨트롤)에 적합 합니다. 이 경우 클래스에는 데이터를 포함 하는 멤버 변수가 있습니다.

`CMemFile m_Cache;`

ActiveX 컨트롤 클래스에서이 메모리 매핑된 파일을 사용 하 여 데이터를 `OnDraw` 표시할 수 있습니다. ActiveX 컨트롤 `CCachedDataPathProperty` 파생 클래스에서 `OnDataAvailable` 기본 클래스 구현을 호출한 후 멤버 함수를 재정의 하 고 컨트롤을 무효화 합니다.

[!code-cpp[NVC_MFCActiveXControl#7](codesnippet/cpp/activex-controls-on-the-internet_7.cpp)]

## <a name="downloading-data-asynchronously-using-activex-controls"></a>ActiveX 컨트롤을 사용 하 여 비동기적으로 데이터 다운로드

네트워크를 통해 데이터를 다운로드 하는 작업은 비동기적으로 수행 해야 합니다. 이렇게 하면 많은 양의 데이터가 전송 되거나 연결이 느려지는 경우 다운로드 프로세스가 클라이언트의 다른 프로세스를 차단 하지 않는다는 이점이 있습니다.

비동기 모니커는 네트워크를 통해 비동기적으로 데이터를 다운로드 하는 방법을 제공 합니다. 비동기 모니커에 대 한 읽기 작업은 작업이 완료 되지 않은 경우에도 즉시 반환 됩니다.

예를 들어, 10 바이트만 사용 가능 하 고 1K 파일에서 Read가 비동기적으로 호출 되는 경우 Read는 차단 되지 않지만 현재 사용할 수 있는 10 바이트를 사용 하 여 반환 됩니다.

클래스를 사용 하 여 [비동기 모니커](asynchronous-monikers-on-the-internet.md) 를 구현 `CAsyncMonikerFile` 합니다. 그러나 ActiveX 컨트롤은 `CDataPathProperty` 에서 파생 된 클래스를 사용 `CAsyncMonikerFile` 하 여 비동기 컨트롤 속성을 구현 하는 데 도움이 됩니다.

## <a name="displaying-a-control-on-a-web-page"></a>웹 페이지에 컨트롤 표시

웹 페이지에 컨트롤을 삽입 하는 데 사용할 수 있는 개체 태그와 특성의 예는 다음과 같습니다.

```xml
<OBJECT
  CLASSID="clsid:FC25B780-75BE-11CF-8B01-444553540000"
  CODEBASE="/ie/download/activex/iechart.ocx"
  ID=chart1
  WIDTH=400
  HEIGHT=200
  ALIGN=center
  HSPACE=0
  VSPACE=0>
  <PARAM NAME="BackColor" value="#ffffff"/>
  <PARAM NAME="ForeColor" value="#0000ff"/>
  <PARAM NAME="url" VALUE="/ie/controls/chart/mychart.txt"/>
</OBJECT>
```

## <a name="updating-an-existing-ole-control-to-use-new-activex-control-features"></a>새 ActiveX 컨트롤 기능을 사용 하도록 기존 OLE 컨트롤 업데이트

4.2 이전 버전의 Visual C++을 사용 하 여 OLE 컨트롤을 만든 경우 성능을 개선 하 고 기능을 향상 시키기 위해 수행할 수 있는 단계가 있습니다. 이러한 변경 내용에 대 한 자세한 내용은 [ActiveX 컨트롤: 최적화](mfc-activex-controls-optimization.md)를 참조 하세요.

비동기 속성 지원을 기존 컨트롤에 추가 하는 경우 준비 상태 속성과 이벤트를 직접 추가 해야 `ReadyStateChange` 합니다. 컨트롤에 대 한 생성자에서 다음을 추가 합니다.

[!code-cpp[NVC_MFCActiveXControl#8](codesnippet/cpp/activex-controls-on-the-internet_8.cpp)]

[COleControl:: InternalSetReadyState](reference/colecontrol-class.md#internalsetreadystate)를 호출 하 여 코드가 다운로드 될 때 준비 상태를 업데이트 합니다. `InternalSetReadyState` `OnProgress` 파생 클래스의 재정의에서 호출할 수 있는 한 가지 위치가 있습니다 `CDataPathProperty` .

## <a name="see-also"></a>참고 항목

[MFC 인터넷 프로그래밍 작업](mfc-internet-programming-tasks.md)<br/>
[MFC 인터넷 프로그래밍 기본 사항](mfc-internet-programming-basics.md)
