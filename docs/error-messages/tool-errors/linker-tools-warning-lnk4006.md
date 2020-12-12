---
description: '자세한 정보: 링커 도구 경고 LNK4006'
title: 링커 도구 경고 LNK4006
ms.date: 11/04/2016
f1_keywords:
- LNK4006
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
ms.openlocfilehash: 526b3f380ef7e05448280094f360c145d7f21c04
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332021"
---
# <a name="linker-tools-warning-lnk4006"></a>링커 도구 경고 LNK4006

개체에 기호가 이미 정의 되어 있습니다. 두 번째 정의가 무시 됨

데코레이팅된 폼으로 표시되는 해당 `symbol` 기호는 여러 번 정의되었습니다. 이 경고가 발생 하면 `symbol` 가 두 번 추가 되지만 첫 번째 폼만 사용 됩니다.

두 개의 가져오기 라이브러리를 하나로 병합 하려고 하면이 경고가 발생할 수 있습니다.

C 런타임 라이브러리를 다시 작성 하는 경우이 메시지를 무시할 수 있습니다.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>아래의 해결 방법 따라 수정합니다.

1. 지정 된은 `symbol` [/gy](../../build/reference/gy-enable-function-level-linking.md)로 컴파일하여 생성 된 패키지 함수 일 수 있습니다. 이 기호가 둘 이상의 파일에 포함 되어 있지만 컴파일 간에 변경 되었습니다. 을 포함 하는 모든 파일을 다시 컴파일합니다 `symbol` .

1. 지정 된이 `symbol` 다른 라이브러리의 두 멤버 개체에 다르게 정의 되어 있을 수 있습니다.

1. 절대값은 두 번 정의 될 수 있으며, 각 정의에 다른 값이 있습니다.

1. 라이브러리를 결합할 때 오류 메시지가 수신 되 면 `symbol` 에 추가 되는 라이브러리에가 이미 있는 것입니다.
