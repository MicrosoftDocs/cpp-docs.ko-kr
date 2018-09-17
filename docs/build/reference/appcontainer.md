---
title: -APPCONTAINER | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /APPCONTAINER
dev_langs:
- C++
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d8e19724183963329b959286a996b4f21d18b4c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709185"
---
# <a name="appcontainer"></a>/APPCONTAINER

앱 컨테이너에서 실행 해야 하는 실행 파일을 표시 합니다.-예를 들어 Microsoft Store 또는 유니버설 Windows 앱.

```

/APPCONTAINER[:NO]
```

## <a name="remarks"></a>설명

**/APPCONTAINER** 옵션이 설정된 실행 파일은 Windows 8에서 도입된 프로세스 격리 환경인 앱 컨테이너에서만 실행할 수 있습니다. Microsoft Store 및 범용 Windows 앱에 대해이 옵션을 설정 해야 합니다.

## <a name="see-also"></a>참고 항목

[EDITBIN 옵션](../../build/reference/editbin-options.md)<br/>
[유니버설 Windows 앱 이란?](/windows/uwp/get-started/universal-application-platform-guide)