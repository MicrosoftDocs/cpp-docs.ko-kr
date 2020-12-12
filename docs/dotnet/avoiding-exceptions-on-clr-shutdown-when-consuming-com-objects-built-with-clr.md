---
description: 자세히 알아보기:/clr을 사용 하 여 빌드한 COM 개체를 사용할 때 CLR 종료 시 예외 방지
title: -Clr로 빌드된 COM 개체에서 throw 되는 예외 방지
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], CLR shutdown exceptions
- /clr compiler option [C++], CLR shutdown exceptions
- mixed assemblies [C++], CLR shutdown exceptions
- /clr compiler option [C++], COM objects
- interoperability [C++], CLR shutdown exceptions
- CLR shutdown exceptions [C++]
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
ms.openlocfilehash: 899f7905aafcf1bff92e37ee70253e74759b3f57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282616"
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>/clr로 빌드한 COM 개체를 사용할 때 CLR 종료 시 예외 방지

CLR (공용 언어 런타임)이 종료 모드로 전환 되 면 네이티브 함수는 CLR 서비스에 대 한 제한 된 액세스 권한을 가집니다. **/Clr** 을 사용 하 여 컴파일된 COM 개체에서 Release를 호출 하려고 할 때 clr은 네이티브 코드로 전환 된 다음 관리 코드로 다시 전환 하 여 관리 코드에 정의 된 IUnknown:: Release 호출을 처리 합니다. CLR은 종료 모드 이기 때문에 관리 코드로 다시 호출을 방지 합니다.

이 문제를 해결 하려면 릴리스 메서드에서 호출 된 소멸자가 네이티브 코드만 포함 하는지 확인 합니다.

## <a name="see-also"></a>참고 항목

[혼합형 (네이티브 및 관리) 어셈블리](../dotnet/mixed-native-and-managed-assemblies.md)
