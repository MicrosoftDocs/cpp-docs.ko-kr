---
description: '자세한 정보: 링커 도구 경고 LNK4222'
title: 링커 도구 경고 LNK4222
ms.date: 11/04/2016
f1_keywords:
- LNK4222
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
ms.openlocfilehash: 215dd04339b783d558b05140bb7dd08c5936d5e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222609"
---
# <a name="linker-tools-warning-lnk4222"></a>링커 도구 경고 LNK4222

내보낸 ' symbol ' 기호에는 서 수를 할당 하면 안 됩니다.

다음 기호는 서 수로 내보낼 수 없습니다.

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllUnregisterServer`

이러한 함수는 항상를 사용 하 여 이름으로 배치 됩니다 `GetProcAddress` . 링커가 이러한 종류의 내보내기에 대 한 경고를 생성 하는 것은 이미지가 클 수 있기 때문입니다. 이 문제는 내보내기에 대 한 서 수 내보내기 범위가 비교적 많지 않은 경우에 발생할 수 있습니다. 예를 들면 다음과 같습니다.

```
EXPORTS
   DllGetClassObject   @1
   MyOtherAPI      @100
```

에는 내보내기 주소 테이블에서 98 (2-99)만 필러로 100 슬롯이 필요 합니다. 다른 한편으로는

```
EXPORTS
   DllGetClassObject
   MyOtherAPI      @100
```

에는 두 개의 슬롯이 필요 합니다. ( [/Export](../../build/reference/export-exports-a-function.md) 링커 옵션을 사용 하 여 내보낼 수도 있습니다.)
