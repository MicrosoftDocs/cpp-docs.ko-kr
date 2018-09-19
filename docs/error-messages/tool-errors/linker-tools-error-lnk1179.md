---
title: 링커 도구 오류 LNK1179 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1179
dev_langs:
- C++
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d22ebb329d390d44aea44ff9dc6f3bf2f86a1d26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117460"
---
# <a name="linker-tools-error-lnk1179"></a>링커 도구 오류 LNK1179

파일이 잘못 되었거나 손상 되었습니다. 'filename' COMDAT가 중복 됩니다

개체 모듈 이름이 같은 둘 이상의 Comdat를 포함합니다.

사용 하 여이 오류를 발생할 수 있습니다 [/H](../../build/reference/h-restrict-length-of-external-names.md), 외부 이름 길이 제한 및 [/Gy](../../build/reference/gy-enable-function-level-linking.md), Comdat에 함수를 패키지 하 합니다.

## <a name="example"></a>예제

다음 코드에서는 `function1` 및 `function2` 처음 8 자에서 동일 합니다. 사용 하 여 컴파일하면 **/Gy** 하 고 **/H8** 링크 오류가 발생 합니다.

```
void function1(void);
void function2(void);

int main() {
    function1();
    function2();
}

void function1(void) {}
void function2(void) {}
```