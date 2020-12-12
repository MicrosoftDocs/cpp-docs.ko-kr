---
description: 자세한 내용은 Command-Line Error D8016을 (를) 확인 하세요.
title: 명령줄 오류 D8016
ms.date: 11/04/2016
f1_keywords:
- D8016
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
ms.openlocfilehash: 2f340cb7574177536310343dc9761058b7b9bc08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115718"
---
# <a name="command-line-error-d8016"></a>명령줄 오류 D8016

' 옵션 1 마이그레이션 ' 및 ' 옵션 2 마이그레이션 ' 명령줄 옵션이 호환 되지 않습니다.

명령줄 옵션은 함께 지정할 수 없습니다.

옵션 사양에 대해 CL과 같은 환경 변수를 확인 합니다.

**/clr** 은 **/eha** 를 암시 하며, **/clr** 을 사용 하 여 다른 **/seh** 컴파일러 옵션을 지정할 수 없습니다. 자세한 내용은 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)를 참조 하세요.

Visual C++ 6.0 프로젝트를 업데이트 한 후에 D8016 될 수 있습니다. 프로젝트 업데이트 마법사 프로세스는 프로젝트의 각 소스 코드 파일에 대해 **/rtc** 를 사용 하도록 설정할 수 있습니다. 그러면 프로젝트의 **/rtc** 설정이 재정의 됩니다.  이 문제를 해결 하려면 프로젝트의 각 소스 코드 파일에 대 한 **/rtc** 설정을 기본 설정으로 변경 합니다. 즉, 각 파일에 대해 **/rtc** 의 프로젝트 설정이 적용 됩니다.

**/Rtc** 속성 설정을 변경 하는 방법에 대 한 자세한 내용은 [/Rtc (런타임 오류 검사)](../../build/reference/rtc-run-time-error-checks.md) 를 참조 하세요.
