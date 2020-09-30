---
title: 스트림 제어
description: Microsoft C 런타임 라이브러리의 스트림 사용에 대 한 개요입니다.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Controlling Streams
helpviewer_keywords:
- streams, controlling
- controlling streams
- streams
ms.assetid: 267e9013-9afc-45f6-91e3-ca093230d9d9
ms.openlocfilehash: 0caa9eca7c960acbb581358c1a92afcc6a8af066
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589720"
---
# <a name="controlling-streams"></a>스트림 제어

[fopen](../c-runtime-library/reference/fopen-wfopen.md)은 형식이 `FILE`인 개체의 주소를 반환합니다. 이 주소를 여러 라이브러리 함수에 대한 `stream` 인수로 사용하여 열려 있는 파일에 대한 다양한 작업을 수행합니다. 바이트 스트림의 경우 [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md)를 호출하여 각 문자를 읽는 것처럼 모든 입력이 수행되고 [fputc](../c-runtime-library/reference/fputc-fputwc.md)를 호출하여 각 문자를 쓰는 것처럼 모든 출력이 수행됩니다. 와이드 스트림의 경우 [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)를 호출하여 각 문자를 읽는 것처럼 모든 입력이 수행되고 [fputwc](../c-runtime-library/reference/fputc-fputwc.md)를 호출하여 각 문자를 쓰는 것처럼 모든 출력이 수행됩니다.

[fclose](../c-runtime-library/reference/fclose-fcloseall.md)를 호출하여 파일을 닫을 수 있으며 이후 `FILE` 개체의 주소가 잘못됩니다.

`FILE` 개체는 다음과 같이 스트림의 상태를 저장합니다.

- 오류 표시기는 읽기 또는 쓰기 오류를 발견한 함수에 의해 0이 아닌 값으로 설정됩니다.

- 파일 끝 표시기는 읽는 동안 파일 끝을 발견한 함수에 의해 0이 아닌 값으로 설정됩니다.

- 파일에서 위치 지정 요청을 지원할 수 있는 경우 파일 위치 표시기는 읽거나 쓸 스트림의 다음 바이트를 지정합니다.

- [스트림 상태](../c-runtime-library/stream-states.md)는 스트림이 읽기 및/또는 쓰기를 허용할지 여부 및 스트림이 바인딩 해제되었는지, 바이트 지향인지, 와이드 지향인지를 지정합니다.

- 변환 상태는 부분적으로 어셈블되거나 생성된 일반화 멀티바이트 문자의 상태는 물론 파일의 바이트 시퀀스에 대한 이동 상태도 기억합니다.

- 파일 버퍼는 라이브러리 함수가 스트림에 대한 읽기 및 쓰기 작업의 성능을 향상시키는 데 사용할 수 있는 배열 개체의 주소 및 크기를 지정합니다.

`FILE` 개체 또는 해당 개체와 함께 사용하기 위해 지정하는 파일 버퍼에 저장된 값을 변경하지 마십시오. `FILE` 개체를 복사하고 간단하게 해당 복사본의 주소를 라이브러리 함수에 대한 `stream` 인수로 사용할 수 없습니다.

## <a name="see-also"></a>참고 항목

[파일 및 스트림](../c-runtime-library/files-and-streams.md)
