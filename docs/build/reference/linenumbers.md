---
description: 자세히 알아보기:/LINENUMBERS
title: /LINENUMBERS
ms.date: 11/04/2016
f1_keywords:
- /linenumbers
helpviewer_keywords:
- LINENUMBERS dumpbin option
- line numbers
- -LINENUMBERS dumpbin option
- /LINENUMBERS dumpbin option
ms.assetid: 1681d582-2c2f-484e-9920-109959549055
ms.openlocfilehash: 9df3d88476a82466f86ec23147c9f8f35f9b3f1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191019"
---
# <a name="linenumbers"></a>/LINENUMBERS

```
/LINENUMBERS
```

## <a name="remarks"></a>설명

이 옵션은 COFF 줄 번호를 표시 합니다. 줄 번호는 프로그램 데이터베이스 (/Zi), C7 호환 (/Z7) 또는 줄 번호만 (/Zd)로 컴파일된 경우 개체 파일에 있습니다. 실행 파일 또는 DLL은 디버그 정보 생성 (/DEBUG)으로 연결 된 경우 COFF 줄 번호를 포함 합니다.

[/GL](gl-whole-program-optimization.md) 컴파일러 옵션으로 생성된 파일에서는 [/HEADERS](headers.md) DUMPBIN옵션만 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[DUMPBIN 옵션](dumpbin-options.md)
