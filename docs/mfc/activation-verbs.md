---
description: '자세히 알아보기: 활성화: 동사'
title: '활성화: 동사'
ms.date: 11/04/2016
helpviewer_keywords:
- verbs [MFC]
- OLE [MFC], activation
- edit verb [MFC]
- activation [MFC], verbs
- OLE [MFC], editing
- Primary verb [MFC]
- OLE activation {MFC]
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
ms.openlocfilehash: 2c680452d87f1fcfd1ee2a0b8362dbaab8c0affd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325934"
---
# <a name="activation-verbs"></a>활성화: 동사

이 문서에서는 OLE [활성화](activation-cpp.md)에서 역할 기본 및 보조 동사 재생에 대해 설명 합니다.

일반적으로 포함 된 항목을 두 번 클릭 하면 사용자가 해당 항목을 편집할 수 있습니다. 그러나 특정 항목은 이러한 방식으로 동작 하지 않습니다. 예를 들어 소리 레코더 응용 프로그램을 사용 하 여 만든 항목을 두 번 클릭 하면 별도의 창에서 서버가 열리지 않습니다. 대신 소리를 재생 합니다.

이 동작의 차이점은 녹음기 항목의 "기본 동사"가 다르기 때문입니다. 기본 동사는 사용자가 OLE 항목을 두 번 클릭할 때 수행 되는 동작입니다. 대부분의 OLE 항목 형식에 대해 기본 동사는 항목을 만든 서버를 시작 하는 편집입니다. 녹음기 항목과 같은 일부 형식의 항목의 경우 기본 동사가 재생 됩니다.

여러 유형의 OLE 항목은 동사를 하나만 지원 하 고 편집은 가장 일반적입니다. 그러나 일부 항목 형식은 여러 동사를 지원 합니다. 예를 들어 녹음기 항목은 편집을 보조 동사로 지원 합니다.

자주 사용 되는 또 다른 동사가 열려 있습니다. 서버 응용 프로그램이 별도의 창에서 시작 되는 경우를 제외 하 고는 Open 동사는 Edit와 동일 합니다. 컨테이너 응용 프로그램 또는 서버 응용 프로그램에서 내부 활성화를 지원 하지 않는 경우이 동사를 사용 해야 합니다.

항목이 선택 되 면 하위 메뉴 명령을 통해 기본 동사 이외의 모든 동사를 호출 해야 합니다. 이 하위 메뉴에는 항목에서 지 원하는 모든 동사가 포함 되며 일반적으로 **편집** 메뉴의 *typename* **개체** 명령으로 도달 합니다. *Typename* **개체** 명령에 대 한 자세한 내용은 [메뉴 및 리소스: 컨테이너 추가](menus-and-resources-container-additions.md)문서를 참조 하세요.

서버 응용 프로그램에서 지 원하는 동사는 Windows 등록 데이터베이스에 나열 됩니다. 서버 응용 프로그램이 MFC 라이브러리를 사용 하 여 작성 된 경우 서버를 시작할 때 모든 동사가 자동으로 등록 됩니다. 그렇지 않은 경우 서버 응용 프로그램의 초기화 단계 중에 등록 해야 합니다. 자세한 내용은 [등록](registration.md)문서를 참조 하세요.

## <a name="see-also"></a>참고 항목

[활성화](activation-cpp.md)<br/>
[컨테이너](containers.md)<br/>
[서버](servers.md)
