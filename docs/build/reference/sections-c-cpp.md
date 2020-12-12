---
description: '자세한 정보: 섹션 (C/c + +)'
title: SECTIONS(C/C++)
ms.date: 11/04/2016
f1_keywords:
- SECTIONS
helpviewer_keywords:
- SECTIONS .def file statement
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
ms.openlocfilehash: aaebeb19c921dfb389c55209c7a371f49043cb56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224766"
---
# <a name="sections-cc"></a>SECTIONS(C/C++)

`definitions`프로젝트의 출력 파일에 있는 섹션의 액세스 지정자 인 하나 이상의 섹션을 소개 합니다.

```
SECTIONS
definitions
```

## <a name="remarks"></a>설명

각 정의는 별도의 줄에 있어야 합니다. `SECTIONS`키워드는 첫 번째 정의와 같은 줄 이나 이전 줄에 있을 수 있습니다. .Def 파일은 하나 이상의 문을 포함할 수 있습니다 `SECTIONS` .

이 `SECTIONS` 문은 이미지 파일의 섹션 하나 이상에 대 한 특성을 설정 하 고 각 섹션 형식에 대 한 기본 특성을 재정의 하는 데 사용할 수 있습니다.

의 형식은 `definitions` 다음과 같습니다.

`.section_name specifier`

여기서 `.section_name` 는 프로그램 이미지의 섹션 이름이 고는 `specifier` 다음 액세스 한정자 중 하나 이상입니다.

|한정자|설명|
|--------------|-----------------|
|`EXECUTE`|섹션이 실행 파일입니다.|
|`READ`|데이터에 대 한 읽기 작업 허용|
|`SHARED`|이미지를 로드 하는 모든 프로세스에서 섹션을 공유 합니다.|
|`WRITE`|데이터에 대 한 쓰기 작업 허용|

지정자 이름을 공백으로 구분 합니다. 예를 들어:

```
SECTIONS
.rdata READ WRITE
```

`SECTIONS` 섹션 목록의 시작 부분을 표시 `definitions` 합니다. 각 `definition` 는 별도의 줄에 있어야 합니다. `SECTIONS`키워드는 첫 번째 또는 이전 줄과 같은 줄에 있을 수 있습니다 `definition` . .Def 파일은 하나 이상의 문을 포함할 수 있습니다 `SECTIONS` . `SEGMENTS`키워드는의 동의어로 지원 됩니다 `SECTIONS` .

이전 버전의 Visual C++ 지원 됩니다.

```
section [CLASS 'classname'] specifier
```

`CLASS`키워드는 호환성을 위해 지원 되지만 무시 됩니다.

섹션 특성을 지정 하는 동일한 방법은 [/SECTION](section-specify-section-attributes.md) 옵션을 사용 하는 것입니다.

## <a name="see-also"></a>참고 항목

[Module-Definition 문에 대 한 규칙](rules-for-module-definition-statements.md)
