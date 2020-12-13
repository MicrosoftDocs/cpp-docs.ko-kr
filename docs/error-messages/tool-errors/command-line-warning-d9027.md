---
description: 자세한 내용은 Command-Line Warning D9027을 (를) 확인 하세요.
title: 명령줄 경고 D9027
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: 8c17750f3310072f8f69c77587a1c17fc9377e79
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136112"
---
# <a name="command-line-warning-d9027"></a>명령줄 경고 D9027

소스 파일 ' '이 (가) \<filename> 무시 됨

CL.exe에서 입력 원본 파일을 무시 했습니다.

이 경고는/Fo 옵션과/c 옵션을 사용 하 여 명령줄의 출력 파일 이름 사이에 공백을 사용 하 여 발생할 수 있습니다. 예를 들어:

```
cl /c /Fo output.obj input.c
```

/Fo와 사이에 공백이 있기 때문에 `output.obj` CL.exe는 `output.obj` 입력 파일의 이름으로를 사용 합니다. 문제를 해결 하려면 다음 공간을 제거 합니다.

```
cl /c /Fooutput.obj input.c
```
