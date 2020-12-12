---
description: 다음에 대 한 자세한 정보:/기준
title: /다시 지정
ms.date: 11/04/2016
f1_keywords:
- /rebase
helpviewer_keywords:
- base addresses [C++]
- -REBASE editbin option
- REBASE editbin option
- DLLs [C++], linking
- executable files [C++], base address
- /REBASE editbin option [C++]
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
ms.openlocfilehash: 6cbbf0a21bd9306167fb165b63c22e810518e161
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225338"
---
# <a name="rebase"></a>/다시 지정

```
/REBASE[:modifiers]
```

## <a name="remarks"></a>설명

이 옵션은 지정 된 파일에 대 한 기본 주소를 설정 합니다. EDITBIN은 각 파일의 크기에 따라 인접 한 주소 공간에 가장 가까운 64 KB로 반올림 된 새 기준 주소를 할당 합니다. 기본 주소에 대 한 자세한 내용은 [기본 주소](base-base-address.md) (/base) 링커 옵션을 참조 하세요.

EDITBIN 명령줄의 *파일* 인수에서 프로그램의 실행 파일 및 dll을 기반으로 할 순서 대로 지정 합니다. 선택적으로 하나 이상의 *한정자* 를 쉼표 (**,**)로 구분 하 여 지정할 수 있습니다.

|한정자|작업|
|--------------|------------|
|**기준 =**<em>주소</em>|기본 주소를 파일에 다시 할당 하기 위한 시작 주소를 제공 합니다. 10 진수 또는 C 언어 표기법으로 *주소* 를 지정 합니다. BASE를 지정 하지 않으면 기본 시작 기본 주소는 0x400000입니다. DOWN을 사용 하는 경우 BASE를 지정 하 고 *주소* 는 기본 주소 범위의 끝을 설정 합니다.|
|**BASEFILE**|COFFBASE.TXT 라는 파일을 만듭니다 .이 파일은 링크의/BASE 옵션에 필요한 형식의 텍스트 파일입니다.|
|**드롭다운**|끝 주소에서 하향 밑 주소를 다시 할당 하도록 EDITBIN에 지시 합니다. 파일은 지정 된 순서 대로 다시 할당 되며, 첫 번째 파일은 주소 범위의 끝 아래에서 가능한 가장 높은 주소에 위치 합니다. 파일 기반으로 충분 한 주소 공간을 확보 하기 위해 밑은 DOWN과 함께 사용 해야 합니다. 지정 된 파일에 필요한 주소 공간을 확인 하려면 파일에 대해/다시 지정을 사용 하 여 EDITBIN을 실행 하 고 표시 된 총 크기에 64 KB를 추가 합니다.|

## <a name="see-also"></a>참고 항목

[EDITBIN 옵션](editbin-options.md)
