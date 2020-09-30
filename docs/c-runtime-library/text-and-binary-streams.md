---
title: 텍스트 및 이진 스트림
description: Microsoft C 런타임 라이브러리의 텍스트 및 이진 스트림 설명입니다.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- binary streams
- text streams
ms.assetid: 57035e4a-955d-4e04-a560-fcf67ce68b4e
ms.openlocfilehash: 522e4d5f119e4415694b59b2b08141a45f06fe5a
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589616"
---
# <a name="text-and-binary-streams"></a>텍스트 및 이진 스트림

텍스트 스트림은 읽을 수 있도록 텍스트 기반 표시에 쓸 수 있는 하나 이상의 텍스트 줄로 구성됩니다. 텍스트 스트림을 읽을 때 프로그램은 각 줄의 끝에서 `NL`(줄 바꿈)을 읽습니다. 텍스트 스트림에 쓸 때 프로그램은 줄의 끝을 알리기 위해 `NL`을 씁니다. 파일의 텍스트를 표현하도록 대상 환경의 서로 다른 규칙을 일치시키기 위해 라이브러리 함수가 프로그램과 텍스트 스트림 간에 전송된 문자의 수와 표현을 변경할 수 있습니다.

텍스트 스트림 내에서의 위치 지정이 제한 됩니다. [fgetpos](../c-runtime-library/reference/fgetpos.md) 또는 [ftell](../c-runtime-library/reference/ftell-ftelli64.md)을 호출하여 현재 파일 위치 표시기를 얻을 수 있습니다. [fsetpos](../c-runtime-library/reference/fsetpos.md) 또는 [fseek](../c-runtime-library/reference/fseek-fseeki64.md)를 호출하여 이런 방법으로 얻은 위치 또는 스트림의 처음이나 끝에 텍스트 스트림을 배치할 수 있습니다. 다른 위치 변경은 지원되지 않습니다.

최대 이식성을 위해 프로그램은 다음을 쓰지 않아야 합니다.

- 빈 파일
- 줄 끝의 공백 문자
- 줄의 일부(파일 끝의 `NL` 생략)
- 인쇄 가능한 문자, NL 및 `HT`(가로 탭) 이외의 문자

이러한 규칙을 따르는 경우 텍스트 스트림에서 읽는 문자의 시퀀스(바이트 또는 멀티바이트 문자)는 파일을 만들 때 텍스트 스트림에 쓴 문자의 시퀀스와 일치합니다. 그렇지 않으면 파일을 닫을 때 파일이 비어 있는 경우 라이브러리 함수가 파일을 제거할 수 있습니다. 또는 파일에 쓴 문자를 삭제하거나 변경할 수 있습니다.

이진 스트림은 하나 이상의 바이트의 임의 정보로 구성됩니다. 임의 개체에 저장된 값을 이진 스트림(바이트 기반)에 쓰고 이때 개체에 저장된 내용을 정확하게 읽을 수 있습니다. 라이브러리 함수는 프로그램과 이진 스트림 사이에서 전송 하는 바이트를 변경 하지 않습니다. 그러나 `NULL` 이진 스트림으로 작성 하는 파일에 임의 바이트 수를 추가할 수 있습니다. 프로그램은 `NULL` 이진 스트림 끝에서 이러한 추가 바이트를 처리 해야 합니다.

스트림의 끝을 기준으로 위치를 지정 하는 경우를 제외 하 고 이진 스트림 내에서의 위치 지정은 잘 정의 되어 있습니다. 텍스트 스트림과 동일하게 현재 파일 위치 표시기를 얻고 변경할 수 있습니다. 스트림의 시작 부분에서 [ftell](../c-runtime-library/reference/ftell-ftelli64.md) 및 [ftell](../c-runtime-library/reference/fseek-fseeki64.md) 수 바이트 (바이트 0)로 사용 되는 오프셋 이므로 이러한 오프셋의 정수 연산은 예측 가능한 결과를 생성 합니다.

바이트 스트림은 파일을 바이트의 시퀀스로 처리합니다. 프로그램에서 스트림은 위에 설명된 변경을 제외하고는 바이트 시퀀스와 같습니다.

## <a name="see-also"></a>참고 항목

[파일 및 스트림](../c-runtime-library/files-and-streams.md)
