---
title: 원격 빌드 이벤트(Linux C++)
ms.date: 06/07/2019
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
ms.openlocfilehash: 4a3e9019d4dacc3d494feb5d6de8f5c2247e4d12
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441505"
---
# <a name="build-event-properties-linux-c"></a>빌드 이벤트 속성(Linux C++)

::: moniker range="vs-2015"

Linux 지원은 Visual Studio 2017 이상에서 사용할 수 있습니다.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="pre-build-event"></a>빌드 전 이벤트

| 속성 | 설명 |
|--|--|
| 명령줄 | 빌드 전 이벤트 도구가 실행할 명령줄을 지정합니다. |
| 설명 | 빌드 전 이벤트 도구가 표시할 설명을 지정합니다. |
| 빌드에 사용 | 이 빌드 이벤트가 현재 구성의 빌드에서 제외되는지 여부를 지정합니다. |
| 복사할 추가 파일 | 원격 시스템에 복사할 추가 파일을 지정합니다. 필요에 따라 fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2와 같은 구문을 사용하여 로컬-원격 매핑 쌍을 지정할 수 있습니다. 여기서 로컬 파일은 원격 시스템의 지정된 원격 위치에 복사될 수 있습니다. |

## <a name="pre-link-event"></a>링크 전 이벤트

| 속성 | 설명 |
|--|--|
| 명령줄 | 링크 전 이벤트 도구가 실행하는 명령줄을 지정합니다. |
| 설명 | 링크 전 이벤트 도구가 표시할 설명을 지정합니다. |
| 빌드에 사용 | 이 빌드 이벤트가 현재 구성의 빌드에서 제외되는지 여부를 지정합니다. |
| 복사할 추가 파일 | 원격 시스템에 복사할 추가 파일을 지정합니다. 필요에 따라 fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2와 같은 구문을 사용하여 로컬-원격 매핑 쌍을 지정할 수 있습니다. 여기서 로컬 파일은 원격 시스템의 지정된 원격 위치에 복사될 수 있습니다. |

## <a name="post-build-event"></a>빌드 후 이벤트

| 속성 | 설명 |
|--|--|
| 명령줄 | 빌드 후 이벤트 도구가 실행하는 명령줄을 지정합니다. |
| 설명 | 빌드 후 이벤트 도구가 표시할 설명을 지정합니다. |
| 빌드에 사용 | 이 빌드 이벤트가 현재 구성의 빌드에서 제외되는지 여부를 지정합니다. |
| 복사할 추가 파일 | 원격 시스템에 복사할 추가 파일을 지정합니다. 필요에 따라 fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2와 같은 구문을 사용하여 로컬-원격 매핑 쌍을 지정할 수 있습니다. 여기서 로컬 파일은 원격 시스템의 지정된 원격 위치에 복사될 수 있습니다. |

## <a name="remote-pre-build-event"></a>원격 빌드 전 이벤트

| 속성 | 설명 |
|--|--|
| 명령줄 | 빌드 전 이벤트 도구가 원격 시스템에서 실행할 명령줄을 지정합니다. |
| 설명 | 빌드 전 이벤트 도구가 표시할 설명을 지정합니다. |
| 빌드에 사용 | 이 빌드 이벤트가 현재 구성의 빌드에서 제외되는지 여부를 지정합니다. |
| 복사할 추가 파일 | 원격 시스템에서 복사할 추가 파일을 지정합니다. 필요에 따라 fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2와 같은 구문을 사용하여 원격-로컬 매핑 쌍을 지정할 수 있습니다. 여기서 원격 파일은 로컬 머신의 지정된 위치에 복사될 수 있습니다. |

## <a name="remote-pre-link-event"></a>원격 링크 전 이벤트

| 속성 | 설명 |
|--|--|
| 명령줄 | 링크 전 이벤트 도구가 원격 시스템에서 실행할 명령줄을 지정합니다. |
| 설명 | 링크 전 이벤트 도구가 표시할 설명을 지정합니다. |
| 빌드에 사용 | 이 빌드 이벤트가 현재 구성의 빌드에서 제외되는지 여부를 지정합니다. |
| 복사할 추가 파일 | 원격 시스템에서 복사할 추가 파일을 지정합니다. 필요에 따라 fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2와 같은 구문을 사용하여 원격-로컬 매핑 쌍을 지정할 수 있습니다. 여기서 원격 파일은 로컬 머신의 지정된 위치에 복사될 수 있습니다. |

## <a name="remote-post-build-event"></a>원격 빌드 후 이벤트

| 속성 | 설명 |
|--|--|
| 명령줄 | 빌드 후 이벤트 도구가 원격 시스템에서 실행할 명령줄을 지정합니다. |
| 설명 | 빌드 후 이벤트 도구가 표시할 설명을 지정합니다. |
| 빌드에 사용 | 이 빌드 이벤트가 현재 구성의 빌드에서 제외되는지 여부를 지정합니다. |
| 복사할 추가 파일 | 원격 시스템에서 복사할 추가 파일을 지정합니다. 필요에 따라 fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2와 같은 구문을 사용하여 원격-로컬 매핑 쌍을 지정할 수 있습니다. 여기서 원격 파일은 로컬 머신의 지정된 위치에 복사될 수 있습니다. |

::: moniker-end
