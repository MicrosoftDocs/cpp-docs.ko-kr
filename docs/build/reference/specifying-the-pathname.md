---
description: '자세한 정보: 경로 이름 지정'
title: 경로 이름 지정
ms.date: 11/04/2016
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
ms.openlocfilehash: a8c55822bcb19864955ffa37ef2dd4cb18765ae5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224532"
---
# <a name="specifying-the-pathname"></a>경로 이름 지정

각 출력 파일 옵션은 출력 파일의 위치와 이름을 지정할 수 있는 *pathname* 인수를 허용 합니다. 인수에는 드라이브 이름, 디렉터리 및 파일 이름이 포함 될 수 있습니다. 옵션과 인수 사이에는 공백이 허용 되지 않습니다.

*Pathname* 이 확장명이 없는 파일 이름을 포함 하는 경우 컴파일러는 출력에 기본 확장을 제공 합니다. *Pathname* 에 디렉터리를 포함 하지만 파일 이름을 포함 하지 않는 경우 컴파일러는 지정 된 디렉터리에 기본 이름으로 파일을 만듭니다. 기본 이름은 소스 파일의 기본 이름과 출력 파일의 형식을 기반으로 하는 기본 확장명을 기반으로 합니다. *Pathname* 을 완전히 벗어나면 컴파일러가 기본 디렉터리에 기본 이름으로 파일을 만듭니다.

또는 *경로* 이름 인수는 파일 이름이 아닌 장치 이름 (AUX, CON, PRN 또는 NUL) 일 수 있습니다. 옵션과 장치 이름 사이에 공백을 사용 하지 마십시오. 또는 장치 이름의 일부로 콜론을 사용 합니다.

|디바이스 이름|나타내는 대상|
|-----------------|----------------|
|AUX|보조 장치|
|CON|콘솔|
|PRN|프린터|
|NUL|Null 장치 (파일을 만들지 않음)|

## <a name="example"></a>예제

다음 명령줄은 프린터에 맵 파일을 보냅니다.

```
CL /FmPRN HELLO.CPP
```

## <a name="see-also"></a>참고 항목

[출력 파일 (/F) 옵션](output-file-f-options.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
