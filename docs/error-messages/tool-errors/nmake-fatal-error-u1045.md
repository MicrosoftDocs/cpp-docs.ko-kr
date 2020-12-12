---
description: '자세한 정보: NMAKE 심각한 오류 U1045'
title: NMAKE 심각한 오류 U1045
ms.date: 08/11/2019
f1_keywords:
- U1045
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
ms.openlocfilehash: 722525d917b7511dfe2294adf2e796efd3078913
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322897"
---
# <a name="nmake-fatal-error-u1045"></a>NMAKE 심각한 오류 U1045

> 생성 실패: *메시지*

NMAKE에 의해 호출 된 프로그램 또는 명령이 *메시지* 의 이유로 실패 했습니다. NMAKE가 컴파일러나 링커 등의 다른 프로그램을 호출 하면 호출이 실패할 수 있습니다. 또는 호출 된 프로그램에서 오류를 반환할 수 있습니다. 이 메시지는 오류를 보고하는 데 사용됩니다.

이 문제를 해결하려면 먼저 오류의 원인을 확인합니다. NMAKE [/n](../../build/reference/running-nmake.md#nmake-options) 옵션을 통해 보고 된 명령을 사용 하 여 환경 설정을 확인 하 고 명령줄에서 nmake에 의해 수행 된 작업을 반복할 수 있습니다.
