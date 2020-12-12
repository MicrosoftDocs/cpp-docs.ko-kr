---
description: 자세히 알아보기:/SECTION (EDITBIN)
title: /SECTION(EDITBIN)
ms.date: 11/04/2016
f1_keywords:
- /section_editbin
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
ms.openlocfilehash: 51d1305ca4f3e0e8222ae9408b44563a4c480d57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224870"
---
# <a name="section-editbin"></a>/SECTION(EDITBIN)

```
/SECTION:name[=newname][,attributes][alignment]
```

## <a name="remarks"></a>설명

이 옵션은 섹션의 특성을 변경 하 여 섹션의 개체 파일이 컴파일 또는 연결 되었을 때 설정 된 특성을 재정의 합니다.

콜론 ( **:** ) 뒤에 섹션의 *이름을* 지정 합니다. 섹션 이름을 변경 하려면 *이름* 에 등호 (=)를 추가 하 고 섹션의 *newname* 을 사용 합니다.

섹션을 설정 하거나 변경 하려면 `attributes` 쉼표 (**,**), 하나 이상의 특성 문자를 차례로 지정 합니다. 특성을 부정 하려면 해당 문자 앞에 느낌표 (!)를 사용 합니다. 다음 문자는 메모리 특성을 지정 합니다.

|특성|설정|
|---------------|-------------|
|c|code|
|일|삭제 가능한|
|e|executable|
|i|초기화 데이터|
|k|캐시 된 가상 메모리|
|분|링크 제거|
|o|링크 정보|
|p|페이징 가상 메모리|
|r|읽기|
|초|공유|
|u|초기화 되지 않은 데이터|
|w|쓰기|

*맞춤* 을 제어 하려면 다음과 같이 문자 **A** 와 다음 문자 중 하나를 지정 하 여 맞춤 크기를 바이트 단위로 설정 합니다.

|문자|맞춤 크기 (바이트)|
|---------------|-----------------------------|
|1|1|
|2|2|
|4|4|
|8|8|
|p|16|
|t|32|
|초|64|
|x|맞춤 없음|

`attributes`및 *맞춤* 문자를 공백이 없는 문자열로 지정 합니다. 문자는 대/소문자를 구분 하지 않습니다.

## <a name="see-also"></a>참고 항목

[EDITBIN 옵션](editbin-options.md)
