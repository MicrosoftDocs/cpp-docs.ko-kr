---
description: '자세한 정보: 사용자 지정 문자열 관리자 구현 (고급 메서드)'
title: 사용자 지정 문자열 관리자 구현 (고급 메서드)
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: 64ab7da9-47c1-4c4a-9cd7-4cc37e7f3f57
ms.openlocfilehash: 042c0759076d14e2fd0cf8dd91e34c4f1d8bb534
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166969"
---
# <a name="implementation-of-a-custom-string-manager-advanced-method"></a>사용자 지정 문자열 관리자 구현 (고급 메서드)

특수 한 경우에는 메모리를 할당 하는 데 사용 되는 힙을 변경 하는 것 보다 더 많은 사용자 지정 문자열 관리자를 구현할 수 있습니다. 이 경우에는 사용자 지정 문자열 관리자로 [i사용자 지정 Stringmgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) 인터페이스를 수동으로 구현 해야 합니다.

이렇게 하려면 먼저 [CStringT](../atl-mfc-shared/reference/cstringt-class.md) 가 해당 인터페이스를 사용 하 여 문자열 데이터를 관리 하는 방법을 이해 하는 것이 중요 합니다. 모든 인스턴스에는 `CStringT` [CStringData](../atl-mfc-shared/reference/cstringdata-class.md) 구조체에 대 한 포인터가 있습니다. 이 가변 길이 구조체는 문자열에 대 한 실제 문자 데이터 뿐만 아니라 길이와 같은 문자열에 대 한 중요 한 정보를 포함 합니다. 모든 사용자 지정 문자열 관리자는의 요청에 이러한 구조를 할당 하 고 해제 해야 `CStringT` 합니다.

`CStringData`구조는 다음 네 개의 필드로 구성 됩니다.

- [Pstringmgr](../atl-mfc-shared/reference/cstringdata-class.md#pstringmgr) 이 필드 `IAtlStringMgr` 는이 문자열 데이터를 관리 하는 데 사용 되는 인터페이스를 가리킵니다. 에서 `CStringT` 문자열 버퍼를 다시 할당 하거나 해제 해야 하는 경우에는이 인터페이스의 재할당 또는 free 메서드를 호출 하 여 `CStringData` 구조체를 매개 변수로 전달 합니다. 문자열 관리자에서 구조체를 할당 하는 경우 `CStringData` 사용자 지정 문자열 관리자를 가리키도록이 필드를 설정 해야 합니다.

- [nDataLength](../atl-mfc-shared/reference/cstringdata-class.md#ndatalength) 이 필드는 종료 null을 제외 하 고 버퍼에 저장 된 문자열의 현재 논리 길이를 포함 합니다. `CStringT` 문자열의 길이가 변경 되 면이 필드를 업데이트 합니다. 구조체를 할당할 때 `CStringData` 문자열 관리자는이 필드를 0으로 설정 해야 합니다. 구조체를 다시 할당 하는 경우 `CStringData` 사용자 지정 문자열 관리자는이 필드를 변경 하지 않고 그대로 두어야 합니다.

- [nAllocLength](../atl-mfc-shared/reference/cstringdata-class.md#nalloclength) 이 필드에는 다시 할당 하지 않고이 문자열 버퍼에 저장할 수 있는 최대 문자 수 (종료 null 제외)가 포함 됩니다. `CStringT`는 문자열의 논리적 길이를 늘려야 할 때마다 먼저이 필드를 확인 하 여 버퍼에 충분 한 공간이 있는지 확인 합니다. 확인이 실패 하면는 `CStringT` 사용자 지정 문자열 관리자를 호출 하 여 버퍼를 다시 할당 합니다. 구조체를 할당 하거나 `CStringData` 재할당할 때이 필드를 Nchars 매개 변수에서 요청 된 문자 수 이상으로 설정 해야 합니다 .이 필드 [는 isnstringmgr:: Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#allocate) 또는 [Isnimgr:: 재할당할](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate).  버퍼에 요청 된 것 보다 더 많은 공간이 있는 경우이 값을 설정 하 여 사용 가능한 실제 공간의 크기를 반영할 수 있습니다. 이렇게 하면에서 문자열을 확장 하 여 `CStringT` 버퍼를 다시 할당 하기 위해 문자열 관리자를 다시 호출 해야 하기 전에 할당 된 전체 공간을 채울 수 있습니다.

- [Nrefs](../atl-mfc-shared/reference/cstringdata-class.md#nrefs) 이 필드는 문자열 버퍼의 현재 참조 횟수를 포함 합니다. 값이 1 이면의 단일 인스턴스가 `CStringT` 버퍼를 사용 합니다. 또한 인스턴스는 버퍼의 내용을 읽고 수정할 수 있습니다. 값이 1 보다 크면의 여러 인스턴스에서 `CStringT` 버퍼를 사용할 수 있습니다. 문자 버퍼가 공유 되기 때문에 `CStringT` 인스턴스는 버퍼의 내용만 읽을 수 있습니다. 콘텐츠를 수정 하기 위해는 `CStringT` 먼저 버퍼의 복사본을 만듭니다. 값이 음수 이면 하나의 인스턴스만 `CStringT` 버퍼를 사용 합니다. 이 경우 버퍼가 잠긴 것으로 간주 됩니다. `CStringT`인스턴스가 잠긴 버퍼를 사용 하는 경우의 다른 인스턴스에서 `CStringT` 버퍼를 공유할 수 없습니다. 대신 이러한 인스턴스는 콘텐츠를 조작 하기 전에 버퍼의 복사본을 만듭니다. 또한 `CStringT` 잠긴 버퍼를 사용 하는 인스턴스는 할당 된 다른 인스턴스의 버퍼를 공유 하려고 시도 하지 않습니다 `CStringT` . 이 경우 `CStringT` 인스턴스는 다른 문자열을 잠긴 버퍼로 복사 합니다.

   구조체를 할당할 때 `CStringData` 버퍼에 허용 되는 공유 유형을 반영 하도록이 필드를 설정 해야 합니다. 대부분의 구현에서는이 값을 1로 설정 합니다. 이를 통해 일반적인 쓰기 복사 공유 동작을 수행할 수 있습니다. 그러나 문자열 관리자가 문자열 버퍼 공유를 지원 하지 않는 경우이 필드를 잠긴 상태로 설정 합니다. 이렇게 `CStringT` 하면가 할당 된 인스턴스에 대해서만이 버퍼를 사용 `CStringT` 합니다.

## <a name="see-also"></a>참고 항목

[CStringT를 사용한 메모리 관리](../atl-mfc-shared/memory-management-with-cstringt.md)
