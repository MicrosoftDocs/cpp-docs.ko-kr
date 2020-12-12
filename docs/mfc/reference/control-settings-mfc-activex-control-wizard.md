---
description: '자세히 알아보기: 컨트롤 설정, MFC ActiveX 컨트롤 마법사'
title: MFC ActiveX 컨트롤 마법사, 컨트롤 설정
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.settings
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
ms.openlocfilehash: 31e8c5fd257128e17017d3d0fa801fc812f99397
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301596"
---
# <a name="control-settings-mfc-activex-control-wizard"></a>MFC ActiveX 컨트롤 마법사, 컨트롤 설정

마법사의이 페이지를 사용 하 여 컨트롤의 동작을 지정할 수 있습니다. 예를 들어 표준 Windows 컨트롤 형식에 대 한 컨트롤의 기반이 되는 컨트롤의 동작과 모양을 최적화 하거나 컨트롤이 다른 컨트롤의 컨테이너 역할을 할 수 있음을 나타낼 수 있습니다.

이 페이지에서 옵션을 선택 하 여 컨트롤의 효율성을 최대화 하는 방법에 대 한 자세한 내용은 [MFC ActiveX 컨트롤: 최적화](../../mfc/mfc-activex-controls-optimization.md)를 참조 하세요.

## <a name="uielement-list"></a>UI 요소 목록

- **다음을 기준으로 컨트롤 만들기**

   이 목록에서 컨트롤이 상속 해야 하는 컨트롤의 종류를 선택할 수 있습니다. 목록은에서 사용할 수 있는 컨트롤 클래스의 하위 집합이 `CreateWindowEx` 며, ctrl. h에 지정 된 추가 공용 컨트롤입니다. 선택 항목은 `PreCreateWindow` *ProjName* Ctrl .cpp 파일의 함수에 있는 컨트롤의 스타일을 결정 합니다. 자세한 내용은 [MFC ActiveX 컨트롤: Windows 컨트롤 서브클래싱](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md)을 참조 하세요.

   |제어|설명|
   |-------------|-----------------|
   |**단추만**|Windows 단추 컨트롤|
   |**상자가**|Windows 콤보 상자 컨트롤입니다.|
   |**편집할**|Windows 편집 상자 컨트롤입니다.|
   |**상자가**|Windows 목록 상자 컨트롤|
   |**SCROLLBAR**|Windows 스크롤 막대 컨트롤입니다.|
   |**정적인**|Windows 정적 컨트롤|
   |**msctls_hotkey32**|핫 키 공용 컨트롤|
   |**msctls_progress32**|진행률 표시줄 공용 컨트롤|
   |**msctls_statusbar32**|상태 표시줄 공용 컨트롤|
   |**msctls_trackbar32**|트랙 표시줄 공용 컨트롤입니다.|
   |**msctls_updown32**|스핀 단추 (또는 up-down) 공용 컨트롤|
   |**SysAnimate32**|애니메이션 공용 컨트롤|
   |**SysHeader32**|헤더 공용 컨트롤|
   |**SysListView32**|목록 뷰 공용 컨트롤|
   |**SysTabControl32**|탭 공용 컨트롤|
   |**SysTreeView32**|트리 뷰 공용 컨트롤|

- **표시 될 때 활성화**

   컨트롤에 액세스할 때 컨트롤에 대 한 창을 만들도록 지정 합니다. 기본적으로 표시 되는 **경우 활성화** 옵션이 선택 됩니다. 사용자가 마우스를 클릭할 때 처럼 컨테이너에 필요할 때까지 컨트롤 활성화를 지연 하려면이 옵션을 선택 취소 합니다. 이 기능을 해제 하면 컨트롤이 필요할 때까지 창 생성 비용이 발생 하지 않습니다. 자세한 내용은 [표시 될 때 활성화 옵션 해제](../../mfc/turning-off-the-activate-when-visible-option.md)를 참조 하세요.

- **런타임에 숨김**

   런타임에 컨트롤에 사용자 인터페이스가 없도록 지정 합니다. 타이머는 표시 하지 않으려는 일종의 컨트롤입니다.

- **[정보] 대화 상자 포함**

   컨트롤에 버전 번호 및 저작권 정보를 표시 하는 표준 Windows **정보** 대화 상자를 포함 하도록 지정 합니다.

   > [!NOTE]
   > 사용자가 컨트롤에 대 한 도움말에 액세스 하는 방법은 도움말을 구현 하는 방법 및 컨테이너 도움말에 컨트롤 도움말을 통합 했는지 여부에 따라 달라 집니다.

   이 옵션을 선택 하면 `AboutBox` 컨트롤 메서드가 프로젝트 컨트롤 클래스 (C *ProjName* Ctrl. .cpp)에 삽입 되 고 aboutbox 함이 프로젝트 디스패치 맵에 추가 됩니다. 이 옵션은 기본적으로 선택됩니다.

