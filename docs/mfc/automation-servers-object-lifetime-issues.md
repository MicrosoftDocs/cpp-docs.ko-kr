---
description: '자동화 서버: Object-Lifetime 문제에 대 한 자세한 정보'
title: '자동화 서버: 개체 수명 문제'
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
ms.openlocfilehash: dd6f60766880f20715cd44f8531639ab78bcc86b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339854"
---
# <a name="automation-servers-object-lifetime-issues"></a>자동화 서버: 개체 수명 문제

자동화 클라이언트에서 OLE 항목을 만들거나 활성화할 때 서버는 해당 개체에 대 한 포인터를 클라이언트에 전달 합니다. 클라이언트는 OLE 함수 [IUnknown:: AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)에 대 한 호출을 통해 개체에 대 한 참조를 설정 합니다. 이 참조는 클라이언트가 [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)를 호출할 때까지 적용 됩니다. MFC 라이브러리의 OLE 클래스로 작성 된 클라이언트 응용 프로그램은 이러한 호출을 수행할 필요가 없습니다. 프레임 워크에서 그렇게 합니다. OLE 시스템과 서버 자체는 개체에 대 한 참조를 설정할 수 있습니다. 개체에 대 한 외부 참조가 적용 되는 동안에는 서버에서 개체를 삭제 하면 안 됩니다.

프레임 워크는 [Ccmdtarget](reference/ccmdtarget-class.md)에서 파생 된 모든 서버 개체에 대 한 참조 수의 내부 수를 유지 합니다. 이 개수는 자동화 클라이언트나 다른 엔터티가 개체에 대 한 참조를 추가 하거나 해제할 때 업데이트 됩니다.

참조 횟수가 0이 되 면 프레임 워크는 [Ccmdtarget:: OnFinalRelease](reference/ccmdtarget-class.md#onfinalrelease)가상 함수를 호출 합니다. 이 함수의 기본 구현에서는 연산자를 호출 **`delete`** 하 여이 개체를 삭제 합니다.

MFC 라이브러리는 외부 클라이언트가 응용 프로그램의 개체에 대 한 참조를 가질 때 응용 프로그램 동작을 제어 하기 위한 추가 기능을 제공 합니다. 서버는 각 개체에 대 한 참조 수를 유지 관리 하는 것 외에도 전체 활성 개체 수를 유지 합니다. [Afxolelockapp 호출](reference/application-control.md#afxolelockapp) 및 [가 afxoleunlockapp](reference/application-control.md#afxoleunlockapp) 전역 함수는 응용 프로그램의 활성 개체 수를 업데이트 합니다. 이 수가 0이 아니면 사용자가 시스템 메뉴에서 닫기를 선택 하거나 파일 메뉴에서 종료를 선택할 때 응용 프로그램이 종료 되지 않습니다. 대신 보류 중인 모든 클라이언트 요청이 완료 될 때까지 응용 프로그램의 주 창이 숨겨집니다 (제거 되지 않음). 일반적으로 `AfxOleLockApp` 및 `AfxOleUnlockApp` 는 자동화를 지 원하는 클래스의 생성자 및 소멸자에서 각각 호출 됩니다.

경우에 따라 클라이언트가 여전히 개체에 대 한 참조를 보유 하는 동안 서버를 강제로 종료 합니다. 예를 들어 서버가 종속 된 리소스를 사용할 수 없게 되어 서버에서 오류가 발생할 수 있습니다. 또한 사용자는 다른 응용 프로그램에서 참조 하는 개체가 포함 된 서버 문서를 닫을 수 있습니다.

Windows SDK 및을 참조 하십시오 `IUnknown::AddRef` `IUnknown::Release` .

## <a name="see-also"></a>참고 항목

[자동화 서버](automation-servers.md)<br/>
[AfxOleCanExitApp](reference/application-control.md#afxolecanexitapp)
