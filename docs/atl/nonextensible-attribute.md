---
description: '자세히 알아보기: nonextensible 특성'
title: 비 확장 가능 특성
ms.date: 11/04/2016
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: 5bad214d6688570bc4a69aca952f6bed98c2b0dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159403"
---
# <a name="nonextensible-attribute"></a>비 확장 가능 특성

런타임에 이중 인터페이스가 확장 되지 않는 경우, 즉 vtable을 통해 사용할 수 없는 메서드 또는 속성을 제공 하지 않을 경우 `IDispatch::Invoke` 인터페이스 정의에 **비 확장 가능** 특성을 적용 해야 합니다. 이 특성은 컴파일 시간에 전체 코드 확인을 사용 하도록 설정 하는 데 사용할 수 있는 클라이언트 언어 (예: Visual Basic)에 대 한 정보를 제공 합니다. 이 특성을 지정 하지 않으면 버그가 클라이언트 코드에서 실행 될 때까지 숨겨진 상태로 유지 될 수 있습니다.

**비 확장** 특성 및 예제에 대 한 자세한 내용은 [비 확장 가능](../windows/attributes/nonextensible.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[이중 인터페이스 및 ATL](../atl/dual-interfaces-and-atl.md)
