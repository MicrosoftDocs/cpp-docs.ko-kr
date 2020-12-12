---
description: 자세한 정보:/ZW (Windows 런타임 컴파일)
title: /ZW(Windows Runtime 컴파일)
ms.date: 04/08/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.CompileAsWinRT
- /zw
helpviewer_keywords:
- /ZW
- -ZW compiler option
- /ZW compiler option
- -ZW
- Windows Runtime compiler option
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
ms.openlocfilehash: b2c39cdfb3f1d22d12c8d07b1e844c550a7a0e3a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273919"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW(Windows Runtime 컴파일)

UWP (유니버설 Windows 플랫폼) 앱을 만들기 위해 Microsoft c + + 구성 요소 확장 c + +/CX를 지원 하도록 소스 코드를 컴파일합니다.

**/Zw** 를 사용 하 여 컴파일하는 경우에는 항상 **/ehsc** 도 지정 해야 합니다.

## <a name="syntax"></a>구문

```cpp
/ZW /EHsc
/ZW:nostdlib /EHsc
```

## <a name="arguments"></a>인수

**nostdlib**<br/>
Platform.winmd, Windows.Foundation.winmd 및 기타 기본 Windows 메타데이터(.winmd) 파일이 컴파일에 자동으로 포함되지 않음을 나타냅니다. 대신 [/fu (강제 #using 파일 이름 지정)](fu-name-forced-hash-using-file.md) 컴파일러 옵션을 사용 하 여 Windows 메타 데이터 파일을 명시적으로 지정 해야 합니다.

## <a name="remarks"></a>설명

**/Zw** 옵션을 지정 하면 컴파일러는 다음 기능을 지원 합니다.

- 앱이 Windows 런타임에서 실행 하는 데 필요한 메타 데이터 파일, 네임 스페이스, 데이터 형식 및 함수입니다.

- 자동 참조-개체의 참조 횟수가 0이 될 때 개체의 자동 삭제와 Windows 런타임 개체의 수를 계산 합니다.

증분 링커는 **/zw** 옵션을 사용 하 여 .obj 파일에 포함 된 Windows 메타 데이터를 지원 하지 않으므로 사용 되지 않는 [/Gm (최소 다시 빌드 사용)](gm-enable-minimal-rebuild.md) 옵션은 **/zw** 와 호환 되지 않습니다.

자세한 내용은 [Visual C++ 언어 참조](../../cppcx/visual-c-language-reference-c-cx.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
