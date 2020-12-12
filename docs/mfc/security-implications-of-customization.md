---
description: '자세한 정보: 사용자 지정의 보안 의미'
title: 사용자 지정의 보안 의미
ms.date: 11/04/2016
helpviewer_keywords:
- security, MFC Feature Pack
- MFC Feature Pack, security
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
ms.openlocfilehash: 64a1029dd3486e3cd653f5e692aa1a14ba6f82b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217759"
---
# <a name="security-implications-of-customization"></a>사용자 지정의 보안 의미

이 항목에서는 MFC의 잠재적인 보안 약점에 대해 설명 합니다.

## <a name="potential-security-weakness"></a>잠재적인 보안 약점

MFC를 사용 하면 사용자가 응용 프로그램 사용자 인터페이스의 모양을 사용자 지정할 수 있습니다. 예를 들어 단추 및 아이콘의 모양을 사용자 지정할 수 있습니다. 또한 MFC는 사용자 정의 도구를 지원 하므로 사용자가 셸 명령을 실행할 수 있습니다. 응용 프로그램의 사용자 지정 된 설정이 레지스트리의 사용자 프로필에 저장 되기 때문에 보안 취약성이 발생 합니다. 레지스트리에 액세스할 수 있는 사용자는 해당 설정을 편집 하 고 응용 프로그램 모양이 나 동작을 변경할 수 있습니다. 예를 들어 컴퓨터의 관리자는 사용자의 응용 프로그램이 임의의 프로그램을 실행 하도록 하 여 사용자를 가장할 수 있습니다 (네트워크 공유 에서도).

## <a name="workarounds"></a>해결 방법

다음 세 가지 방법 중 하나를 수행 하 여 레지스트리의 취약성을 닫는 것이 좋습니다.

- 여기에 저장 된 데이터를 암호화 합니다.

- 레지스트리 대신 보안 파일에 데이터를 저장 합니다.

   이러한 처음 두 가지 방법 중 하나를 수행 하려면 [Csettingsstore 클래스](../mfc/reference/csettingsstore-class.md) 에서 클래스를 파생 하 고 해당 메서드를 재정의 하 여 레지스트리 외부에서 암호화 또는 저장소를 구현 합니다.

- 응용 프로그램에서 사용자 지정을 사용 하지 않도록 설정할 수도 있습니다.

## <a name="see-also"></a>참고 항목

[MFC에 대한 사용자 지정](../mfc/customization-for-mfc.md)
