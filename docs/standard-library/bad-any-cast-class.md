---
description: Bad_any_cast 클래스에 대해 자세히 알아보세요.
title: bad_any_cast 클래스
ms.date: 04/04/2019
f1_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
helpviewer_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
ms.openlocfilehash: 5b38405bf1fc826592995df4037c5853e88ad9eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321629"
---
# <a name="bad_any_cast-class"></a>bad_any_cast 클래스

에서 throw 된 개체는 실패 했습니다 `any_cast` .

## <a name="syntax"></a>Syntax

```cpp
class bad_any_cast
```

### <a name="member-functions"></a>멤버 함수

|Name|설명|
|-|-|
|[이며](#what)|형식을 반환 합니다.|

## <a name="what"></a><a name="what"></a> 이며

형식을 반환 합니다.

```cpp
const char* what() const noexcept override;
```
