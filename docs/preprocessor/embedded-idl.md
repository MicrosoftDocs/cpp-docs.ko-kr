---
description: '자세한 정보: 특성 가져오기 embedded_idl'
title: embedded_idl 가져오기 특성
ms.date: 08/29/2019
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: a56c6e664c082db4b6eac078b7133a1ead947d3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300595"
---
# <a name="embedded_idl-import-attribute"></a>embedded_idl 가져오기 특성

**C++ 전용**

특성 생성 코드를 유지 하 여 형식 라이브러리를 파일에 쓸지 여부를 지정 합니다 `.tlh` .

## <a name="syntax"></a>Syntax

> **#import** *type-library* **embedded_idl** [ **(** { **"emitidl"**  |  **"no_emitidl"** } **)** ]

### <a name="parameters"></a>매개 변수

**emitidl**\
*형식 라이브러리* 에서 가져온 형식 정보가 특성 사용 프로젝트에 대해 생성 된 IDL에 존재 합니다. 이 동작은 기본값이 며에 매개 변수를 지정 하지 않는 경우에 적용 됩니다 `embedded_idl` .

**"no_emitidl"**\
*형식 라이브러리* 에서 가져온 형식 정보가 특성 사용 프로젝트에 대해 생성 된 IDL에 없습니다.

## <a name="example"></a>예제

```cpp
// import_embedded_idl.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib2")];
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")
```

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
