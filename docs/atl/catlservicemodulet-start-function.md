---
description: '자세히 알아보기: CAtlServiceModuleT:: Start 함수'
title: 'CAtlServiceModuleT:: Start 함수'
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: cfdae47f88c7957a4470da3129f3d3e071614276
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148319"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT:: Start 함수

서비스가 실행 되 면는를 호출 하 여 `_tWinMain` `CAtlServiceModuleT::WinMain` 을 호출 `CAtlServiceModuleT::Start` 합니다.

`CAtlServiceModuleT::Start``SERVICE_TABLE_ENTRY`각 서비스를 시작 함수에 매핑하는 구조체의 배열을 설정 합니다. 그런 다음이 배열은 Win32 API 함수 [startservicectrldispatcher가](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw)에 전달 됩니다. 이론적으로 한 EXE는 여러 서비스를 처리할 수 있으며 배열에는 여러 개의 구조가 있을 수 있습니다 `SERVICE_TABLE_ENTRY` . 그러나 현재는 ATL 생성 서비스가 EXE 당 하나의 서비스만 지원 합니다. 따라서 배열에는 서비스 이름과 시작 함수를 포함 하는 단일 항목이 있습니다 `_ServiceMain` . `_ServiceMain` 는 비정적 `CAtlServiceModuleT` 멤버 함수를 호출 하는의 정적 멤버 함수입니다 `ServiceMain` .

> [!NOTE]
> `StartServiceCtrlDispatcher`SCM (서비스 제어 관리자)에 연결 하지 못하면 프로그램이 서비스로 실행 되 고 있지 않을 수 있습니다. 이 경우 프로그램에서 직접를 호출 `CAtlServiceModuleT::Run` 하 여 프로그램이 로컬 서버로 실행 될 수 있도록 합니다. 로컬 서버로 프로그램을 실행 하는 방법에 대 한 자세한 내용은 [디버깅 팁](../atl/debugging-tips.md)을 참조 하십시오.

## <a name="see-also"></a>참고 항목

[Services](../atl/atl-services.md)<br/>
[CAtlServiceModuleT:: Start](../atl/reference/catlservicemodulet-class.md#start)
