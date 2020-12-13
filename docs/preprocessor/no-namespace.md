---
description: '자세한 정보: 특성 가져오기 no_namespace'
title: no_namespace 가져오기 특성
ms.date: 08/29/2019
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: e1503015f455af65a138e4e3e6843fd0516d2773
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333317"
---
# <a name="no_namespace-import-attribute"></a>no_namespace 가져오기 특성

**C++ 전용**

컴파일러가 네임 스페이스 이름을 생성 하지 않도록 지정 합니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **no_namespace**

## <a name="remarks"></a>설명

`#import` 헤더 파일의 형식 라이브러리 콘텐츠는 일반적으로 네임스페이스에 정의됩니다. 네임 스페이스 이름은 `library` 원래 IDL 파일의 문에 지정 됩니다. **No_namespace** 특성이 지정 된 경우이 네임 스페이스는 컴파일러에서 생성 되지 않습니다.

다른 네임 스페이스 이름을 사용 하려면 [rename_namespace](../preprocessor/rename-namespace.md) 특성을 대신 사용 합니다.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
