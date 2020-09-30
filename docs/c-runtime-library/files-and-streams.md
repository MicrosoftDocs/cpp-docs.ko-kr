---
title: 파일 및 스트림
description: Microsoft C 런타임 라이브러리의 파일 및 스트림에 대 한 개요입니다.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files [C++]
- streams
ms.assetid: f61e712b-eac9-4c28-bb18-97c3786ef387
ms.openlocfilehash: 39133cfdb4784c42561a159d6d176bcbd23644af
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589967"
---
# <a name="files-and-streams"></a>파일 및 스트림

프로그램은 파일을 읽고 써서 대상 환경과 통신합니다. 파일은 다음일 수 있습니다.

- 반복적으로 읽고 쓸 수 있는 데이터 집합

- 프로그램에 의해 생성되는 바이트 스트림(예: 파이프라인)

- 주변 디바이스와 주고받은 바이트 스트림

마지막 두 항목은 대화형 파일입니다. 파일은 일반적으로 프로그램과 상호 작용하기 위한 주요 수단입니다. 이러한 모든 종류의 파일은 거의 동일한 방법(라이브러리 함수 호출)으로 조작합니다. 이러한 함수 대부분을 선언할 때는 표준 헤더 STDIO.H를 포함합니다.

파일에 대해 작업을 수행하려면 많은 경우 먼저 파일을 열어야 합니다. 파일을 열면 해당 파일이 스트림과 연결됩니다. 스트림은 다양한 종류의 파일 간에 존재하는 많은 차이점에 주석을 다는 표준 C 라이브러리 내 데이터 구조입니다. 라이브러리는 FILE 형식의 개체에 각 스트림의 상태를 유지합니다.

대상 환경은 프로그램을 시작하기 전에 세 가지 파일을 엽니다. 두 가지 인수를 사용하여 라이브러리 함수 [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)을 호출하면 파일을 열 수 있습니다. 함수는 `fopen` 더 이상 사용 되지 않습니다. 대신 [fopen_s를 사용 _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) .) 첫 번째 인수는 파일 이름입니다. 두 번째 인수는 다음을 지정하는 C 문자열입니다.

- 파일에서 데이터를 읽을 계획인지, 파일에 데이터를 쓸 계획인지, 아니면 두 작업을 모두 수행할 계획인지 여부

- 파일에 대해 새 콘텐츠를 생성하거나 파일이 아직 없는 경우 파일을 만들 계획인지, 아니면 기존 콘텐츠를 제자리에 둘 것인지 여부

- 파일에 쓸 때 기존 콘텐츠가 변경될 수 있는지, 아니면 파일의 끝에 바이트를 추가만 할지 여부

- 텍스트 스트림을 조작할지, 아니면 이진 스트림을 조작할지 여부

파일이 열리면 스트림이 바이트 지향(바이트 스트림)인지, 아니면 와이드 지향(와이드 스트림)인지 확인할 수 있습니다. 스트림은 처음에 바인딩되어 있지 않습니다. 스트림에 대해 특정 함수를 호출하면 바이트 지향 스트림이 되고 다른 특정 함수를 호출하면 와이드 지향 스트림이 됩니다. 설정된 후에는 [fclose](../c-runtime-library/reference/fclose-fcloseall.md) 또는 [freopen](../c-runtime-library/reference/freopen-wfreopen.md)을 호출하여 닫힐 때까지 스트림이 자신의 성향을 유지합니다.

© 1989-2001. 작성: P.J. Plauger 및 Jim Brodie. All rights reserved.

## <a name="see-also"></a>참고 항목

[텍스트 및 이진 스트림](../c-runtime-library/text-and-binary-streams.md)<br/>
[바이트 및 와이드 스트림](../c-runtime-library/byte-and-wide-streams.md)<br/>
[스트림 제어](../c-runtime-library/controlling-streams.md)<br/>
[스트림 상태](../c-runtime-library/stream-states.md)
