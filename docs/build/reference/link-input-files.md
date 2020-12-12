---
description: '자세한 정보: 링크 입력 파일'
title: LINK 입력 파일
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], LINK
- module definition files
- resources [C++], linker files
- LINK tool [C++], input files
- module definition files, linker files
- input files [C++], LINK
- linker [C++], input files
- import libraries [C++], linker files
- command input to linker files [C++]
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
ms.openlocfilehash: 3bf25d36ab61b35dfe3d1551e9f85e8c2f26862b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199508"
---
# <a name="link-input-files"></a>LINK 입력 파일

개체, 가져오기 및 표준 라이브러리, 리소스, 모듈 정의 및 명령 입력을 포함 하는 파일을 링커에 제공 합니다. 링크는 파일 확장명을 사용 하 여 파일의 내용에 대 한 가정을 수행 하지 않습니다. 대신, LINK는 각 입력 파일을 검사 하 여 파일의 종류를 확인 합니다.

명령줄의 개체 파일은 명령줄에 표시 된 순서 대로 처리 됩니다. 라이브러리는 명령줄 순서로도 검색 됩니다. 예를 들어 라이브러리에서 개체 파일을 가져올 때 확인 되지 않은 기호는 해당 라이브러리에서 먼저 검색 된 후 명령줄과 [/DEFAULTLIB (기본 라이브러리 지정)](defaultlib-specify-default-library.md) 지시문에서 다음 라이브러리를 검색 한 다음 명령줄의 시작 부분에 있는 라이브러리에 대해 검색 됩니다.

> [!NOTE]
> 링크는 응답 파일 및 순서 파일에서 주석 시작으로 더 이상 세미콜론 (또는 다른 문자)을 허용 하지 않습니다. 세미콜론은 모듈 정의 파일 (.def)에서 주석의 시작 으로만 인식 됩니다.

LINK에서는 다음과 같은 유형의 입력 파일을 사용 합니다.

- [.obj 파일](dot-obj-files-as-linker-input.md)

- [.netmodule 파일](netmodule-files-as-linker-input.md)

- [.lib 파일](dot-lib-files-as-linker-input.md)

- [.exp 파일](dot-exp-files-as-linker-input.md)

- [.def 파일](dot-def-files-as-linker-input.md)

- [.pdb 파일](dot-pdb-files-as-linker-input.md)

- [.res 파일](dot-res-files-as-linker-input.md)

- [.exe 파일](dot-exe-files-as-linker-input.md)

- [.txt 파일](dot-txt-files-as-linker-input.md)

- [.ilk 파일](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>참고 항목

[MSVC 링커 참조](linking.md)<br/>
[MSVC 링커 옵션](linker-options.md)
