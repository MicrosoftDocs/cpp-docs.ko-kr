---
description: '자세히 알아보기: CFixedStringT: 사용자 지정 문자열 관리자의 예'
title: 'CFixedStringT: 사용자 지정 문자열 관리자의 예'
ms.date: 11/04/2016
helpviewer_keywords:
- CFixedStringT class, using a custom string manager
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
ms.openlocfilehash: c9af2530500ad5972c01d063116e7ac981109493
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142508"
---
# <a name="cfixedstringt-example-of-a-custom-string-manager"></a>CFixedStringT: 사용자 지정 문자열 관리자의 예

ATL 라이브러리는 Cfixedstringt 클래스의 [Cfixedstringt](../atl-mfc-shared/reference/cfixedstringt-class.md)클래스에서 사용 하는 사용자 지정 문자열 관리자의 한 예를 구현 합니다. `CFixedStringT` 는 [CStringT](../atl-mfc-shared/reference/cstringt-class.md) 에서 파생 되며 `CFixedStringT` 문자열이의 템플릿 매개 변수에서 지정한 길이 보다 작은 경우 해당 문자 데이터를 개체 자체의 일부로 할당 하는 문자열을 구현 `t_nChars` `CFixedStringT` 합니다. 이 방법을 사용 하면 문자열의 길이가 고정 버퍼의 크기를 초과 하는 경우를 제외 하 고는 힙이 전혀 필요 하지 않습니다. `CFixedStringT`는 항상 힙을 사용 하 여 문자열 데이터를 할당 하지 않으므로 문자열 관리자로 사용할 수 없습니다 `CAtlStringMgr` . 사용자 지정 문자열 관리자 ()를 사용 하 여 `CFixedStringMgr` [Iatlstringmgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) 인터페이스를 구현 합니다. 이 인터페이스는 [사용자 지정 문자열 관리자 (고급 메서드) 구현](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)에서 설명 합니다.

의 생성자는 `CFixedStringMgr` 세 개의 매개 변수를 사용 합니다.

- *.pdata:* 사용할 고정 구조체에 대 한 포인터 `CStringData` 입니다.

- *Nchars:* 구조체에서 보유할 수 있는 최대 문자 수 `CStringData` 입니다.

- *Pmgr:* `IAtlStringMgr` "백업 문자열 관리자"의 인터페이스에 대 한 포인터입니다.

생성자는 해당 멤버 변수 (및)에 *.pdata* 및 *pmgr* 의 값을 `m_pData` 저장 `m_pMgr` 합니다. 그런 다음 버퍼의 길이를 0으로 설정 하 고, 사용 가능한 길이를 고정 버퍼의 최대 크기와 동일 하 게 설정 하 고, 참조 횟수를-1로 설정 합니다. 참조 횟수 값은 버퍼가 잠겨 있고이 인스턴스를 문자열 관리자로 사용 함을 나타냅니다 `CFixedStringMgr` .

버퍼를 잠금 상태로 표시 하면 다른 `CStringT` 인스턴스에서 버퍼에 대 한 공유 참조를 보유할 수 없습니다. 다른 `CStringT` 인스턴스에서 버퍼를 공유할 수 있는 경우에 포함 된 버퍼를 삭제 하는 것이 가능 하 고 `CFixedStringT` 다른 문자열은 여전히 버퍼를 사용 하 고 있는 것입니다.

`CFixedStringMgr` 는 인터페이스의 전체 구현입니다 `IAtlStringMgr` . 각 메서드의 구현은 별도로 설명 합니다.

## <a name="implementation-of-cfixedstringmgrallocate"></a>CFixedStringMgr:: Allocate 구현

의 구현은 `CFixedStringMgr::Allocate` 먼저 요청 된 문자열 크기가 고정 버퍼의 크기 (멤버에 저장 됨) 보다 작거나 같은지 확인 `m_pData` 합니다. 고정 버퍼가 충분히 크면에서 `CFixedStringMgr` 길이가 0 인 고정 버퍼를 잠급니다. 문자열 길이가 고정 버퍼의 크기를 초과 하지 않는 한는 버퍼를 다시 할당할 필요가 `CStringT` 없습니다.

