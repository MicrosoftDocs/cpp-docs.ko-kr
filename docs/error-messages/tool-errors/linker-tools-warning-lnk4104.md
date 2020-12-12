---
description: '자세한 정보: 링커 도구 경고 LNK4104'
title: 링커 도구 경고 LNK4104
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: ab48885a4a8d2806154d3a8911bdc65453359e2c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294433"
---
# <a name="linker-tools-warning-lnk4104"></a>링커 도구 경고 LNK4104

' symbol ' 기호 내보내기는 PRIVATE 이어야 합니다.

는 `symbol` 다음 중 하나일 수 있습니다.

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllGetDocumentation`

- `DllInitialize`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllRegisterServerExW`

- `DllUnload`

- `DllUnregisterServer`

- `RasCustomDeleteEntryNotify`

- `RasCustomDial`

- `RasCustomDialDlg`

- `RasCustomEntryDlg`

이 경고는 DLL에 대 한 가져오기 라이브러리를 빌드하고 모듈 정의 파일에서 전용으로 지정 하지 않고 위의 함수 중 하나를 내보내는 경우에 내보내집니다. 일반적으로 이러한 함수는 OLE 에서만 사용 하도록 내보내집니다. 라이브러리에 연결 된 프로그램이 잘못 된 기능을 호출 하면이를 가져오기 라이브러리에 배치 하면 비정상적인 동작이 발생할 수 있습니다. PRIVATE 키워드에 대 한 자세한 내용은 [내보내기](../../build/reference/exports.md)를 참조 하세요.
