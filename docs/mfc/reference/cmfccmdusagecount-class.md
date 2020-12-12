---
description: '자세한 정보: CMFCCmdUsageCount 클래스'
title: CMFCCmdUsageCount 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::AddCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::GetCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::HasEnoughInformation
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::IsFreqeuntlyUsedCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Reset
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Serialize
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::SetOptions
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
ms.openlocfilehash: 40d09e96672cafb022baab98787fe10b1258048b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327726"
---
# <a name="cmfccmdusagecount-class"></a>CMFCCmdUsageCount 클래스

사용자가 메뉴에서 항목을 선택 하는 경우와 같은 Windows 메시지의 사용 횟수를 추적 합니다.

## <a name="syntax"></a>구문

```
class CMFCCmdUsageCount : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|-|-|
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|기본 생성자입니다.|
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|-|-|
|[CMFCCmdUsageCount:: AddCmd](#addcmd)|지정 된 명령과 연결 된 카운터를 하나씩 늘립니다.|
|[CMFCCmdUsageCount:: GetCount](#getcount)|지정 된 명령 ID와 연결 된 사용 횟수를 검색 합니다.|
|[CMFCCmdUsageCount:: Hasenou징 정보](#hasenoughinformation)|이 개체가 추적 데이터의 최소 양을 수집 했는지 여부를 확인 합니다.|
|[CMFCCmdUsageCount:: IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|지정 된 명령이 자주 사용 되는지 여부를 확인 합니다.|
|[CMFCCmdUsageCount:: Reset](#reset)|모든 명령의 사용 횟수를 지웁니다.|
|[CMFCCmdUsageCount:: Serialize](#serialize)|보관 저장소에서이 개체를 읽거나 보관 파일에 기록 합니다. ( [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)를 재정의합니다.)|
|[CMFCCmdUsageCount:: SetOptions](#setoptions)|공유 클래스 데이터 멤버의 값을 설정 합니다 `CMFCCmdUsageCount` .|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|-|-|
|`m_CmdUsage`|`CMap`명령을 사용 횟수에 매핑하는 개체입니다.|
|`m_nMinUsagePercentage`|명령이 자주 사용 되는 최소 사용 백분율입니다.|
|`m_nStartCount`|이 개체가 추적 데이터의 최소 양을 수집 했는지 여부를 확인 하는 데 사용 되는 시작 카운터입니다.|
|`m_nTotalUsage`|모든 추적 된 명령의 수입니다.|

### <a name="remarks"></a>설명

`CMFCCmdUsageCount`클래스는 각 숫자 Windows 메시지 식별자를 32 비트 부호 없는 정수 카운터에 매핑합니다. `CMFCToolBar` 이 클래스를 사용 하 여 자주 사용 되는 도구 모음 항목을 표시 합니다. 에 대 한 자세한 내용은 `CMFCToolBar` [Cmfctoolbar 클래스](../../mfc/reference/cmfctoolbar-class.md)를 참조 하세요.

`CMFCCmdUsageCount`프로그램 실행 사이에 클래스 데이터를 유지할 수 있습니다. [Cmfccmdusagecount:: Serialize](#serialize) 메서드를 사용 하 여 클래스 멤버 데이터를 Serialize 하 고 [Cmfccmdusagecount:: SetOptions](#setoptions) 메서드를 사용 하 여 공유 멤버 데이터를 설정 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxcmdusagecount

## <a name="cmfccmdusagecountaddcmd"></a><a name="addcmd"></a> CMFCCmdUsageCount:: AddCmd

지정 된 명령과 연결 된 카운터를 하나씩 늘립니다.

```cpp
void AddCmd(UINT uiCmd);
```

### <a name="parameters"></a>매개 변수

*uiCmd*\
진행 증가 시킬 명령 카운터를 지정 합니다.

### <a name="remarks"></a>설명

이 메서드는 항목이 없는 경우 명령 개수의 맵 구조에 새 항목을 추가 `m_CmdUsage` 합니다.

이 메서드는 다음과 같은 경우에는 아무 작업도 수행 하지 않습니다.

- 도구 모음 프레임 워크는 사용자 지정 모드에 있습니다 ( [Cmfctoolbar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) 메서드는 0이 아닌 값을 반환).

- 명령은 하위 메뉴 또는 메뉴 구분 기호를 참조 합니다 ( *Uicmd* 는 0 또는-1과 같음).

- *Uicmd* 는 표준 명령 (global `IsStandardCommand` 함수는 0이 아닌 값을 반환)을 참조 합니다.

## <a name="cmfccmdusagecountgetcount"></a><a name="getcount"></a> CMFCCmdUsageCount:: GetCount

지정 된 명령 ID와 연결 된 사용 횟수를 검색 합니다.

```
UINT GetCount(UINT uiCmd) const;
```

### <a name="parameters"></a>매개 변수

*uiCmd*\
진행 검색할 명령 카운터의 ID입니다.

### <a name="return-value"></a>반환 값

지정 된 명령 ID와 연결 된 사용 횟수입니다.

## <a name="cmfccmdusagecounthasenoughinformation"></a><a name="hasenoughinformation"></a> CMFCCmdUsageCount:: Hasenou징 정보

이 개체가 추적 데이터의 최소 크기를 받았는지 여부를 확인 합니다.

```
BOOL HasEnoughInformation() const;
```

### <a name="return-value"></a>반환 값

이 개체가 추적 데이터의 최소 크기를 받은 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

모든 추적 된 명령의 총 개수가 `m_nTotalUsage` 초기 카운트 보다 크거나 같으면이 메서드는 0이 아닌 값을 반환 `m_nStartCount` 합니다. 기본적으로 프레임 워크는 초기 카운트 0을 설정 합니다. [Cmfccmdusagecount:: SetOptions](#setoptions) 메서드를 사용 하 여이 값을 재정의할 수 있습니다.

이 메서드는 [Cmfcmenubar:: IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) 에서 사용 가능한 모든 메뉴 명령을 표시할지 여부를 결정 하는 데 사용 됩니다.

## <a name="cmfccmdusagecountisfreqeuntlyusedcmd"></a><a name="isfreqeuntlyusedcmd"></a> CMFCCmdUsageCount:: IsFreqeuntlyUsedCmd

지정 된 명령이 자주 사용 되는지 여부를 확인 합니다.

```
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;
```

### <a name="parameters"></a>매개 변수

*uiCmd*\
진행 확인할 명령을 지정 합니다.

### <a name="return-value"></a>반환 값

명령이 자주 사용 되는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 전체 명령 사용법가 0 인 경우 0을 반환 `m_nTotalUsage` 합니다. 그렇지 않으면 지정 된 명령이 사용 되는 백분율이 최소 백분율, 보다 큰 경우이 메서드는 0이 아닌 값을 반환 합니다 `m_nMinUsagePercentage` . 기본적으로 프레임 워크는 최소 비율을 5로 설정 합니다. [Cmfccmdusagecount:: SetOptions](#setoptions) 메서드를 사용 하 여이 값을 재정의할 수 있습니다. 최소 백분율이 0 이면 지정 된 명령 수가 0 보다 큰 경우이 메서드는 0이 아닌 값을 반환 합니다.

[Cmfctoolbar:: IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) 는이 메서드를 사용 하 여 명령이 거의 사용 되지 않는지 여부를 확인 합니다.

## <a name="cmfccmdusagecountreset"></a><a name="reset"></a> CMFCCmdUsageCount:: Reset

모든 명령의 사용 횟수를 지웁니다.

```cpp
void Reset();
```

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 명령 수의 map 구조에서 모든 항목을 지우고, 및를 사용 하 여 `m_CmdUsage` 전체 명령 사용, 카운터를 0으로 다시 설정 합니다 `m_nTotalUsage` .

## <a name="cmfccmdusagecountserialize"></a><a name="serialize"></a> CMFCCmdUsageCount:: Serialize

보관 저장소에서이 개체를 읽거나 보관 파일에 기록 합니다.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>매개 변수

*방어력*\
진행 `CArchive` 또는에서 serialize 할 개체입니다.

### <a name="remarks"></a>설명

이 메서드는 명령 수의 map 구조, `m_CmdUsage` 및의 전체 명령 사용, `m_nTotalUsage` , 카운터를 지정 된 보관 파일에서 serialize 합니다.

Serialization 예제는 [serialization: 개체 직렬화](../../mfc/serialization-serializing-an-object.md)를 참조 하세요.

## <a name="cmfccmdusagecountsetoptions"></a><a name="setoptions"></a> CMFCCmdUsageCount:: SetOptions

공유 클래스 데이터 멤버의 값을 설정 합니다 `CMFCCmdUsageCount` .

```
static BOOL __stdcall SetOptions(
    UINT nStartCount,
    UINT nMinUsagePercentage);
```

### <a name="parameters"></a>매개 변수

*nStartCount*\
진행 모든 추적 된 명령의 새 초기 개수입니다.

*nMinUsagePercentage*\
진행 새 최소 사용 백분율입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 TRUE이 고, *nMinUsagePercentage* 매개 변수가 100 보다 크거나 같으면 FALSE입니다.

### <a name="remarks"></a>설명

이 메서드는 공유 `CMFCCmdUsageCount` 클래스 데이터 멤버 `m_nStartCount` 및 `m_nMinUsagePercentage` 를 각각 *Nstartcount* 및 *nMinUsagePercentage* 로 설정 합니다. `m_nStartCount` 이 개체가 추적 데이터의 최소 양을 수집 했는지 여부를 확인 하기 위해 [Cmfccmdusagecount:: HasEnoughInformation](#hasenoughinformation) 메서드에 사용 됩니다. `m_nMinUsagePercentage` 는 [Cmfccmdusagecount:: IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) 메서드에서 지정 된 명령이 자주 사용 되는지 여부를 확인 하는 데 사용 됩니다.

디버그 빌드에서 *nMinUsagePercentage* 매개 변수가 100 보다 크거나 같으면이 메서드는 어설션 오류를 생성 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)
