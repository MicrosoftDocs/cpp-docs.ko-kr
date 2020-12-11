---
description: '자세한 정보: ATL 모듈 클래스'
title: ATL 모듈 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
ms.openlocfilehash: 16c38a6a38f4179e5846a445bd9573e7dc4500f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163303"
---
# <a name="atl-module-classes"></a>ATL 모듈 클래스

이 항목에서는 ATL 7.0의 새로운 모듈 클래스에 대해 설명 합니다.

## <a name="ccommodule-replacement-classes"></a>CComModule 대체 클래스

이전 버전의 ATL이 사용 `CComModule` 되었습니다. ATL 7.0에서는 `CComModule` 기능이 여러 클래스로 대체 됩니다.

- [Catlbasemodule](../atl/reference/catlbasemodule-class.md) ATL을 사용 하는 대부분의 응용 프로그램에 필요한 정보를 포함 합니다. 모듈의 HINSTANCE와 리소스 인스턴스를 포함 합니다.

- [Catlcommodule](../atl/reference/catlcommodule-class.md) ATL의 COM 클래스에 필요한 정보를 포함 합니다.

- [Catlwinmodule](../atl/reference/catlwinmodule-class.md) ATL의 창 고 클래스에 필요한 정보를 포함 합니다.

- [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) 인터페이스 디버깅에 대 한 지원을 포함 합니다.

- [Catlmodule](../atl/reference/catlmodule-class.md) 다음 `CAtlModule` 파생 클래스는 특정 응용 프로그램 유형에 필요한 정보를 포함 하도록 사용자 지정 됩니다. 이러한 클래스의 멤버 대부분은 재정의할 수 있습니다.

  - [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) DLL 응용 프로그램에서 사용 됩니다. 표준 내보내기에 대 한 코드를 제공 합니다.

  - [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) EXE 응용 프로그램에서 사용 됩니다. EXE에 필요한 코드를 제공 합니다.

  - [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) Windows NT 및 Windows 2000 서비스를 만들 수 있도록 지원 합니다.

`CComModule` 는 이전 버전과의 호환성을 위해 계속 사용할 수 있습니다.

## <a name="reasons-for-distributing-ccommodule-functionality"></a>CComModule 기능을 배포 하는 이유

의 기능은 `CComModule` 다음과 같은 이유로 여러 새로운 클래스에 배포 되었습니다.

- 기능을 세부적으로 만듭니다 `CComModule` .

   COM, 창 이동, 인터페이스 디버깅 및 응용 프로그램별 (DLL 또는 EXE) 기능에 대 한 지원은 이제 개별 클래스에 있습니다.

- 이러한 각 모듈의 전역 인스턴스를 자동으로 선언 합니다.

   필수 모듈 클래스의 전역 인스턴스는 프로젝트에 연결 됩니다.

- Init 및 Term 메서드를 호출할 필요가 없습니다.

   Init 및 Term 메서드는 모듈 클래스의 생성자 및 소멸자로 이동 되었습니다. 더 이상 Init 및 Term을 호출할 필요가 없습니다.

## <a name="see-also"></a>참고 항목

[개념](../atl/active-template-library-atl-concepts.md)<br/>
[클래스 개요](../atl/atl-class-overview.md)
