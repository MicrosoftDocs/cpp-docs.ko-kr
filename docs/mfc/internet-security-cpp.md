---
description: '자세한 정보: 인터넷 보안 (c + +)'
title: 인터넷 보안(C++)
ms.date: 11/04/2016
helpviewer_keywords:
- code signing [MFC], Internet security
- sandboxing [MFC]
- digital signatures [MFC], Internet security
- code signing [MFC]
- Web application security [MFC]
- code access security [MFC], Internet security considerations
- security [MFC]
- security [MFC], Internet
- Internet applications [MFC], security
- Web application security [MFC], Internet security approaches
ms.assetid: bf0da697-81bc-41f0-83fa-d7f82ed83df8
ms.openlocfilehash: 870695abc89ba022a333829ec974d2f1e9147a53
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335849"
---
# <a name="internet-security-c"></a>인터넷 보안(C++)

코드 보안은 개발자와 인터넷 응용 프로그램 사용자에 게 중요 한 문제입니다. 악의적인 코드, 변조 된 코드, 알 수 없는 사이트나 작성자의 코드 등의 위험이 있습니다.

인터넷을 개발할 때 두 가지 기본 보안 방법이 있습니다. 첫 번째는 "샌드 박싱" 이라고 합니다. 이 방법에서는 응용 프로그램이 특정 Api 집합으로 제한 되 고 잠재적으로 위험할 수 있습니다. 예를 들어 프로그램에서 사용자의 컴퓨터에 있는 데이터를 제거할 수 있는 파일 i/o와 같은 위험에서 제외 됩니다. 두 번째는 디지털 서명을 사용 하 여 구현 됩니다. 이 접근 방식을 인터넷에 대 한 "shrinkwrap" 이라고 합니다. 코드는 개인 키/공개 키 기술을 사용 하 여 확인 되 고 서명 됩니다. 코드를 실행 하기 전에 디지털 서명을 확인 하 여 코드가 알려진 인증 된 소스에서 가져온 것 이며 서명 된 이후 코드가 변경 되지 않았는지 확인 합니다.

첫 번째 경우에는 응용 프로그램에서 피해를 주지 않으며 응용 프로그램의 출처를 신뢰 하 게 됩니다. 두 번째에서는 디지털 서명을 사용 하 여 정품 인증을 확인 합니다. 디지털 서명은 코드의 게시자에 대 한 세부 정보를 식별 하 고 제공 하는 데 사용 되는 업계 표준입니다. 해당 기술은 RSA 및 x.509를 비롯 한 표준을 기반으로 합니다. 일반적으로 브라우저에서는 알 수 없는 출처의 코드를 다운로드 하 고 실행할지 여부를 선택할 수 있습니다.

## <a name="see-also"></a>참고 항목

[MFC 인터넷 프로그래밍 작업](mfc-internet-programming-tasks.md)<br/>
[MFC 인터넷 프로그래밍 기본 사항](mfc-internet-programming-basics.md)
