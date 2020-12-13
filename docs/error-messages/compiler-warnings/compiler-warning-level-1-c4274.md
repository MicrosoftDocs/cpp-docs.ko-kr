---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4274'
title: 컴파일러 경고 (수준 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: aa1f6d3b07c7d788d9e47955c4bb51930522b7a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340101"
---
# <a name="compiler-warning-level-1-c4274"></a>컴파일러 경고 (수준 1) C4274

\#ident 무시 됨 #pragma 주석 (exestr, ' string ')에 대 한 설명서를 참조 하세요.

`#ident`개체 또는 실행 파일에 사용자 지정 문자열을 삽입 하는 지시문은 사용 되지 않습니다. 따라서 컴파일러는 지시문을 무시 합니다.

> [!CAUTION]
> 경고 C4274는 [#pragma 주석 (exestr, ' string ')](../../preprocessor/comment-c-cpp.md) 지시문을 사용 하도록 권장 합니다. 그러나이 권장 사항은 더 이상 사용 되지 않으며, 이후 버전의 컴파일러에서 수정 될 예정입니다. 지시문을 사용 하는 경우 `#pragma` 링커 도구 (LINK.exe)는 지시문에 의해 생성 된 주석 레코드를 무시 하 고 경고 [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)를 발생 시킵니다. `#ident`지시문 대신 응용 프로그램에서 파일 버전 리소스 문자열을 사용 하는 것이 좋습니다.

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

- `#ident "` *문자열* `"` 지시어를 제거 합니다.

## <a name="see-also"></a>참고 항목

[C 주석(C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[링커 도구 경고 LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[리소스 파일 작업](../../windows/working-with-resource-files.md)
