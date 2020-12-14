---
description: '자세한 정보: 방법: 전역 어셈블리 캐시에 네이티브 DLL 추가'
title: '방법: 전역 어셈블리 캐시에 네이티브 DLL 추가'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
ms.openlocfilehash: 267bc2f08fdd40da03b71222c48786ab7cc150fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335406"
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>방법: 전역 어셈블리 캐시에 네이티브 DLL 추가

네이티브 DLL (COM 아님)을 전역 어셈블리 캐시에 배치할 수 있습니다.

## <a name="example"></a>예제

**/ASSEMBLYLINKRESOURCE** 를 사용 하면 어셈블리에 네이티브 DLL을 포함할 수 있습니다.

자세한 내용은 [/ASSEMBLYLINKRESOURCE (.NET Framework 리소스에 대 한 링크)](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)를 참조 하세요.

```
/ASSEMBLYLINKRESOURCE:MyComponent.dll
```

## <a name="see-also"></a>참고 항목

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
