---
description: '자세히 알아보기: 다중 인라인 파일'
title: 인라인 파일이 여러 개인 경우
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
ms.openlocfilehash: d739591910007f69eca5d4834f6943ae0a0082ed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190603"
---
# <a name="multiple-inline-files"></a>인라인 파일이 여러 개인 경우

명령은 둘 이상의 인라인 파일을 만들 수 있습니다.

## <a name="syntax"></a>구문

```
command << <<
inlinetext
<<[KEEP | NOKEEP]
inlinetext
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>설명

각 파일에 대해 하나 이상의 인라인 텍스트 줄을 지정 하 고 그 뒤에 구분 기호를 포함 하는 닫는 줄을 지정 합니다. 첫 번째 파일의 구분 기호 다음 줄에서 두 번째 파일의 텍스트를 시작 합니다.

## <a name="see-also"></a>참고 항목

[메이크파일의 인라인 파일](inline-files-in-a-makefile.md)
