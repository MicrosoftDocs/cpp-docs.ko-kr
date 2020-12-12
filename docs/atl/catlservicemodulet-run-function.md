---
description: 'CAtlServiceModuleT:: Run 함수에 대해 자세히 알아보세요.'
title: 'CAtlServiceModuleT:: Run 함수'
ms.date: 11/04/2016
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
ms.openlocfilehash: f8bba170236138f6491c49506bccd29bc23d9dec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148345"
---
# <a name="catlservicemoduletrun-function"></a>CAtlServiceModuleT:: Run 함수

`Run` , 및에 대 한 호출을 포함 `PreMessageLoop` `RunMessageLoop` `PostMessageLoop` 합니다. 가 호출 된 후는 `PreMessageLoop` 먼저 서비스의 스레드 ID를 저장 합니다. 서비스는 Win32 API 함수 [Postthreadmessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew)를 사용 하 여 WM_QUIT 메시지를 전송 하 여이 ID를 사용 합니다.

`PreMessageLoop` 그런 다음 `InitializeSecurity` 를 호출 합니다. 기본적으로는 `InitializeSecurity` 보안 설명자가 NULL로 설정 된 [CoInitializeSecurity](/windows/win32/api/combaseapi/nf-combaseapi-coinitializesecurity) 를 호출 합니다. 즉, 사용자가 개체에 액세스할 수 있습니다.

서비스에서 자체 보안을 지정 하지 않으려는 경우를 재정의 하 고를 `PreMessageLoop` 호출 하지 않으면 `InitializeSecurity` COM이 레지스트리에서 보안 설정을 결정 합니다. 레지스트리 설정을 편리 하 게 구성 하는 방법은이 섹션의 뒷부분에서 설명 하는 [DCOMCNFG](../atl/dcomcnfg.md) 유틸리티를 사용 하는 것입니다.

보안이 지정 되 면 새 클라이언트에서 프로그램에 연결할 수 있도록 개체가 COM에 등록 됩니다. 마지막으로 프로그램은 SCM (서비스 제어 관리자)이 실행 중임을 알려 주며 프로그램은 메시지 루프를 입력 합니다. 프로그램은 서비스가 종료 될 때 종료 메시지를 게시할 때까지 계속 실행 됩니다.

## <a name="see-also"></a>참고 항목

[Services](../atl/atl-services.md)<br/>
[CSecurityDesc 클래스](../atl/reference/csecuritydesc-class.md)<br/>
[CSid 클래스](../atl/reference/csid-class.md)<br/>
[CDacl 클래스](../atl/reference/cdacl-class.md)<br/>
[CAtlServiceModuleT:: Run](../atl/reference/catlservicemodulet-class.md#run)
