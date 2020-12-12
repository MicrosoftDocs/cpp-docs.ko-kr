---
description: '자세한 정보: ATL 연결 지점 예제'
title: ATL 연결 지점 예제
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
ms.openlocfilehash: 6416720b5366838f9687f31947cac9a6824da058
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165812"
---
# <a name="atl-connection-point-example"></a>ATL 연결 지점 예제

이 예제에서는 [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) 를 나가는 인터페이스로 지 원하는 개체를 보여 줍니다.

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

를 나가는 인터페이스로 지정 하는 경우 `IPropertyNotifySink` 대신 [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) 클래스를 사용할 수 있습니다 `IConnectionPointImpl` . 예를 들어:

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>참고 항목

[연결점](../atl/atl-connection-points.md)
