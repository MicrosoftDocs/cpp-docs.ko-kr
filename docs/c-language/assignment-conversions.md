---
title: 할당 변환
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
ms.openlocfilehash: 6caed3d7a8079bc6b02e9ad17859cd4062cbee7f
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152718"
---
# <a name="assignment-conversions"></a>할당 변환

할당 연산에서 할당 중인 값의 형식은 할당을 받는 변수의 형식으로 변환됩니다. C를 사용하면 변환 시 정보가 손실되더라도 정수 계열 형식과 부동 소수점 형식 간 할당을 통해 변환할 수 있습니다. 사용되는 변환 메서드는 [일반적인 산술 변환](../c-language/usual-arithmetic-conversions.md) 및 다음 단원에 설명된 대로 할당에 관련된 형식에 따라 다릅니다.

- [부호 있는 정수 계열 형식에서 변환](../c-language/conversions-from-signed-integral-types.md)

- [부호 없는 정수 계열 형식에서 변환](../c-language/conversions-from-unsigned-integral-types.md)

- [부동 소수점 형식에서 변환](../c-language/conversions-from-floating-point-types.md)

- [포인터 형식과의 변환](../c-language/conversions-to-and-from-pointer-types.md)

- [다른 형식에서 변환](../c-language/conversions-from-other-types.md)

**const** I-value는 할당의 왼쪽에 사용할 수 없지만, 형식 한정자는 변환 허용 가능성에 영향을 주지 않습니다.

## <a name="see-also"></a>참고 항목

[형식 변환](../c-language/type-conversions-c.md)
