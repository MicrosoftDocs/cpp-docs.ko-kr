---
title: 견고성 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 235eafb6fefb644ce5097b07b6cd55d91adf31aa
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
---
# <a name="robustness"></a>견고성

다음 C 런타임 라이브러리 함수를 사용하여 프로그램의 견고성을 높입니다.

## <a name="run-time-robustness-functions"></a>런타임 견고성 함수

|함수|사용|
|--------------|---------|
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|**new** 연산자에서 메모리 할당에 실패하는 경우 오류 처리 메커니즘에 제어를 전달합니다.|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Win32 예외(C 구조적 예외)를 C++ 형식 예외로 처리합니다.|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|[terminate](../c-runtime-library/reference/terminate-crt.md)로 호출하는 자체 종료 함수를 설치합니다.|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|[unexpected](../c-runtime-library/reference/unexpected-crt.md)로 호출하는 자체 종료 함수를 설치합니다.|

## <a name="see-also"></a>참고 항목

[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
 [SetUnhandledExceptionFilter](http://msdn.microsoft.com/library/windows/desktop/ms680634.aspx)<br/>
