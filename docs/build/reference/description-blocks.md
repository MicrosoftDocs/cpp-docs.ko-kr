---
title: 설명 블록
description: NMAKE는 설명 블록을 사용 하 여 메이크파일의 대상, 종속성 및 명령을 연결 합니다.
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: 8f7bf3a26eadde91471e8b45ec26e0abea906244
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506593"
---
# <a name="description-blocks"></a>설명 블록

설명 블록은 메이크파일의 핵심을 형성 합니다. 대상을 만드는 데 필요한 파일, *대상*, 만들 파일 및 해당 *종속성*을 설명 합니다. 설명 블록에는 종속성에서 대상을 만드는 방법을 설명 하는 *명령이*포함 되어 있을 수 있습니다. 설명 블록은 종속성 줄 이며, 필요에 따라 명령 블록이 옵니다.

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>종속성 줄

*종속성 줄* 은 하나 이상의 대상과 0 개 이상의 종속 항목을 지정 합니다. 대상이 존재 하지 않거나 종속 된 타임 스탬프 보다 이전 타임 스탬프를 포함 하는 경우 NMAKE는 명령 블록의 명령을 실행 합니다. NMAKE는 대상이 [의사](#pseudotargets)인 인 경우에도 명령 블록을 실행 합니다. 종속성 줄의 예는 다음과 같습니다.

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

이 종속성 줄에서 `hi_bye.exe` 는 대상입니다. 해당 종속성은 `hello.obj` , `goodbye.obj` 및 `helper.lib` 입니다. 종속성 줄은 `hello.obj` , `goodbye.obj` 또는 `helper.lib` 가 보다 최근에 변경 될 때마다 NMAKE에 대상을 빌드하도록 지시 합니다 `hi_bye.exe` .

대상은 줄의 시작 부분에 있어야 합니다. 공백이 나 탭으로 들여쓸 수 없습니다. 콜론 ()을 사용 `:` 하 여 종속 항목의 대상을 구분 합니다. 대상, 콜론 구분 기호 () 및 종속 항목 사이에는 공백 또는 탭을 사용할 수 있습니다 `:` . 종속성 줄을 분할 하려면 `\` 대상 또는 종속 뒤에 백슬래시 ()를 사용 합니다.

NMAKE는 명령 블록을 실행 하기 전에 모든 종속성 및 적용 가능한 모든 유추 규칙을 검색 하 여 *종속성 트리*를 작성 합니다. 종속성 트리는 대상을 완전히 업데이트 하는 데 필요한 단계를 지정 합니다. NMAKE는 종속 관계가 다른 종속성 목록에 있는 대상 인지 여부를 재귀적으로 확인 합니다. 종속성 트리를 빌드한 후 NMAKE는 타임 스탬프를 확인 합니다. 트리의 모든 종속 항목이 대상 보다 최신인 경우 NMAKE는 대상을 작성 합니다.

## <a name="targets"></a><a name="targets"></a> 대상

종속성 줄의 대상 섹션은 하나 이상의 대상을 지정 합니다. 대상은 유효한 파일 이름, 디렉터리 이름 또는 [의사](#pseudotargets)대상이 될 수 있습니다. 하나 이상의 공백이 나 탭을 사용 하 여 여러 대상을 구분 합니다. 대상은 대/소문자를 구분 하지 않습니다. 파일 이름에 경로를 사용할 수 있습니다. 대상 및 경로는 256 자를 초과할 수 없습니다. 콜론 앞의 대상이 단일 문자인 경우 구분 하는 공간을 사용 합니다. 그렇지 않으면 NMAKE는 문자-콜론 조합을 드라이브 지정자로 해석 합니다.

### <a name="multiple-targets"></a><a name="multiple-targets"></a> 여러 대상

NMAKE는 각각 별도의 설명 블록에 지정 된 것 처럼 단일 종속성의 여러 대상을 평가 합니다.

예를 들어 다음과 같은 규칙이 있습니다.

```makefile
bounce.exe leap.exe : jump.obj
   echo Building...
```

는 다음과 같이 계산 됩니다.

```makefile
bounce.exe : jump.obj
   echo Building...

leap.exe : jump.obj
   echo Building...
```

### <a name="cumulative-dependencies"></a><a name="cumulative-dependencies"></a> 누적 종속성

대상이 반복 되는 경우 종속성은 설명 블록에서 누적 됩니다.

예를 들어, 다음과 같은 규칙 집합이 있습니다.

```makefile
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

는 다음과 같이 계산 됩니다.

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

단일 설명 블록의 여러 종속성 줄에 대상이 여러 개 있는 경우 NMAKE는 각각 별도의 description 블록에 지정 된 것 처럼 계산 합니다. 그러나 마지막 종속성 줄의 대상만 commands 블록을 사용 합니다. NMAKE는 다른 대상에 대 한 유추 규칙을 사용 하려고 합니다.

예를 들어, 다음과 같은 규칙 집합이 있습니다.

```makefile
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

는 다음과 같이 계산 됩니다.

```makefile
leap.exe : jump.obj
# invokes an inference rule

bounce.exe : jump.obj up.obj
   echo Building bounce.exe...

climb.exe : up.obj
   echo Building bounce.exe...
```

### <a name="targets-in-multiple-description-blocks"></a><a name="targets-in-multiple-description-blocks"></a> 여러 설명 블록의 대상

다른 명령을 사용 하 여 둘 이상의 설명 블록에서 대상을 업데이트 하려면 두 개의 연속 콜론 (::) 대상 및 종속 항목 사이

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a><a name="dependency-side-effects"></a> 종속성 부작용

콜론을 사용 하 여 대상을 지정할 수 있습니다 (:) 다른 위치에 있는 두 개의 종속성 줄에 있습니다. 명령 줄 중 하나만 표시 되는 경우 NMAKE는 줄이 인접 하거나 결합 된 것 처럼 종속성을 해석 합니다. 명령이 없는 종속성에 대 한 유추 규칙은 호출 하지 않습니다. 대신 NMAKE는 종속성이 하나의 설명 블록에 속하며 다른 종속성으로 지정 된 명령을 실행 한다고 가정 합니다. 이러한 규칙 집합을 고려 합니다.

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

는 다음과 같이 계산 됩니다.

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

이중 콜론 ()이 사용 되는 경우이 효과가 발생 하지 않습니다 `::` . 예를 들어 다음 규칙 집합이 있습니다.

```makefile
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

는 다음과 같이 계산 됩니다.

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

### <a name="pseudotargets"></a><a name="pseudotargets"></a> 의사 대상

*의사* (으)는 종속성 줄에서 파일 이름 대신 사용 되는 레이블입니다. 이 파일은 존재 하지 않는 파일로 해석 되므로 최신 상태가 아닙니다. NMAKE는 대상의 타임 스탬프가 해당 하는 모든 종속 항목의 타임 스탬프와 동일 하다 고 가정 합니다. 종속 항목이 없는 경우 현재 시간으로 간주 됩니다. 의사 대상이 대상으로 사용 되는 경우 해당 명령이 항상 실행 됩니다. 종속으로 사용 되는 의사 결정은 다른 종속성에서 대상으로도 표시 되어야 합니다. 그러나 해당 종속성에는 명령 블록을 사용할 필요가 없습니다.

의사 (names) 이름은 대상에 대 한 파일 이름 구문 규칙을 따릅니다. 그러나 이름에 확장명이 없는 경우에는 파일 이름에 대 한 8 자 제한을 초과할 수 있으며 최대 256 자까지 사용할 수 있습니다.

의사 대상는 NMAKE가 둘 이상의 대상을 자동으로 빌드하려고 할 때 유용 합니다. NMAKE는 명령줄에 지정 된 대상만 빌드합니다. 또는 명령줄 대상이 지정 되지 않은 경우 메이크파일의 첫 번째 종속성에 첫 번째 대상만 빌드합니다. 명령줄에 개별적으로 나열 하지 않고 여러 대상을 빌드하도록 NMAKE에 지시할 수 있습니다. 의사 대상이 포함 된 종속성이 있는 설명 블록을 작성 하 고 해당 종속 항목으로 빌드할 대상을 나열 합니다. 그런 다음이 설명 블록을 메이크파일의 맨 앞에 두거나 NMAKE 명령줄에서 의사 (으)로 지정 합니다.

이 예제에서 업데이트는 의사 (으)로 업데이트 됩니다.

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

업데이트를 평가 하면 NMAKE는 현재 디렉터리에 있는 모든 파일을 지정 된 드라이브와 디렉터리에 복사 합니다.

다음 메이크파일에는 `all` `project1.exe` `project2.exe` `all` 명령줄에서 대상이 지정 되거나 지정 되지 않은 경우 의사 대상이 둘 다와를 빌드합니다. 의사는 `setenv` 파일이 업데이트 되기 전에 LIB 환경 변수를 변경 합니다 `.exe` .

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a><a name="dependents"></a> 종속

종속성 줄에서 `:` `::` 유효한 파일 이름 또는 [의사](#pseudotargets)(으)를 사용 하 여 콜론 () 또는 이중 콜론 () 뒤에 0 개 이상의 종속 항목을 지정 합니다. 하나 이상의 공백이 나 탭을 사용 하 여 여러 종속 항목을 분리 합니다. 종속 항목은 대/소문자를 구분 하지 않습니다. 파일 이름에 경로를 사용할 수 있습니다.

### <a name="inferred-dependents"></a><a name="inferred-dependents"></a> 유추 된 종속 항목

NMAKE는 종속성 줄에 명시적으로 나열 된 종속 항목을 사용 하 여 *유추 된 종속*항목을 가정할 수 있습니다. 유추 된 종속은 유추 규칙에서 파생 되며 명시적으로 종속 되기 전에 계산 됩니다. 유추 된 종속 관계가 해당 대상과 비교 하 여 오래 된 경우 NMAKE는 종속성에 대 한 명령 블록을 호출 합니다. 유추 된 종속 항목이 존재 하지 않거나 해당 종속 항목에 대해 오래 된 경우 NMAKE는 먼저 유추 된 종속 항목을 업데이트 합니다. 유추 된 종속 항목에 대 한 자세한 내용은 [유추 규칙](inference-rules.md)을 참조 하세요.

### <a name="search-paths-for-dependents"></a><a name="search-paths-for-dependents"></a> 종속 파일의 경로 검색

각 종속 항목에 대해 선택적 검색 경로를 지정할 수 있습니다. 검색할 디렉터리 집합을 지정 하는 구문은 다음과 같습니다.

> **{**_directory_ \[ **;** _디렉터리_...] **}**_종속_

디렉터리 이름은 중괄호 ()로 묶습니다 `{ }` . 여러 디렉터리를 세미콜론 ()으로 구분 `;` 합니다. 공백 또는 탭은 허용 되지 않습니다. NMAKE는 현재 디렉터리에서 종속 된를 먼저 찾은 다음 지정 된 순서로 디렉터리 목록에서 찾습니다. 매크로를 사용 하 여 검색 경로의 일부 또는 전체를 지정할 수 있습니다. 지정 된 종속 파일만이 검색 경로를 사용 합니다.

#### <a name="directory-search-path-example"></a>디렉터리 검색 경로 예

이 종속성 줄은 검색에 대 한 디렉터리 사양을 만드는 방법을 보여 줍니다.

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

대상에는 `reverse.exe` 하나의 종속이 `retro.obj` 있습니다. 중괄호로 묶인 목록은 두 개의 디렉터리를 지정 합니다. NMAKE `retro.obj` 는 먼저 현재 디렉터리에서을 검색 합니다. 없으면 NMAKE는 `\src\omega` 디렉터리를 검색 한 다음 디렉터리를 검색 합니다 `e:\repo\backwards` .

## <a name="see-also"></a>참고 항목

[NMAKE 참조](nmake-reference.md)
