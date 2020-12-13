---
description: '자세한 정보: 특성 가져오기 no_auto_exclude'
title: no_auto_exclude 가져오기 특성
ms.date: 08/29/2019
f1_keywords:
- no_auto_exclude
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
ms.openlocfilehash: 81e4d7e7f9295a4ed983e2a5024d891e30fe1361
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333359"
---
# <a name="no_auto_exclude-import-attribute"></a>no_auto_exclude 가져오기 특성

**C++ 전용**

자동 제외를 사용하지 않도록 설정합니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **no_auto_exclude**

## <a name="remarks"></a>설명

형식 라이브러리가 시스템 헤더 또는 다른 형식 라이브러리에 정의된 항목 정의를 포함할 수 있습니다. `#import`는 다양한 정의 오류를 자동으로 제외하여 해당 오류를 방지하려고 합니다. 제외 될 각 항목에 대해 [컴파일러 경고 (수준 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) 가 실행 됩니다. 이 특성을 사용 하 여 자동 제외를 사용 하지 않도록 설정할 수 있습니다.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
