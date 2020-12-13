---
description: '자세한 정보: 특성 가져오기 no_dual_interfaces'
title: no_dual_interfaces 가져오기 특성
ms.date: 08/29/2019
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: 1c3010b252ac71e38312fa193520938fbb4d681a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333344"
---
# <a name="no_dual_interfaces-import-attribute"></a>no_dual_interfaces 가져오기 특성

**C++ 전용**

컴파일러가 이중 인터페이스 메서드에 대한 래퍼 함수를 생성하는 방법을 변경합니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **no_dual_interfaces**

## <a name="remarks"></a>설명

일반적으로 래퍼는 인터페이스에 대 한 가상 함수 테이블을 통해 메서드를 호출 합니다. **No_dual_interfaces** 를 사용 하는 경우 래퍼는를 호출 하 여 메서드를 호출 합니다 `IDispatch::Invoke` .

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
