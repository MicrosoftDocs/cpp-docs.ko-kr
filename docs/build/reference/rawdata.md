---
description: 자세히 알아보기:/RAWDATA
title: /RAWDATA
ms.date: 11/04/2016
f1_keywords:
- /rawdata
helpviewer_keywords:
- RAWDATA dumpbin option
- raw data
- -RAWDATA dumpbin option
- /RAWDATA dumpbin option
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
ms.openlocfilehash: efe2001c0170b8539b98902591849dedaf0fb819
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225377"
---
# <a name="rawdata"></a>/RAWDATA

```
/RAWDATA[:{1|2|4|8|NONE[,number]]
```

## <a name="remarks"></a>설명

이 옵션은 파일의 각 섹션에 대 한 원시 내용을 표시 합니다. 인수는 아래와 같이 표시 형식을 제어 합니다.

|인수|결과|
|--------------|------------|
|1|기본값입니다. 콘텐츠는 16 진수 바이트 및 인쇄 된 표현이 있는 경우 ASCII 문자로 표시 됩니다.|
|2|콘텐츠는 16 진수 2 바이트 값으로 표시 됩니다.|
|4|콘텐츠는 16 진수 4 바이트 값으로 표시 됩니다.|
|8|콘텐츠는 16 진수 8 바이트 값으로 표시 됩니다.|
|없음|원시 데이터는 표시 되지 않습니다. 이 인수는/ALL의 출력을 제어 하는 데 유용 합니다.|
|*Number*|표시 된 선은 줄 당 값을 포함 하는 너비로 설정 됩니다 `number` .|

[/GL](gl-whole-program-optimization.md) 컴파일러 옵션으로 생성된 파일에서는 [/HEADERS](headers.md) DUMPBIN옵션만 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[DUMPBIN 옵션](dumpbin-options.md)
