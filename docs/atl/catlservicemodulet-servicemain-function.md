---
description: '자세히 알아보기: CAtlServiceModuleT:: ServiceMain 함수'
title: 'CAtlServiceModuleT:: ServiceMain 함수'
ms.date: 11/04/2016
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: 97093d13a2f13ea0d6bd4ba5db46bef45d239cc9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148332"
---
# <a name="catlservicemoduletservicemain-function"></a>CAtlServiceModuleT:: ServiceMain 함수

SCM (서비스 제어 관리자)은 서비스 `ServiceMain` 제어판 응용 프로그램을 열고 서비스를 선택 하 고 **시작** 을 클릭 하면 호출 됩니다.

SCM `ServiceMain` 이 호출 되 면 서비스는 scm에 처리기 함수를 제공 해야 합니다. 이 함수를 통해 SCM은 서비스의 상태를 가져오고 특정 지침 (예: 일시 중지 또는 중지)을 전달할 수 있습니다. SCM은 서비스가 `_Handler` Win32 API 함수 [RegisterServiceCtrlHandler](/windows/win32/api/winsvc/nf-winsvc-registerservicectrlhandlerw)에 전달 될 때이 함수를 가져옵니다. `_Handler`는 비정적 멤버 함수 [처리기](../atl/reference/catlservicemodulet-class.md#handler)를 호출 하는 정적 멤버 함수입니다.

시작할 때 서비스는 SCM에 현재 상태를 알려야 합니다. 이를 위해 Win32 API 함수 [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus)에 SERVICE_START_PENDING를 전달 합니다.

`ServiceMain` 그런 다음 `CAtlExeModuleT::InitializeCom` [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex)함수를 호출 하는 Win32 API 함수를 호출 합니다. 기본적으로는 `InitializeCom` COINIT_MULTITHREADED 플래그를 함수에 전달 합니다. 이 플래그는 프로그램이 자유 스레드된 서버 임을 나타냅니다.

이제 `CAtlServiceModuleT::Run` 서비스의 주요 작업을 수행 하기 위해가 호출 됩니다. `Run` 서비스가 중지 될 때까지 계속 실행 됩니다.

## <a name="see-also"></a>참고 항목

[Services](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)
