---
title: "CMFCCmdUsageCount 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0db24894777170d2860ba8d1639fd44e3893732a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="cmfccmdusagecount-class"></a>CMFCCmdUsageCount 클래스
Windows 메시지를 사용자가 메뉴에서 항목을 선택 하는 경우 등의 사용 횟수를 추적 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CMFCCmdUsageCount : public CObject  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|||  
|-|-|  
|이름|설명|  
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|기본 생성자입니다.|  
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|소멸자|  
  
### <a name="public-methods"></a>Public 메서드  
  
|||  
|-|-|  
|이름|설명|  
|[CMFCCmdUsageCount::AddCmd](#addcmd)|지정된 된 명령과와 연결 된 카운터를 1 씩 증가 합니다.|  
|[CMFCCmdUsageCount::GetCount](#getcount)|지정한 명령 ID와 연결 된 사용 횟수를 검색 합니다.|  
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|이 개체가 최소한의 추적 데이터 수집 여부를 결정 합니다.|  
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|지정된 된 명령을 자주 사용 되는지 여부를 결정 합니다.|  
|[CMFCCmdUsageCount::Reset](#reset)|모든 명령의 사용 횟수를 지웁니다.|  
|[CMFCCmdUsageCount::Serialize](#serialize)|보관 파일에서이 개체를 읽거나 보관 파일에 씁니다. ( [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)를 재정의합니다.)|  
|[CMFCCmdUsageCount::SetOptions](#setoptions)|설정 값의 공유 `CMFCCmdUsageCount` 클래스 데이터 멤버입니다.|  
  
### <a name="data-members"></a>데이터 멤버  
  
|||  
|-|-|  
|name|설명|  
|`m_CmdUsage`|A `CMap` 명령을 해당 사용 횟수에 매핑되는 개체입니다.|  
|`m_nMinUsagePercentage`|자주 사용 하는 명령에 대 한 최소 사용량 비율입니다.|  
|`m_nStartCount`|이 개체에 최소한의 추적 데이터를 수집 하는지 여부를 결정 하는 데 사용 되는 시작 카운터입니다.|  
|`m_nTotalUsage`|추적 된 모든 명령의 수입니다.|  
  
### <a name="remarks"></a>설명  
 `CMFCCmdUsageCount` 클래스 32 비트 부호 없는 정수 카운터에 각 숫자 Windows 메시지 식별자를 매핑합니다. `CMFCToolBar`이 클래스를 사용 하 여 자주 사용 하는 도구 모음 항목을 표시 합니다. 에 대 한 자세한 내용은 `CMFCToolBar`, 참조 [CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)합니다.  
  
 지속할 수 있습니다 `CMFCCmdUsageCount` 프로그램의 실행 간에 데이터 클래스입니다. 사용 하 여는 [CMFCCmdUsageCount::Serialize](#serialize) 클래스 멤버 데이터를 직렬화 하는 메서드 및 [CMFCCmdUsageCount::SetOptions](#setoptions) 메서드 공유 멤버 데이터를 설정 합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxcmdusagecount.h  
  
##  <a name="addcmd"></a>CMFCCmdUsageCount::AddCmd  
 지정된 된 명령과와 연결 된 카운터를 1 씩 증가 합니다.  
  
```  
void AddCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>매개 변수  
  
|||  
|-|-|  
|매개 변수|설명|  
|[in] `uiCmd`|명령 카운터를 증가를 지정 합니다.|  
  
### <a name="remarks"></a>설명  
 이 메서드는 명령 수의 맵 구조에 새 항목을 추가 `m_CmdUsage`항목이 이미 존재 하지 않는 경우.  
  
 이 메서드는 다음과 같은 경우에 아무 것도 수행합니다.  
  
-   사용자 지정 모드에 있는 도구 모음 프레임 워크입니다 (의 [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) 0이 아닌 값을 반환 하는 메서드).  
  
-   명령 참조는 하위 메뉴 또는 메뉴 구분 기호 ( `uiCmd` equals 0 또는-1).  
  
- `uiCmd`표준 명령 참조 (전역 `IsStandardCommand` 함수가 0이 아닌 값을 반환).  
  
##  <a name="getcount"></a>CMFCCmdUsageCount::GetCount  
 지정한 명령 ID와 연결 된 사용 횟수를 검색 합니다.  
  
```  
UINT GetCount(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>매개 변수  
  
|||  
|-|-|  
|매개 변수|설명|  
|[in] `uiCmd`|검색할 명령 카운터의 ID입니다.|  
  
### <a name="return-value"></a>반환 값  
 지정한 명령 ID와 연결 된 사용 횟수  
  
##  <a name="hasenoughinformation"></a>CMFCCmdUsageCount::HasEnoughInformation  
 이 개체 추적 데이터의 최소 크기를 받았는지 확인 합니다.  
  
```  
BOOL HasEnoughInformation() const;  
```  
  
### <a name="return-value"></a>반환 값  
 이 개체에서 추적 데이터;의 최소 크기를 받는 경우 0이 아닌 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 경우 0이 아닌 값을 반환 총 개수 `m_nTotalUsage`, 초기 카운트 크거나은 추적 된 모든 명령의 `m_nStartCount`합니다. 기본적으로 프레임 워크는 초기 카운트 0을 설정합니다. 사용 하 여이 값을 재정의할 수는 [CMFCCmdUsageCount::SetOptions](#setoptions) 메서드.  
  
 이 메서드를 사용 하 여 [CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) 사용 가능한 메뉴 명령을 모두 표시 여부를 결정 합니다.  
  
##  <a name="isfreqeuntlyusedcmd"></a>CMFCCmdUsageCount::IsFreqeuntlyUsedCmd  
 지정된 된 명령을 자주 사용 되는지 여부를 결정 합니다.  
  
```  
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>매개 변수  
  
|||  
|-|-|  
|매개 변수|설명|  
|[in] `uiCmd`|확인 하려면 명령을 지정 합니다.|  
  
### <a name="return-value"></a>반환 값  
 이 명령은 자주 사용 되는; 경우 0이 아닌 그렇지 않으면 0입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 경우 0을 반환 총 명령 사용법 `m_nTotalUsage`은 0입니다. 그렇지 않으면이 메서드는 지정 된 명령이 사용 되는 백분율의 최소 비율 보다 큰 경우 0이 아닌 반환 `m_nMinUsagePercentage`합니다. 기본적으로 프레임 워크는 최소 비율을 5로 설정합니다. 사용 하 여이 값을 재정의할 수는 [CMFCCmdUsageCount::SetOptions](#setoptions) 메서드. 최소 백분율 0 인 경우이 메서드는 지정 된 명령 수는 0 보다 큰 경우 0이 아닌 값을 반환 합니다.  
  
 [CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) 이 메서드를 사용 하 여 명령을 거의 사용 여부를 결정 합니다.  
  
##  <a name="reset"></a>CMFCCmdUsageCount::Reset  
 모든 명령의 사용 횟수를 지웁니다.  
  
```  
void Reset();
```  
  
### <a name="remarks"></a>설명  
 명령 수의 맵 구조에서 모든 항목을 삭제 하려면이 메서드를 호출 `m_CmdUsage`, 총 명령 사용법을 재설정할 수 `m_nTotalUsage`카운터를 0으로, 합니다.  
  
##  <a name="serialize"></a>CMFCCmdUsageCount::Serialize  
 이 개체는 보관 파일에서 읽거나 보관 파일에 씁니다.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>매개 변수  
  
|||  
|-|-|  
|매개 변수|설명|  
|[in] `ar`|A `CArchive` 를 원본 또는 대상 serialize 할 개체입니다.|  
  
### <a name="remarks"></a>설명  
 이 메서드는 직렬화 명령 수의 맵 구조 `m_CmdUsage`, 및 총 명령 사용법 `m_nTotalUsage`, 카운터에 있는 지정 된 보관 합니다.  
  
 Serialization 예제를 보려면 [Serialization: 개체를 직렬화](../../mfc/serialization-serializing-an-object.md)합니다.  
  
##  <a name="setoptions"></a>CMFCCmdUsageCount::SetOptions  
 설정 값의 공유 `CMFCCmdUsageCount` 클래스 데이터 멤버입니다.  
  
```  
static BOOL __stdcall SetOptions(
    UINT nStartCount,  
    UINT nMinUsagePercentage);
```  
  
### <a name="parameters"></a>매개 변수  
  
|||  
|-|-|  
|매개 변수|설명|  
|[in] `nStartCount`|새 초기 추적 된 모든 명령 수입니다.|  
|[in] `nMinUsagePercentage`|새 최소 사용량 백분율입니다.|  
  
### <a name="return-value"></a>반환 값  
 `TRUE`메서드가 성공 하면 `FALSE` 경우는 `nMinUsagePercentage` 매개 변수는 100 보다 크거나 같은 경우입니다.  
  
### <a name="remarks"></a>설명  
 이 메서드는 공유 설정 `CMFCCmdUsageCount` 클래스 데이터 멤버 `m_nStartCount` 및 `m_nMinUsagePercentage` 를 `nStartCount` 및 `nMinUsagePercentage`각각. `m_nStartCount`사용 되는 [CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation) 이 개체가 최소한의 추적 데이터 수집 여부를 결정 하는 메서드. `m_nMinUsagePercentage`사용 되는 [CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) 메서드를 지정된 된 명령 자주 사용 되 고 있는지 확인 합니다.  
  
 디버그 빌드에서이 메서드는 어설션 오류 경우 생성 된 `nMinUsagePercentage` 매개 변수는 100 보다 크거나 같은 경우입니다.  
  
## <a name="see-also"></a>참고 항목  
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [클래스](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 클래스](../../mfc/reference/cmfctoolbar-class.md)
