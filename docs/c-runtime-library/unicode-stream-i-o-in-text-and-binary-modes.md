---
title: 텍스트 및 이진 모드의 유니코드 스트림 I/O | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e3b2a4d82a07a719bdbd0308727a4fd3b26a867e
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>텍스트 및 이진 모드의 유니코드 스트림 I/O

텍스트 모드(기본값)로 열린 파일에서 유니코드 스트림 I/O 루틴(예: **fwprintf**, **fwscanf**, **fgetwc**, **fputwc**, **fgetws** 또는 **fputws**)이 작동하는 경우 두 가지 종류의 문자 변환이 수행됩니다.

- 유니코드에서 MBCS로 또는 MBCS에서 유니코드로의 변환. 유니코드 스트림 I/O 함수를 텍스트 모드에서 사용할 경우 원본 또는 대상 스트림은 멀티바이트 문자 시퀀스로 간주됩니다. 따라서 유니코드 스트림 입력 함수는 **mbtowc** 함수 호출과 마찬가지로 멀티바이트 문자를 와이드 문자로 변환합니다. 동일한 이유로 유니코드 스트림 출력 함수는 **wctomb** 함수 호출과 마찬가지로 와이드 문자를 멀티바이트 문자로 변환합니다.

- 캐리지 리턴 - 줄 바꿈(CR-LF) 변환. 이 변환은 MBCS에서 유니코드로 변환(유니코드 스트림 입력 함수) 전 및 유니코드에서 MBCS로 변환(유니코드 스트림 출력 함수) 이후에 발생합니다. 입력하는 동안 각 캐리지 리턴 - 줄 바꿈 조합은 단일 줄 바꿈 문자로 변환됩니다. 출력하는 동안 각 줄 바꿈 문자는 캐리지 리턴 - 줄 바꿈 조합으로 변환됩니다.

그러나 유니코드 스트림 I/O 함수가 이진 모드에서 작동하는 경우 파일은 유니코드로 간주되며 입력 또는 출력하는 동안 CR-LF 변환 또는 문자 변환이 발생합니다. 유니코드 텍스트 파일에서 wcin을 올바르게 사용하려면 _setmode( _fileno( stdin ), _O_BINARY );를 사용하십시오.

## <a name="see-also"></a>참고 항목

[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
[입력 및 출력](../c-runtime-library/input-and-output.md)<br/>
