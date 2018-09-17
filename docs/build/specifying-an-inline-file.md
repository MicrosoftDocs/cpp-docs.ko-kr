---
title: 인라인 파일 지정 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73983094f10088920100b4fbbb8d870aee13f05e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720566"
---
# <a name="specifying-an-inline-file"></a>인라인 파일 지정

2 개의 꺾쇠 괄호를 지정 합니다. (<<) 명령에 있는 *filename* 표시 하는 것입니다. 꺾쇠 괄호는 매크로 확장이 수 없습니다.

## <a name="syntax"></a>구문

```
<<[filename]
```

## <a name="remarks"></a>설명

꺾쇠 괄호 안의 명령이 실행 되 면으로 바뀝니다 *filename*지정 하는 경우, 고유한 NMAKE에서 생성 된 이름으로 합니다. 를 지정 하는 경우 *filename* 공백 또는 탭 하지 않고 꺾쇠 괄호를 따라야 합니다. 경로 허용 됩니다. 확장명이 필요 하지 않거나 것으로 간주 합니다. 경우 *filename* 현재에서 파일을 만들 지정 하지 않거나 지정한 디렉터리 해당 이름으로 파일 기존 덮어쓰지;이 고, 그렇지 TMP 디렉터리에 만들어집니다 (또는 현재 디렉터리 경우 TMP 환경 변수 정의 되지 않았습니다). 이전 하는 경우 *filename* 는 다시 NMAKE 이전 파일을 대체 합니다.

## <a name="see-also"></a>참고 항목

[메이크파일의 인라인 파일](../build/inline-files-in-a-makefile.md)