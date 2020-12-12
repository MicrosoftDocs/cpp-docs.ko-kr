---
description: '자세한 정보: C 런타임 오류 R6031'
title: C 런타임 오류 R6031
ms.date: 11/04/2016
f1_keywords:
- R6031
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
ms.openlocfilehash: cd3a9e62e4209df5aa232ac9df6b69ce8a63d10a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206619"
---
# <a name="c-runtime-error-r6031"></a>C 런타임 오류 R6031

CRT를 두 번 이상 초기화 하려고 합니다. 이는 응용 프로그램의 버그를 나타냅니다.

> [!NOTE]
> 앱을 실행 하는 동안이 오류 메시지가 표시 되 면 내부 문제가 있기 때문에 앱이 종료 되었습니다. 앱에 버그가 있거나 앱에서 사용 하는 추가 기능 또는 확장의 버그로 인해 버그가 발생할 수 있습니다.
>
> 이 오류를 해결하려면 다음 단계를 시도할 수 있습니다.
>
> - **제어판** 의 **앱 및 기능** 또는 **프로그램 및 기능** 페이지를 사용 하 여 프로그램을 복구 하거나 다시 설치 합니다.
> - **제어판** 의 **앱 및 기능** 또는 **프로그램 및 기능** 페이지를 사용 하 여 앱에서 사용 하는 추가 기능 또는 확장 프로그램을 제거, 복구 또는 다시 설치할 수 있습니다.
> - **제어판** 의 소프트웨어 업데이트에 대 한 **Windows 업데이트** 를 확인 합니다.
> - 앱의 업데이트 된 버전을 확인 합니다. 문제가 지속 되 면 앱 공급 업체에 문의 하세요.

**프로그래머를 위한 정보**

이 진단은 로더 잠금 중 MSIL 명령이 실행 되 고 있음을 나타냅니다. 자세한 내용은 [혼합 어셈블리 초기화](../../dotnet/initialization-of-mixed-assemblies.md)를 참조 하세요.
