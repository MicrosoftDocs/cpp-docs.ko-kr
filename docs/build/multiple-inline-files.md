---
title: 인라인 파일이 여러 개인 경우
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
ms.openlocfilehash: 5b41d448c89ac30d891c41d1ad1e314cbf9724a8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425616"
---
# <a name="multiple-inline-files"></a>인라인 파일이 여러 개인 경우

명령을은 인라인 파일이 여러 개 만들 수 있습니다.

## <a name="syntax"></a>구문

```
command << <<
inlinetext
<<[KEEP | NOKEEP]
inlinetext
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>설명

각 파일에 대해 하나 이상의 줄 뒤에 닫는 줄 구분 기호를 포함 하는 인라인 텍스트를 지정 합니다. 첫 번째 파일의 구분 줄을 다음 줄에 두 번째 파일의 텍스트를 시작 합니다.

## <a name="see-also"></a>참고자료

[메이크파일의 인라인 파일](../build/inline-files-in-a-makefile.md)
