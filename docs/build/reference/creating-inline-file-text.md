---
description: '자세한 정보: 인라인 파일 텍스트 만들기'
title: 인라인 파일 텍스트 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
ms.openlocfilehash: 849273fff4ca0853e4589a38096cbb067c380aae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196856"
---
# <a name="creating-inline-file-text"></a>인라인 파일 텍스트 만들기

인라인 파일은 일시적 이거나 영구적입니다.

## <a name="syntax"></a>구문

```
inlinetext
.
.
.
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>설명

명령 뒤의 첫 번째 줄에 *inlinetext* 를 지정 합니다. 별도 줄의 시작 부분에 이중 꺾쇠 괄호 (<<)로 끝을 표시 합니다. 이 파일에는 구분 대괄호 앞에 있는 모든 *inlinetext* 포함 됩니다. *Inlinetext* 에는 매크로 확장 및 대체가 있을 수 있지만 지시문 또는 메이크파일 주석은 포함할 수 없습니다. 공백, 탭 및 줄 바꿈 문자는 문자 그대로 취급 됩니다.

임시 파일은 세션 기간 동안 존재 하며 다른 명령으로 다시 사용할 수 있습니다. NMAKE 세션 다음에 파일을 유지 하려면 닫는 꺾쇠 괄호 다음에 **유지** 를 지정 합니다. 명명 되지 않은 파일은 생성 된 파일 이름을 사용 하 여 디스크에 유지 됩니다. 임시 파일에 대해 **NOKEEP** 을 지정 하거나 아무 것도 지정 하지 않습니다. **KEEP** 및 **NOKEEP** 은 대/소문자를 구분 하지 않습니다.

## <a name="see-also"></a>참고 항목

[메이크파일의 인라인 파일](inline-files-in-a-makefile.md)
