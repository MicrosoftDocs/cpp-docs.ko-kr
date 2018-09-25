---
title: 웹 클라이언트 응용 프로그램 재배포 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cdde0f8d4edc13e8c1e1a53d8f4393dc7c2dac40
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372472"
---
# <a name="redistributing-web-client-applications"></a>웹 클라이언트 응용 프로그램 재배포

응용 프로그램에서 WebBrowser 컨트롤(예: `CHtmlView` 또는 `CHtmlEditView`)을 구현하는 MFC 클래스를 사용하는 경우, 대상 컴퓨터에 최소한 Microsoft Internet Explorer 4.0 이상이 설치되어 있어야 합니다.

최신 버전의 Internet Explorer를 설치하면 대상 컴퓨터에 최신 공용 컨트롤 파일도 설치됩니다.

최소 Internet Explorer 구성 요소를 설치하는 방법에 대한 정보는 다음 기술 자료 문서에서 제공됩니다.

- Q185375, 방법: Internet Explorer의 단일 EXE 설치 만들기([http://support.microsoft.com/support/kb/articles/q185/3/75.asp](http://support.microsoft.com/support/kb/articles/q185/3/75.asp))

기술 자료 문서는 MSDN 라이브러리 또는 [http://support.microsoft.com](http://support.microsoft.com)에서 찾을 수 있습니다.

## <a name="see-also"></a>참고 항목

[데스크톱 응용 프로그램 배포](../ide/deploying-native-desktop-applications-visual-cpp.md)