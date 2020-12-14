---
description: '자세한 정보: 리소스 컴파일러 오류 RC2104'
title: 리소스 컴파일러 오류 RC2104
ms.date: 11/04/2016
f1_keywords:
- RC2104
helpviewer_keywords:
- RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
ms.openlocfilehash: 74f50088d15fcc86ebfc7000d8ee618c94464c63
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259983"
---
# <a name="resource-compiler-error-rc2104"></a>리소스 컴파일러 오류 RC2104

정의되지 않은 키워드 또는 키 이름: 키

지정한 키워드 또는 키 이름이 정의되지 않았습니다.

이 오류는 리소스 정의 또는 포함된 헤더 파일의 오타로 인해 발생하는 경우가 많습니다. 헤더 파일이 없어도 발생할 수 있습니다.

문제를 해결하려면 정의된 키워드 또는 키 이름을 포함해야 하는 헤더 파일을 찾은 다음 리소스 파일에 해당 이름이 포함되어 있으며 키워드 또는 키 이름의 철자가 올바른지 확인합니다. 미리 컴파일된 헤더를 사용하여 프로젝트를 만든 후 제거한 경우에는 리소스 파일에 아직 필요한 헤더가 포함되어 있는지 확인합니다.

리소스 파일에 정의 된 키워드 및 키 이름을 확인 하려면 Visual Studio에서 **리소스 뷰** 창을 엽니다. 메뉴 모음에서 **보기**, **리소스 뷰** 를 선택 하 고 .rc 파일에 대 한 바로 가기 메뉴를 연 다음, **리소스 기호** 를 선택 하 여 정의 된 기호 목록을 볼 수 있습니다. 포함 된 헤더를 수정 하려면 .rc 파일에 대 한 바로 가기 메뉴를 열고 **리소스 포함** 을 선택 합니다.

다음 메시지가 표시되는 경우

```
undefined keyword or key name: MFT_STRING
```

\MCL\MFC\Include\AfxRes.h를 열고 아래 include 지시문을 추가합니다.

```
#include <winresrc.h>
```
