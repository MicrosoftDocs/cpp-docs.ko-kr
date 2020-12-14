---
description: '다음에 대 한 자세한 정보: 스텁'
title: STUB
ms.date: 11/04/2016
f1_keywords:
- STUB
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
ms.openlocfilehash: 79a2002c119bf211652e2aab51d9656b36e3d159
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230291"
---
# <a name="stub"></a>STUB

VxD (가상 장치 드라이버)를 작성 하는 모듈 정의 파일에서 사용 되는 경우에는 IMAGE_DOS_HEADER 구조 (WINNT에 정의 됨)를 포함 하는 파일 이름을 지정할 수 있습니다. H)를 사용 하 여 기본 헤더가 아닌 VxD (가상 장치 드라이버)에서 사용할 수 있습니다.

```
STUB:filename
```

## <a name="remarks"></a>설명

*Filename* 을 지정 하는 동일한 방법은 [/STUB](stub-ms-dos-stub-file-name.md) 링커 옵션을 사용 하는 것입니다.

STUB은 VxD를 빌드하는 경우에만 모듈 정의 파일에서 유효 합니다.

## <a name="see-also"></a>참고 항목

[Module-Definition 문에 대 한 규칙](rules-for-module-definition-statements.md)
