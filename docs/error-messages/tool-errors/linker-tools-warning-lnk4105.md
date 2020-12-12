---
description: '자세한 정보: 링커 도구 경고 LNK4105'
title: 링커 도구 경고 LNK4105
ms.date: 11/04/2016
f1_keywords:
- LNK4105
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
ms.openlocfilehash: 6536273a0b3e5b6e60b782e5953a70a7b3eb2798
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294420"
---
# <a name="linker-tools-warning-lnk4105"></a>링커 도구 경고 LNK4105

' option ' 옵션에 지정 된 인수가 없습니다. 옵션 무시

이 경고는 [/libpath](../../build/reference/libpath-additional-libpath.md) 옵션이 설정 된 경우에만 발생 합니다. 이 옵션을 사용 하 여 디렉터리를 지정 하지 않으면 링커가 옵션을 무시 하 고이 경고 메시지를 생성 합니다.

기존 환경 라이브러리 설정을 재정의할 필요가 없으면 링커 명령줄에서/LIBPATH 옵션을 제거 합니다. 라이브러리에 대 한 대체 검색 경로를 사용 하려면/LIBPATH 옵션 뒤에 대체 경로를 지정 합니다.

## <a name="example"></a>예제

```
link /libpath:c:\filepath\lib bar.obj
```

는 `c:\filepath\lib` 기본 위치에서 검색 하기 전에에서 필요한 라이브러리를 검색 하도록 링커에 지시 합니다.
