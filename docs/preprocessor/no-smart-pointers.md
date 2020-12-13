---
description: '자세한 정보: 특성 가져오기 no_smart_pointers'
title: no_smart_pointers 가져오기 특성
ms.date: 08/29/2019
f1_keywords:
- no_smart_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: cf2299668a2e1b24cdf45069766466f448ee9d66
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333281"
---
# <a name="no_smart_pointers-import-attribute"></a>no_smart_pointers 가져오기 특성

**C++ 전용**

형식 라이브러리의 모든 인터페이스에 대한 스마트 포인터를 만들지 않습니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **no_smart_pointers**

## <a name="remarks"></a>설명

`#import`를 사용하는 경우 기본적으로 형식 라이브러리에 있는 모든 인터페이스에 대한 스마트 포인터 선언을 가져옵니다. 이러한 스마트 포인터는 [_com_ptr_t](../cpp/com-ptr-t-class.md)유형입니다.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
