---
title: ConnectionManager 참조
description: 명령줄 도구에서 원격 SSH 연결을 관리하는 방법
ms.date: 10/7/2020
f1_keywords:
- ConnectionManager
helpviewer_keywords:
- ConnectionManager program
ms.openlocfilehash: 2f38fec21e7526fa214db811b00fc545504f0610
ms.sourcegitcommit: 611e903f222ec794ef14195796b332851ab98904
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91847140"
---
# <a name="connectionmanager-reference"></a>ConnectionManager 참조

::: moniker range="<=vs-2017"

ConnectionManager.exe는 Visual Studio 2019 버전 16.5 이상에서 사용할 수 있습니다.

::: moniker-end

::: moniker range="vs-2019"

ConnectionManager.exe는 Visual Studio 외부에서 원격 개발 연결을 관리하는 명령줄 유틸리티입니다. 새 개발 컴퓨터를 프로비저닝하는 등의 작업에 유용합니다. 또는 연속 통합을 위해 Visual Studio를 설정하는 데 사용할 수 있습니다.개발자 명령 프롬프트 창에서 사용할 수 있습니다. 개발자 명령 프롬프트에 대한 자세한 내용은 [명령줄에서 Microsoft C++ 도구 세트 사용](../build/building-on-the-command-line.md)을 참조하세요.

ConnectionManager.exe는 Visual Studio 2019 버전 16.5 이상에서 사용할 수 있습니다. Visual Studio 설치 관리자의 **C++를 사용한 Linux 개발** 워크로드의 일부입니다. 설치 관리자에서 **연결 관리자** 구성 요소를 선택하는 경우에도 자동으로 설치됩니다. *% VCIDEInstallDir%\\Linux\\bin\\ConnectionManagerExe\\ConnectionManager.exe* 에 설치됩니다.

ConnectionManager.exe의 기능은 Visual Studio에서도 사용할 수 있습니다. IDE에서 원격 개발 연결을 관리하려면 메뉴 모음에서 **도구** > **옵션** 을 선택하여 옵션 대화 상자를 엽니다. 옵션 대화 상자에서 **플랫폼 간** > **연결 관리자** 를 선택합니다.

## <a name="syntax"></a>구문

> **`ConnectionManager.exe`** *command* \[*arguments* ] \[*options* ]

### <a name="commands-and-arguments"></a>명령 및 인수

- **`add`** *user\@host* \[ **`--port`** *port* ] \[ **`--password`** *password* ] \[ **`--privatekey`** *privatekey_file* ]

  새 연결을 인증하고 추가합니다. 기본적으로 포트 22 및 암호 인증을 사용합니다. (암호를 입력하라는 메시지가 표시됩니다.) **-`-password`** 및 **`--privatekey`** 를 모두 사용하여 프라이빗 키의 암호를 지정합니다.

- **`remove`** \[*connection_id* \| *user\@host* \[ **`--port`** *port* ]]

  연결을 제거합니다. 인수를 지정하지 않으면 제거할 연결을 지정하라는 메시지가 표시됩니다.
  
- **`modify`** \[*default* \| *connection_id* \| *user\@host* \[ **`--port`** *port* ]] \[ **`--property`** *key=value* ]

  연결의 속성을 정의하거나 수정합니다.\
  *value* 가 비어 있는 경우 *key* 속성이 삭제됩니다.\
  인증에 실패하면 변경 내용이 적용되지 않습니다.\
  연결을 지정하지 않은(위에서 *default* 의 의미) 경우 사용자의 기본 원격 연결이 사용됩니다.

- **`remove-all`**

  저장된 연결을 모두 제거합니다.
  
- **`clean`**

  더 이상 존재하지 않는 연결의 헤더 캐시를 삭제합니다. 

- **`list`** \[**`--properties`** ]

  저장된 모든 연결의 정보와 ID 및 속성을 표시합니다. 

- **`help`**

  도움말 화면을 표시합니다.

- **`version`**

  버전 정보를 표시합니다.

### <a name="options"></a>옵션

- **`-q`** , **`--quiet`**

  `stdout` 또는 `stderr` 출력을 방지합니다.

- **`--no-prompt`**

  적절한 경우 메시지 표시 대신 실패입니다.

- **`--no-verify`**

  인증 없이 연결을 추가하거나 수정합니다.

- **`--file`** *filename*

  제공된 *파일 이름* 에서 연결 정보를 읽습니다.

- **`--no-telemetry`**

  사용 데이터를 Microsoft로 다시 보내지 않습니다. **`--no-telemetry`** 플래그가 전달되지 않는 경우 사용량 현황 데이터가 수집되어 Microsoft로 다시 전송됩니다.  

- **`-n`** , **`--dry-run`**

  명령의 시험 실행을 수행합니다.
 
- **`--p`**

  **`--password`** 와 같습니다.

- **`-i`**

  **`--privatekey`** 와 같습니다.

## <a name="examples"></a>예

이 명령은 localhost에 “user”라는 사용자에 대한 연결을 추가합니다. 연결은 *% USERPROFILE%\.ssh\id_rsa* 에 있는 인증에 키 파일을 사용합니다.

```cmd
ConnectionManager.exe add user@127.0.0.1 --privatekey "%USERPROFILE%\.ssh\id_rsa"
```

이 명령은 연결 목록에서 ID가 1975957870인 연결을 제거합니다.

```cmd
ConnectionManager.exe remove 1975957870
```

이 명령은 연결 ID가 21212121인 연결에 대한 셸 선택을 재정의합니다. 지원되는 셸은 **`sh, csh, bash, tcsh, ksh, zsh, dash`** 입니다. Linux 시스템에서 있는 셸이 지원되지 않는 경우 모든 명령에 대해 **`sh`** 을 명시적으로 사용하도록 대체합니다.

```cmd
ConnectionManager.exe modify 21212121 --property shell=csh
```

## <a name="see-also"></a>참고 항목

[Visual Studio에서 대상 Linux 시스템에 연결](connect-to-your-remote-linux-computer.md)

::: moniker-end