---
description: '자세한 정보: CDWordArray 클래스'
title: CDWordArray 클래스
ms.date: 11/04/2016
f1_keywords:
- CDWordArray
- AFXCOLL/CDWordArray
- AFXCOLL/CDWordArray::CDWordArray
- AFXCOLL/CDWordArray::Add
- AFXCOLL/CDWordArray::Append
- AFXCOLL/CDWordArray::Copy
- AFXCOLL/CDWordArray::ElementAt
- AFXCOLL/CDWordArray::FreeExtra
- AFXCOLL/CDWordArray::GetAt
- AFXCOLL/CDWordArray::GetCount
- AFXCOLL/CDWordArray::GetData
- AFXCOLL/CDWordArray::GetSize
- AFXCOLL/CDWordArray::GetUpperBound
- AFXCOLL/CDWordArray::InsertAt
- AFXCOLL/CDWordArray::IsEmpty
- AFXCOLL/CDWordArray::RemoveAll
- AFXCOLL/CDWordArray::RemoveAt
- AFXCOLL/CDWordArray::SetAt
- AFXCOLL/CDWordArray::SetAtGrow
- AFXCOLL/CDWordArray::SetSize
helpviewer_keywords:
- CDWordArray [MFC], CDWordArray
- CDWordArray [MFC], Add
- CDWordArray [MFC], Append
- CDWordArray [MFC], Copy
- CDWordArray [MFC], ElementAt
- CDWordArray [MFC], FreeExtra
- CDWordArray [MFC], GetAt
- CDWordArray [MFC], GetCount
- CDWordArray [MFC], GetData
- CDWordArray [MFC], GetSize
- CDWordArray [MFC], GetUpperBound
- CDWordArray [MFC], InsertAt
- CDWordArray [MFC], IsEmpty
- CDWordArray [MFC], RemoveAll
- CDWordArray [MFC], RemoveAt
- CDWordArray [MFC], SetAt
- CDWordArray [MFC], SetAtGrow
- CDWordArray [MFC], SetSize
ms.assetid: 581be11e-ced6-47d1-8679-e0b8e7d99494
ms.openlocfilehash: b77073228cac1861741751572af55c912d4a76e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184753"
---
# <a name="cdwordarray-class"></a>CDWordArray 클래스

32비트 2배 워드를 지원합니다.

## <a name="syntax"></a>구문

```
class CDWordArray : public CObject
```

## <a name="members"></a>멤버

의 멤버 함수는 `CDWordArray` [CObArray](../../mfc/reference/cobarray-class.md)클래스의 멤버 함수와 비슷합니다. 이처럼 두 함수가 비슷하므로 `CObArray` 참조 설명서에서 멤버 함수 관련 사항을 확인할 수 있습니다. `CObject`포인터가 함수 매개 변수 또는 반환 값으로 표시 되는 경우에는를 대체 `DWORD` 합니다.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

예를 들어 위의 코드는

`DWORD CDWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDWordArray:: CDWordArray](../../mfc/reference/cobarray-class.md#cobarray)|빈 배열을 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDWordArray:: Add](../../mfc/reference/cobarray-class.md#add)|배열 끝에 요소를 추가하고 필요하면 배열을 확장합니다.|
|[CDWordArray:: Append](../../mfc/reference/cobarray-class.md#append)|배열에 다른 배열을 추가하고 필요하면 배열을 확장합니다.|
|[CDWordArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|배열에 다른 배열을 복사하고 필요하면 배열을 확장합니다.|
|[CDWordArray:: ElementAt](../../mfc/reference/cobarray-class.md#elementat)|배열 내의 바이트에 대 한 임시 참조를 반환 합니다.|
|[CDWordArray:: FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|현재 상한을 초과하며 사용되지 않는 모든 메모리를 해제합니다.|
|[CDWordArray:: GetAt](../../mfc/reference/cobarray-class.md#getat)|지정된 인덱스의 값을 반환합니다.|
|[CDWordArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|이 배열에 있는 요소의 수를 가져옵니다.|
|[CDWordArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|배열의 요소에 대한 액세스를 허용합니다. NULL일 수 있습니다.|
|[CDWordArray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|이 배열에 있는 요소의 수를 가져옵니다.|
|[CDWordArray:: System.array.getupperbound](../../mfc/reference/cobarray-class.md#getupperbound)|유효한 최대 인덱스를 반환합니다.|
|[CDWordArray:: InsertAt](../../mfc/reference/cobarray-class.md#insertat)|지정한 인덱스에 요소 하나 또는 다른 배열의 모든 요소를 삽입합니다.|
|[CDWordArray:: IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|배열이 비어 있는지를 확인합니다.|
|[CDWordArray:: RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|이 배열의 모든 요소를 반환합니다.|
|[CDWordArray:: RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|특정 인덱스의 요소를 제거합니다.|
|[CDWordArray:: SetAt](../../mfc/reference/cobarray-class.md#setat)|지정된 인덱스의 값을 설정합니다. 배열은 확장할 수 없습니다.|
|[CDWordArray:: SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|지정된 인덱스의 값을 설정합니다. 필요한 경우 배열을 확장합니다.|
|[CDWordArray:: SetSize](../../mfc/reference/cobarray-class.md#setsize)|이 배열에 포함된 요소의 수를 설정합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CDWordArray:: operator \[\]](../../mfc/reference/cobarray-class.md#operator_at)|지정한 인덱스에 있는 요소를 설정하거나 가져옵니다.|

## <a name="remarks"></a>설명

`CDWordArray`는 serialization 및 요소 덤프를 지원하기 위해 `IMPLEMENT_SERIAL` 매크로를 통합합니다. 오버 로드 된 삽입 () 연산자 또는 멤버 함수를 사용 하 여 더블 워드의 배열을 보관 파일에 저장 한 경우 **<<** `Serialize` 각 요소는 차례로 serialize 됩니다.

> [!NOTE]
> 배열을 사용하기 전에 `SetSize`를 사용하여 배열 크기를 설정하고 배열에 대해 메모리를 할당합니다. `SetSize`를 사용하지 않는 경우 배열에 요소를 추가하면 배열이 자주 다시 할당되고 복사됩니다. 이처럼 다시 할당 및 복사가 자주 수행되면 효율성이 떨어지며 메모리가 조각화될 수 있습니다.

배열의 개별 요소에서 디버그 출력을 요구 하는 경우 개체의 깊이를 `CDumpContext` 1 이상으로 설정 해야 합니다.

사용에 대 한 자세한 내용은 `CDWordArray` [컬렉션](../../mfc/collections.md)문서를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** afxcoll.h

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CObArray 클래스](../../mfc/reference/cobarray-class.md)
