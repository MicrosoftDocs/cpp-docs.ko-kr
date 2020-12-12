---
description: '에 대 한 자세한 정보: MBCS Support in Visual C++'
title: Visual C++에서 MBCS 지원
ms.date: 11/04/2016
helpviewer_keywords:
- tools [C++], MBCS support
- Asian languages [C++]
- Code Editor [C++], MBCS support
- IME [C++]
- Chinese characters [C++]
- Input Method Editor [C++], MBCS
- resource editors [C++], MBCS support
- debugger [C++], MBCS support
- character sets [C++], multibyte
- Japanese characters [C++]
- multibyte characters [C++]
- Kanji character support [C++]
- NMAKE program, MBCS support
- double-byte character sets [C++]
- IME [C++], MBCS
- Input Method Editor [C++]
- MBCS [C++], enabling
ms.assetid: 6179f6b7-bc61-4a48-9267-fb7951223e38
ms.openlocfilehash: f216e381db8111c54f30b2c2fe326f4914024956
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207139"
---
# <a name="mbcs-support-in-visual-c"></a>Visual C++에서 MBCS 지원

MBCS를 사용 하는 Windows 버전에서 실행 하는 경우에는 메모리 창을 제외 하 고 Visual C++ 개발 시스템 (통합 소스 코드 편집기, 디버거 및 명령줄 도구 포함)이 MBCS를 사용 하도록 설정 됩니다.

메모리 창은 바이트를 ANSI 또는 유니코드 문자로 해석할 수 있는 경우에도 바이트의 데이터를 MBCS 문자로 해석 하지 않습니다. ANSI 문자는 항상 1 바이트 크기 이며 유니코드 문자 크기는 2 바이트입니다. MBCS를 사용 하는 경우 문자 크기는 1 또는 2 바이트 이며 사용 중인 코드 페이지에 따라 해석 됩니다. 따라서 메모리 창에서 MBCS 문자를 안정적으로 표시 하기 어렵습니다. 메모리 창에서 문자의 시작 바이트를 알 수 없습니다. 개발자는 메모리 창에서 바이트 값을 확인 하 고 테이블의 값을 조회 하 여 문자 표현을 확인할 수 있습니다. 이는 개발자가 소스 코드를 기반으로 하는 문자열의 시작 주소를 알고 있기 때문에 가능 합니다.

Visual C++는이 작업을 수행 하는 데 적합 한 경우 항상 더블 바이트 문자를 허용 합니다. 여기에는 대화 상자에 있는 경로 이름 및 파일 이름과 Visual C++ 리소스 편집기의 텍스트 항목 (예: 대화 상자 편집기의 정적 텍스트 및 아이콘 편집기의 정적 텍스트 항목)이 포함 됩니다. 또한 전처리기는 문의 파일 이름과 `#include` 및 pragma의 인수로 일부 더블 바이트 지시문을 인식 `code_seg` `data_seg` 합니다. 소스 코드 편집기에서 주석 및 문자열 리터럴의 더블 바이트 문자는 허용 되지만 C/c + + 언어 요소 (예: 변수 이름)에서는 허용 되지 않습니다.

## <a name="support-for-the-input-method-editor-ime"></a><a name="_core_support_for_the_input_method_editor_.28.ime.29"></a> IME (Input Method Editor) 지원

MBCS (예: 일본)를 사용 하는 동아시아 시장 용으로 작성 된 응용 프로그램은 일반적으로 단일 및 더블 바이트 문자를 입력 하기 위해 Windows IME를 지원 합니다. Visual C++ 개발 환경에는 IME에 대 한 완벽 한 지원이 포함 되어 있습니다.

일본어 키보드는 간지 문자를 직접 지원 하지 않습니다. IME는 다른 일본어 알파벳 (로마지, 가타카나 또는 히라가나) 중 하나에 입력 된 윗주 문자열을 가능한 간지 표현으로 변환 합니다. 모호성이 있는 경우 여러 대안에서 선택할 수 있습니다. 원하는 간지 문자를 선택 하면 IME는 `WM_CHAR` 제어 응용 프로그램에 두 개의 메시지를 전달 합니다.

ALT + 키 조합으로 활성화 된 IME는 \` 단추 집합 (표시기) 및 변환 창으로 나타납니다. 응용 프로그램이 텍스트 삽입 지점에 창을 배치 합니다. 응용 프로그램은 `WM_MOVE` `WM_SIZE` 대상 창의 새 위치 또는 크기에 맞게 변환 창의 위치를 조정 하 여 및 메시지를 처리 해야 합니다.

응용 프로그램 사용자가 간지 문자를 입력할 수 있도록 하려면 응용 프로그램에서 Windows IME 메시지를 처리 해야 합니다. IME 프로그래밍에 대 한 자세한 내용은 [입력 방법 관리자](/windows/win32/intl/input-method-manager)를 참조 하세요.

## <a name="visual-c-debugger"></a>Visual C++ 디버거

Visual C++ 디버거는 IME 메시지에 중단점을 설정 하는 기능을 제공 합니다. 또한 메모리 창에 더블 바이트 문자가 표시 될 수도 있습니다.

## <a name="command-line-tools"></a>명령줄 도구

컴파일러, NMAKE 및 리소스 컴파일러 (RC.EXE)를 비롯 한 Visual C++ 명령줄 도구는 MBCS를 사용 합니다. 리소스 컴파일러의/c 옵션을 사용 하 여 응용 프로그램의 리소스를 컴파일할 때 기본 코드 페이지를 변경할 수 있습니다.

소스 코드 컴파일 시간에 기본 로캘을 변경 하려면 [#pragma setlocale](../preprocessor/setlocale.md)을 사용 합니다.

## <a name="graphical-tools"></a>그래픽 도구

Spy + + 및 리소스 편집 도구와 같은 Visual C++ Windows 기반 도구는 IME 문자열을 완벽 하 게 지원 합니다.

## <a name="see-also"></a>참고 항목

[Mbcs (멀티 바이트 문자 집합) 지원](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[MBCS 프로그래밍 팁](../text/mbcs-programming-tips.md)
