---
description: 자세히 알아보기:/CLRUNMANAGEDCODECHECK (SuppressUnmanagedCodeSecurityAttribute 제거)
title: /CLRUNMANAGEDCODECHECK(SuppressUnmanagedCodeSecurityAttribute 제거)
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.openlocfilehash: e08b7b4b18a463122316b041ad81d6ddd2598bca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182400"
---
# <a name="clrunmanagedcodecheck-remove-suppressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK(SuppressUnmanagedCodeSecurityAttribute 제거)

**/CLRUNMANAGEDCODECHECK** 는 관리 코드로부터 원시 DLL로의 링크 생성 `PInvoke` 호출에 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>를 적용하지 않습니다.

## <a name="syntax"></a>Syntax

> **/CLRUNMANAGEDCODECHECK**[**:NO**]

## <a name="remarks"></a>설명

기본적으로 링커는 **SuppressUnmanagedCodeSecurityAttribute** 를 링커 생성 `PInvoke` 호출에 적용합니다. **/CLRUNMANAGEDCODECHECK** 가 적용되면 **SuppressUnmanagedCodeSecurityAttribute** 가 제거됩니다. **SuppressUnmanagedCodeSecurityAttribute** 호출을 링커 생성 `PInvoke` 호출에 명시적으로 적용하려면 **/CLRUNMANAGEDCODECHECK:NO** 를 사용할 수 있습니다.

링커는 **/clr** 또는 **/clr:pure** 를 사용하여 컴파일된 개체에만 특성을 추가합니다. 그러나 **/clr:pure** 컴파일러 옵션은 Visual Studio 2015에서는 더 이상 사용되지 않으며 Visual Studio 2017 이상에서는 지원되지 않습니다.

`PInvoke` 호출은 링커가 관리되는 호출자로부터의 참조를 만족하는 관리되는 기호를 찾을 수 없으나 해당 참조를 만족하는 원시 기호를 찾을 수 있을 때 링커가 생성됩니다. `PInvoke`에 대한 자세한 내용은 [관리 코드에서 네이티브 함수 호출](../../dotnet/calling-native-functions-from-managed-code.md)을 참조하세요.

코드에서 <xref:System.Security.AllowPartiallyTrustedCallersAttribute>를 사용할 경우 명시적으로 **/CLRUNMANAGEDCODECHECK** 를 설정하여 **SuppressUnmanagedCodeSecurity** 특성을 제거해야 합니다. 이미지가 **SuppressUnmanagedCodeSecurity** 및 **AllowPartiallyTrustedCallers** 특성을 모두 포함할 경우 보안 취약점의 가능성이 있습니다.

**SuppressUnmanagedCodeSecurityAttribute** 사용의 의미에 대한 자세한 정보는 [비관리 코드 사용을 위한 안전한 코딩 지침](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code)을 참조하세요.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 링커 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성** 노드를 확장합니다.

1. **링커** 노드를 확장합니다.

1. **고급** 속성 페이지를 클릭합니다.

1. **CLR 비관리 코드 검사** 속성을 수정합니다.

### <a name="to-set-this-linker-option-programmatically"></a>프로그래밍 방식으로 이 링커 옵션을 설정하려면

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

- [MSVC 링커 참조](linking.md)
- [MSVC 링커 옵션](linker-options.md)
