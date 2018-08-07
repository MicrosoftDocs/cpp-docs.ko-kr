---
title: 다른 형식에서 변환 | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e919782022ee64f657611a14d6eae6173a67b8c0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32382681"
---
# <a name="conversions-from-other-types"></a>다른 형식에서 변환

**enum** 값은 정의에 따라 **int** 값이므로 **enum** 값 간에 변환하는 작업은 **int** 유형에 대한 변환 작업과 동일합니다. Microsoft C 컴파일러의 경우 정수는 **long**과 같습니다.

**Microsoft 전용**

구조체 또는 공용 구조체 형식 간의 변환은 허용되지 않습니다.

어떤 값이든 **void**로 변환할 수는 있지만 해당 변환의 결과는 식 문에서와 같이 식 값이 삭제되는 컨텍스트에서만 사용할 수 있습니다.

**void** 형식은 정의에 따라 값을 포함하지 않습니다. 따라서 해당 형식을 다른 형식으로 변환할 수 없으며 다른 형식을 할당별로 **void**로 변환할 수도 없습니다. 그러나 [형식 캐스트 변환](../c-language/type-cast-conversions.md)의 설명에 따라 명시적으로 값을 **void** 형식으로 캐스트할 수는 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고 항목

[할당 변환](../c-language/assignment-conversions.md)  
