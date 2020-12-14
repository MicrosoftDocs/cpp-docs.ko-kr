---
description: 다음에 대해 자세히 알아보세요. `process`
title: 프로세스
ms.date: 11/04/2016
f1_keywords:
- process_cpp
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
ms.openlocfilehash: ea5baee65b3375e062939f49bc30f3780c312852
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198599"
---
# `process`

프로세스의 모든 애플리케이션 도메인에서 공유되는 특정 전역 변수, 정적 멤버 변수 또는 정적 지역 변수의 단일 복사본이 관리되는 애플리케이션 프로세스에 있어야 함을 지정합니다. 이는 **`/clr:pure`** Visual studio 2015에서 더 이상 사용 되지 않으며 Visual studio 2017에서 지원 되지 않는로 컴파일할 때 주로 사용 됩니다. 를 사용 하 여 컴파일할 때 **`/clr`** 전역 및 정적 변수는 기본적으로 프로세스별 이며를 사용할 필요가 없습니다 **`__declspec(process)`** .

전역 변수, 정적 멤버 변수 또는 네이티브 형식의 정적 지역 변수만로 표시할 수 있습니다 **`__declspec(process)`** .

**`process`** 는로 컴파일하는 경우에만 유효 [`/clr`](../build/reference/clr-common-language-runtime-compilation.md) 합니다.

각 응용 프로그램 도메인에 전역 변수의 자체 복사본을 포함 하려면 [appdomain](../cpp/appdomain.md)을 사용 합니다.

자세한 내용은 [응용 프로그램 도메인 및 Visual C++](../dotnet/application-domains-and-visual-cpp.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[`__declspec`](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)
