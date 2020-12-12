---
description: '자세한 정보: 링커 도구 오류 LNK2011'
title: 링커 도구 오류 LNK2011
ms.date: 11/04/2016
f1_keywords:
- LNK2011
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
ms.openlocfilehash: f149324a61d34333e8f29f70bf5fee4cd952ba8b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338475"
---
# <a name="linker-tools-error-lnk2011"></a>링커 도구 오류 LNK2011

미리 컴파일된 개체가에 연결 되지 않았습니다. 이미지가 실행 되지 않을 수 있습니다.

미리 컴파일된 헤더를 사용 하는 경우 링크를 사용 하려면 미리 컴파일된 헤더를 사용 하 여 만든 모든 개체 파일이에 연결 되어야 합니다. 다른 원본 파일과 함께 사용 하기 위해 미리 컴파일된 헤더를 생성 하는 데 사용 하는 소스 파일이 있는 경우 이제는 미리 컴파일된 헤더와 함께 만들어진 개체 파일을 포함 해야 합니다.

예를 들어 다른 원본 파일과 함께 사용할 미리 컴파일된 헤더를 만들기 위해 STUB .cpp 라는 파일을 컴파일하는 경우에는 스텁이 .obj와 연결 해야 합니다. 그렇지 않으면이 오류가 발생 합니다. 다음 명령줄에서 line one을 사용 하 여 미리 컴파일된 헤더, 즉 PROG1 및 PROG2와 함께 2 줄과 3 번 줄에서 사용 되는 공용 .pch를 만듭니다. 파일 스텁에는 `#include` 줄 ( `#include` PROG1 및 PROG2와 같은 줄)만 포함 되며 미리 컴파일된 헤더를 생성 하는 데만 사용 됩니다. LNK2011을 방지 하려면 마지막 줄에서 스텁을 연결 해야 합니다.

```
cl /c /Yccommon.h stub.cpp
cl /c /Yucommon.h prog1.cpp
cl /c /Yucommon.h prog2.cpp
link /out:prog.exe stub.obj prog1.obj prog2.obj
```
