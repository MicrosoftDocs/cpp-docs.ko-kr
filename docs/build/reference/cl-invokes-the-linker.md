---
description: '자세히 알아보기: CL은 링커를 호출 합니다.'
title: CL에서의 링커 호출
ms.date: 11/04/2016
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
ms.openlocfilehash: ddd693cdba625756b8085d2f8cb3870d8cdc6add
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179163"
---
# <a name="cl-invokes-the-linker"></a>CL에서의 링커 호출

/C 옵션을 사용 하지 않으면 컴파일하는 동안 CL에서 자동으로 링커를 호출 합니다. CL은 컴파일하는 동안 생성 된 .obj 파일의 이름과 명령줄에 지정 된 다른 파일의 이름을 링커에 전달 합니다. 링커는 링크 환경 변수에 나열 된 옵션을 사용 합니다. /Link 옵션을 사용 하 여 CL 명령줄에서 링커 옵션을 지정할 수 있습니다. /Link 옵션을 따르는 옵션은 LINK 환경 변수의 해당 옵션을 재정의 합니다. 다음 표의 옵션은 연결을 표시 하지 않습니다.

|옵션|설명|
|------------|-----------------|
|/C|링크 하지 않고 컴파일|
|/E,/EP,/P|컴파일하거나 링크 하지 않고 전처리 합니다.|
|/Zg|함수 프로토타입 생성|
|/Zs|구문 검사|

연결에 대 한 자세한 내용은 [MSVC 링커 옵션](linker-options.md)을 참조 하세요.

## <a name="example"></a>예제

세 개의 C 소스 파일 (MOD1, 및 MOD2)을 컴파일하는 것으로 가정 합니다. 각 파일에는 다른 파일에 정의 된 함수에 대 한 호출이 포함 됩니다.

- MOD1에서 함수를 호출 `func1` 하 고 MOD2에서 함수를 호출 `func2` 합니다.

- MOD1는 표준 라이브러리 함수 및를 호출 `printf_s` 합니다 `scanf_s` .

- MOD2 `myline` `mycircle` 는 mygraph .lib 라는 라이브러리에 정의 된 및 라는 그래픽 함수를 호출 합니다.

이 프로그램을 빌드하려면 다음 명령줄을 사용 하 여 컴파일합니다.

```
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib
```

CL은 먼저 C 소스 파일을 컴파일하고 개체 파일의 기본 .obj, MOD1 및 MOD2를 만듭니다. 컴파일러는 각 .obj 파일에 표준 라이브러리의 이름을 배치 합니다. 자세한 내용은 [Run-Time 라이브러리 사용](md-mt-ld-use-run-time-library.md)을 참조 하세요.

CL은 이름이 MYGRAPH .lib 인 .obj 파일의 이름을 링커에 전달 합니다. 링커는 다음과 같이 외부 참조를 확인 합니다.

1. 기본 .obj에서는 MOD1의 정의를 사용 하 여에 대 한 참조를 확인 합니다. `func1` `func2` MOD2의 정의를 사용 하 여에 대 한 참조를 확인 합니다.

1. MOD1에서 및에 대 한 참조는 `printf_s` `scanf_s` 링커가 MOD1 내에서 찾은 명명 된 라이브러리의 정의를 사용 하 여 확인 됩니다.

1. MOD2에서 및에 대 한 참조는 `myline` `mycircle` mygraph. lib의 정의를 사용 하 여 확인 됩니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[컴파일러 옵션 설정](compiler-command-line-syntax.md)
