---
description: '자세한 정보: Naked 함수'
title: Naked 함수
ms.date: 11/04/2016
helpviewer_keywords:
- naked functions
- functions [C++], naked
- prolog code
- epilog code
ms.assetid: 2543c8af-00d4-4a2a-8a87-e746da1f9929
ms.openlocfilehash: 1cea9bf2497a14bc7007f97b2c3db68eafc15059
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243356"
---
# <a name="naked-functions"></a>Naked 함수

**Microsoft 전용**

`naked` 스토리지 클래스 특성은 Microsoft 전용 C 언어 확장입니다. `naked` 스토리지 클래스 특성으로 선언된 함수의 경우, 컴파일러는 코드를 프롤로그 및 에필로그 코드 없이 생성합니다. 이 기능을 이용하여 인라인 어셈블러 코드로 사용자 정의 프롤로그/에필로그 코드 시퀀스를 작성할 수 있습니다. naked 함수는 가상 디바이스 드라이버 작성에 특히 유용합니다.

`naked` 특성은 함수의 정의에만 관련되고 형식 수정자가 아니기 때문에 naked 함수는 확장된 특성 구문을 사용합니다([확장된 스토리지 클래스 특성](../c-language/c-extended-storage-class-attributes.md) 참조).

다음 예제에서는 `naked` 특성으로 함수를 정의합니다.

```
__declspec( naked ) int func( formal_parameters )
{
   /* Function body */
}
```

또는

```
#define Naked   __declspec( naked )

Naked int func( formal_parameters )
{
   /* Function body */
}
```

`naked` 특성은 함수의 프롤로그 및 에필로그 시퀀스에 사용되는 컴파일러 코드 생성에만 영향을 줍니다. 이러한 함수를 호출하기 위해 생성되는 코드에는 영향을 주지 않습니다. 따라서 `naked` 특성을 함수 형식의 일부로 간주하지 않으며, 함수 포인터는 `naked` 특성을 가질 수 없습니다. 또한 `naked` 특성은 데이터 정의에 적용될 수 없습니다. 예를 들어, 다음 코드는 오류를 생성합니다.

```
__declspec( naked ) int i;  /* Error--naked attribute not */
                            /* permitted on data declarations. */
```

`naked` 특성은 함수 정의에만 관련되며, 함수의 프로토타입에 지정될 수 없습니다. 다음 코드에서는 컴파일러 오류가 생성됩니다.

```
__declspec( naked ) int func();   /* Error--naked attribute not */
                     /* permitted on function declarations.    */   \
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[C 함수 정의](../c-language/c-function-definitions.md)