요청 된 문자열 크기가 고정 버퍼 보다 크면 `CFixedStringMgr` 요청을 백업 문자열 관리자로 전달 합니다. 백업 문자열 관리자는 힙에서 버퍼를 할당 하는 것으로 간주 됩니다. 그러나이 버퍼를 반환 하기 전에 `CFixedStringMgr` 버퍼를 잠그고 버퍼의 문자열 관리자 포인터를 개체에 대 한 포인터로 바꿉니다 `CFixedStringMgr` . 이렇게 하면에서 버퍼를 다시 할당 하거나 해제 하려고 시도할 `CStringT` 때가를 호출 `CFixedStringMgr` 합니다.

## <a name="implementation-of-cfixedstringmgrreallocate"></a>CFixedStringMgr:: 재할당의 구현

구현은의 구현과 `CFixedStringMgr::ReAllocate` 매우 유사 `Allocate` 합니다.

재할당 중인 버퍼가 고정 버퍼이 고 요청 된 버퍼 크기가 고정 버퍼 보다 작은 경우 할당이 수행 되지 않습니다. 그러나 재할당 중인 버퍼가 고정 버퍼가 아닌 경우에는 백업 관리자를 사용 하 여 할당 된 버퍼 여야 합니다. 이 경우에는 백업 관리자를 사용 하 여 버퍼를 다시 할당 합니다.

다시 할당 중인 버퍼가 고정 버퍼이 고 새 버퍼 크기가 너무 커서 고정 버퍼에 맞지 않는 경우는 `CFixedStringMgr` 백업 관리자를 사용 하 여 새 버퍼를 할당 합니다. 그런 다음 고정 된 버퍼의 내용을 새 버퍼에 복사 합니다.

## <a name="implementation-of-cfixedstringmgrfree"></a>CFixedStringMgr:: Free 구현

의 구현은 `CFixedStringMgr::Free` 및와 동일한 패턴을 따릅니다 `Allocate` `ReAllocate` . 해제 되는 버퍼가 고정 버퍼 이면 메서드는이를 길이가 0 인 잠긴 버퍼로 설정 합니다. 해제 되는 버퍼가 백업 관리자에 할당 된 경우는 백업 관리자를 사용 하 여 해당 버퍼를 `CFixedStringMgr` 해제 합니다.

## <a name="implementation-of-cfixedstringmgrclone"></a>CFixedStringMgr:: Clone 구현

의 구현은 `CFixedStringMgr::Clone` 항상이 아니라 백업 관리자에 대 한 포인터를 반환 합니다 `CFixedStringMgr` . 이는의 모든 인스턴스가 `CFixedStringMgr` 의 단일 인스턴스에만 연결 될 수 있기 때문에 발생 `CStringT` 합니다. 관리자를 복제 하려는 다른 모든 인스턴스에서는 `CStringT` 대신 백업 관리자를 가져와야 합니다. 이는 백업 관리자가 공유 하는 것을 지원 하기 때문입니다.

## <a name="implementation-of-cfixedstringmgrgetnilstring"></a>CFixedStringMgr:: GetNilString 구현

의 구현은 `CFixedStringMgr::GetNilString` 고정 버퍼를 반환 합니다. 및의 일대일 대응 때문에 `CFixedStringMgr` `CStringT` 의 지정 된 인스턴스에서 한 `CStringT` 번에 둘 이상의 버퍼를 사용 하지 않습니다. 따라서 nil 문자열과 실제 문자열 버퍼는 동시에 필요 하지 않습니다.

고정 버퍼가 사용 되 고 있지 않을 때마다는 `CFixedStringMgr` 길이가 0 인 초기화 되도록 합니다. 이렇게 하면이를 nil 문자열로 사용할 수 있습니다. 추가 보너스로 `nAllocLength` 고정 버퍼의 멤버는 항상 고정 버퍼의 전체 크기로 설정 됩니다. 즉,에서 `CStringT` nil 문자열에 대해서도 isttstststd [:: 재할당](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate)을 호출 하지 않고 문자열을 늘릴 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:** cstringt. h

## <a name="see-also"></a>참고 항목

[CStringT를 사용한 메모리 관리](../atl-mfc-shared/memory-management-with-cstringt.md)
