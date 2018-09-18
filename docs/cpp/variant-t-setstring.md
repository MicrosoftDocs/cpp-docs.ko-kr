---
title: _variant_t::SetString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::SetString
dev_langs:
- C++
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 52ea719a2c9296ca1e64d881ac150994c041e206
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018732"
---
# <a name="varianttsetstring"></a>_variant_t::SetString

**Microsoft 전용**

이 `_variant_t` 개체에 문자열을 할당합니다.

## <a name="syntax"></a>구문

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>매개 변수

*pSrc*<br/>
문자열에 대한 포인터입니다.

## <a name="remarks"></a>설명

ANSI 문자열을 유니코드 `BSTR` 문자열로 변환하고 이 `_variant_t` 개체에 할당합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고자료

[_variant_t 클래스](../cpp/variant-t-class.md)