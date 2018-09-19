---
title: 컴파일러 경고 C4394 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4394
dev_langs:
- C++
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d99200dd01db610aa558e8a9df18b7afacdf3d7d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099514"
---
# <a name="compiler-warning-c4394"></a>컴파일러 경고 C4394

'function': appdomain 별 기호는 __declspec (dllexport)로 표시할 수 없습니다

로 표시 한 함수를 [appdomain](../../cpp/appdomain.md) `__declspec` 한정자 (필요가 네이티브), MSIL 및 내보내기 테이블에 컴파일됩니다 ([내보내기](../../windows/export.md) `__declspec` 한정자) 관리 되는 함수에 대 한 지원 되지 않습니다.

공용 액세스 가능성을 갖도록 관리되는 함수를 선언할 수 있습니다. 자세한 내용은 참조 하세요. [표시 유형 입력](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) 하 고 [멤버 표시 유형](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility)합니다.

C4394은 항상 오류로 실행 됩니다.  사용 하 여이 경고를 해제할 수 있습니다 합니다 `#pragma warning` 나 **/wd**; 참조 [경고](../../preprocessor/warning.md) 또는 [/w, / w0, / w1, / w2, / w3, / w4, / w1, / w2, / w3, / w4, /Wall, /wd, / we, /wo, /Wv, /WX (경고 수준)](../../build/reference/compiler-option-warning-level.md)자세한 내용은 합니다.

## <a name="example"></a>예제

다음 샘플 C4394를 생성합니다.

```
// C4394.cpp
// compile with: /clr /c
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394
__declspec(dllexport) int g2 = 0;   // OK
```