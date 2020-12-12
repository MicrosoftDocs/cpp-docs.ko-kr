---
description: '자세한 정보: 가져오기 특성 제외'
title: 가져오기 특성 제외
ms.date: 08/29/2019
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: e856544f812fd5d0b14676beb8423c4350e40da1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269317"
---
# <a name="exclude-import-attribute"></a>가져오기 특성 제외

**C++ 전용**

생성되는 형식 라이브러리 헤더 파일에서 항목을 제외시킵니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **제외 (** "*Name1*" [ **,** "*Name2*" ...] **)**

### <a name="parameters"></a>매개 변수

*Name1*\
제외시킬 첫 번째 항목입니다.

*Name2*\
필드 필요한 경우 제외할 두 번째와 이후 항목입니다.

## <a name="remarks"></a>설명

형식 라이브러리가 시스템 헤더 또는 다른 형식 라이브러리에 정의된 항목 정의를 포함할 수 있습니다. 이 특성에는 임의 개수의 인수를 사용할 수 있습니다. 각 인수는 제외할 최상위 형식 라이브러리 항목입니다.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
