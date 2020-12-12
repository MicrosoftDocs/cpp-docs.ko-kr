---
description: '자세한 정보: 라이브러리'
title: LIBRARY
ms.date: 11/04/2016
f1_keywords:
- LIBRARY
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
ms.openlocfilehash: 3d8c63f323568949cf2fb30935d2557755346422
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199534"
---
# <a name="library"></a>LIBRARY

DLL을 만들기 위한 링크를 알려 줍니다. 이와 동시에, 빌드에서 .exp 파일을 사용 하지 않는 경우 링크는 가져오기 라이브러리를 만듭니다.

```
LIBRARY [library][BASE=address]
```

## <a name="remarks"></a>설명

*Library* 인수는 DLL의 이름을 지정 합니다. [/Out](out-output-file-name.md) 링커 옵션을 사용 하 여 DLL의 출력 이름을 지정할 수도 있습니다.

BASE =*address* 인수는 운영 체제에서 DLL을 로드 하는 데 사용 하는 기본 주소를 설정 합니다. 이 인수는 0x10000000의 기본 DLL 위치를 재정의 합니다. 기본 주소에 대 한 자세한 내용은 [/base](base-base-address.md) 옵션에 대 한 설명을 참조 하십시오.

DLL을 빌드할 때는 [/dll](dll-build-a-dll.md) 링커 옵션을 사용 해야 합니다.

## <a name="see-also"></a>참고 항목

[Module-Definition 문에 대 한 규칙](rules-for-module-definition-statements.md)
