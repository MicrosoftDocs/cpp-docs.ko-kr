---
description: '자세히 알아보기: Collection 클래스 도우미'
title: 컬렉션 클래스 도우미
ms.date: 11/04/2016
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
ms.openlocfilehash: 9d3838ba0ba05441debb183e47d7df4e39229742
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331390"
---
# <a name="collection-class-helpers"></a>컬렉션 클래스 도우미

컬렉션 클래스 `CMap` , `CList` 및는 `CArray` 요소 비교, 복사 및 직렬화와 같은 목적으로 템플릿 기반 전역 도우미 함수를 사용 합니다. , 및를 기반으로 하는 클래스 구현의 일환으로 `CMap` , `CList` `CArray` 맵, 목록 또는 배열에 저장 된 데이터 형식에 맞게 조정 된 버전을 사용 하 여 필요에 따라 이러한 함수를 재정의 해야 합니다. 와 같은 도우미 함수를 재정의 하는 방법에 대 한 자세한 내용은 컬렉션 `SerializeElements` [: Type-Safe 컬렉션을 만드는 방법](../../mfc/how-to-make-a-type-safe-collection.md)을 참조 하세요. 및는 `ConstructElements` `DestructElements` 더 이상 사용 되지 않습니다.

MFC 라이브러리는 컬렉션 클래스를 사용자 지정할 수 있도록 afxtempl.h에서 다음 전역 함수를 제공 합니다.

### <a name="collection-class-helpers"></a>컬렉션 클래스 도우미

