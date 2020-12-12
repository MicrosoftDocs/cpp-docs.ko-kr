---
description: '자세히 알아보기: CManualAccessor 클래스'
title: CManualAccessor 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- CManualAccessor.AddBindEntry
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
- ATL::CManualAccessor::CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
- ATL::CManualAccessor::CreateParameterAccessor
- ATL.CManualAccessor.CreateParameterAccessor
- CManualAccessor.CreateParameterAccessor
- CreateParameterAccessor
- CManualAccessor::CreateParameterAccessor
helpviewer_keywords:
- CManualAccessor class
- AddBindEntry method
- AddParameterEntry method
- CreateAccessor method
- CreateParameterAccessor method
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
ms.openlocfilehash: 3d625a9a02431445cc1505c6a3f7e9673a04201d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170557"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor 클래스

고급 사용을 위해 디자인 된 접근자 형식을 나타냅니다.

## <a name="syntax"></a>Syntax

```cpp
class CManualAccessor : public CAccessorBase
```

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[AddBindEntry](#addbindentry)|출력 열에 바인드 항목을 추가 합니다.|
|[AddParameterEntry](#addparameterentry)|매개 변수 접근자에 매개 변수 항목을 추가 합니다.|
|[CreateAccessor](#createaccessor)|열 바인딩 구조에 메모리를 할당 하 고 열 데이터 멤버를 초기화 합니다.|
|[CreateParameterAccessor](#createparameteraccessor)|매개 변수 바인딩 구조에 메모리를 할당 하 고 매개 변수 데이터 멤버를 초기화 합니다.|

## <a name="remarks"></a>설명

를 사용 하 여 `CManualAccessor` 런타임 함수 호출을 통해 매개 변수 및 출력 열 바인딩을 지정할 수 있습니다.

## <a name="cmanualaccessoraddbindentry"></a><a name="addbindentry"></a> CManualAccessor:: AddBindEntry

출력 열에 바인드 항목을 추가 합니다.

### <a name="syntax"></a>구문

```cpp
void AddBindEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL) throw ();
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 를 참조 하세요.

*nOrdinal*<br/>
진행 열 번호입니다.

*wType*<br/>
진행 데이터 형식입니다.

*nColumnSize*<br/>
진행 열 크기 (바이트)입니다.

*pData*<br/>
진행 버퍼에 저장 된 열 데이터에 대 한 포인터입니다.

*pLength*<br/>
진행 필요한 경우 필드 길이에 대 한 포인터입니다.

*pStatus*<br/>
진행 필요한 경우 열 상태에 바인딩될 변수에 대 한 포인터입니다.

### <a name="remarks"></a>설명

이 함수를 사용 하려면 먼저 [Createaccessor](#createaccessor)를 호출 해야 합니다. 에 지정 된 열 개수 보다 많은 항목을 추가할 수 없습니다 `CreateAccessor` .

## <a name="cmanualaccessoraddparameterentry"></a><a name="addparameterentry"></a> CManualAccessor:: AddParameterEntry

매개 변수 엔트리를 매개 변수 항목 구조에 추가 합니다.

### <a name="syntax"></a>구문

```cpp
void AddParameterEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL,
   DBPARAMIO eParamIO = DBPARAMIO_INPUT) throw ();
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 를 참조 하세요.

*nOrdinal*<br/>
진행 매개 변수 번호입니다.

*wType*<br/>
진행 데이터 형식입니다.

*nColumnSize*<br/>
진행 열 크기 (바이트)입니다.

*pData*<br/>
진행 버퍼에 저장 된 열 데이터에 대 한 포인터입니다.

*pLength*<br/>
진행 필요한 경우 필드 길이에 대 한 포인터입니다.

*pStatus*<br/>
진행 필요한 경우 열 상태에 바인딩될 변수에 대 한 포인터입니다.

*eParamIO*<br/>
진행 바인딩과 연결 된 매개 변수가 입력, 입/출력 또는 출력 매개 변수 인지 여부를 지정 합니다.

### <a name="remarks"></a>설명

이 함수를 사용 하려면 먼저 [Createparameteraccessor](#createparameteraccessor)를 호출 해야 합니다.

## <a name="cmanualaccessorcreateaccessor"></a><a name="createaccessor"></a> CManualAccessor:: CreateAccessor

열 바인딩 구조에 메모리를 할당 하 고 열 데이터 멤버를 초기화 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT CreateAccessor(int nBindEntries,
  void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>매개 변수

*nBindEntries*<br/>
진행 열 수입니다. 이 수는 [CManualAccessor:: AddBindEntry](#addbindentry) 함수에 대 한 호출 수와 일치 해야 합니다.

*pBuffer*<br/>
진행 출력 열이 저장 되는 버퍼에 대 한 포인터입니다.

*nBufferSize*<br/>
진행 버퍼의 크기 (바이트)입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

함수를 호출 하기 전에이 함수를 호출 `CManualAccessor::AddBindEntry` 합니다.

## <a name="cmanualaccessorcreateparameteraccessor"></a><a name="createparameteraccessor"></a> CManualAccessor:: CreateParameterAccessor

매개 변수 바인딩 구조에 메모리를 할당 하 고 매개 변수 데이터 멤버를 초기화 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT CreateParameterAccessor(int nBindEntries,
   void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>매개 변수

*nBindEntries*<br/>
진행 열 수입니다.

*pBuffer*<br/>
진행 입력 열이 저장 되는 버퍼에 대 한 포인터입니다.

*nBufferSize*<br/>
진행 버퍼의 크기 (바이트)입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

[Addparameterentry](#addparameterentry)를 호출 하기 전에이 함수를 호출 해야 합니다.

## <a name="see-also"></a>참고 항목

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 클래스](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor 클래스](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor 클래스](../../data/oledb/cdynamicparameteraccessor-class.md)
