---
description: '자세한 정보: 링커 도구 오류 LNK1179'
title: 링커 도구 오류 LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: 691476eeffadece2436518c5249ca523adca51c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253444"
---
# <a name="linker-tools-error-lnk1179"></a>링커 도구 오류 LNK1179

파일이 잘못 되었거나 손상 되었습니다. ' filename ' COMDAT이 중복 되었습니다.

개체 모듈에 이름이 같은 Comdat가 두 개 이상 포함 되어 있습니다.

이 오류는 외부 이름의 길이를 제한 하는 [/h](../../build/reference/h-restrict-length-of-external-names.md)와 comdat에서 함수를 패키지 하는 [/gy](../../build/reference/gy-enable-function-level-linking.md)를 사용 하 여 발생할 수 있습니다.

## <a name="example"></a>예제

다음 코드에서 `function1` 및 `function2` 는 처음 8 자에서 동일 합니다. **/Gy** 및 **/h 8** 을 사용 하 여 컴파일하면 링크 오류가 발생 합니다.

```cpp
void function1(void);
void function2(void);

int main() {
    function1();
    function2();
}

void function1(void) {}
void function2(void) {}
```
