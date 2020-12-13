---
description: '자세히 알아보기: tlbid import 특성'
title: tlbid import 특성
ms.date: 08/29/2019
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: 9bbf15f64c1813013fcd839a2d4f0a34c9872aff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339051"
---
# <a name="tlbid-import-attribute"></a>tlbid import 특성

**C++ 전용**

기본 형식 라이브러리 이외의 라이브러리를 로드할 수 있도록 합니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리-dll* **tlbid (** *number* **)**

### <a name="parameters"></a>매개 변수

*수많은*\
형식 *라이브러리 dll* 에 있는 형식 라이브러리의 번호입니다.

## <a name="remarks"></a>설명

단일 DLL에 여러 형식 라이브러리가 내장 되어 있는 경우 **tlbid** 를 사용 하 여 기본 형식 라이브러리 이외의 라이브러리를 로드할 수 있습니다.

예를 들어:

```cpp
#import <MyResource.dll> tlbid(2)
```

이는 다음과 동등합니다.

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