|Name|설명|
|-|-|
|[CompareElements](#compareelements)|요소가 동일한 지 여부를 나타냅니다.|
|[CopyElements](#copyelements)|한 배열에서 다른 배열로 요소를 복사 합니다.|
|[DumpElements](#dumpelements)|스트림 지향 진단 출력을 제공 합니다.|
|[HashKey](#hashkey)|해시 키를 계산 합니다.|
|[SerializeElements](#serializeelements)|보관 파일 또는 보관 파일에서 요소를 저장 하거나 검색 합니다.|

## <a name="compareelements"></a><a name="compareelements"></a> CompareElements

[CList:: Find] (clist-class. md # clist__find not_found에서 직접 호출 되며, [cmap__lookup](cmap-class.md#lookup) 하 고 [cmap__operator &#91;&#93;](cmap-class.md#operator_at)하 여 간접적으로 호출 됩니다.

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
비교할 첫 번째 요소의 형식입니다.

*pElement1*<br/>
비교할 첫 번째 요소에 대 한 포인터입니다.

*ARG_TYPE*<br/>
비교할 두 번째 요소의 형식입니다.

*pElement2*<br/>
비교할 두 번째 요소에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

*PElement1* 가 가리키는 개체가 *pElement2* 가 가리키는 개체와 같으면 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`CMap`호출에서는 `CMap` 템플릿 매개 변수 *키* 와 *ARG_KEY* 를 사용 합니다.

기본 구현에서는 *\* pElement1* 및 *\* pElement2* 비교 결과를 반환 합니다. 응용 프로그램에 적합 한 방식으로 요소를 비교 하도록이 함수를 재정의 합니다.

C + + 언어는 `==` 단순 형식 (,, 등)에 대 한 비교 연산자 ()를 정의 **`char`** **`int`** **`float`** 하지만 클래스 및 구조체에 대 한 비교 연산자를 정의 하지 않습니다. 또는를 사용 하 여이를 사용 하 `CompareElements` 는 컬렉션 클래스 중 하나를 인스턴스화하려면 `CompareElements` 적절 한 값을 반환 하는 버전을 사용 하 여 비교 연산자 또는 오버 로드를 정의 해야 합니다.

### <a name="requirements"></a>요구 사항

   **헤더:** afxtempl.h

## <a name="copyelements"></a><a name="copyelements"></a> CopyElements

이 함수는 [CArray:: Append](carray-class.md#append) 및 [CArray:: Copy](carray-class.md#copy)를 통해 직접 호출 됩니다.

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
복사할 요소의 형식을 지정 하는 템플릿 매개 변수입니다.

*pDest*<br/>
요소가 복사 되는 대상에 대 한 포인터입니다.

*.Psrc*<br/>
복사할 요소의 소스에 대 한 포인터입니다.

*nCount*<br/>
복사할 요소의 수입니다.

### <a name="remarks"></a>설명

기본 구현에서는 단순 할당 연산자 ()를 사용 **=** 하 여 복사 작업을 수행 합니다. 복사할 형식에 오버 로드 된 연산자 =가 없으면 기본 구현에서 비트 복사를 수행 합니다.

이 도우미 함수 및 다른 도우미 함수를 구현 하는 방법에 대 한 자세한 내용은 컬렉션 [: Type-Safe 컬렉션을 만드는 방법](../how-to-make-a-type-safe-collection.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxtempl.h

## <a name="dumpelements"></a><a name="dumpelements"></a> 로의 요소

재정의할 때 컬렉션의 요소에 대해 텍스트 형식으로 스트림 지향 진단 출력을 제공 합니다.

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>매개 변수

*dc*<br/>
덤프 하는 요소에 대 한 컨텍스트를 덤프 합니다.

*TYPE*<br/>
요소의 형식을 지정 하는 템플릿 매개 변수입니다.

*pElements*<br/>
덤프 될 요소에 대 한 포인터입니다.

*nCount*<br/>
덤프할 요소의 수입니다.

### <a name="remarks"></a>설명

`CArray::Dump`, `CList::Dump` 및 함수는 `CMap::Dump` 덤프 깊이가 0 보다 큰 경우이를 호출 합니다.

기본 구현은 아무 작업도 수행하지 않습니다. 컬렉션의 요소가에서 파생 되는 경우 `CObject` 재정의는 일반적으로 컬렉션의 요소를 반복 하 여 `Dump` 각 요소에 대해 차례로를 호출 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxtempl.h

## <a name="hashkey"></a><a name="hashkey"></a> HashKey

지정 된 키에 대 한 해시 값을 계산 합니다.

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>매개 변수

*ARG_KEY*<br/>
지도 키에 액세스 하는 데 사용 되는 데이터 형식을 지정 하는 템플릿 매개 변수입니다.

*key*<br/>
해시 값을 계산할 키입니다.

### <a name="return-value"></a>반환 값

키의 해시 값입니다.

### <a name="remarks"></a>설명

이 함수는 [cmap:: RemoveKey](cmap-class.md#removekey) 에서 직접 호출 되며 [Cmap:: Lookup](cmap-class.md#lookup) 및 [cmap:: Operator &#91;&#93;](cmap-class.md#operator_at)에 의해 간접적으로 호출 됩니다.

기본 구현에서는 *키* 를 오른쪽으로 네 위치로 이동 하 여 해시 값을 만듭니다. 응용 프로그램에 적합 한 해시 값을 반환 하도록이 함수를 재정의 합니다.

### <a name="example"></a>예제

```cpp
template <> UINT AFXAPI HashKey(unsigned __int64 key)
{
   // Generate the hash value by XORing the lower 32 bits of the number
   // with the upper 32 bits
   return(UINT(key) ^ UINT(key >> 32));
}
```

### <a name="requirements"></a>요구 사항

  **헤더** afxtempl.h

## <a name="serializeelements"></a><a name="serializeelements"></a> SerializeElements

[CArray](carray-class.md), [CList](clist-class.md)및 [cmap](cmap-class.md) 은이 함수를 호출 하 여 요소를 serialize 합니다.

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>매개 변수

*TYPE*<br/>
요소의 형식을 지정 하는 템플릿 매개 변수입니다.

*ar*<br/>
보관 하거나 보관할 보관 개체입니다.

*pElements*<br/>
보관 되는 요소에 대 한 포인터입니다.

*nCount*<br/>
보관 되는 요소 수

### <a name="remarks"></a>설명

기본 구현은 비트 읽기 또는 쓰기를 수행 합니다.

이 도우미 함수 및 다른 도우미 함수를 구현 하는 방법에 대 한 자세한 내용은 컬렉션 [: Type-Safe 컬렉션을 만드는 방법](../how-to-make-a-type-safe-collection.md)을 참조 하세요.

### <a name="example"></a>예제

컬렉션 [Type-Safe 컬렉션을 만드는 방법](../how-to-make-a-type-safe-collection.md)문서에서 예제를 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxtempl.h

## <a name="see-also"></a>참고 항목

[매크로 및 전역](mfc-macros-and-globals.md)<br/>
[CMap 클래스](cmap-class.md)<br/>
[CList 클래스](clist-class.md)<br/>
[CArray 클래스](carray-class.md)
