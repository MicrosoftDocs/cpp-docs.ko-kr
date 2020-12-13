---
description: '자세한 정보: 링커 도구 경고 LNK4210'
title: 링커 도구 경고 LNK4210
ms.date: 11/04/2016
f1_keywords:
- LNK4210
helpviewer_keywords:
- LNK4210
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
ms.openlocfilehash: 7634952df026dc664aed2a2f9625a7380b3a38b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150607"
---
# <a name="linker-tools-warning-lnk4210"></a>링커 도구 경고 LNK4210

> 섹션 *섹션이* 있습니다. 처리 되지 않은 정적 이니셜라이저 또는 종결자가 있을 수 있습니다.

## <a name="remarks"></a>설명

일부 코드는 정적 이니셜라이저 또는 종결자를 도입 했지만 응용 프로그램이 시작 될 때 VCRuntime 라이브러리 시작 코드 또는이에 해당 하는 항목 (정적 이니셜라이저 또는 종결자를 실행 해야 함)이 실행 되지 않습니다. 다음은 정적 이니셜라이저가 나 종결자가 필요한 코드의 몇 가지 예입니다.

- 생성자, 소멸자 또는 가상 함수 테이블이 포함 된 전역 클래스 변수입니다.

- 비 컴파일 시간 상수로 초기화 된 전역 변수입니다.

이 문제를 해결 하려면 다음 중 하나를 수행 합니다.

- 정적 이니셜라이저가 있는 모든 코드를 제거 합니다.

- [/NOENTRY](../../build/reference/noentry-no-entry-point.md)를 사용 하지 마세요. /NOENTRY를 제거한 후에는 링커 명령줄에서 [/nodefaultlib](../../build/reference/nodefaultlib-ignore-libraries.md) 를 제거 해야 할 수도 있습니다.

- 빌드에서/MT를 사용 하는 경우 링커 명령줄에 libcmt.lib, 라이브러리 라이브러리 및 li를 추가 합니다. 빌드에서/MTd를 사용 하는 경우 libcmtd.lib, vcruntimed 및 li를 추가 합니다.

- /Clr: pure 컴파일에서/clr로 이동 하는 경우 링커 줄에서 [/entry](../../build/reference/entry-entry-point-symbol.md) 옵션을 제거 합니다. 이를 통해 CRT 초기화를 사용할 수 있으며 응용 프로그램 시작 시 정적 이니셜라이저가 실행 될 수 있습니다. **/Clr: pure** 컴파일러 옵션은 visual studio 2015에서는 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

[/Gs](../../build/reference/gs-buffer-security-check.md) 컴파일러 옵션은 함수에의 한 초기화가 필요 합니다 `__security_init_cookie` . 이 초기화는에서 실행 되는 VCRuntime 라이브러리 시작 코드에서 기본적으로 제공 됩니다 `_DllMainCRTStartup` .

- 프로젝트를/ENTRY를 사용 하 여 빌드하고/ENTRY가 이외의 함수를 전달 하는 경우 `_DllMainCRTStartup` 함수는를 호출 하 여 CRT를 초기화 해야 합니다 `_CRT_INIT` . DLL에서/GS를 사용 하거나, 정적 이니셜라이저가 필요 하거나, MFC 또는 ATL 코드의 컨텍스트에서를 호출 하는 경우에는이 호출 만으로는 충분 하지 않습니다. 자세한 내용은 [dll 및 Visual C++ 런타임 라이브러리 동작](../../build/run-time-library-behavior.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

- [링커 옵션 설정](../../build/reference/linking.md)
