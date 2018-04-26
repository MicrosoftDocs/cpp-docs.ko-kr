---
title: 입력-출력 대체 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- I/O [C++], alternatives
ms.assetid: 9f8401c7-d90d-4285-8918-63573df74a80
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 292f47f1431b1c184f972d87ab85c078297822d5
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
---
# <a name="inputoutput-alternatives"></a>입력/출력 대체

Visual C++는 I/O 프로그래밍을 위해 여러 가지 대체 방법을 제공합니다.

- C 런타임 라이브러리 버퍼링되지 않은 직접 I/O

- ANSI C 런타임 라이브러리 스트림 I/O

- 콘솔 및 포트 직접 I/O

- Microsoft Foundation Class 라이브러리

- Microsoft C++ 표준 라이브러리

iostream 클래스는 버퍼링된 서식 있는 텍스트 I/O에 유용합니다. 또한 C++ 프로그래밍 인터페이스가 필요하고 MFC(Microsoft Foundation Class) 라이브러리를 사용하지 않으려는 경우 이진 또는 버퍼링되지 않은 I/O에도 유용합니다. iostream 클래스는 C 런타임 함수 대신 사용되는 개체 지향 I/O입니다.

iostream 클래스는 Microsoft Windows 운영 체제에서 사용할 수 있습니다. 문자열 및 파일 스트림은 제한 없이 작동하지만 문자 모드 스트림 개체 `cin`, `cout`, `cerr` 및 `clog`는 Windows 그래픽 사용자 인터페이스와 일치하지 않습니다. 또한 Windows 환경과 직접 상호 작용하는 사용자 지정 스트림 클래스를 파생시킬 수 있습니다.

## <a name="see-also"></a>참고자료

[스트림이란](../standard-library/what-a-stream-is.md)<br/>
