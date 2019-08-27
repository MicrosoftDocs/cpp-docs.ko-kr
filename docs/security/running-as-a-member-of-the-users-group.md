---
title: 사용자 그룹의 멤버로 실행
ms.date: 11/04/2016
f1_keywords:
- PRJ0050
- VCD0047
helpviewer_keywords:
- Users Group [C++]
- security [C++], Users Group
- Windows accounts [C++]
- non administrator users [C++]
- user accounts [C++]
- administrator (not running as) [C++]
ms.assetid: e48a03ec-d345-49f6-809a-1a291eecbc81
ms.openlocfilehash: dc06e2dc58d28c34a646ccffc0be90368b3297f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411294"
---
# <a name="running-as-a-member-of-the-users-group"></a>사용자 그룹의 멤버로 실행

이 항목에서는 Windows 사용자 계정을 관리자 그룹이 아닌 사용자 그룹의 멤버로 구성하면 악의적인 코드에 감염될 가능성이 줄어들어 보안이 강화된다는 점에 대해 설명합니다.

## <a name="security-risks"></a>보안 위험

관리자 권한으로 실행하면 시스템이 "트로이 목마" 및 "버퍼 오버런"과 같은 몇 가지 종류의 보안 공격에 취약해집니다. 관리자 권한으로는 인터넷 사이트에 방문하기만 해도 악의적인 코드가 인터넷 사이트에서 다운로드되어 컴퓨터를 공격할 수 있으므로 시스템이 손상될 수 있습니다. 이러한 상황이 발생하면 악의적인 코드에서 사용자의 관리자 권한을 상속한 다음 모든 파일 삭제, 하드 드라이브 다시 포맷, 관리자 액세스 권한을 가지는 새 사용자 계정 생성 등의 작업을 수행할 수 있습니다.

## <a name="non-administrator-user-groups"></a>관리자가 아닌 사용자 그룹

개발자가 일반적으로 사용하는 Windows 사용자 계정은 사용자 또는 고급 사용자 그룹에 추가해야 합니다. 개발자는 디버깅 그룹에도 추가되어야 합니다. 사용자 그룹의 멤버가 되면 컴퓨터를 불필요한 위험에 노출시키지 않고 프로그램 실행 및 인터넷 사이트 방문 등의 일상적인 작업을 수행할 수 있습니다. 고급 사용자 그룹의 멤버가 되면 애플리케이션 설치, 프린터 설치 및 대부분의 제어판 작업도 함께 수행할 수 있습니다. 운영 체제 업그레이드 또는 시스템 매개 변수 구성과 같은 관리자 작업을 수행해야 하는 경우 관리자 작업을 수행하는 동안만 관리자 계정으로 로그인해야 합니다. Windows 또는 **runas** 명령은 관리 액세스를 사용 하 여 특정 응용 프로그램을 시작 하려면 사용할 수 있습니다.

## <a name="exposing-customers-to-security-risks"></a>고객을 보안 위험에 노출

개발자의 입장에서 관리자 그룹의 멤버가 되지 않는 것이 중요한 이유는 개발 컴퓨터의 보호 외에도 개발하는 애플리케이션을 실행하기 위해 고객이 관리자 그룹에 가입해야 하는 코드를 개발자가 실수로 작성하는 것을 막는다는 것입니다. 개발 도중 관리자 액세스가 필요한 코드가 사용되면 애플리케이션에서 고객이 관리자 권한으로 실행해야 한다는 경고가 나타나면서 런타임에 이 코드가 실패합니다.

## <a name="code-that-requires-administrator-privileges"></a>관리자 권한이 필요한 코드

일부 코드를 실행하려면 관리자 액세스가 필요합니다. 가능한 경우에는 이러한 코드에 대한 대체 코드를 찾아야 합니다. 관리자 액세스가 필요한 코드 작업에는 다음과 같은 예가 있습니다.

- Windows 또는 Program Files 디렉터리와 같은 파일 시스템의 보호된 영역에 쓰기

- HKEY_LOCAL_MACHINE과 같은 레지스트리의 보호된 영역에 쓰기

- GAC(전역 어셈블리 캐시)에 어셈블리 설치

일반적으로 이들 작업은 애플리케이션 설치 프로그램으로 제한됩니다. 따라서 사용자는 일시적으로만 관리자 상태를 사용할 수 있습니다.

## <a name="debugging"></a>디버깅

디버깅 그룹의 멤버가 되면 관리자가 아닌 권한으로도 Visual Studio 내에서 실행하는 네이티브 및 관리되지 않는 모든 애플리케이션을 디버깅할 수 있습니다. 여기에는 프로세스에 연결 명령을 사용하여 실행 중인 애플리케이션에 연결하는 기능이 포함됩니다. 그러나 다른 사용자가 실행한 네이티브 또는 관리되는 애플리케이션을 디버깅하려면 관리자 그룹의 멤버가 되어야 합니다.

## <a name="see-also"></a>참고자료

[보안 모범 사례](security-best-practices-for-cpp.md)
