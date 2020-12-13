---
description: '다음에 대 한 자세한 정보: piecewise_contruct_t 구조체'
title: piecewise_contruct_t 구조체
ms.date: 11/04/2016
f1_keywords:
- utility/std::piecewise_contruct_t
helpviewer_keywords:
- piecewise_contruct_t class
- piecewise_contruct_t structure
ms.openlocfilehash: 7fefacff75b47c25cb9ae07cc894498eadb551df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340751"
---
# <a name="piecewise_contruct_t-structure"></a>piecewise_contruct_t 구조체

구조체는 `piecewise_construct_t` 별도의 생성자와 함수 오버 로드를 유지 하는 데 사용 되는 빈 구조체 형식입니다. 특히에는 `pair` 첫 번째 인수로를 사용 하 고 `piecewise_construct_t` 두 개의 인수를 사용 하는 생성자가 있습니다 `tuple` .

## <a name="syntax"></a>구문

```cpp
struct piecewise_construct_t { explicit piecewise_construct_t() = default; };

inline constexpr piecewise_construct_t piecewise_construct{};
```
