---
description: '자세한 정보: CL 환경 변수'
title: CL 환경 변수
ms.date: 06/06/2019
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 1be95d2c2eddd204846fbcdc8675f28d71c25c0d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179176"
---
# <a name="cl-environment-variables"></a>CL 환경 변수

CL 도구는 다음과 같은 환경 변수를 사용합니다.

- CL 및 \_ CL_ (정의 된 경우). CL 도구는 CL 환경 변수에 정의 된 옵션 및 인수를 명령줄 인수 앞에 추가 하 고, \_ 처리 하기 전에 CL_에 정의 된 옵션 및 인수를 추가 합니다.

- Visual Studio 설치의 \include 하위 디렉터리를 가리켜야 하는를 포함 합니다.

- LIBPATH- [#using](../../preprocessor/hash-using-directive-cpp.md)에서 참조 되는 메타 데이터 파일을 검색할 디렉터리를 지정 합니다. LIBPATH에 대 한 자세한 내용은 [#using](../../preprocessor/hash-using-directive-cpp.md)를 참조 하세요.

\_다음 구문을 사용 하 여 CL 또는 CL_ 환경 변수를 설정할 수 있습니다.

> SET CL = [[*옵션*] ... [*file*] ...] [/link *링크-opt* ...] \
> SET \_ CL \_ = [[*옵션*] ... [*file*] ...] [/link *링크-opt* ...]

CL 및 CL_ 환경 변수에 대 한 인수에 대 한 자세한 \_ 내용은 [MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)을 참조 하세요.

이러한 환경 변수를 사용 하 여 자주 사용 하는 파일 및 옵션을 정의할 수 있습니다. 그런 다음 명령줄을 사용 하 여 특정 용도에 대 한 추가 파일 및 옵션을 CL에 제공 합니다. CL 및 \_ CL_ 환경 변수는 1024 자로 제한 됩니다 (명령줄 입력 제한).

[/D](d-preprocessor-definitions.md) 옵션을 사용 하 여 등호 ()를 사용 하는 기호를 정의할 수 없습니다 **=** . 대신 등호 기호에 숫자 기호 ()를 사용할 수 있습니다 **#** . 이러한 방식으로 CL 또는 CL_ 환경 변수를 사용 하 여를 정의할 때와 같이 \_ 명시적 값으로 전처리기 상수를 정의할 수 있습니다 `/DDEBUG#1` `DEBUG=1` .

관련 정보는 [환경 변수 설정](../setting-the-path-and-environment-variables-for-command-line-builds.md)을 참조 하세요.

## <a name="examples"></a>예제

다음 명령은 CL 환경 변수를 설정 하는 예입니다.

> SET CL =/Zp2/Ox/I\INCLUDE\MYINCLS \ENT\BINMO\BINMO\BINMO. 인스턴스인

CL 환경 변수를 설정 하는 경우 명령줄에를 입력 하면 `CL INPUT.C` 유효 명령이 다음과 같이 됩니다.

> CL/zp2/ox/I\INCLUDE\MYINCLS \ent\binmo\binstststp\binmost OBJ 입력. C

다음 예제에서는 일반 CL 명령을 사용하여 소스 파일 FILE1.c 및 FILE2.c를 컴파일한 다음 개체 파일 FILE1.obj, FILE2.obj 및 FILE3.obj를 연결합니다.

> SET CL = FILE1 C FILE2. C
> \_CL_ = FILE3를 설정 합니다. 인스턴스인
> CL

이러한 환경 변수를 사용 하면 CL 호출은 다음 명령줄과 동일한 효과를 가집니다.

> CL FILE1 C FILE2. C FILE3. 인스턴스인

## <a name="see-also"></a>참고 항목

[컴파일러 옵션 설정](compiler-command-line-syntax.md) \
[MSVC 컴파일러 옵션](compiler-options.md)
