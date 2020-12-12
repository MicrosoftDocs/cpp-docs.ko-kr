---
description: '자세한 정보: COM 소개'
title: COM 소개
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
ms.openlocfilehash: 635bce8c1214dddfc258ae6d2d6c7e751f778e9c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147669"
---
# <a name="introduction-to-com"></a>COM 소개

COM은 ActiveX 컨트롤 및 OLE가 빌드되는 기본적인 "개체 모델"입니다. COM은 개체가 해당 기능을 다른 구성 요소에 노출 하 고 응용 프로그램을 호스팅할 수 있도록 합니다. 개체 자체를 표시 하는 방법과 이러한 노출이 프로세스와 네트워크 간에 작동 하는 방식을 정의 합니다. 또한 COM은 개체의 수명 주기를 정의 합니다.

COM의 기본 개념은 다음과 같습니다.

- [인터페이스](../atl/interfaces-atl.md) -개체가 해당 기능을 노출 하는 메커니즘입니다.

- [IUnknown](../atl/iunknown.md) -다른 모든의 기반이 되는 기본 인터페이스입니다. COM을 통해 실행 되는 참조 계산 및 인터페이스 쿼리 메커니즘을 구현 합니다.

- [참조 횟수](../atl/reference-counting.md) -개체가 더 이상 사용 되지 않는 경우를 결정 하는 기술 이며, 따라서 자신을 자유롭게 제거할 수 있습니다.

- [QueryInterface](../atl/queryinterface.md) — 지정 된 인터페이스에 대 한 개체를 쿼리 하는 데 사용 되는 메서드입니다.

- [마샬링](../atl/marshaling.md) — 위치 독립성을 허용 하는 스레드, 프로세스 및 네트워크 경계에서 개체를 사용할 수 있도록 하는 메커니즘입니다.

- [집계](../atl/aggregation.md) -한 개체가 다른 개체를 사용할 수 있는 방법입니다.

## <a name="see-also"></a>참고 항목

[COM 및 ATL 소개](../atl/introduction-to-com-and-atl.md)<br/>
[구성 요소 개체 모델](/windows/win32/com/the-component-object-model)
