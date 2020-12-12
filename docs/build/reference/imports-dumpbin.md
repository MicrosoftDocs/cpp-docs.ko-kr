---
description: 자세히 알아보기:/IMPORTS (DUMPBIN)
title: /IMPORTS(DUMPBIN)
ms.date: 11/04/2016
f1_keywords:
- /imports
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
ms.openlocfilehash: 86c428280bbca3a4957f7d7a0a640482607547de
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199794"
---
# <a name="imports-dumpbin"></a>/IMPORTS(DUMPBIN)

```
/IMPORTS[:file]
```

이 옵션은 실행 파일 또는 DLL로 가져온 Dll (정적으로 연결 되 고 [로드 된 지연](linker-support-for-delay-loaded-dlls.md)) 목록과 각 dll의 모든 개별 가져오기를 표시 합니다.

선택적 지정 `file` 을 사용 하면 해당 DLL에 대 한 가져오기만 표시 되도록 지정할 수 있습니다. 다음은 그 예입니다.

```
dumpbin /IMPORTS:msvcrt.dll
```

## <a name="remarks"></a>설명

이 옵션으로 표시 되는 출력은 [/proeroutput](dash-exports.md) 과 비슷합니다.

[/GL](gl-whole-program-optimization.md) 컴파일러 옵션으로 생성된 파일에서는 [/HEADERS](headers.md) DUMPBIN옵션만 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[DUMPBIN 옵션](dumpbin-options.md)
