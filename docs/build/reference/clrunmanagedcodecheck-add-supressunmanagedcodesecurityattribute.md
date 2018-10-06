---
title: /CLRUNMANAGEDCODECHECK (제거 SuppressUnmanagedCodeSecurityAttribute) | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
dev_langs:
- C++
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9868f0c35f4a988ac8e0aee8076f232f86c04afd
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820927"
---
# <a name="clrunmanagedcodecheck-remove-suppressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (제거 SuppressUnmanagedCodeSecurityAttribute)

**/CLRUNMANAGEDCODECHECK** 링커는 적용 되지 않습니다 지정 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 링커 생성 `PInvoke` 관리 코드에서 네이티브 Dll로 호출 합니다.

## <a name="syntax"></a>구문

> **/CLRUNMANAGEDCODECHECK**[**: NO**]

## <a name="remarks"></a>설명

기본적으로 링커는 다음과 같이 적용 됩니다. 합니다 **SuppressUnmanagedCodeSecurityAttribute** 링커 생성 `PInvoke` 호출 합니다. 때 **/CLRUNMANAGEDCODECHECK** 적용 **SuppressUnmanagedCodeSecurityAttribute** 제거 됩니다. 명시적으로 적용 합니다 **SuppressUnmanagedCodeSecurityAttribute** 링커 생성 `PInvoke` 호출을 사용할 수 **/CLRUNMANAGEDCODECHECK:NO**합니다.

만 링커를 사용 하 여 컴파일된 개체에 특성을 추가 **/clr** 하거나 **/clr: pure**합니다. 그러나 합니다 **/clr: pure** 컴파일러 옵션은 Visual Studio 2015에서 더 이상 Visual Studio 2017에서 지원 되지 않는 합니다.

`PInvoke` 호출은 관리 되는 호출자에서 참조를 충족 하기 위해 관리 되는 기호를 찾을 수 없지만 해당 참조를 충족 하기 위해 네이티브 기호를 찾을 수 있습니다 하는 경우 링커에 의해 생성 됩니다. 에 대 한 자세한 내용은 `PInvoke`를 참조 하세요 [관리 코드에서 네이티브 함수 호출](../../dotnet/calling-native-functions-from-managed-code.md)합니다.

사용 하는 경우 사용자에 게 유의 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 코드를 명시적으로 설정 해야 **/CLRUNMANAGEDCODECHECK** 제거 하는 **SuppressUnmanagedCodeSecurity** 특성입니다. 이미지 모두를 포함 하는 경우 잠재적인 보안 취약점으로 인 한 것은 **SuppressUnmanagedCodeSecurity** 하 고 **AllowPartiallyTrustedCallers** 특성입니다.

참조 [보안 코딩 지침 비관리 코드에 대 한](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code) 사용의 의미에 대 한 자세한 내용은 **SuppressUnmanagedCodeSecurityAttribute**합니다.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. **구성 속성** 노드를 확장합니다.

1. 확장 된 **링커** 노드.

1. 선택 된 **고급** 속성 페이지.

1. 수정 된 **CLR 비관리 코드 검사** 속성입니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>을 참조하세요.

## <a name="see-also"></a>참고자료

- [링커 옵션 설정](../../build/reference/setting-linker-options.md)
- [링커 옵션](../../build/reference/linker-options.md)
