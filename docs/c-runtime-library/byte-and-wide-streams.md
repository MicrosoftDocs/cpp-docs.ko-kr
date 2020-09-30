---
title: 바이트 및 와이드 스트림
description: Microsoft C 런타임 라이브러리의 바이트 스트림에 대 한 개요입니다.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Byte and Wide Streams
helpviewer_keywords:
- byte streams
- wide streams
ms.assetid: 61ef0587-4cbc-4eb8-aae5-4c298dbbc6f9
ms.openlocfilehash: 38949206e65ff84836b9a3e83b78723adfe30582
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590279"
---
# <a name="byte-and-wide-streams"></a>바이트 및 와이드 스트림

바이트 스트림은 파일을 바이트의 시퀀스로 처리합니다. 프로그램에서 스트림은 바이트 시퀀스와 동일합니다.

반면, 와이드 스트림은 파일을 일반화된 멀티바이트 문자 시퀀스로 처리하므로 광범위한 인코딩 규칙이 적용될 수 있습니다. 텍스트 및 이진 파일은 앞에서 설명한 대로 읽고 씁니다. 프로그램 내에서 스트림은 와이드 문자의 해당 시퀀스와 같습니다. 이러한 두 표현 간의 변환은 표준 C 라이브러리에서 진행됩니다. 원칙적으로 변환 규칙은 `LC_CTYPE` 범주를 변경하는 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 호출에 의해 변경될 수 있습니다. 각 와이드 스트림은 와이드 방향이 될 때 해당 변환 규칙을 결정하고, 나중에 범주 `LC_CTYPE`이 변경되더라도 이러한 규칙을 유지합니다.

와이드 스트림 내의 위치 지정은 텍스트 스트림과 동일한 제한이 적용됩니다. 또한 파일 위치 표시기는 상태 종속적 인코딩을 처리해야 할 수 있습니다. 일반적으로는 여기에는 스트림 내의 바이트 오프셋과 `mbstate_t` 형식의 개체가 모두 포함됩니다. 따라서 와이드 스트림 내에서 파일 위치를 가져오는 믿을 수 있는 유일한 방법은 [fgetpos](../c-runtime-library/reference/fgetpos.md)를 호출하는 것이며, 이 방법으로 획득한 위치를 복원하는 믿을 수 있는 유일한 방법은 [fsetpos](../c-runtime-library/reference/fsetpos.md)를 호출하는 것입니다.

## <a name="see-also"></a>참고 항목

[파일 및 스트림](../c-runtime-library/files-and-streams.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)
