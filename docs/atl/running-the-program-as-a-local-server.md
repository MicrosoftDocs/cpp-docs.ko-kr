---
description: '자세한 정보: 프로그램을 로컬 서버로 실행'
title: 로컬 서버로 프로그램 실행
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
ms.openlocfilehash: 1cdf3cef0773769318d68964b28bb60ca66666d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157493"
---
# <a name="running-the-program-as-a-local-server"></a>로컬 서버로 프로그램 실행

프로그램을 서비스로 실행 하는 것이 불편 한 경우 일시적으로 레지스트리를 변경 하 여 프로그램이 일반 로컬 서버로 실행 되도록 할 수 있습니다. AppID에서 값의 이름을 `LocalService` 로 변경 하 `_LocalService` 고 `LocalServer32` CLSID 아래의 키가 올바르게 설정 되어 있는지 확인 합니다. (DCOMCNFG를 사용 하 여 응용 프로그램이 다른 컴퓨터에서 실행 되도록 지정 하려면 키의 이름을 `LocalServer32` 로 바꿉니다 `_LocalServer32` .) 에서에 대 한 호출에 `StartServiceCtrlDispatcher` `CAtlServiceModuleT::Start` 실패 하기 전에 몇 초 정도 소요 되기 때문에 프로그램을 로컬 서버로 실행 하면 시작 하는 데 몇 초 정도 걸립니다.

## <a name="see-also"></a>참고 항목

[디버깅 팁](../atl/debugging-tips.md)
