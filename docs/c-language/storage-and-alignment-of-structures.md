---
description: '자세한 정보: 스토리지 및 구조체의 맞춤'
title: 스토리지 및 구조체의 맞춤
ms.date: 11/04/2016
helpviewer_keywords:
- alignment of structures
- structure storage
- storing structures
- packing structures
ms.assetid: 60ff292f-2595-4f37-ae00-4c4b4f047196
ms.openlocfilehash: 8cffc3ddfcc868a7ccb727a5092e2389dbf016a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213691"
---
# <a name="storage-and-alignment-of-structures"></a>스토리지 및 구조체의 맞춤

**Microsoft 전용**

구조체 멤버는 선언된 순서에 따라 순차적으로 저장됩니다. 즉, 첫 멤버가 가장 낮은 메모리 주소를 갖고 마지막 멤버가 가장 높은 주소를 갖습니다.

모든 데이터 개체에는 *alignment-requirement* 가 있습니다. 구조체의 경우 요구 사항이 해당 멤버 중 가장 큽니다. 다음과 같이 되도록 모든 개체에 *오프셋* 이 할당됩니다.

*offset* `%` *alignment-requirement* `==` 0

정수 계열 형식의 크기가 같으며 다음 비트 필드가 비트 필드의 일반 할당 요구 사항에 따라 적용되는 경계를 벗어나지 않고 현재 할당 단위에 맞는 경우 인접 비트 필드는 동일한 1, 2 또는 4바이트 할당 단위로 압축됩니다.

공간을 아끼거나 기존 데이터 구조를 따르려면 구조체를 다소 조밀하게 저장해야 할 수 있습니다. [/Zp](../build/reference/zp-struct-member-alignment.md)[*n*] 컴파일러 옵션 및 [#pragma pack](../preprocessor/pack.md)은 구조체 데이터가 메모리에 "압축"되는 방법을 제어합니다. /Zp[*n*] 옵션을 사용하면(*n*: 1, 2, 4, 8 또는 16) 첫 번째 이후의 각 구조체 멤버가 바이트 경계(필드의 맞춤 요구 사항이나 압축 크기(*n*) 중 더 작은 값)에 저장됩니다. 수식으로 표현된 바이트 경계는 다음과 같습니다.

```
min( n, sizeof( item ) )
```

여기서 *n* 은 /Zp[*n*] 옵션으로 표현되는 압축 크기이며 *item* 은 구조체 멤버입니다. 기본 압축 크기는 /Zp8입니다.

`pack` pragma를 사용하여 특정 구조체에 대해 명령줄에서 지정한 압축 이외의 압축을 지정하려면 압축 크기가 1, 2, 4, 8 또는 16인 `pack` pragma를 구조체 앞에 제공하십시오. 명령줄에서 지정한 압축을 복구하려면 `pack` pragma를 인수 없이 지정하십시오.

Microsoft C 컴파일러의 경우 비트 필드의 기본 크기는 **`long`** 입니다. 구조체 멤버는 형식의 크기나 /Zp[*n*] 크기 중 더 작은 값에 맞춰집니다. 기본 크기는 4입니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[구조체 선언](../c-language/structure-declarations.md)
