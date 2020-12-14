---
description: '자세한 정보: 추출 오류 테스트'
title: 추출 오류 테스트
ms.date: 11/04/2016
helpviewer_keywords:
- extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
ms.openlocfilehash: c4a9b5c1ffe4f78718563b33e39012272cfb8042
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259359"
---
# <a name="testing-for-extraction-errors"></a>추출 오류 테스트

[오류 처리 함수](../standard-library/output-file-stream-member-functions.md)에서 설명하는 출력 오류 처리 함수는 입력 스트림에 적용됩니다. 추출 중에는 반드시 오류를 테스트해야 합니다. 다음 문을 고려해 보십시오.

```cpp
cin>> n;
```

`n`이 부호 있는 정수인 경우 값이 32,767(허용되는 최대값, MAX_INT)보다 크면 스트림의 `fail` 비트가 설정되며 `cin` 개체를 사용할 수 없게 됩니다. 모든 후속 추출에서는 값이 저장되지 않은 결과가 즉시 반환됩니다.

## <a name="see-also"></a>참고 항목

[입력 스트림](../standard-library/input-streams.md)
