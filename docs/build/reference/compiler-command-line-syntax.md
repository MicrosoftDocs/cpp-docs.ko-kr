---
description: '자세한 정보: 컴파일러 Command-Line 구문'
title: MSVC 컴파일러 Command-Line 구문
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 91340aa543f0e79d3071b93921742b8147918b2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182218"
---
# <a name="compiler-command-line-syntax"></a>컴파일러 명령줄 구문

CL 명령줄은 다음 구문을 사용 합니다.

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

다음 표에서는 CL 명령에 대 한 입력을 설명 합니다.

|입력|의미|
|-----------|-------------|
|*옵션*|하나 이상의 [CL 옵션](compiler-options.md)입니다. 모든 옵션은 지정 된 모든 소스 파일에 적용 됩니다. 옵션은 슬래시 (/) 또는 대시 (-) 중 하나로 지정 됩니다. 옵션이 인수를 사용 하는 경우 옵션의 설명은 옵션과 인수 사이에 공백이 허용 되는지 여부를 문서화 합니다. 옵션 이름 (/HELP 옵션 제외)은 대/소문자를 구분 합니다. 자세한 내용은 [CL 옵션 순서](order-of-cl-options.md) 를 참조 하세요.|
|`file`|하나 이상의 소스 파일, .obj 파일 또는 라이브러리의 이름입니다. CL은 소스 파일을 컴파일하고 .obj 파일 및 라이브러리의 이름을 링커에 전달 합니다. 자세한 내용은 [CL 파일 이름 구문](cl-filename-syntax.md) 을 참조 하세요.|
|*lib*|하나 이상의 라이브러리 이름입니다. CL은 이러한 이름을 링커에 전달 합니다.|
|*명령 파일*|여러 옵션 및 파일 이름을 포함 하는 파일입니다. 자세한 내용은 [CL 명령 파일](cl-command-files.md) 을 참조 하세요.|
|*링크-옵트인*|하나 이상의 [MSVC 링커 옵션](linker-options.md)입니다. CL은 이러한 옵션을 링커에 전달 합니다.|

명령줄의 문자 수가 1024을 초과 하지 않는 한 옵션, 파일 이름 및 라이브러리 이름을 원하는 수 만큼 지정할 수 있으며,이는 운영 체제에 의해 결정 됩니다.

cl.exe의 반환 값에 대 한 자세한 내용은 [cl.exe반환 값 ](return-value-of-cl-exe.md) 을 참조 하세요.

> [!NOTE]
> 명령줄 입력 제한인 1024 문자는 이후 버전의 Windows에서 동일 하 게 유지 되지 않을 수 있습니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)
