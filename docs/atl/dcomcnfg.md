---
description: '다음에 대 한 자세한 정보: DCOMCNFG'
title: DCOMCNFG
ms.date: 11/04/2016
helpviewer_keywords:
- DCOMCNFG utility
- DCOM, configuring in ATL
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
ms.openlocfilehash: d99b0018d63cedbccaf57ec4cadeb649f390dcf1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153163"
---
# <a name="dcomcnfg"></a>DCOMCNFG

DCOMCNFG는 레지스트리의 다양 한 DCOM 특정 설정을 구성할 수 있는 Windows NT 4.0 유틸리티입니다. DCOMCNFG 창에는 기본 보안, 기본 속성 및 응용 프로그램의 3 개 페이지가 있습니다. Windows 2000에는 기본 프로토콜인 네 번째 페이지가 있습니다.

## <a name="default-security-page"></a>기본 보안 페이지

기본 보안 페이지를 사용 하 여 시스템의 개체에 대 한 기본 사용 권한을 지정할 수 있습니다. 기본 보안 페이지에는 액세스, 시작 및 구성의 세 섹션이 있습니다. 섹션의 기본값을 변경 하려면 해당 하는 **기본값 편집** 단추를 클릭 합니다. 이러한 기본 보안 설정은의 레지스트리에 저장 됩니다 `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE` .

## <a name="default-protocols-page"></a>기본 프로토콜 페이지

이 페이지에는이 컴퓨터의 DCOM에서 사용할 수 있는 네트워크 프로토콜 집합이 나열 되어 있습니다. 순서는 사용 되는 우선 순위를 반영 합니다. 목록의 첫 번째는 우선 순위가 가장 높습니다. 이 페이지에서 프로토콜을 추가 하거나 삭제할 수 있습니다.

## <a name="default-properties-page"></a>기본 속성 페이지

다른 컴퓨터의 클라이언트가이 컴퓨터에서 실행 되는 COM 개체에 액세스 하도록 하려면 기본 속성 페이지에서 **이 컴퓨터에 분산 COM 사용** 확인란을 선택 해야 합니다. 이 옵션을 선택 하면 `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM` 값이로 설정 `Y` 됩니다.

## <a name="applications-page"></a>응용 프로그램 페이지

응용 프로그램 페이지를 사용 하 여 특정 개체에 대 한 설정을 변경할 수 있습니다. 목록에서 응용 프로그램을 선택 하 고 **속성** 단추를 클릭 하면 됩니다. 속성 창에는 5 개의 페이지가 있습니다.

- 일반 페이지에서는 작업 중인 응용 프로그램을 확인 합니다.

- 위치 페이지에서는 클라이언트에서 관련 CLSID를 호출할 때 응용 프로그램이 실행 되는 위치를 지정할 수 있습니다 `CoCreateInstance` . **다음 컴퓨터에서 응용 프로그램 실행** 확인란을 선택 하 고 컴퓨터 이름을 입력 하는 경우 `RemoteServerName` 해당 응용 프로그램에 대 한 AppID 아래에 값이 추가 됩니다. **이 컴퓨터에서 응용 프로그램 실행** 확인란의 선택을 취소 하면 `LocalService` 값이로 바뀌고 `_LocalService` 사용 하지 않도록 설정 됩니다.

- 보안 페이지는 이러한 설정이 현재 응용 프로그램에만 적용 된다는 점을 제외 하 고 DCOMCNFG 창에 있는 기본 보안 페이지와 비슷합니다. 그러면 해당 개체에 대 한 AppID 아래에 설정이 저장 됩니다.

- 식별 페이지는 응용 프로그램을 실행 하는 데 사용 되는 사용자를 식별 합니다.

- 끝점 페이지에는 선택한 DCOM 서버의 클라이언트에서 사용할 수 있는 프로토콜 및 끝점 집합이 나열 됩니다.

## <a name="see-also"></a>참고 항목

[Services](../atl/atl-services.md)
