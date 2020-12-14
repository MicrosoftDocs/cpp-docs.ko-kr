---
description: '자세한 정보: 인라인 파일 지정'
title: 인라인 파일 지정
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
ms.openlocfilehash: 461bf507f707512aa690e81dc5752a97d0c1c4ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224610"
---
# <a name="specifying-an-inline-file"></a>인라인 파일 지정

*Filename* 이 표시 되는 명령에서 두 개의 꺾쇠 괄호 (<<)를 지정 합니다. 꺾쇠 괄호는 매크로 확장 일 수 없습니다.

## <a name="syntax"></a>구문

```
<<[filename]
```

## <a name="remarks"></a>설명

명령이 실행 되 면 꺾쇠 괄호는 *filename*(지정 된 경우) 또는 고유한 NMAKE 생성 이름으로 바뀝니다. 지정 하는 경우 *파일 이름* 에 공백이 나 탭 없이 꺾쇠 괄호를 추가 해야 합니다. 경로를 사용할 수 있습니다. 확장이 필요 하거나 가정 하지 않습니다. *Filename* 을 지정 하는 경우 파일은 현재 또는 지정 된 디렉터리에 생성 되 고 해당 이름으로 기존 파일을 덮어씁니다. 그렇지 않으면 TMP 디렉터리 (또는 TMP 환경 변수가 정의 되지 않은 경우 현재 디렉터리)에 만들어집니다. 이전 파일 *이름을* 다시 사용 하는 경우 NMAKE는 이전 파일을 대체 합니다.

## <a name="see-also"></a>참고 항목

[메이크파일의 인라인 파일](inline-files-in-a-makefile.md)
