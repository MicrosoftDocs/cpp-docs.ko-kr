---
description: '자세한 정보: 메시지 처리 및 명령 대상'
title: 메시지 처리 및 명령 대상
ms.date: 11/04/2016
f1_keywords:
- IOleCommandTarget
helpviewer_keywords:
- command targets [MFC]
- message handling [MFC], active documents
- IOleCommandTarget interface [MFC]
- command routing [MFC], command targets
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
ms.openlocfilehash: 35dc54687c7f3742f72d58f5c84cd274bc8fee09
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203291"
---
# <a name="message-handling-and-command-targets"></a>메시지 처리 및 명령 대상

명령 디스패치 인터페이스는 `IOleCommandTarget` 명령을 쿼리하고 실행 하기 위한 간단 하 고 확장 가능한 메커니즘을 정의 합니다. 이 메커니즘은 `IDispatch` 표준 명령 집합에 전적으로 의존 하기 때문에 자동화 보다 간단 합니다. 명령에는 거의 인수가 없고 형식 정보는 포함 되지 않습니다 (명령 인수에 대해서도 형식 안전성이 떨어집니다.).

명령 디스패치 인터페이스 디자인에서 각 명령은 **GUID** 로 식별 되는 "명령 그룹"에 속합니다. 따라서 누구나 새 그룹을 정의 하 고 Microsoft 또는 기타 공급 업체와의 협력이 없어도 해당 그룹 내의 모든 명령을 정의할 수 있습니다. 이는 기본적 **으로 Automation에서** **의 추가 정의와** 동일한 정의 수단입니다. 여기에 중복이 있습니다 .이 명령 라우팅 메커니즘은 명령 라우팅에만 사용할 수 있지만, 대규모 규모의 스크립팅/프로그래밍 기능에는 자동화 핸들로 사용할 수 없습니다.

`IOleCommandTarget` 는 다음과 같은 시나리오를 처리 합니다.

- 개체가 활성화 된 상태 이면 일반적으로 개체의 도구 모음만 표시 되 고 개체 도구 모음에는 **인쇄**, **인쇄 미리 보기**, **저장**, **새로 만들기**, **확대/축소** 등의 일부 컨테이너 명령에 대 한 단추가 포함 될 수 있습니다. (내부 활성화 표준은 개체가 도구 모음에서 해당 단추를 제거 하거나 최소한 사용 하지 않도록 설정 하는 것을 권장 합니다. 이러한 디자인을 통해 해당 명령을 사용 하도록 설정 하 고 올바른 처리기로 라우팅할 수 있습니다. 현재는 개체에서 컨테이너에 이러한 명령을 디스패치할 수 있는 메커니즘이 없습니다.

- 활성 문서가 활성 문서 컨테이너 (예: Office 바인더)에 포함 된 경우 컨테이너는 **인쇄**, **페이지 설정**, **속성** 등의 명령을 포함 된 활성 문서에 보내야 할 수도 있습니다.

이 간단한 명령 라우팅은 기존 Automation 표준 및을 통해 처리할 수 있습니다 `IDispatch` . 그러나와 관련 된 오버 헤드는 `IDispatch` 여기에 필요 합니다. 따라서는 `IOleCommandTarget` 동일한 종료를 달성할 수 있는 간단한 방법을 제공 합니다.

```
interface IOleCommandTarget : IUnknown
    {
    HRESULT QueryStatus(
        [in] GUID *pguidCmdGroup,
        [in] ULONG cCmds,
        [in,out][size_is(cCmds)] OLECMD *prgCmds,
        [in,out] OLECMDTEXT *pCmdText);
    HRESULT Exec(
        [in] GUID *pguidCmdGroup,
        [in] DWORD nCmdID,
        [in] DWORD nCmdExecOpt,
        [in] VARIANTARG *pvaIn,
        [in,out] VARIANTARG *pvaOut);
    }
```

`QueryStatus`여기서 메서드는 특정 명령 집합, 즉 **GUID** 로 식별 되는 집합이 지원 되는지 여부를 테스트 합니다. 이 호출은 **Olecmd** 값 (구조체)의 배열을 지원 되는 명령 목록으로 채우고 명령 및/또는 상태 정보의 이름을 설명 하는 텍스트를 반환 합니다. 호출자는 명령을 호출 하려는 경우 옵션 및 인수와 함께 명령 (및 집합 **GUID**)을에 전달 하 여 `Exec` 반환 값을 다시 가져올 수 있습니다.

## <a name="see-also"></a>참고 항목

[액티브 문서 컨테이너](active-document-containers.md)
