---
title: 공용 구조체의 저장소 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 516de9411a91f4bb8dd5f8775544ef32e7863bb3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038271"
---
# <a name="storage-of-unions"></a>공용 구조체의 저장소

공용 구조체 변수와 연결된 저장소는 공용 구조체의 최대 멤버에 필요한 저장소입니다. 작은 멤버를 저장하면 사용하지 않는 메모리 공간에 공용 구조체 변수에 포함될 수 있습니다. 모든 멤버가 같은 메모리 공간에 저장되고 같은 주소에서 시작됩니다. 값이 다른 멤버에 할당될 때마다 저장된 값을 덮어씁니다. 예:

```
union         /* Defines a union named x */
{
    char *a, b;
    float f[20];
} x;
```

`x` 공용 구조체의 멤버는 선언 순서대로 `char` 값의 포인터, `char` 값, **float** 값의 배열입니다. `x`는 공용 구조체의 가장 긴 멤버이므로 `f`에 할당된 저장소는 요소가 20개인 배열 `f`에 필요한 저장소입니다. 공용 구조체에 연결된 태그가 없으므로 해당 형식에 이름이 없거나 "익명"입니다.

## <a name="see-also"></a>참고 항목

[공용 구조체 선언](../c-language/union-declarations.md)