---
description: '자세한 정보: fseek, _lseek 상수'
title: fseek, _lseek 상수
ms.date: 11/04/2016
f1_keywords:
- SEEK_END
- SEEK_SET
- SEEK_CUR
helpviewer_keywords:
- SEEK_SET constant
- SEEK_END constant
- SEEK_CUR constant
ms.assetid: 9deeb13e-5aa3-4c33-80d8-721c80a4de9d
ms.openlocfilehash: be12597682074f610b0a69395146b400fed4d6b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319819"
---
# <a name="fseek-_lseek-constants"></a>fseek, _lseek 상수

## <a name="syntax"></a>구문

```
#include <stdio.h>
```

## <a name="remarks"></a>설명

*origin* 인수는 초기 위치를 지정하며 다음 매니페스트 상수 중 하나가 될 수 있습니다.

|상수|의미|
|--------------|-------------|
|`SEEK_END`|파일 끝|
|`SEEK_CUR`|파일 포인터의 현재 위치|
|`SEEK_SET`|파일 시작 부분|

## <a name="see-also"></a>참고 항목

[fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)<br/>
[_lseek, _lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)<br/>
[전역 상수](../c-runtime-library/global-constants.md)
