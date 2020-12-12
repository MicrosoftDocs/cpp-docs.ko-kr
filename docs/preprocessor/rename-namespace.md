---
description: '자세한 정보: 특성 가져오기 rename_namespace'
title: rename_namespace 가져오기 특성
ms.date: 08/29/2019
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: 402d9c9cd8dee5979dd71e16fec1a606d8b4b996
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167385"
---
# <a name="rename_namespace-import-attribute"></a>rename_namespace 가져오기 특성

**C++ 전용**

형식 라이브러리의 콘텐츠가 들어있는 네임스페이스의 이름을 바꿉니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **rename_namespace (** "*NewName*" **)**

### <a name="parameters"></a>매개 변수

*이름*\
네임스페이스의 새 이름입니다.

## <a name="remarks"></a>설명

**Rename_namespace** 특성은 네임 스페이스의 새 이름을 지정 하는 단일 인수인 *NewName* 을 사용 합니다.

네임 스페이스를 제거 하려면 [no_namespace](../preprocessor/no-namespace.md) 특성을 대신 사용 합니다.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