- **최적화 된 그리기 코드**

   동일한 장치 컨텍스트로 그려진 모든 컨테이너 컨트롤이 그려진 후 컨테이너가 원래 GDI 개체를 자동으로 복원 하도록 지정 합니다. 이 기능에 대 한 자세한 내용은 [컨트롤 그리기 최적화](../../mfc/optimizing-control-drawing.md)를 참조 하세요.

- **창 없는 활성화**

   컨트롤이 활성화 될 때 창을 생성 하지 않도록 지정 합니다. 창 없는 활성화는 사각형이 아닌 투명 한 컨트롤을 허용 하 고 창 없는 컨트롤은 창이 필요한 컨트롤 보다 시스템 오버 헤드가 더 적게 필요 합니다. 창 없는 컨트롤은 잘리지 않는 장치 컨텍스트 또는 깜빡임 없는 활성화를 허용 하지 않습니다. 1996 이전에 생성 된 컨테이너는 창 없는 활성화를 지원 하지 않습니다. 이 옵션을 사용 하는 방법에 대 한 자세한 내용은 [창 없는 활성화 제공](../../mfc/providing-windowless-activation.md)을 참조 하세요.

- **잘리지 않는 장치 컨텍스트**

   에서에 대 한 호출을 사용 하지 않도록 설정 하려면 컨트롤 헤더 (*projname* ctrl. h)에서 [COleControl:: getcontrolflags](../../mfc/reference/colecontrol-class.md#getcontrolflags) 를 재정의 `IntersectClipRect` `COleControl` 합니다. 이 옵션을 선택 하면 작은 속도의 이점이 제공 됩니다. **창 없는 활성화** 를 선택 하면이 기능을 사용할 수 없습니다. 자세한 내용은 [잘리지 않는 장치 컨텍스트 사용](../../mfc/using-an-unclipped-device-context.md)을 참조 하세요.

- **깜빡임 없는 활성화**

   컨트롤의 활성 및 비활성 상태 간에 발생 하는 그리기 작업 및 해당 시각적 개체를 제거 합니다. **창 없는 활성화** 를 선택 하면이 기능을 사용할 수 없습니다. 이 옵션을 설정 하는 경우 `noFlickerActivate` 플래그는 [COleControl:: getcontrolflags](../../mfc/reference/colecontrol-class.md#getcontrolflags)에서 반환 하는 플래그 중 하나입니다. 자세한 내용은 [Flicker-Free 활성화 제공](../../mfc/providing-flicker-free-activation.md)을 참조 하세요.

- **개체 삽입 대화 상자에서 사용 가능**

   사용할 수 있는 컨테이너에 대 한 **개체 삽입** 대화 상자에서 컨트롤을 사용할 수 있도록 지정 합니다. 이 옵션을 선택 하면 `afxRegInsertable` 플래그가에서 반환 하는 플래그 중 하나입니다 `AfxOleRegisterControlClass` . 사용자는 **개체 삽입** 대화 상자를 사용 하 여 새로 만들었거나 기존 개체를 복합 문서에 삽입할 수 있습니다.

- **비활성 상태인 경우 마우스 포인터 알림**

   컨트롤이 활성화 되었는지 여부에 관계 없이 컨트롤이 마우스 포인터 알림을 처리할 수 있도록 합니다. 이 옵션을 선택 하는 경우 `pointerInactive` 플래그는 [COleControl:: getcontrolflags](../../mfc/reference/colecontrol-class.md#getcontrolflags)에서 반환 하는 플래그 중 하나입니다. 이 옵션을 사용 하는 방법에 대 한 자세한 내용은 [비활성 상태에서 마우스 상호 작용 제공](../../mfc/providing-mouse-interaction-while-inactive.md)을 참조 하세요.

- **간단한 프레임 컨트롤 역할을 합니다.**

   컨트롤의 OLEMISC_SIMPLEFRAME 비트를 설정 하 여 컨트롤을 다른 컨트롤의 컨테이너로 지정 합니다. 자세한 내용은 [Simple Frame Site 포함](/windows/win32/com/simple-frame-site-containment)을 참조 하세요.

- **비동기적으로 속성 로드**

   이전 비동기 데이터를 다시 설정 하 고 컨트롤의 비동기 속성에 대 한 새 로드를 시작 합니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤 마법사](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[MFC ActiveX 컨트롤 마법사, 응용 프로그램 설정](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[MFC ActiveX 컨트롤 마법사, 컨트롤 이름](../../mfc/reference/control-names-mfc-activex-control-wizard.md)
