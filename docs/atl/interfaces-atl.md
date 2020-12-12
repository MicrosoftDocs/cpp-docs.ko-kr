---
description: '자세히 알아보기: 인터페이스 (ATL)'
title: 인터페이스(ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: d68f482d05ff828631f5f9f27085f24af188d643
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147695"
---
# <a name="interfaces-atl"></a>인터페이스(ATL)

인터페이스는 개체가 해당 기능을 외부 세계에 노출 하는 방법입니다. COM에서 인터페이스는 개체에서 구현 하는 함수에 대 한 포인터의 테이블 (예: c + + vtable)입니다. 이 표는 인터페이스와 해당 인터페이스가 가리키는 함수를 나타냅니다. 개체는 선택 하는 만큼 많은 인터페이스를 노출할 수 있습니다.

각 인터페이스는 기본 COM 인터페이스 [IUnknown](../atl/iunknown.md)을 기반으로 합니다. 의 메서드를 `IUnknown` 사용 하 여 개체에서 노출 하는 다른 인터페이스를 탐색할 수 있습니다.

또한 각 인터페이스에는 고유한 IID (인터페이스 ID)가 지정 됩니다. 이러한 고유성을 사용 하면 인터페이스 버전 관리를 쉽게 지원할 수 있습니다. 새 인터페이스 버전은 새 IID를 포함 하는 새 인터페이스 일 뿐입니다.

> [!NOTE]
> 표준 COM 및 OLE 인터페이스에 대 한 Iid는 미리 정의 되어 있습니다.

## <a name="see-also"></a>참고 항목

[COM 소개](../atl/introduction-to-com.md)<br/>
[COM 개체 및 인터페이스](/windows/win32/com/com-objects-and-interfaces)
