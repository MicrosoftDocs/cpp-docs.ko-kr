---
title: 프로그램 (c + +) 내에서 버전 정보에 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 18622333-d9e8-4309-9465-677cd10c79b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b9340ffc4e951a08b77ce44afd6666d8b3a94db9
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315264"
---
# <a name="accessing-version-information-from-within-your-program-c"></a>프로그램 (c + +) 내에서 버전 정보 액세스

### <a name="to-access-version-information-from-within-your-program"></a>프로그램 내에서 버전 정보에 액세스하려면

1. 프로그램 내에서 버전 정보에 액세스 하려는 경우 사용 합니다 [GetFileVersionInfo](/windows/desktop/api/winver/nf-winver-getfileversioninfoa) 함수는 [VerQueryValue](/windows/desktop/api/winver/nf-winver-verqueryvaluea) 함수입니다.

관리 되는 프로젝트에 리소스를 추가 하는 방법에 대 한 정보를 참조 하세요 [데스크톱 앱의 리소스](/dotnet/framework/resources/index) 에 *.NET Framework Developer's Guide*합니다. 수동으로 관리 되는 프로젝트에 리소스 파일을 추가, 리소스 액세스, 정적 리소스 표시 및 속성에 리소스 문자열 할당에 대 한 내용은 참조 하세요 [데스크톱 앱에 대 한 리소스 파일 만들기](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)합니다. 전역화 및 지역화 관리 되는 앱의 리소스에 대 한 내용은 참조 하세요 [Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[버전 정보 편집기](../windows/version-information-editor.md)  
[버전 정보 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)