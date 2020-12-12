---
description: '자세한 정보: 특성 가져오기 inject_statement'
title: inject_statement 가져오기 특성
ms.date: 08/29/2019
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: b7ab8059e95ed3799857fe1b899ef2efff729ffb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236427"
---
# <a name="inject_statement-import-attribute"></a>inject_statement 가져오기 특성

**C++ 전용**

소스 텍스트로서 인수를 형식 라이브러리 헤더에 삽입합니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **inject_statement (** "*원본-텍스트*" **)**

### <a name="parameters"></a>매개 변수

*원본-텍스트*\
형식 라이브러리 헤더 파일에 삽입되는 소스 텍스트입니다.

## <a name="remarks"></a>설명

텍스트는 헤더 파일의 *형식 라이브러리* 콘텐츠를 래핑하는 네임 스페이스 선언의 시작 부분에 배치 됩니다.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
