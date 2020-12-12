---
description: '자세한 정보: 참조 계산'
title: 참조 횟수 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: 0e80986f530d1d0c79fd5c271eb21e292dec06de
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165747"
---
# <a name="reference-counting"></a>참조 횟수

COM 자체는 개체가 더 이상 사용 되지 않는 것으로 간주 될 때 메모리에서 개체를 자동으로 제거 하려고 시도 하지 않습니다. 대신 개체 프로그래머가 사용 하지 않는 개체를 제거 해야 합니다. 프로그래머는 참조 횟수를 기준으로 개체를 제거할 수 있는지 여부를 확인 합니다.

COM은 `IUnknown` [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) 및 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)메서드를 사용 하 여 개체에 대 한 인터페이스의 참조 횟수를 관리 합니다. 이러한 메서드를 호출 하는 일반적인 규칙은 다음과 같습니다.

- 클라이언트에서 인터페이스 포인터를 받을 때마다는 `AddRef` 인터페이스에서를 호출 해야 합니다.

- 클라이언트는 인터페이스 포인터를 사용 하 여 완료할 때마다를 호출 해야 `Release` 합니다.

간단한 구현에서는 각 호출이 `AddRef` 증가 하 고 각 `Release` 호출은 개체 내의 카운터 변수를 감소 시킵니다. 개수가 0으로 반환 되 면 인터페이스에 더 이상 사용자가 없으며 메모리에서 해당 인터페이스를 제거할 수 없습니다.

개체에 대 한 각 참조 (개별 인터페이스가 아님)가 계산 되도록 참조 횟수를 구현할 수도 있습니다. 이 경우 각 및는 `AddRef` `Release` 개체의 중앙 구현에 대 한 대리자를 호출 하 고 `Release` 참조 횟수가 0에 도달할 때 전체 개체를 해제 합니다.

> [!NOTE]
> 연산자를 `CComObject` 사용 하 여 파생 개체가 생성 되는 경우 **`new`** 참조 횟수는 0입니다. 따라서 파생 개체를 성공적으로 만든 후에 대 한 호출을 `AddRef` 수행 해야 합니다 `CComObject` .

## <a name="see-also"></a>참고 항목

[COM 소개](../atl/introduction-to-com.md)<br/>
[참조 횟수를 통해 개체 수명 관리](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
