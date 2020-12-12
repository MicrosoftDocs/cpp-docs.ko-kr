---
description: '다음에 대 한 자세한 정보: execution_character_set pragma'
title: execution_character_set pragma
ms.date: 08/29/2019
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
ms.openlocfilehash: 057013e669d7c6a4b31c02fe9c6319ea05eb7780
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300488"
---
# <a name="execution_character_set-pragma"></a>execution_character_set pragma

문자열 및 문자 리터럴에 사용 되는 실행 문자 집합을 지정 합니다. 접두사로 표시 된 리터럴에는이 지시문이 필요 하지 않습니다 `u8` .

## <a name="syntax"></a>Syntax

> **#pragma execution_character_set (** "*대상*" **)**

### <a name="parameters"></a>매개 변수

*대상을*\
대상 실행 문자 집합을 지정 합니다. 현재 지원 되는 유일한 대상 실행 집합은 "utf-8"입니다.

## <a name="remarks"></a>설명

이 컴파일러 지시문은 Visual Studio 2015 업데이트 2부터 사용 되지 않습니다. `/execution-charset:utf-8` `/utf-8` `u8` 좁은 문자 및 확장 문자를 포함 하는 문자열 리터럴에 접두사를 사용 하 여 또는 컴파일러 옵션을 함께 사용 하는 것이 좋습니다. 접두사에 대 한 자세한 내용은 `u8` [문자열 및 문자 리터럴](../cpp/string-and-character-literals-cpp.md)을 참조 하세요. 컴파일러 옵션에 대 한 자세한 내용은 [/execution-charset (실행 문자 집합 설정)](../build/reference/execution-charset-set-execution-character-set.md) 및 [/utf-8 (소스 및 실행 문자 집합을 u t f-8로 설정)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)을 참조 하세요.

`#pragma execution_character_set("utf-8")`지시문은 소스 코드의 좁은 문자 및 좁은 문자열 리터럴을 실행 파일의 u t f-8로 인코딩하려면 컴파일러에 지시 합니다. 이 출력 인코딩은 사용 되는 소스 파일 인코딩과는 독립적입니다.

기본적으로 컴파일러는 현재 코드 페이지를 실행 문자 집합으로 사용 하 여 좁은 문자와 좁은 문자열을 인코딩합니다. 즉, 현재 코드 페이지의 범위를 벗어나는 리터럴의 유니코드 또는 DBCS 문자는 출력에서 기본 대체 문자로 변환 됩니다. 유니코드 및 DBCS 문자는 하위 바이트로 잘립니다. 이것은 의도 한 것이 아닙니다. 접두사를 사용 하 여 소스 파일의 리터럴에 대해 UTF-8 인코딩을 지정할 수 있습니다 `u8` . 컴파일러는 이러한 u t f-8로 인코딩된 문자열을 변경 되지 않은 출력으로 전달 합니다. U8를 사용 하 여 접두사로 사용 되는 좁은 문자 리터럴은 1 바이트에 맞아야 하며 출력 시 잘립니다.

기본적으로 Visual Studio는 출력에 대 한 소스 코드를 해석 하는 데 사용 되는 소스 문자 집합으로 현재 코드 페이지를 사용 합니다. 에서 파일을 읽을 때, Visual Studio는 파일 코드 페이지가 설정 되지 않은 경우 또는 파일의 시작 부분에서 BOM (바이트 순서 표시) 또는 UTF-16 문자를 검색 하지 않는 한 현재 코드 페이지에 따라 해석 합니다. U t f-8을 현재 코드 페이지로 설정할 수 없으므로 자동 검색에서 BOM 없이 u t f-8로 인코드된 소스 파일이 발견 되 면 Visual Studio는 현재 코드 페이지를 사용 하 여 인코딩 되었다고 가정 합니다. 소스 파일에서 지정 되거나 자동으로 검색 된 코드 페이지 범위를 벗어난 문자는 컴파일러 경고 및 오류를 일으킬 수 있습니다.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 \_ \_ pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/sv-ecin 문자 집합 (실행 문자 집합 설정)](../build/reference/execution-charset-set-execution-character-set.md)\
[/utf-8 (원본 및 실행 파일 문자 집합을 u t f-8로 설정)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)
