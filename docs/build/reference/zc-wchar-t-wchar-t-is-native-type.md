---
description: '자세한 정보:/Zc: wchar_t (wchar_t 네이티브 형식)'
title: /Zc:wchar_t(wchar_t를 네이티브 형식으로 인식)
ms.date: 03/01/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
ms.openlocfilehash: 3dc826bf60c760f45464bcab73dc5fcb79edc3cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178903"
---
# <a name="zcwchar_t-wchar_t-is-native-type"></a>/Zc:wchar_t(wchar_t를 네이티브 형식으로 인식)

**`wchar_t`** C + + 표준에 따라 기본 제공 형식으로 구문 분석 합니다.

## <a name="syntax"></a>Syntax

> **/Zc: wchar_t**[ **-** ]

## <a name="remarks"></a>설명

**/Zc: wchar_t** 이 on 인 경우 **`wchar_t`** 는 c + +로 컴파일된 코드에서 기본 제공 정수 형식에 대 한 키워드입니다. **/Zc: wchar_t-** (빼기 기호 포함)을 지정 하거나 C로 컴파일된 코드에서 **`wchar_t`** 기본 제공 형식이 아닙니다. 대신 **`wchar_t`** 는 **`typedef`** **`unsigned short`** 정식 헤더 stddef. h에서에 대해로 정의 됩니다. Microsoft 구현에서는이를 다른 헤더에서 정의 합니다. 여기에는 stddef와 기타 표준 헤더가 포함 되어 있습니다.

**/Zc: wchar_t** 을 권장 하지 않습니다. c + + 표준에는 **`wchar_t`** 기본 제공 형식이 필요 하기 때문입니다. 버전을 사용 하면 **`typedef`** 이식성 문제가 발생할 수 있습니다. 이전 버전의 Visual Studio에서 업그레이드 하 고 코드가를로 암시적으로 변환 하려고 하기 때문에 컴파일러 오류 [c 2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) 발생 하는 경우 **`wchar_t`** **`unsigned short`** **/zc: wchar_t-** 를 설정 하는 대신 오류를 수정 하는 코드를 변경 하는 것이 좋습니다.

**/Zc: wchar_t** 옵션은 c + + 컴파일에 기본적으로 설정 되어 있으며 c 컴파일에서는 무시 됩니다. [/Permissive-](permissive-standards-conformance.md) 옵션은 **/zc: wchar_t** 에 영향을 주지 않습니다.

Microsoft **`wchar_t`** 는 부호 없는 2 바이트 값으로를 구현 합니다. Microsoft 전용 네이티브 형식에 매핑됩니다 **`__wchar_t`** . 에 대 한 자세한 내용은 **`wchar_t`** [데이터 형식 범위](../../cpp/data-type-ranges.md) 및 [기본 형식](../../cpp/fundamental-types-cpp.md)을 참조 하세요.

버전을 사용 하는 이전 코드와 상호 운용 해야 하는 새 코드를 작성 하는 경우 **`typedef`** **`wchar_t`** 의 및 변형에 대 한 오버 로드를 제공 하 여 **`unsigned short`** **`__wchar_t`** 코드를 **`wchar_t`** **/zc: wchar_t** 을 사용 하 여 컴파일된 코드에 연결 하거나 코드를 사용 하지 않고 컴파일할 수 있습니다. 그렇지 않으면 라이브러리의 서로 다른 두 빌드를 제공 해야 합니다. 하나는 **/zc: wchar_t** 을 사용 하지 않고 하나씩 사용 합니다. 그러나 이 경우 새 코드를 컴파일하는 데 사용하는 것과 같은 컴파일러를 사용하여 이전 코드를 빌드하는 것이 좋습니다. 다른 컴파일러로 컴파일된 이진 파일을 혼합해서는 안 됩니다.

**/Zc: wchar_t** 을 지정 하면 **\_ wchar \_ t가 \_ 정의** 되 고 **\_ 네이티브 \_ wchar \_ t \_ 정의** 된 기호가 정의 됩니다. 자세한 내용은 [Predefined Macros](../../preprocessor/predefined-macros.md)을 참조하세요.

코드에서 컴파일러 COM 전역 함수를 사용 하는 경우 ( **/zc: wchar_t** 는 현재 기본적으로 설정 되어 있으므로 [주석 pragma](../../preprocessor/comment-c-cpp.md) 또는 명령줄에서) comsupp.lib에 대 한 명시적 참조를 변경 하는 것이 좋습니다. **/Zc: wchar_t-** 를 사용 하 여 컴파일해야 하는 경우 comsupp.lib를 사용 합니다. Comdef 헤더 파일을 포함 하는 경우 올바른 라이브러리가 지정 됩니다. 컴파일러 COM 지원에 대 한 자세한 내용은 [컴파일러 Com 지원](../../cpp/compiler-com-support.md)을 참조 하세요.

**`wchar_t`** C 코드를 컴파일할 때는 기본 제공 형식이 지원 되지 않습니다. Visual C++의 규칙 문제에 대 한 자세한 내용은 [비표준 동작](../../cpp/nonstandard-behavior.md)을 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **언어** 페이지를 선택 합니다.

1. Wchar_t를 **기본 제공 형식으로 처리** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/Zc(규칙)](zc-conformance.md)<br/>
