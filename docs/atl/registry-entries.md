---
description: '자세한 정보: 레지스트리 항목'
title: 레지스트리 항목 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
ms.openlocfilehash: c89c8f64a91c09f16333c3381a33d792332543d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138582"
---
# <a name="registry-entries"></a>레지스트리 항목

DCOM에서는 하나 이상의 DCOM 개체에 대 한 구성 옵션을 레지스트리의 중앙 위치에 그룹화 하는 응용 프로그램 Id (Appid) 라는 개념을 도입 했습니다. 개체의 CLSID 아래에 있는 AppID 명명 된 값에 해당 값을 표시 하 여 AppID를 지정 합니다.

기본적으로 ATL 생성 서비스에서는 해당 CLSID를 해당 AppID의 GUID로 사용 합니다. 에서 `HKEY_CLASSES_ROOT\AppID` DCOM 관련 항목을 지정할 수 있습니다. 처음에는 두 가지 항목이 있습니다.

- `LocalService`-값이 서비스 이름과 동일 합니다. 이 값이 있으면 `LocalServer32` CLSID 아래의 키 대신 사용 됩니다.

- `ServiceParameters`이며 값은와 같습니다 `-Service` . 이 값은 서비스가 시작 될 때 서비스에 전달 되는 매개 변수를 지정 합니다. 이러한 매개 변수는가 아니라 서비스의 함수에 전달 됩니다 `ServiceMain` `WinMain` .

또한 DCOM 서비스는에서 다른 키를 만들어야 `HKEY_CLASSES_ROOT\AppID` 합니다. 이 키는 실행 파일의 이름과 같으며, AppID 항목을 다시 가리키는 AppID 값을 포함 하므로 상호 참조 역할을 합니다.

## <a name="see-also"></a>참고 항목

[Services](../atl/atl-services.md)
