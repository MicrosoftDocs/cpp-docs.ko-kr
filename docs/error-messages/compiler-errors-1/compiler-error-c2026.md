---
title: 컴파일러 오류 C2026
description: Microsoft C/c + + 컴파일러 오류 C2026, 해당 원인 및 해결 방법에 대해 설명 합니다.
ms.date: 09/25/2020
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: 39195568f964f07c6131fa43ef4a0f06121795da
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414050"
---
# <a name="compiler-error-c2026"></a>컴파일러 오류 C2026

> 문자열이 너무 커서 후행 문자가 잘렸습니다.

문자열이 16380 바이트의 한도 보다 깁니다.

## <a name="remarks"></a>설명

인접 문자열이 연결 되기 전에 문자열은 16380 싱글바이트 문자 보다 길 수 없습니다.

이 길이에 대 한 유니코드 문자열은이 오류도 생성 합니다.

## <a name="example"></a>예제

다음과 같이 정의 된 문자열이 있는 경우 C2026을 생성 합니다.

```C
char sz[] =
"\
imagine a really, really \
long string here\
";
```

다음과 같이 나눌 수 있습니다.

```C
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

사용자 지정 리소스나 외부 파일에 매우 긴 문자열 리터럴 (32K 이상)을 저장 하는 것이 좋습니다. 자세한 내용은 [새 사용자 지정 또는 데이터 리소스를 만들려면을](../../windows/binary-editor.md#to-create-a-new-custom-or-data-resource)참조 하세요.
